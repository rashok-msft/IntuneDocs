---
# required metadata
title: iOS device settings in Microsoft Intune - Azure | Microsoft Docs
titleSuffix:
description: Add, configure, or create settings on iOS devices to restrict features, including setting password requirements, control the locked screen, use built-in apps, add restricted or approved apps, handle bluetooth devices, connect to the cloud for backup and storage, enable kiosk mode, add domains, and control how users interact with the Safari web browser in Microsoft Intune.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology:

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
---

# iOS and iPadOS device settings to allow or restrict features using Intune

This article lists and describes the different settings you can control on iOS and iPadOS devices. As part of your mobile device management (MDM) solution, use these settings to allow or disable features, set password rules, allow or restrict specific apps, and more.

These settings are added to a device configuration profile in Intune, and then assigned or deployed to your iOS devices.

> [!TIP]
> These settings use Apple's MDM settings. For more information on these settings, see [Apple's mobile device management settings](https://support.apple.com/guide/mdm/welcome/web) (opens Apple's web site).

## Before you begin

[Create a device restrictions configuration profile](../device-restrictions-configure.md).

> [!NOTE]
> These settings apply to different enrollment types, with some settings applying to all enrollment options. For more information on the different enrollment types, see [iOS enrollment](../ios-enroll.md).

## General

### Settings apply to: All enrollment types

- **Share usage data**: Choose **Block** to prevent the device from sending diagnostic and usage data to Apple. **Not configured** (default) allows this data to be sent.

- **Screen capture**: Choose **Block** to prevent screenshots or screen captures on the device. In iOS 9.0 and newer, it also blocks screen recordings. **Not configured** (default) lets the user capture the screen contents as an image or as a video.

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Untrusted TLS certificates**: Choose **Block** to prevent untrusted Transport Layer Security (TLS) certificates on the device. **Not configured** (default) allows TLS certificates.
- **Block over-the-air PKI updates**: **Block** prevents your users from receiving software updates unless the device is connected to a computer. **Not configured** (default): allows a device to receive software updates without being connected to a computer.
- **Limit ad tracking**: Choose **Limit** to disable the device advertising identifier. **Not configured** (default) keeps it enabled.

### Settings apply to: Automated device enrollment (supervised)

- **Diagnostics submission settings modification**: **Block** prevents the user from changing the diagnostic submission and app analytics settings in **Diagnostics and Usage** (device Settings). **Not configured** (default) allows the user to change these device settings.

  To use this setting, set the **Share usage data** setting to **Block**.

  This feature applies to:  
  - iOS 9.3.2 and newer

- **Remote screen observation by Classroom app**: Choose **Block** to prevent the Classroom app from remotely viewing the screen on the device. **Not configured** (default) allows the Apple Classroom app to view the screen.

  To use this setting, set the **Screen capture** setting to **Block**.

  This feature applies to:  
  - iOS 9.3 and newer

- **Unprompted screen observation by Classroom app**: If set to **Allow**, teachers can silently observe the screen of students iOS devices using the Classroom app without the students' knowledge. Student devices enrolled in a class using the Classroom app automatically give permission to that course’s teacher. **Not configured** (default) prevents this feature.

  To use this setting, set the **Screen capture** setting to **Block**.

- **Enterprise app trust**: Choose **Block** to remove the **Trust Enterprise Developer** button in Settings > General > Profiles & Device Management on the device. **Not configured** (default) lets the user choose to trust apps that aren't downloaded from the app store.
- **Account modification**: When set to **Block**, the user can't update the device-specific settings from the iOS settings app. For example, the user can't create new device accounts, or change the user name or password. **Not configured** (default) allows users to change these settings.

  This feature also applies to settings accessible from the iOS settings app, such as Mail, Contacts, Calendar, Twitter, and more. This feature doesn't apply to apps with account settings that aren't configurable from the iOS settings app, such as the Microsoft Outlook app.

- **Screen time**: Choose **Block** to prevent users from setting their own restrictions in Screen Time (device settings). **Not configured** allows the user to configure device restrictions (such as parental controls or content, and privacy restrictions) on the device.

  This setting was renamed from **Enabling restrictions in the device settings**. Impact of this change:  
  
  - iOS 11.4.1 and earlier: **Block** prevents end users from setting their own restrictions in the device settings. The behavior is the same; and there are no changes for end users.
  - iOS 12.0 and newer: **Block** prevents end users from setting their own **Screen Time** in the device settings (Settings > General > Screen Time), including content and privacy restrictions. Devices upgraded to iOS 12.0 won't see the restrictions tab in the device settings anymore (Settings > General > Device Management > Management Profile > Restrictions). These settings are in **Screen Time**.
  
- **Use of the erase all content and settings option on the device**: Choose **Block** so users can't use the erase all content and settings option on the device. **Not configured** (default) gives users access to these settings.
- **Device name modification**: Choose **Block** so the device name can't be changed. **Not configured** (default) allows the user to change the name of the device.
- **Notification settings modification**: Choose **Block** so the notification settings can't be changed. **Not configured** (default) allows the user to change the device notification settings.
- **Wallpaper modification**: **Block** prevents the wallpaper from being changed. **Not configured** (default) allows the user to change the wallpaper on the device.
- **Enterprise app trust settings modification**: **Block** prevents the user from changing the enterprise app trust settings on supervised devices. **Not configured** (default) allows the user to trust apps that aren't downloaded from the app store.
- **Configuration profile changes**: **Block** prevents configuration profile changes on the device. **Not configured** (default) allows the user to install configuration profiles.
- **Activation Lock**: Choose **Allow** to enable Activation Lock on supervised iOS devices. Activation Lock makes it harder for a lost or stolen device to be reactivated.
- **Block app removal**: Choose **Block** to prevent users from removing apps. **Not configured** (default) allows users to remove apps from the device.
- **Allow USB accessories while device is locked**: **Allow** lets USB accessories exchange data with a device that's been locked for over an hour. **Not configured** (default) doesn't update USB Restricted mode on the device, and USB accessories will be blocked from transferring data from the device if locked for over an hour.
- **Force automatic date and time**: **Require** forces supervised devices to set the Date & Time automatically. The device's time zone is updated when the device has cellular connections or has Wi-Fi with location services enabled.
- **Require students to request permission to leave Classroom course**: **Require** forces students enrolled in an unmanaged course using the Classroom app to request permission from the teacher to leave the course. **Not configured** (default) doesn't force the student to ask for permission.

  This feature applies to:  
  - iOS 11.3 and newer

- **Allow Classroom to lock to an app and lock the device without prompting**: **Enable** allows teacher to lock apps or lock the device using the Classroom app without prompting the student. Locking apps means the device can only access teacher specified apps. **Not configured** (default) prevents teachers from locking apps or devices using the Classroom app without prompting the student.

  This feature applies to:  
  - iOS 11.0 and newer

- **Automatically join Classroom classes without prompting**: **Enable** automatically allows students to join a class that is in the Classroom app without prompting the teacher. **Not configured** (default) prompts the teacher that students want to join a class that is in the Classroom app.

  This feature applies to:  
  - iOS 11.0 and newer

- **Block VPN creation**: **Block** prevents users from creating VPN configuration settings. **Not configured** (default) lets users create VPNs on the device.
- **Modifying eSIM settings**: **Block** prevents users from removing or adding a cellular plan to the eSIM on the device. **Not configured** (default) allows users to change these settings.

  This feature applies to:  
  - iOS 12.1 and newer

- **Defer software updates**: When set to **Not configured** (default), software updates are shown on the device as Apple releases them. For example, if an iOS update gets released by Apple on a specific date, then that update naturally shows up on the device around the release date.

  **Enable** allows you to delay when software updates are shown on devices, from 0-90 days. This setting doesn't control when updates are or aren't installed. 

  - **Delay visibility of software updates**: Enter a value from 0-90 days. When the delay expires, users get a notification to update to the earliest version of the OS available when the delay was triggered.

    For example, if iOS 12.a is available on **January 1**, and **Delay visibility** is set to **5 days**, then iOS 12.a isn't shown as an available update on end user devices. On the **sixth day** following the release, that update is available, and end users can install it.

    This setting applies to:  
    - iOS 11.3 and newer

## Password

### Settings apply to: All enrollment types

- **Password**: **Require** the end user to enter a password to access the device. **Not configured** (default) allows users to access the device without entering a password.

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

> [!IMPORTANT]
> On user-enrolled devices, if you configure any password setting, then the **Simple passwords** settings is automatically set to **Block**, and a 6 digit PIN is enforced.
>
> For example, you configure the **Password expiration** setting, and push this policy to user-enrolled devices. On the devices, the following happens:
>
> - The **Password expiration** setting is ignored.
> - Simple passwords, such as `1111` or `1234`, aren't allowed.
> - A 6 digit pin is enforced.

- **Simple passwords**: Choose **Block** to require more complex passwords. **Not configured** allows simple passwords, such as `0000` and `1234`.

- **Required password type**: Choose the type of password your organization require. Your options:
  - **Device default**
  - **Numeric**
  - **Alphanumeric**
- **Number of non-alphanumeric characters in password**: Enter the number of symbol characters, such as `#` or `@`, that must be included in the password.

- **Minimum password length**: Enter the minimum length a user must enter, between 4 and 14 characters. On user enrolled devices, enter a length between 4 and 6 characters.
  
  > [!NOTE]
  > For devices that are user enrolled, users can set a PIN greater than 6 digits. But, no more than 6 digits are enforced on the device. For example, an administrator sets the minimum length to `8`. On user-enrolled devices, users are only required to set a 6 digit PIN. Intune doesn't force a PIN greater than 6 digits on user-enrolled devices.

- **Number of sign-in failures before wiping device**: Enter the number of failed sign-ins to allow before the device is wiped (between 4-11).
  
  iOS has built-in security that can impact this setting. For example, iOS may delay triggering the policy depending on the number of sign in failures. It may also consider repeatedly entering the same passcode as one attempt. Apple's [iOS security guide](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) (opens Apple's web site) is a good resource, and provides more specific details on passcodes.
  
- **Maximum minutes after screen lock before password is required**<sup>1</sup>: Enter how long the device stays idle before the user must reenter their password. If the time you enter is longer than what's currently set on the device, then the device ignores the time you enter. Supported on iOS 8.0 and newer devices.

- **Maximum minutes of inactivity until screen locks**<sup>1</sup>: Enter the maximum number of minutes of inactivity allowed on the device until the screen locks.

  **iOS options**:  

  - **Not configured** (Default): Intune doesn't touch this setting.
  - **Immediately**: Screen locks after 30 seconds of inactivity.
  - **1**: Screen locks after 1 minute of inactivity.
  - **2**: Screen locks after 2 minutes of inactivity.
  - **3**: Screen locks after 3 minutes of inactivity.
  - **4**: Screen locks after 4 minutes of inactivity.
  - **5**: Screen locks after 5 minutes of inactivity.
    
  **iPadOS options**:  

  - **Not configured** (Default): Intune doesn't touch this setting.
  - **Immediately**: Screen locks after 2 minutes of inactivity.
  - **2**: Screen locks after 2 minutes of inactivity.
  - **5**: Screen locks after 5 minutes of inactivity.
  - **10**: Screen locks after 10 minutes of inactivity.
  - **15**: Screen locks after 15 minutes of inactivity.

  If a value doesn't apply to iOS or iPadOS, then Apple uses the closest *lowest* value. For example, if you enter `4` minutes, then iPadOS devices use `2` minutes. If you enter `10` minutes, then iOS devices use `5` minutes. This is an Apple limitation.
  
  > [!NOTE]
  > The Intune UI for this setting doesn't separate the iOS and iPadOS supported values. The UI might be updated in a future release.

- **Password expiration (days)**: Enter the number of days before the device password must be changed.
- **Prevent reuse of previous passwords**: Enter the number of new passwords that must be used until an old one can be reused.
- **Touch ID and Face ID unlock**: Choose **Block** to prevent using a fingerprint or face to unlock the device. **Not configured** allows the user to unlock the device using these methods.

  Blocking this setting also prevents using FaceID authentication to unlock the device.

  Face ID applies to:  
  - iOS 11.0 and newer

### Settings apply to: Automated device enrollment (supervised)

- **Passcode modification**: Choose **Block** to stop the passcode from being changed, added, or removed. Changes to passcode restrictions are ignored on supervised devices after blocking this feature. **Not configured** (default) allows passcodes to be added, changed, or removed.

  - **Touch ID and Face ID modification**: **Block** stops the user from changing, adding, or removing TouchID fingerprints and Face ID. **Not configured** (default) allows the user to update the TouchID fingerprints and Face ID on the device.

    Blocking this setting also stops the user from changing, adding, or removing FaceID authentication.

    Face ID applies to:  
    - iOS 11.0 and newer

- **Block password AutoFill**: Choose **Block** to prevent using the AutoFill Passwords feature on iOS. Choosing **Block** also has the following impact:

  - Users aren't prompted to use a saved password in Safari or in any apps.
  - Automatic Strong Passwords are disabled, and strong passwords aren't suggested to users.

  **Not configured** (default) allows these features.

- **Block password proximity requests**: Choose **Block** so a user’s device doesn't request passwords from nearby devices. **Not configured** (default) allows these password requests.
- **Block password sharing**: **Block** prevents sharing passwords between devices using AirDrop. **Not configured** (default) allows passwords to be shared.
- **Require Touch ID or Face ID authentication for password or credit card information AutoFill**: When set to **Require**, users must authenticate using TouchID or FaceID before passwords or credit card information can be auto filled in Safari and other apps. **Not configured** (default) allows users to control this feature in the device settings.

  This feature applies to:  
  - iOS 11.0 and newer
  
<sup>1</sup>When you configure the **Maximum minutes of inactivity until screen locks** and **Maximum minutes after screen lock before password is required** settings, they're applied in sequence. For example, if you set the value for both settings to **5** minutes, the screen turns off automatically after five minutes, and the device is locked after an additional five minutes. However, if the user turns off the screen manually, the second setting is immediately applied. In the same example, after the user turns off the screen, the device locks five minutes later.

## Locked Screen Experience

### Settings apply to: All enrollment types

- **Control Center access while device locked**: Choose **Block** to prevent access to the Control Center app while device is locked. **Not configured** (default) allows users access to the Control Center app when the device is locked.
- **Notifications while device locked**: **Block** prevents access to notifications when the device is locked. **Not configured** (default) allows the user to access the notifications without unlocking the device.
- **Today view while device locked**: **Block** prevents access to the Today view when the device is locked. **Not configured** (default) allows the user to see the Today view when the device is locked.

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Wallet notifications while device locked**: **Block** prevents access to the Wallet app when the device is locked. **Not configured** (default) allows the user to access the Wallet app while the device is locked.

## App Store, Doc Viewing, Gaming

### Settings apply to: All enrollment types

- **Viewing corporate documents in unmanaged apps**: **Block** prevents viewing corporate documents in unmanaged apps. **Not configured** (default) allows corporate documents to be viewed in any app. For example, you want to prevent users from saving files from the OneDrive app to Dropbox. Configure this setting as **Block**. After the device receives the policy (for example, after a restart), it no longer allows saving.


  > [!NOTE]
  > When this setting is blocked, third party keyboards installed from the App Store are also blocked.

  - **Allow unmanaged apps to read from managed contacts accounts**: When set to **Allow**, unmanaged apps, such as the built-in iOS Contacts app, can read and access contact information from managed apps, including the Outlook mobile app. **Not configured** (default) prevents reading, including removing duplicates, from the built-in Contacts app on the device.  
  
    This setting allows or prevents reading contact information. It doesn't control syncing contacts between the apps.
  
    To use this setting, set the **Viewing corporate documents in unmanaged apps** setting to **Block**.

  For more information about these two settings, and their impact on Outlook for iOS contact export synchronization, see [Support Tip: Use Intune custom profile settings with the iOS Native Contacts App](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **Treat AirDrop as an unmanaged destination**: **Require** forces AirDrop to be considered an unmanaged drop target. It stops managed apps from sending data using Airdrop. 
- **Viewing non-corporate documents in corporate apps**: **Block** prevents viewing non-corporate documents in corporate apps. **Not configured** (default) allows any document to be viewed in corporate managed apps.

  Setting to **Block** also prevents contact export synchronization in Outlook for iOS. For more information, see [Support Tip: Enabling Outlook iOS Contact Sync with iOS12 MDM Controls](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Require iTunes Store password for all purchases**: **Require** the user to enter the Apple ID password for each in-app or ITunes purchase. **Not configured** (default) allows purchases without prompting for a password every time.
- **In-app purchases**: Choose **Block** to prevent in-app purchases from the store. **Not configured** (default) allows store purchases within a running app.
- **Download content from iBook store flagged as 'Erotica'**: Choose **Block** to prevent stops users from downloading media from the iBook store that's tagged as erotica. **Not configured** (default) allows the user to download books with the "Erotica" category.
- **Allow managed apps to write contacts to unmanaged contacts accounts**: When set to **Allow**, managed apps, such as the Outlook mobile app, can save or sync contact information, including business and corporate contacts, to the built-in iOS Contacts app. When set to **Not configured** (default), managed apps can't save or sync contact information to the built-in iOS Contacts app on the device.
  
  To use this setting, set the **Viewing corporate documents in unmanaged apps** setting to **Block**.

- **Ratings region**: Choose the ratings region you want to use for allowed downloads. And then choose the allowed ratings for **Movies**, **TV Shows**, and **Apps**.

### Settings apply to: Automated device enrollment (supervised)

- **App store**: **Block** prevents access to the app store on supervised devices. **Not configured** (default) allows access.

  Starting with iOS 13.0, this setting requires supervised devices.

  - **Installing apps from App Store**: Choose **Block** to block the app store from the device home screen. End users can continue to use iTunes or the Apple Configurator to install apps. **Not configured** (default) allows the app store on the home screen.
  - **Automatic app downloads**: Choose **Block** to prevent automatic downloading of apps bought on other devices. It doesn't affect updates to existing apps. **Not configured** (default) allows apps bought on other iOS devices to download on the device.

- **Explicit iTunes music, podcast, or news content**: Choose **Block** to prevent explicit iTunes music, podcast, or news content. **Not configured** (default) allows the device to access content rated as adult from the store. iOS 13 and newer may require supervised only devices. 

  Starting with iOS 13.0, this setting requires supervised devices.

- **Adding Game Center friends**: **Block** prevents users from adding Game Center friends. **Not configured** (default) allows the user to add friends in Game Center.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Game Center**: **Block** the use of the Game Center app. **Not configured** (default) allows using the Game Center app on the device.
- **Multiplayer gaming**: Choose **Block** to prevent multiplayer gaming. **Not configured** (default) allows the user to play multiplayer games on the device.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Access to network drive in Files app**: Using the Server Message Block (SMB) protocol, devices can access files or other resources on a network server. **Disable** prevents accessing files on a network SMB drive. **Not configured** (default) allows access.

  This feature applies to:  
  - iOS and iPadOS 13.0 and newer

## Built-in Apps

### Settings apply to: All enrollment types

- **Siri**: **Block** prevents access to Siri. **Not configured** (default) allows using the Siri voice assistant on the device.
  - **Siri while device is locked**: Choose **Block** to prevent access to Siri when the device is locked. **Not configured** (default) allows using the Siri voice assistant on the device when it's locked.

- **Safari fraud warnings**: **Require** fraud warnings to be shown in the web browser on the device. **Not configured** (default) disables this feature.

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Spotlight search to return results from internet**: **Block** stops Spotlight from returning any results from an Internet search. **Not configured** (default) allows Spotlight search connect to the Internet to provide search results.

- **Safari cookies**: Choose how cookies are handled on the device. Your options:
  - Allow
  - Block all cookies
  - Allow cookies from visited web sites
  - Allow cookies from current web site

- **Safari JavaScript**: **Block** prevents Java scripts in the browser from running on the device. **Not configured** (default) allows Java scripts.

- **Safari Pop-ups**: **Block** to disable the pop-up blocker in the web browser. **Not configured** (default) allows the pop-up blocker.

### Settings apply to: Automated device enrollment (supervised)

- **Camera**: Choose **Block** to prevent access to the camera on the device. **Not configured** (default) allows access to the device's camera.

  Starting with iOS 13.0, this setting requires supervised devices.

  - **FaceTime**: **Block** to prevent access to the FaceTime app. **Not configured** (default) allows access to the FaceTime app on the device.

    Starting with iOS 13.0, this setting requires supervised devices.

- **Siri profanity filter**: **Require** prevents Siri from dictating, or speaking profane language.

  To use this setting, set the **Siri** setting to **Block**.

- **Siri to query user-generated content from the internet**: **Block** prevents Siri from accessing websites to answer questions. **Not configured** (default) allows Siri to access user-generated content from the internet.

  To use this setting, set the **Siri** setting to **Block**.

- **Apple News**: Choose **Block** to prevent access to the Apple News app on the device. **Not configured** (default) allows using the Apple News app.
- **iBooks store**: **Block** prevents access to the iBooks store. **Not configured** (default) allows users to browse and buy books from the iBooks store.
- **Messages app on the device**: **Block** prevents users from using the Messages app for iMessage. If the device supports text messaging, the user can still send and receive text messages using SMS. **Not configured** (default) allows using the Messages app to send and read messages over the internet.
- **Podcasts**: **Block** prevents users using the Podcasts app. **Not configured** (default) allows using the Podcasts app.
- **Music service**: **Block** reverts the Music app to classic mode and disables the Music service. **Not configured** (default) allows using the Apple Music app.
- **iTunes Radio service**: **Block** prevents users from using the iTunes Radio app. **Not configured** (default) allows using the iTunes Radio app.
- **iTunes store**: **Not configured** (default) allows iTunes on the devices. **Block** prevents users from using iTunes on the device. 

  This feature applies to:  
  - iOS 4.0 and newer

- **Find my iPhone**: **Not configured** (default) allows using this Find My app feature to get the approximate location of the device. **Block** prevents this feature in the Find My app. 

  This feature applies to:  
  - iOS 13.0 and iPadOS 13.0 and newer

- **Find my Friends**: **Not configured** (default) allows using this Find My app feature to find family and friends from an Apple device or iCloud.com. **Block** prevents this feature in the Find My app.

  This feature applies to:  
  - iOS 13.0 and iPadOS 13.0 and newer

- **Changes to the Find My Friends app settings**: **Block** prevents changes to the Find My Friends app settings. **Not configured** (default) allows the user to change settings for the Find My Friends app.

- **Spotlight search to return results from internet**: **Block** stops Spotlight from returning any results from an Internet search. **Not configured** (default) allows Spotlight search connect to the Internet to provide search results.

- **Block removal of system apps from device**: Choosing **Block** disables the ability to remove system apps from the device. **Not configured** (default) allows users to remove system apps.

- **Safari**: **Block** using the Safari browser on the device. **Not configured** (default) allows users to use the Safari browser.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Safari Autofill**: **Block** disables the autofill feature in Safari on the device. **Not configured** (default) allows users to change autocomplete settings in the web browser.

  Starting with iOS 13.0, this setting requires supervised devices.

## Restricted apps

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Type of restricted apps list**: Create a list of apps that users aren't allowed to install or use. Your options:

  - **Not configured** (default): There are no restrictions from Intune. Users have access to apps you assign, and built-in apps.
  - **Prohibited apps**: Apps not managed by Intune that you don't want installed on the device. Users aren't prevented from installing a prohibited app. But if a user installs an app from this list, it's reported in Intune.
  - **Approved apps**: Apps that users are allowed to install. Users must not install apps that aren't listed. Apps that are managed by Intune are automatically allowed. Users aren't prevented from installing an app that isn't on the approved list. But if they do, it's reported in Intune.

To add apps to these lists, you can:

- **Add** the iTunes App store URL of the app you want. For example, to add the Microsoft Work Folders app, enter `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` or `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  To find the URL of an app, open the iTunes App Store, and search for the app. For example, search for `Microsoft Remote Desktop` or `Microsoft Word`. Select the app, and copy the URL.

  You can also use iTunes to find the app, and then use the **Copy Link** task to get the app URL.

- **Import** a CSV file with details about the app, including the URL. Use the `<app url>, <app name>, <app publisher>` format. Or, **Export** an existing list that includes the restricted apps list in the same format.

> [!IMPORTANT]
> Device profiles that use the restricted app settings must be assigned to groups of users.

## Show or hide apps

Applies to devices running iOS 9.3 or newer.

### Settings apply to: Automated device enrollment (supervised)

- **Type of apps list**: Create a list of apps to show or hide. You can show or hide built-in apps and line-of-business apps. Apple's web site has a list of [built-in Apple apps](https://support.apple.com/HT208094). Your options:

  - **Hidden apps**: Enter a list of apps that are hidden from users. Users can't view, or open these apps.
  
    Apple prevents hiding some native apps. For example, you can't hide the **Settings** app on the device. [Delete built-in Apple apps](https://support.apple.com/HT208094) lists the apps that can be hidden.
  
  - **Visible apps**: Enter a list of apps that users can view and launch. No other apps can be viewed or launched.

- **App URL**: Enter the store app URL of the app you want to show or hide. For example:

  - To add the Microsoft Work Folders app, enter `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` or `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - To add the Microsoft Word app, enter `https://itunes.apple.com/de/app/microsoft-word/id586447913` or `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  To find the URL of an app, open the iTunes App Store, and search for the app. For example, search for `Microsoft Remote Desktop` or `Microsoft Word`. Select the app, and copy the URL.

  You can also use iTunes to find the app, and then use the **Copy Link** task to get the app URL.
  
  For more information about locating a Bundle ID, see [How to find the bundle ID for an iOS app](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- **App Bundle ID**: Enter the app [bundle ID](bundle-ids-built-in-ios-apps.md) of the app you want. You can show or hide built-in apps and line-of-business apps. Apple's web site has a list of [built-in Apple apps](https://support.apple.com/HT208094).
- **App name**: Enter the app name of the app you want. You can show or hide built-in apps and line-of-business apps. Apple's web site has a list of [built-in Apple apps](https://support.apple.com/HT208094).
- **Publisher**: Enter the publisher of the app you want.

To add apps, you can:

- **Add**: Select to create your list of apps.
- **Import** a CSV file with details about the app, including the URL. Use the `<app url>, <app name>, <app publisher>` format. Or, **Export** to create a list of the restricted apps you added, in the same format.

## Wireless

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

Note needed for Data Roaming (Tip or important note to help with customer confusion): This setting will not show up on the targeted device's management profile. That is because this setting is treated as a remote device action, and every time the state of data roaming is changed on the device, it will become blocked again by the Intune service. Even though it is not in the management profile, it is working if it showing as a success from the reporting in the admin console. 
- **Data roaming**: Choose **Block** to prevent data roaming over the cellular network. **Not configured** (default) allows data roaming when the device is on a cellular network.

  > [!IMPORTANT]
  > This setting is treated as a remote device action. So, this setting isn't shown in the management profile on the device. Every time the data roaming status changes on the device, **Data roaming** is blocked by the Intune service. In Intune, if the reporting status shows a success, then know that it's working, even though the setting isn't shown in the management profile on the device.

- **Global background fetch while roaming**: **Block** prevents using the global background fetch feature when roaming over the cellular network. **Not configured** (default) allows the device to fetch data, such as email, when it's roaming on a cellular network.
- **Voice dialing**: Choose **Block** to prevent users from using the voice dialing feature on the device. **Not configured** (default) allows voice dialing on the device.
- **Voice roaming**: Choose **Block** to prevent voice roaming over the cellular network. **Not configured** (default) allows voice roaming when the device is on a cellular network.
- **Personal Hotspot**: **Block** turns off the personal hotspot on the users' device with every device sync. This setting might not be compatible with some carriers. **Not configured** (default) keeps the personal hotspot configuration as the default set by the user.

  > [!IMPORTANT]
  > This setting is treated as a remote device action. So, this setting isn't shown in the management profile on the device. Every time the personal hotspot status changes on the device, **Personal Hotspot** is blocked by the Intune service. In Intune, if the reporting status shows a success, then know that it's working, even though the setting isn't shown in the management profile on the device.

- **Cellular usage rules (managed apps only)**: Define the data types that managed apps can use when on cellular networks. Your options:
  - **Block use of cellular data**: Block using cellular data for **All managed apps** or **Choose specific apps**.
  - **Block use of cellular data when roaming**: Block using cellular data when roaming for **All managed apps** or **Choose specific apps**.

### Settings apply to: Automated device enrollment (supervised)

- **Changes to app cellular data usage settings**: Choose **Block** to prevent changes to the app cellular data usage settings. **Not configured** (default) allows the user to control which apps are allowed to use cellular data.
- **Changes to cellular plan settings**: **Block** prevents users from changing any settings in the cellular plan. **Not configured** (default) allows users to make changes.

  This feature applies to:  
  - iOS 11.0 and newer

- **User modification of Personal Hotspot**: When set to **Block**, the user can't change the personal hotspot setting. **Not configured** (default) allows end users to enable or disable their personal hotspot.

  If you block this setting and block the **Personal Hotspot** setting, the personal hotspot is turned off.

  This feature applies to:  
  - iOS 12.2 and newer

- **Join Wi-Fi networks only using configuration profiles**: **Require** forces the device to use only Wi-Fi networks set up through Intune configuration profiles. **Not configured** (default) allows the device to use other Wi-Fi networks.
- **Wi-Fi always turned on**: When set to **Require**, Wi-Fi stays on in the Settings app. It can't be turned off in Settings or in the Control Center, even when the device is in airplane mode. **Not configured** (default) allows the user to control turning on or turning off Wi-Fi.

  Configuring this setting doesn't prevent users from selecting a Wi-Fi network.

  This feature applies to:  
  - iOS and iPadOS 13.0 and newer

## Connected Devices

### Settings apply to: All enrollment types

- **Wrist detection for paired Apple watch**: **Require** forces a paired Apple watch to use wrist detection. When required, the Apple Watch won't display notifications when it's not being worn. 

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Require AirPlay outgoing requests pairing password**: **Require** a pairing password when the user uses AirPlay to stream content to other Apple devices. **Not configured** (default) allows the user to stream content using AirPlay without entering a password.

### Settings apply to: Automated device enrollment (supervised)

- **AirDrop**: **Block** prevents using AirDrop on the device. **Not configured** (default) allows using the AirDrop feature to exchange content with nearby devices.
- **Apple Watch pairing**: **Block** prevents pairing with an Apple Watch. **Not configured** (default) allows the device to pair with an Apple Watch.
- **Bluetooth modification**: **Block** stops the end user from changing Bluetooth settings on the device. **Not configured** (default) allows the user to change these settings.
- **Host pairing to control the devices an iOS device can pair with**: **Not configured** (default) allows host pairing to let the administrator control which devices an iOS device can pair with. **Block** prevents host pairing.
- **Block AirPrint**: Choose **Block** to prevent using the AirPrint feature on the device. **Not configured** (default) allows the user to use AirPrint.
  - **Block storage of AirPrint credentials in Keychain**: **Block** prevents using Keychain storage for username and password on the device. **Not configured** (default) allows storing the AirPrint username and password in the Keychain app.
  - **Require a trusted TLS certificate for AirPrint**: **Require** forces the device to use trusted certificates for TLS printing communication.
  - **Block iBeacon discovery of AirPrint printers**: **Block** prevents malicious AirPrint Bluetooth beacons from phishing for network traffic. **Not configured** (default) allows advertising AirPrint printers on the device.
- **Block setting up new nearby devices**: **Block** disables the prompt to set up new devices that are nearby. **Not configured** (default) allows prompts for users to connect to other nearby Apple devices.

  This feature applies to:  
  - iOS 11.0 and newer

- **Access to files on USB drive**: Devices can connect and open files on a USB drive. **Disable** prevents device access to the USB drive in the Files app when a USB is connected to the device. Disabling this feature also blocks end users from transferring files onto a USB drive connected to an iPad. **Not configured** (default) allows access to a USB drive in the Files app.

  This feature applies to:  
  - iOS and iPadOS 13.0 and newer

## Keyboard and Dictionary

### Settings apply to: Automated device enrollment (supervised)

- **Word definition lookup**: **Block** prevents user from highlighting a word, and then looking up its definition on the device. **Not configured** (default) allows access to the definition lookup feature.
- **Predictive keyboards**: **Not configured** (default) allows using predictive keyboards to suggest words the user might want. **Block** prevents this feature.
- **Auto-correction**: **Not configured** (default) allows the device to automatically correct misspelled words. **Block** prevents using autocorrection.
- **Keyboard spell-check**: **Not configured** (default) allows using spellchecker on the device. **Block** allows spell checker.
- **Keyboard shortcuts**: **Not configured** (default) allows using keyboard shortcuts on the device. **Block** stops the user from using keyboard shortcuts.
- **Dictation**: **Block** stops the user from using voice input to enter text. **Not configured** (default) allows the user to use dictation input.
- **QuickPath**: **Not configured** (default) allows users to use QuickPath, which allows a continuous input on the device's keyboard. Users can type by swiping across the keys to create words. **Block** prevents users from using QuickPath. 

  This feature applies to:  
  - iOS 13.0 and iPadOS 13.0 and newer

## Cloud and Storage

### Settings apply to: All enrollment types

- **Encrypted backup**: **Require** so device backups must be encrypted.
- **Managed apps sync to cloud**: **Not configured** (default) allows your Intune-manages apps to sync data to the user's iCloud account. **Block** prevents this data sync to iCloud.
- **Block Enterprise Book Backup**: Choose **Block** to prevent users from backing up enterprise books. **Not configured** (default) allows users to back up these books.
- **Block enterprise book metadata sync (notes and highlights)**: **Block** prevents syncing notes and highlights in enterprise books. **Not configured** (default) allows the syncing.

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Photo stream syncing to iCloud**: **Not configured** (default) lets users enable **My Photo Stream** on their device to sync to iCloud, and have photos available on all the user's devices. **Block** prevents photo stream syncing to iCloud. Blocking this feature may cause data loss. 
- **iCloud Photo Library**: Set to **Block** to disable using iCloud photo library to store photos and videos in the cloud. Any photos not fully downloaded from iCloud Photo Library to the device are removed from the device. **Not configured** (default) allows using the iCloud photo library.
- **Shared photo stream**: Choose **Block** to disable **iCloud Photo Sharing** on the device. **Not configured** (default) allows shared photo streaming.
- **Handoff**: **Not configured** (default) allows users to start work on an iOS device, and then continue the work they started on another iOS or macOS device. **Block** prevents this handoff.

### Settings apply to: Automated device enrollment (supervised)

- **Backup to iCloud**: **Not configured** (default) allows the user to back up the device to iCloud. **Block** stops the user from backing up the device to iCloud.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Block iCloud Document sync**: **Not configured** (default) allows document and key-value synchronization to your iCloud storage space. **Block** prevents iCloud from syncing documents and data.

  Starting with iOS 13.0, this setting requires supervised devices.

- **Block iCloud Keychain sync**: Choose **Block** to disable syncing credentials stored in the Keychain to iCloud. **Not configured** (default) allows users to sync these credentials.

  Starting with iOS 13.0, this setting requires supervised devices.

## Autonomous single app mode

Use these settings to configure iOS devices to run specific apps in autonomous single app mode. When this mode is configured, and the app is run, the device is locked. It can only run that app. For example, add an app that lets users take a test on the device. When the apps actions are complete, or you remove this policy, the device returns to its normal state.

### Settings apply to: Automated device enrollment (supervised)

- **App name**: Enter the name of the app you want.
- **App Bundle ID**: Enter the [bundle ID](bundle-ids-built-in-ios-apps.md) of the app you want.
- **Add**: Select to create your list of apps.

You can also **Import** a CSV file with the list of app names and their bundle IDs. Or, **Export** an existing list that includes the apps.

## Kiosk

### Settings apply to: Automated device enrollment (supervised)

- **App to run in kiosk mode**: Choose the type of apps you want to run in kiosk mode. Your options:
  - **Not configured** (default): Kiosk settings aren't applied. The device doesn't run in kiosk-mode.
  - **Store App**: Enter the URL to an app in the iTunes App store.
  - **Managed App**: Choose an app you added to Intune.
  - **Built-In App**: Enter the [bundle ID](bundle-ids-built-in-ios-apps.md) of the built-in app.

- **Assistive touch**: **Require** the Assistive Touch accessibility setting be on the device. This feature helps users with on-screen gestures that might be difficult for them. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Invert colors**: **Require** the Invert Colors accessibility setting so users with visual impairments can change the display screen. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Mono audio**: **Require** the Mono audio accessibility setting be on the device. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Voice control**: **Require** enables voice control on the device, and allows users to fully control the OS using Siri commands. **Not configured** disables voice control on the device.

  This setting applies to:  
  - iOS 13.0 and newer
  - iPadOS 13.0 and newer
  
  > [!TIP]
  > If you have LOB apps available for your organization, and they're not **Voice Control** ready on day 0 when iOS 13.0 releases, then we recommend you leave this setting as **Not configured**.

- **VoiceOver**: **Require** the VoiceOver accessibility setting be on the device to read text on the screen out loud. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Zoom**: **Require** the Zoom setting be on the device to let users use touch to zoom in on the screen. **Not configured** doesn't run or enable this feature in kiosk mode.
- **Auto lock**: **Block** prevents automatic locking of the device. **Not configured** allows this feature.
- **Ringer switch**: **Block** disables the ringer (mute) switch on the device. **Not configured** allows this feature.
- **Screen rotation**: **Block** prevents changing the screen orientation when the user rotates the device. **Not configured** allows this feature.
- **Screen sleep button**: Choose **Block** to disable the screen sleep wake button on the device. **Not configured** allows this feature.
- **Touch**: **Block** disables the touchscreen on the device. **Not configured** allows the user to use the touchscreen.
- **Volume buttons**: **Block** prevents using the volume buttons on the device. **Not configured** allows the volume buttons.
- **Assistive touch control**: **Allow** let users use the assistive touch function. **Not configured** disables this feature.
- **Invert colors control**: **Allow** invert color changes to let users adjust the invert colors function. **Not configured** disables this feature.
- **Speak on selected text**: **Allow** the Speak Selection accessibility settings be on the device. This feature reads text that the user selects out loud. **Not configured** disables this feature.
- **Voice control modification**: **Allow** users to change the state of voice control on their devices. **Not configured** blocks users from changing the state of voice control on their devices.

  This setting applies to:  
  - iOS 13.0 and newer
  - iPadOS 13.0 and newer

- **VoiceOver control**: **Allow** voiceover changes to let users update the VoiceOver function, such as how fast on-screen text is read out loud. **Not configured** prevents voiceover changes.
- **Zoom control**: **Allow** zoom changes by the user. **Not configured** prevents zoom changes.

> [!NOTE]
> Before you can configure an iOS device for kiosk mode, you must use the Apple Configurator tool or the Apple Device Enrollment Program to put the device into supervised mode. See Apple's guide on using the Apple Configurator tool.
> If the iOS app you enter is installed after you assign the profile, then the device doesn't enter kiosk mode until the device is restarted.

## Domains

### Settings apply to: Device enrollment, Automated device enrollment (supervised)

- **Unmarked email domains** > **Email Domain URL**: Add one or more URLs to the list. When end users receive an email from a domain other than the domains you enter, the email is marked as untrusted in the iOS Mail app.

- **Managed web domains** > **Web Domain URL**; Add one or more URLs to the list. When documents are downloaded from the domains you enter, they're considered managed. This setting applies only to documents downloaded using the Safari browser.

### Settings apply to: Automated device enrollment (supervised)

- **Safari password autofill domains** > **Domain URL**: Add one or more URLs to the list. Users can only save web passwords from URLs in this list. This setting applies only to the Safari browser, and devices in supervised mode. If you don't enter any URLs, then passwords can be saved from all web sites.

  This setting applies to:  
  - iOS 9.3 and newer

## Settings that require supervised mode

iOS supervised mode can only be enabled during initial device setup through Apple’s Device Enrollment Program, or by using Apple Configurator. Once supervised mode is enabled, Intune can configure a device with the following functionality:

- App Lock (Single App Mode) 
- Global HTTP Proxy 
- Activation Lock Bypass 
- Autonomous Single App Mode 
- Web Content Filter 
- Set background and lock screen 
- Silent App Push 
- Always-On VPN 
- Allow managed app installation exclusively 
- iBookstore 
- iMessages 
- Game Center 
- AirDrop 
- AirPlay 
- Host pairing 
- Cloud Sync 
- Spotlight search 
- Handoff 
- Erase device 
- Restrictions UI 
- Installation of configuration profiles by UI 
- News 
- Keyboard shortcuts 
- Passcode modifications 
- Device name changes 
- Automatic app downloads 
- Changes to enterprise app trust 
- Apple Music 
- Mail Drop 
- Pair with Apple Watch 

> [!NOTE]
> Apple confirmed that certain settings move to supervised-only in 2019. We recommend taking this into consideration when using these settings, instead of waiting for Apple to migrate them to supervised-only:
>
> - App installation by end users
> - App removal
> - FaceTime
> - Safari
> - iTunes
> - Explicit content
> - iCloud documents and data
> - Multiplayer gaming
> - Add Game Center friends
> - Siri

## Next steps

[Assign the profile](../device-profile-assign.md) and [monitor its status](../device-profile-monitor.md).

You can also restrict device features and settings on [macOS](device-restrictions-macos.md) devices.
