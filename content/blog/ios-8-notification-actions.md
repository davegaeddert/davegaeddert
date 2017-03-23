---
date: 2014-09-16T00:00:00-00:00
draft: false
title: iOS 8 Notification Actions
---

[Skip to the code](#tutorial)

I am finally getting around to adding some of the new iOS 8 features to [Beluga](https://itunes.apple.com/us/app/beluga-shared-tasks./id836830314?mt=8). For whatever reason, I haven't been able to find any documentation on the new ability to add actions to notifications:
![iOS 8 Notification](/img/blog/Screen-Shot-2014-09-16-at-5-28-05-PM.png)

Maybe I didn't look hard enough, who knows. Anyway I decided to make quick demo of how to do this based on the [WWDC 2014 session video "What's New in iOS Notifications"](https://developer.apple.com/videos/wwdc/2014/).

---

# <span id="tutorial"></span>Tutorial
All of the following can be found in a ready-to-go Xcode project on [GitHub](https://github.com/davegaeddert/tut-ios8-notifications), I know I always just jump there...

## Create a notification action
```language-objectivec
UIMutableUserNotificationAction *acceptAction = [[UIMutableUserNotificationAction alloc] init];
acceptAction.identifier = @"ACCEPT_IDENTIFIER";
acceptAction.title = @"Accept";

// Given seconds, not minutes, to run in the background
acceptAction.activationMode = UIUserNotificationActivationModeBackground;

// If YES the action is red
acceptAction.destructive = NO;

// If YES requires passcode, but does not unlock the device
acceptAction.authenticationRequired = NO;
```
## Create a notification action category
This allows you to group notifications, so for a 'Mail' category your might have 'Reply', 'Delete', and 'Archive'. Right now we're creating an 'Invite' category, with our one action of 'Accept'.
```language-objectivec
UIMutableUserNotificationCategory *inviteCategory = [[UIMutableUserNotificationCategory alloc] init];
inviteCategory.identifier = @"INVITE_CATEGORY";

// You can define up to 4 actions in the 'default' context
// On the lock screen, only the first two will be shown
// If you want to specify which two actions get used on the lockscreen, use UIUserNotificationActionContextMinimal
[inviteCategory setActions:@[acceptAction] forContext:UIUserNotificationActionContextDefault];

// These would get set on the lock screen specifically
// [inviteCategory setActions:@[declineAction, acceptAction] forContext:UIUserNotificationActionContextMinimal];
```

## Now register for those notifications
```language-objectivec
UIUserNotificationType types = (UIUserNotificationTypeAlert | UIUserNotificationTypeBadge | UIUserNotificationTypeSound);

NSSet *categories = [NSSet setWithObjects:inviteCategory, nil];
UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:categories];

[[UIApplication sharedApplication] registerUserNotificationSettings:settings];
```

When registering notification settings, this callback will be called:
```language-objectivec
- (void)application:(UIApplication *)application didRegisterUserNotificationSettings:(UIUserNotificationSettings *)notificationSettings {

    // Get the notifications types that have been allowed, do whatever with them
    UIUserNotificationType allowedTypes = [notificationSettings types];

    NSLog(@"Registered for notification types: %u", allowedTypes);

    // You can get this setting anywhere in your app by using this:
    // UIUserNotificationSettings *currentSettings = [[UIApplication sharedApplication] currentUserNotificationSettings];
}
```

## Send yourself a local notification
![](/img/blog/Screen-Shot-2014-09-16-at-6-02-50-PM.png)
![](/img/blog/Screen-Shot-2014-09-16-at-6-04-01-PM.png)
```language-objectivec
UILocalNotification *notification = [[UILocalNotification alloc] init];
notification.alertBody = @"Hey!";
notification.category = @"INVITE_CATEGORY";

// The notification will arrive in 5 seconds, leave the app or lock your device to see
// it since we aren't doing anything to handle notifications that arrive while the app is open
notification.fireDate = [NSDate dateWithTimeIntervalSinceNow:5];

[[UIApplication sharedApplication] scheduleLocalNotification:notification];
```

## Handle the action

Sweet! Now you should have received the notification (note: you need to be anywhere but the app to see the notification with its actions: home screen, lock screen, another app, etc.), if you choose the 'Accept' action we created then this callback will be called so you can deal with it.

```language-objectivec
- (void)application:(UIApplication *)application handleActionWithIdentifier:(NSString *)identifier forLocalNotification:(UILocalNotification *)notification completionHandler:(void (^)())completionHandler {

    if ([identifier isEqualToString:@"ACCEPT_IDENTIFIER"]) {
        // handle it
        NSLog(@"Invite accepted! Handle that somehow...");
    }

    // Call this when you're finished
    completionHandler();
}
```

[View the full code on Github (look in AppDelegate.m)](https://github.com/davegaeddert/tut-ios8-notifications)
