---
# required metadata

title: Device restriction settings for Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: See a list of all the settings and their descriptions for creating device restrictions on Windows 10 and later devices. Use these settings in a configuration profile to control screenshots, password requirements, kiosk settings, apps in the store, Microsoft Edge browser, Windows defender, access to the cloud, start menu, and more in Microsoft Intune.
keywords:
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/18/2019
ms.topic: reference
ms.prod:
ms.service: microsoft-intune
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

# Windows 10 (and newer) device settings to allow or restrict features using Intune

This article lists and describes all the different settings you can control on Windows 10 and newer devices. As part of your mobile device management (MDM) solution, use these settings to allow or disable features, set password rules, customize the lock screen, use Windows Defender, and more.

These settings are added to a device configuration profile in Intune, and then assigned or deployed to your Windows 10 devices.

> [!Note]
> Not all options are available on all editions of Windows. To see the supported editions, refer to the [policy CSPs](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (opens another Microsoft web site).

## Before you begin

[Create a device configuration profile](device-restrictions-configure.md#create-the-profile).

## App Store

These settings use the [ApplicationManagement policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement), which also lists the supported Windows editions.

- **App store** (mobile only): **Not configured** (default) allows end users access to the app store on mobile devices. **Block** prevents using the app store.
- **Auto-update apps from store**: **Not configured** (default) allows apps installed from the Microsoft Store to be automatically updated. **Block** prevents updates from being automatically installed.
- **Trusted app installation**: Choose if non-Microsoft Store apps can be installed, also known as sideloading. Sideloading is installing, and then running or testing an app that isn't certified by the Microsoft Store. For example, an app that is internal to your company only. Your options:
  - **Not configured** (default): Uses the OS default.
  - **Block**: Prevents sideloading. Non-Microsoft Store apps can't be installed.
  - **Allow**: Allows sideloading. Non-Microsoft Store apps can be installed.
- **Developer unlock**: Allow Windows developer settings, such as allowing sideloaded apps to be modified by end users. Your options:
  - **Not configured** (default): Uses the OS default.
  - **Block**: Prevents developer mode and sideloading apps.
  - **Allow**: Allows developer mode and sideloading apps.

  [Enable your device for development](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) has more information on this feature.

- **Shared user app data**: Choose **Allow** to share application data between different users on the same device and with other instances of that app. **Not configured** (default) prevents sharing data with other users and other instances of the same app.
- **Use private store only**: **Allow** only allows apps to be downloaded from a private store, and not downloaded from the public store, including a retail catalog. **Not configured** (default) allows apps to be downloaded from a private store and a public store.
- **Store originated app launch**: **Block** disables all apps that were pre-installed on the device, or downloaded from the Microsoft Store. **Not configured** (default) allows these apps to open.
- **Install app data on system volume**: **Block** stops apps from storing data on the system volume of the device. **Not configured** (default) allows apps to store data on the system disk volume.
- **Install apps on system drive**: **Block** prevents apps from installing on the system drive on the device. **Not configured** (default) allows apps to install on the system drive.
- **Game DVR** (desktop only): **Block** disables Windows Game recording and broadcasting. **Not configured** (default) allows recording and broadcasting of games.
- **Apps from the store only**: **Require** forces end users to only install apps from the Windows App Store. **Not configured** allows end users to install apps from places other than the Windows App Store.

Select **OK** to save your changes.

## Cellular and Connectivity

These settings use the [connectivity policy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) and [Wi-Fi policy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) CSPs, which also list the supported Windows editions.

- [Wi-Fi policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Cellular data channel**: Choose if end users can use data, like browsing the web, when connected to a cellular network. Your options:
  - **Not configured** (default): Uses the OS default, which may allow the cellular data channel. End users can turn it off.
  - **Block**: Don't allow the cellular data channel. End users can't turn it on.
  - **Allow (not editable)**: Allows the cellular data channel. End users can't turn it off.

- **Data roaming**: **Block** prevents cellular data roaming on the device. **Not configured** (default) allows roaming between networks when accessing data.
- **VPN over the cellular network**: **Block** prevents the device from accessing VPN connections when connected to a cellular network. **Not configured** (default) allows VPN to use any connection, including cellular.
- **VPN roaming over the cellular network**: **Block** stops the device from accessing VPN connections when roaming on a cellular network. **Not configured** (default) allows VPN connections when roaming.
- **Connected devices service**: **Block** disables the Connected Devices Platform (CDP) component. CDP enables discovery and connection to other devices (through Bluetooth/LAN or the cloud) to support remote app launching, remote messaging, remote app sessions, and other cross-device experiences. **Not configured** (default) allows the connected devices service, which enables discovery and connection to other Bluetooth devices.
- **NFC**: **Block** prevents near field communications (NFC) capabilities. **Not configured** (default) allows users to enable and configure NFC features on the device.
- **Wi-Fi**: **Block** prevents users from and enabling, configuring, and using Wi-Fi connections on the device. **Not configured** (default) allows Wi-Fi connections.
- **Automatically connect to Wi-Fi hotspots**: **Block** prevents devices from automatically connecting to Wi-Fi hotspots. **Not configured** (default) lets devices automatically connect to free Wi-Fi hotspots, and automatically accept any terms and conditions for the connection.
- **Manual Wi-Fi configuration**: **Block** prevents devices from connecting to Wi-Fi outside of MDM server-installed networks. **Not configured** (default) allows end users to add and configure their own Wi-Fi connections network SSIDs.
- **Wi-Fi scan interval**: Enter how often devices scan for Wi-Fi networks. Enter a value from 1 (most frequent) to 500 (least frequent). Default is `0` (zero).

### Bluetooth

These settings use the [Bluetooth policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth); which also lists the supported Windows editions.

- **Bluetooth**: **Block** prevents users from enabling Bluetooth. **Not configured** (default) allows Bluetooth on the device.
- **Bluetooth discoverability**: **Block** prevents the device from being discoverable by other Bluetooth-enabled devices. **Not configured** (default) allows other Bluetooth-enabled devices, such as a headset, to discover the device.
- **Bluetooth pre-pairing**: **Block** prevents specific Bluetooth devices to automatically pair with a host device. **Not configured** (default) allows automatic pairing with the host device.
- **Bluetooth advertising**: **Block** prevents the device from sending out Bluetooth advertisements. **Not configured** (default) allows the device to send out Bluetooth advertisements.
- **Bluetooth allowed services**: **Add** a list of allowed Bluetooth services and profiles as hex strings, such as `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  [ServicesAllowedList usage guide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) has more information on the service list.

Select **OK** to save your changes.

## Cloud and Storage

These settings use the [accounts policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts); which also lists the supported Windows editions.

- **Microsoft account**: **Block** prevents end users from associating a Microsoft account with the device. **Not configured** (default) allows adding and using a Microsoft account.
- **Non-Microsoft account**: **Block** prevents end users from adding non-Microsoft accounts using the user interface. **Not configured** (default) allows users to add email accounts that aren't associated with a Microsoft account.
- **Settings synchronization for Microsoft account**: **Not configured** (default) allows device and app settings associated with a Microsoft account to synchronize between devices. **Block** prevents this synchronization.
- **Microsoft Account sign-in assistant**: When set to **Not configured** (default), end users can start and stop the **Microsoft Account Sign-In Assistant** (wlidsvc) service. This operating system service allows users to sign in to their Microsoft account. **Disable** prevents end users from controlling the Microsoft Sign-in Assistant service (wlidsvc).

Select **OK** to save your changes.

## Cloud Printer

These settings use the [EnterpriseCloudPrint policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint); which also lists the supported Windows editions.

- **Printer discovery URL**: Enter the URL for finding cloud printers. For example, enter `https://cloudprinterdiscovery.contoso.com`.
- **Printer access authority URL**: Enter the authentication endpoint URL to get OAuth tokens. For example, enter `https://azuretenant.contoso.com/adfs`.
- **Azure native client app GUID**: Enter the GUID of a client application allowed to get OAuth tokens from the OAuthAuthority. For example, enter `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **Print service resource URI**: Enter the OAuth resource URI for print service configured in the Azure portal. For example, enter `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Maximum printers to query**: Enter the maximum number of printers that you want to be queried. The default value is `20`.
- **Printer discovery service resource URI**: Enter the OAuth resource URI for printer discovery service configured in the Azure portal. For example, enter `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> After you setup a [Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), you can configure these settings, and then deploy to your Windows devices.

Select **OK** to save your changes.

## Control Panel and Settings

- **Settings app**: **Block** prevents end users from accessing to the Windows settings app. **Not configured** (default) allows users to open the Settings app on the device.
  - **System**: **Block** prevents access to the System area of the Settings app. **Not configured** (default) allows access.
    - **Power and sleep settings modification** (desktop only): **Block** prevents end users from changing the power and sleep settings on the device. **Not configured** (default) allows users to change power and sleep settings.
  - **Devices**: **Block** prevents access to the Devices area of the Settings app on the device. **Not configured** (default) allows access.
  - **Network Internet**: **Block** prevents access to the Network & Internet area of the Settings app on the device. **Not configured** (default) allows access.
  - **Personalization**: **Block** prevents access to the Personalization area of the Settings app on the device. **Not configured** (default) allows access.
  - **Apps**: **Block** prevents access to the Apps area of the Settings app on the device. **Not configured** (default) allows access.
  - **Accounts**: **Block** prevents access to the Accounts area of the Settings app on the device. **Not configured** (default) allows access.
  - **Time and Language**: **Block** prevents access to the Time & Language area of the Settings app on the device. **Not configured** (default) allows access.
    - **System Time modification**: **Block** prevents end users from changing the date and time settings on the device. **Not configured** allows users to change these settings.
    - **Region settings modification** (desktop only): **Block** prevents end users from changing the region settings on the device. **Not configured** allows users to change these settings.
    - **Language settings modification (desktop only)**: **Block** prevents end users from changing the language settings on the device. **Not configured** allows users to change these settings.

      [Settings policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Gaming**: **Block** prevents access to the Gaming area of the Settings app on the device. **Not configured** (default) allows access.
  - **Ease of Access**: **Block** prevents access to the Ease of Access area of the Settings app on the device. **Not configured** (default) allows access.
  - **Privacy**: **Block** prevents access to the Privacy area of the Settings app on the device. **Not configured** (default) allows access.
  - **Update and Security**: **Block** prevents access to the Update & Security area of the Settings app on the device. **Not configured** (default) allows access.

Select **OK** to save your changes.

## Display

These settings use the [display policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display); which also lists the supported Windows editions.

GDI DPI scaling enables applications that aren't DPI aware to become per monitor DPI aware.

- **Turn on GDI scaling for apps**: **Add** the legacy apps that you want GDI DPI scaling turned on. For example, enter `filename.exe` or `%ProgramFiles%\Path\Filename.exe`.

  GDI DPI scaling is turned on for all legacy applications in your list.

- **Turn off GDI scaling for apps**: **Add** the legacy apps that you want GDI DPI scaling turned off. For example, enter `filename.exe` or `%ProgramFiles%\Path\Filename.exe`.

  GDI DPI scaling is turned off for all legacy applications in your list.

You can also **Import** a .csv file with the list of apps.

Select **OK** to save your changes.

## General

These settings use the [experience policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience); which also lists the supported Windows editions. 

- **Screen capture** (mobile only): **Block** prevents end users from getting screenshots on the device. **Not configured** (default) allows this feature.
- **Copy and paste (mobile only)**: **Block** prevents end users from using copy-and-paste between apps on the device. **Not configured** (default) allows this feature.
- **Manual unenrollment**: **Block** prevents end users from deleting the workplace account using the workplace control panel on the device. **Not configured** (default) allows this feature.

  This policy setting doesn't apply if the computer is Azure AD joined and auto-enrollment is enabled.

- **Manual root certificate installation** (mobile only): **Block** prevents end users from manually installing root certificates, and intermediate CAP certificates. **Not configured** (default) allows this feature.
- **Camera**: **Block** prevents end users from using the camera on the device. **Not configured** (default) allows this feature.
- **OneDrive file sync**: **Block** prevents end users from synchronizing files to OneDrive from the device. **Not configured** (default) allows this feature.
- **Removable storage**: **Block** prevents end users from using external storage devices, like SD cards with the device. **Not configured** (default) allows this feature.
- **Geolocation**: **Block** prevents end users from turning on location services on the device. **Not configured** (default) allows this feature.
- **Internet sharing**: **Block** prevents Internet connection sharing on the device. **Not configured** (default) allows this feature.
- **Phone reset**: **Block** prevents end users from wiping or doing a factory reset on the device. **Not configured** (default) allows this feature.
- **USB connection**: **Block** prevents access to external storage devices through a USB connection on the device. **Not configured** (default) allows this feature. USB charging isn't affected by this setting.
- **AntiTheft mode** (mobile only): **Block** prevents end users from selecting AntiTheft mode preference on the device. **Not configured** (default) allows this feature.
- **Cortana**: **Block** disable the Cortana voice assistant on the device. When Cortana is off, users can still search to find items on the device. **Not configured** (default) allows Cortana.
- **Voice recording** (mobile only): **Block** prevents end users from using the device voice recorder on the device. **Not configured** (default) allows voice recording for apps.
- **Device name modification** (mobile only): **Block** prevents end users from changing the name of the device. **Not configured** (default) allows this feature.
- **Add provisioning packages**: **Block** prevents the run time configuration agent that installs provisioning packages on the device. **Not configured** (default) allows this feature.
- **Remove provisioning packages**: **Block** prevents the run time configuration agent that removes provisioning packages from the device. **Not configured** (default) allows this feature.
- **Device discovery**: **Block** prevents the device from being discovered by other devices. **Not configured** (default) allows this feature.
- **Task Switcher** (mobile only): **Block** prevents task switching on the device. **Not configured** (default) allows this feature.
- **SIM card error dialog** (mobile only): **Block** error messages from showing on the device if no SIM card is detected. **Not configured** (default) shows the error messages.
- **Ink Workspace**: Choose if and how user access the ink workspace. Your options:
  - **Not configured** (default): Turns on the ink workspace, and the user is allowed to use it above the lock screen.
  - **Disabled on lock screen**: The ink workspace is enabled and feature is turned on. But, the user can't access it above the lock screen.
  - **Disabled**: Access to ink workspace is disabled. The feature is turned off.

  [WindowsInkWorkspace policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Automatic redeployment**: Choose **Allow** so users with administrative rights can delete all user data and settings using **CTRL + Win + R** at the device lock screen. The device is automatically reconfigured and re-enrolled into management. **Not configured** (default) prevents this feature.
- **Require users to connect to network during device setup**: Choose **Require** so the device connects to a network before going past the Network page during Windows setup. **Not configured** (default) allows users to go past the Network page, even if it's not connected to a network.

  The setting becomes effective the next time the device is wiped or reset. Like any other Intune configuration, the device must be enrolled and managed by Intune to receive configuration settings. But once it's enrolled, and receiving policies, then resetting the device enforces the setting during the next Windows setup.

- **Direct Memory Access**: **Block** prevents direct memory access (DMA) for all hot pluggable PCI downstream ports until a user signs into Windows. **Enabled** (default) allows access to DMA, even when a user isn't signed in.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **End processes from Task Manager**: This setting determines whether non-administrators can use Task Manager to end tasks. **Block** prevents standard users (non-administrators) from using Task Manager to end a process or task on the device. **Not configured** (default) allows standard users to end a process or task using Task Manager.

Select **OK** to save your changes.

## Locked screen experience

- **Action center notifications (mobile only)**: **Block** prevents Action Center notifications from showing on the device lock screen. **Not configured** (default) allows users to choose which apps show notifications on the lock screen.

  [AboveLock/AllowActionCenterNotifications CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications)

- **Locked screen picture URL (desktop only)**: Enter the URL to a picture in JPG, JPEG, or PNG format that's used as the Windows lock screen wallpaper. For example, enter `https://contoso.com/image.png`. This setting locks the image, and can't be changed afterwards.
- **User configurable screen timeout (mobile only)**: **Allow** lets users configure the screen timeout. **Not configured** (default) doesn't give users this option.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig)

- **Cortana on locked screen** (desktop only): **Block** prevents users from interact with Cortana when the device is on the lock screen. **Not configured** (default) allows interaction with Cortana.

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Toast notifications on locked screen**: **Block** prevents toast notifications from showing on the device lock screen. **Not configured** (default) allows these notifications.

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Screen timeout (mobile only)**: Set the duration (in seconds) from the screen locking to the screen turning off. Supported values are 11-1800. For example, enter `300` to set this timeout to 5 minutes.

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked)

Select **OK** to save your changes.

## Messaging

These settings use the [messaging policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging); which also lists the supported Windows editions.

- **Message sync (mobile only)**: **Block** disables text messages from being backed up and restored, and from syncing messages between Windows devices. Disabling helps avoid information being stored on servers outside of the organization's control. **Not configured** (default) allows users to change these settings, and sync their messages.
- **MMS (mobile only)**: **Block** disables MMS send and receive functionality on the device. For enterprises, use this policy to disable MMS on devices as part of the auditing or management requirement. **Not configured** (default) allows MMS send and receive.
- **RCS (mobile only)**: **Block** disables Rich Communication Services (RCS) send and receive functionality on the device. For enterprises, use this policy to disable RCS on devices as part of the auditing or management requirement. **Not configured** (default) allows RCS send and receive.

Select **OK** to save your changes.

## Microsoft Edge Browser

These settings use the [browser policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser), which also lists the supported Windows editions.

### Use Microsoft Edge kiosk mode

The available settings change depending on what you choose. Your options:

- **No** (default): Microsoft Edge isn't running in kiosk mode. All Microsoft Edge settings are available for you to change and configure.
- **Digital/Interactive signage (single app kiosk)**: Filters Microsoft Edge settings that are applicable for Digital/Interactive signage Microsoft Edge Kiosk mode for use only on Windows 10 single-app kiosks. Choose this setting to open a URL full screen, and only show the content on that website. [Set up digital signs](https://docs.microsoft.com/windows/configuration/setup-digital-signage) provides more information on this feature.
- **InPrivate Public browsing (single app kiosk)**: Filters Microsoft Edge settings that are applicable for InPrivate Public Browsing Microsoft Edge Kiosk mode for use on Windows 10 single-app kiosks. Runs a multi-tab version of Microsoft Edge.
- **Normal mode (multi-app kiosk)**: Filters Microsoft Edge settings that are applicable for Normal Microsoft Edge Kiosk mode. Runs a full-version of Microsoft Edge with all browsing features.
- **Public browsing (multi-app kiosk)**: Filters Microsoft Edge settings that are applicable for Public browsing on a Windows 10 multi-app kiosk.  Runs a multi-tab version of Microsoft Edge InPrivate.

> [!TIP]
> For more information on what these options do, see [Microsoft Edge kiosk mode configuration types](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

This device restrictions profile is directly related to the kiosk profile you create using the [Windows kiosk settings](kiosk-settings-windows.md). To summarize:

1. Create the [Windows kiosk settings](kiosk-settings-windows.md) profile to run the device in kiosk mode. Select Microsoft Edge as the application and set the Microsoft Edge Kiosk Mode in the Kiosk profile.
2. Create the device restrictions profile described in this article, and configure specific features and settings allowed in Microsoft Edge. Be sure to choose the same Microsoft Edge kiosk mode type as selected in your kiosk profile ([Windows kiosk settings](kiosk-settings-windows.md)). 

    [Supported kiosk mode settings](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) is a great resource.

> [!IMPORTANT] 
> Be sure to assign this Microsoft Edge profile to the same devices as your kiosk profile ([Windows kiosk settings](kiosk-settings-windows.md)).

[ConfigureKioskMode CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### Start experience

- **Start Microsoft Edge with**: Choose which pages open when Microsoft Edge starts. Your options:
  - **Custom start pages**: Enter the start pages, such as `http://www.contoso.com`. Microsoft Edge loads the start pages you enter.
  - **New Tab page**: Microsoft Edge load whatever is entered in the **New Tab URL** setting.
  - **Last session’s page**: Microsoft Edge loads the last session page.
  - **Start pages in local app settings**: Microsoft Edge start with the default start page defined by the OS.

- **Allow user to change start pages**: **Yes** (default) lets users change the start pages. Administrators can use the `EdgeHomepageUrls` to enter the start pages that users see by default when open Microsoft Edge. **No** blocks users from changing the start pages.
- **Allow web content on new tab page​**: When set to **Yes** (default), Microsoft Edge opens the URL entered in the **New Tab URL** setting. If the **New Tab URL** setting is blank, Microsoft Edge opens the new tab page listed in Microsoft Edge settings. Users can change it. When set to **No**, Microsoft Edge opens a new tab with a blank page. Users can't change it.​​
- **New Tab URL**: Enter the URL to open on the New Tab page. For example, enter `https://www.bing.com` or `https://www.contoso.com`.

- **Home button**: Choose what happens when the home button is selected. Your options:
  - **Start pages**: Opens the option you chose in the **Start Microsoft Edge with** setting
  - **New Tab page**: Opens the URL you entered in the **New Tab URL** setting.
  - **Home button URL**: Enter the URL to open. For example, enter `https://www.bing.com` or `https://www.contoso.com`.
  - **Hide Home button**: Hides the home button
- **Allow users to change home button**: **Yes** lets users change the home button. The user's changes override any administrator settings to the home button.​ **No** (default) blocks users from changing how the administrator configured the home button.
- **Show First Run Experience page (Mobile only)**: **Yes** (default) shows the first use introduction page in Microsoft Edge. **No** stops the introduction page from showing the first time you run Microsoft Edge. This feature allows enterprises, such as organizations enrolled in zero emissions configurations, to block this page.
- **First Run Experience URL list location** (Windows 10 Mobile only): Enter the URL that points to the XML file containing the first run page URL(s). For example, enter `https://www.contoso.com/sites.xml`.

- **Refresh browser after idle time**: Enter the number of idle minutes until the browser is refreshed, from 0-1440 minutes. Default is `5` minutes. When set to `0` (zero), the browser doesn't refresh after being idle.

  This setting is only available when running in [InPrivate Public browsing (single-app kiosk)](#use-microsoft-edge-kiosk-mode).

- **Allow pop-ups** (desktop only): **Yes** (default) allows pop-ups in the web browser. **No** prevents pop-up windows in the browser.
- **Send intranet traffic to Internet Explorer** (Desktop only): **Yes** lets users open intranet websites in Internet Explorer instead of Microsoft Edge. This setting is for backwards compatibility. **No** (default) allows users to use Microsoft Edge.
- **Enterprise mode site list location** (Desktop only): Enter the URL that points to the XML file containing a list of web sites that open in Enterprise mode. Users can't change this list. For example, enter `https://www.contoso.com/sites.xml`.
- **Message when opening sites in Internet Explorer**: Use this setting to configure Microsoft Edge to show a notification before a site opens in Internet Explorer 11. Your options:
  - **Don't show message**: The OS default behavior is used, which may not show a message.
  - **Show message that site is opened in Internet Explorer 11**: Show the message when opening sites in IE. Sites open in IE. 
  - **Show message with option to open sites in Microsoft Edge**: Show the message when opening sites in Edge. The message includes a **Keep going in Microsoft Edge** link so users can choose Microsoft Edge instead of IE.

  > [!IMPORTANT]
  > This setting requires you to use the **Enterprise mode site list location** setting, the **Send intranet traffic to Internet Explorer** setting, or both settings.

- **Allow Microsoft compatibility list**: **Yes** (default) allows using a Microsoft compatibility list. **No** prevents the Microsoft compatibility list in Microsoft Edge. This list from Microsoft helps Microsoft Edge properly display sites with known compatibility issues.
- **Preload start pages and New Tab page**: **Yes** (default) uses the OS default behavior, which may be to preload these pages. Preloading minimizes the time to start Microsoft Edge, and load new tabs. **No** prevents Microsoft Edge from preloading start pages and the new tab page.
- **Prelaunch Start pages and New Tab page**: **Yes** (default) uses the OS default behavior, which may be to prelaunch these pages. Pre-launching helps the performance of Microsoft Edge, and minimizes the time required to start Microsoft Edge. **No** prevents Microsoft Edge from pre-launching the start pages and new tab page.

Select **OK** to save your changes.

### Favorites and search

- **Show Favorites bar**: Choose what happens to the favorites bar on any Microsoft Edge page. Your options:
  - **On Start and new Tab pages**: Shows the favorites bar when Microsoft Edge starts, and on all Tab pages. End users can change this setting.
  - **On all pages**: Shows the favorites bar on all pages. End users can't change this setting.
  - **Hidden**: Hides the favorites bar on all pages. End users can't change this setting.
- **Allow changes to favorites**: **Yes** (default) uses the OS default, which allows users to change the list. **No** prevents end users from adding, importing, sorting, or editing the Favorites list.
  - **Favorites List**: Add a list of URLs to the favorites file. For example, add `http://contoso.com/favorites.html`.
- **Sync favorites between Microsoft browsers** (Desktop only): **Yes** forces Windows to synchronize favorites between Internet Explorer and Microsoft Edge. Additions, deletions, modifications, and order changes to favorites are shared between browsers.  **No** (default) uses the OS default, which may give users the choice to sync favorites between the browsers.
- **Default search engine**: Choose the default search engine on the device. End users can change this value at any time. Your options:
  - Search engine in client Microsoft Edge settings
  - Bing
  - Google
  - Yahoo
  - Custom value: In **OpenSearch Xml URL**, enter an HTTPS URL with the XML file that includes the short name and the URL to the search engine, at minimum. For example, enter `https://www.contoso.com/opensearch.xml`.
- **Show search suggestions**: **Yes** (default) lets your search engine suggest sites as you type search phrases in the address bar. **No** prevents this feature.
- **Allow changes to search engine**: **Yes** (default) allows users to add new search engines, or change the default search engine in Microsoft Edge. Choose **No** to prevent users from customizing the search engine.

  This setting is only available when running in [Normal mode (multi-app kiosk)](#use-microsoft-edge-kiosk-mode).

Select **OK** to save your changes.

### Privacy and security

- **Allow InPrivate browsing**: **Yes** (default) allows InPrivate browsing in Microsoft Edge. After closing all InPrivate tabs, Microsoft Edge deletes the browsing data from the device. **No** prevents end users from opening InPrivate browsing sessions.
- **Save browsing history**: **Yes** (default) allow saving the browsing history in Microsoft Edge. **No** prevents saving the browsing history.
- **Clear browsing data on exit** (desktop only): **Yes** clears the history, and browsing data when the user exits Microsoft Edge. **No** (default) uses the OS default, which may cache the browsing data.
- **Sync browser settings between user's devices**: Choose how you want to sync browser settings between devices. Your options:
  - **Allow**: Allow syncing of Microsoft Edge browser settings between user’s devices
  - **Block and enable user override**: Block syncing of Microsoft Edge browser settings between user’s devices. Users can override this setting.
  - **Block**: Block syncing of Microsoft Edge browser setting between users devices. Users can't override this setting.

When "block and enable user override" is selected, user can override admin designation.

- **Allow Password Manager**: **Yes** (default) allows Microsoft Edge to automatically use Password Manager, which allows users to save and manage passwords on the device. **No** prevents Microsoft Edge from using Password Manager.
- **Cookies**: Choose how cookies are handled in the web browser. Your options:
  - **Allow**: Cookies are stored on the device.
  - **Block all cookies**: Cookies aren't stored on the device.
  - **Block only third party cookies**: Third party or partner cookies aren't stored on the device.
- **Allow Autofill in forms**: **Yes** (default) allows users to change autocomplete settings in the browser, and populate form fields automatically. **No** disables the Autofill feature in Microsoft Edge.
- **Send do-not-track headers**: **Yes** sends do-not-track headers to websites requesting tracking info (recommended). **No** (default) does not send headers which allows websites to track the user. User can configure.
- **Show WebRTC localhost IP address**: **Yes** (default) allows users' localhost IP address to be shown when making phone calls using this protocol. **No** prevents users' localhost IP address from being shown. 
- **Allow live tile data collection**: **Yes** (default) allows Microsoft Edge to collect information from Live Tiles pinned to the start menu. **No** prevents collecting this information, which may provide users with a limited experience.
- **User can override certificate errors**: **Yes** (default) allows users to access websites that have Secure Sockets Layer/Transport Layer Security (SSL/TLS) errors. **No** (recommended for increased security) prevents users from accessing websites with SSL or TLS errors.

Select **OK** to save your changes.

### Additional

- **Allow Microsoft Edge browser** (mobile only): **Yes** (default) allows using the Microsoft Edge web browser on the mobile device. **No** prevents using Microsoft Edge on the device. If you choose **No**, the other individual settings only apply to desktop.
- **Allow address bar dropdown**: **Yes** (default) allows Microsoft Edge to show the address bar drop-down with a list of suggestions. **No** stops Microsoft Edge from showing a list of suggestions in a drop-down list when you type. When set to **No**, you:
  - Help minimize network bandwidth between Microsoft Edge and Microsoft services.
  - Disable the **Show search and site suggestions as I type** in Microsoft Edge > Settings.
- **Allow full screen mode**: **Yes** (default) allows Microsoft Edge to use fullscreen mode, which shows only the web content and hides the Microsoft Edge UI. **No** prevents fullscreen mode in Microsoft Edge.
- **Allow about flags page**: **Yes** (default) uses the OS default, which may allow accessing the `about:flags` page. The `about:flags` page allows users to change developer settings and enable experimental features. **No** prevents end users from accessing the `about:flags` page in Microsoft Edge.
- **Allow developer tools**: **Yes** (default) allows users to use the F12 developer tools to build and debug web pages by default. **No** prevents end users from using the F12 developer tools.
- **Allow JavaScript**: **Yes** (default) allows scripts, such as Javascript, to run in the Microsoft Edge browser. **No** prevents Java scripts in the browser from running.
- **User can install extensions**: **Yes** (default) allows end users to install Microsoft Edge extensions on the device. **No** prevents the installation.
- **Allow sideloading of developer extensions**: **Yes** (default) uses the OS default, which may allow sideloading. Sideloading installs and runs unverified extensions. **No** prevents Microsoft Edge from sideloading using the **Load extensions** feature. It doesn't prevent sideloading extensions using other ways, such as PowerShell.
- **Required extensions**: Choose which extensions can't be turned off by end users in Microsoft Edge. Enter the package family names, and select **Add**. [Find a package family name (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) provides some guidance.

  You can also **Import** a CSV file that includes the package family names. Or, **Export** the package family names you enter.

Select **OK** to save your changes.

## Network proxy

These settings use the [NetworkProxy policy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp), which also lists the supported Windows editions.

- **Automatically detect proxy settings**: **Block** disables the device from automatically detecting a proxy auto config (PAC) script. **Not configured** (default) enables this feature. When enabled, the device tries to find the path to a PAC script.
- **Use proxy script**: Choose **Allow** to enter a path to your PAC script to configure the proxy server. **Not configured** (default) doesn't let you enter the URL to a PAC script.
  - **Setup script address URL**: Enter the URL of a PAC script you want to use to configure the proxy server.
- **Use manual proxy server**: Choose **Allow** to manually enter the  name or IP address, and TCP port number of a proxy server. **Not configured** (default) doesn't let you manually enter details of a proxy server.
  - **Address**: Enter the name, or IP address of the proxy server.
  - **Port number**: Enter the port number of your proxy server.
  - **Proxy exceptions**: Enter any URLs that must not use the proxy server. Use a semicolon to separate each item.
  - **Bypass proxy server for local address**: **Not configured** (default) prevents using a proxy server for local addresses on your intranet. **Allow** uses a proxy server for local addresses.

Select **OK** to save your changes.

## Password

These settings use the [DeviceLock policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock), which also lists the supported Windows editions. This policy only applies for local account.

- **Password**: **Require** the end user to enter a password to access the device. **Not configured** (default) allows access to the device without a password.
  - **Required password type**: Choose the type of password. Your options:
    - **Not configured**: Password can include numbers and letters.
    - **Numeric**: Password must only be numbers.
    - **Alphanumeric**: Password must be a mix of numbers and letters.
  - **Minimum password length**: Enter the minimum number or characters required, from 4-16. For example, enter `6` to require at least six characters in the password length.
  - **Number of sign-in failures before wiping device**: Enter the number of authentication failures allowed before the device is wiped, from 1-11. `0` (zero)  may disable the device wipe functionality.

    This setting has a different impact depending on the edition. For specific details, see the [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - **Maximum minutes of inactivity until screen locks**: Enter the length of time a device must be idle before the screen is locked.
  - **Password expiration (days)**: Enter the length of time in days when the device password must be changed, from 1-365. For example, enter `90` to expire the password after 90 days.
  - **Prevent reuse of previous passwords**: Enter the number of previously used passwords that can't be used, from 1-24. For example, enter `5` so users can't set a new password to their current password or any of their previous four passwords.
  - **Require password when device returns from idle state** (Mobile and Holographic): Choose **Require** so users must enter a password to unlock the device after being idle. **Not configured** (default) doesn't require a PIN or password when the device resumes from an idle state.
  - **Simple passwords**: Set to **Block** so users can't create simple passwords, such as `1234` or `1111`. Set to **Not configured** (default) to let users create passwords like `1234` or `1111`. This setting also allows or blocks the use of Windows picture passwords.
- **Automatic encryption during AADJ**: **Block** prevents automatic BitLocker device encryption when the device is prepared for first use, when the device is Azure AD joined. **Not configured** (default) uses the operating system default, which may enable encryption. More on [BitLocker device encryption](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Federal Information Processing Standard (FIPS) policy**: **Allow** uses the Federal Information Processing Standard (FIPS) policy, which is a U.S. government standard for encryption, hashing, and signing. **Not configured** (default) uses the operating system default, which doesn't use FIPS.

  [Cryptography/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello device authentication**: **Allow** users to use a Windows Hello companion device, such as a phone, fitness band, or IoT device, to sign in to a Windows 10 computer. **Not configured** (default) uses the operating system default, which may prevent Windows Hello companion devices from authenticating with Windows.

  [Authentication/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Web sign-in**: Enables Windows sign in support for non-ADFS (Active Directory Federation Services) federated providers, such as Security Assertion Markup Language (SAML). SAML uses secure tokens that provide web browsers a single sign-on (SSO) experience. Your options:

  - **Not configured** (default): Uses the operating system default on the device.
  - **Enabled**: The Web Credential Provider is enabled for sign in.
  - **Disabled**: The Web Credential Provider is disabled for sign in.

  [Authentication/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Preferred Azure AD tenant domain**: Enter an existing domain name in your Azure AD organization. When users in this domain sign in, they don't have to type the domain name. For example, enter `contoso.com`. Users in the `contoso.com` domain can sign in using their user name, such as `abby`, instead of `abby@contoso.com`.

  [Authentication/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

Select **OK** to save your changes.

## Per-app privacy exceptions

You can add apps that should have a different privacy behavior from what you define in “Default privacy”.

- **Package Name**: App package family name.
- **App Name**: The name of the app.

### Exceptions

- **Account information**: Define whether this app can access the user name, picture, and other contact info.
- **Background apps**: Define whether this app can run in the background.
- **Calendar**: Define whether this app can access the calendar.
- **Call history**: Define whether this app can access my call history.
- **Camera**: Define whether this app can access the camera.
- **Contacts**: Define whether this app can access contacts.
- **Email**: Define whether this app can access and send email.
- **Location**: Define whether this app can access location information.
- **Messaging**: Define whether this app can read or send text or MMS messages.
- **Microphone**: Define whether this app can use the microphone.
- **Motion**: Define whether this app can access device motion information.
- **Notifications**: Define whether this app can access notifications.
- **Phone**: Define whether this app can access the phone.
- **Radios**: Some apps use radios (for example, Bluetooth) in your device to send and receive data and need to turn these radios on or off. Define whether this app can control these radios.
- **Tasks**: Define whether this app can access your tasks.
- **Trusted devices**: Choose if this app can use trusted devices. Trusted devices are hardware you've already connected, or hardware that comes with device. For example, use TVs, projectors, and so on, as trusted devices.
- **Feedback and diagnostics**: Define whether this app can access diagnostic information.
- **Sync with devices**: Choose if this app can automatically share and sync info with wireless devices that don't explicitly pair with the device.

Select **OK** to save your changes.

## Personalization

These settings use the [personalization policy CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp), which also lists the supported Windows editions.

- **Desktop background picture URL (Desktop only)**: Enter the URL to a picture in .jpg, .jpeg or .png format that you want to use as the Windows desktop wallpaper. Users can't change the picture. For example, enter `https://contoso.com/logo.png`.

Select **OK** to save your changes.

## Printer

- **Printers**: List of local printers that have been added.
- **Default printer**: Set the default printer.
- **User access to add new printers**: Allow or block use of local printers.

Select **OK** to save your changes.

## Privacy

These settings use the [privacy policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy), which also lists the supported Windows editions.

- **Input personalization**: **Block** prevents prevents using voice for dictation and to talk to Cortana and other apps that use Microsoft cloud-based speech recognition. It's disabled and users can't enable online speech recognition using settings. **Not configured** (default) lets users choose. If you allow these services, Microsoft may collect voice data to improve the service.
- **Automatic acceptance of the pairing and privacy user consent prompts**: Choose **Allow** so Windows can automatically accept pairing and privacy consent messages when running apps. **Not configured** (default) prevents the automatic acceptance of the pairing and privacy user consent window when opening apps.
- **Publish user activities**: **Block** prevents shared experiences and discovery of recently used resources in the activity feed. **Not configured** (default) enables this feature so apps can publish end user activities.
- **Local activities only**: **Block** prevents shared experiences and the discovery of recently used resources in task switcher, based only on local activity. **Not configured** (default) enables this feature.

You can configure information that all apps on the device can access. Also, define exceptions on a per-app basis using **Per-app privacy exceptions**.

Select **OK** to save your changes.

### Exceptions

- **Account information**: Define whether this app can access the user name, picture, and other contact info.
- **Background apps**: Define whether this app can run in the background.
- **Calendar**: Define whether this app can access the calendar.
- **Call history**: Define whether this app can access my call history.
- **Camera**: Define whether this app can access the camera.
- **Contacts**: Define whether this app can access contacts.
- **Email**: Define whether this app can access and send email.
- **Location**: Define whether this app can access location information.
- **Messaging**: Define whether this app can read or send text or MMS messages.
- **Microphone**: Define whether this app can use the microphone.
- **Motion**: Define whether this app can access device motion information.
- **Notifications**: Define whether this app can access notifications.
- **Phone**: Define whether this app can access the phone.
- **Radios**: Some apps use radios (for example, Bluetooth) in your device to send and receive data and need to turn these radios on or off. Define whether this app can control these radios.
- **Tasks**: Define whether this app can access your tasks.
- **Trusted devices**: Choose if this app can use trusted devices. Trusted devices are hardware you've already connected, or hardware that comes with the device. For example, use TVs, projectors, and so on, as trusted devices.
- **Feedback and diagnostics**: Choose if this app can access diagnostic information.
- **Sync with devices** -Define whether this app can automatically share and sync info with wireless devices that don't explicitly pair with this PC, tablet, or phone.

Select **OK** to save your changes.

## Projection

These settings use the [WirelessDisplay policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay), which also lists the supported Windows editions.

- **User input from wireless display receivers**: **Block** prevents user input from wireless display receivers. **Not configured** (default) allows a wireless display to send keyboard, mouse, pen, and touch input back to the source device.
- **Projection to this PC**: **Block** prevents other devices from finding the device for projection. **Not configured** (default) allows the device to be discoverable, and can project to the device above the lock screen.
- **Require PIN for pairing**: Choose **Require** to always prompt for a PIN when connecting to a projection device. **Not configured** (default) doesn't require a PIN to pair the device to a projection device.

Select **OK** to save your changes.

## Reporting and telemetry

- **Share usage data**: Choose the level of diagnostic data that's submitted. Your options:
  - **Not configured**: No data is shared.
  - **Security**: Information that's required to help keep Windows more secure, including data about the Connected User Experience and Telemetry component settings, the Malicious Software Removal Tool, and Windows Defender.
  - **Basic**: Basic device info, including quality-related data, app compatibility, app usage data, and data from the Security level.
  - **Enhanced**: Additional insights, including: how Windows, Windows Server, System Center, and apps are used, how they perform, advanced reliability data, and data from both the Basic and the Security levels.
  - **Full**: All data necessary to identify and help to fix problems, plus data from the Security, Basic, and Enhanced levels.

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Send Microsoft Edge browsing data to Microsoft 365 Analytics**: To use this feature, set the **Share usage data** settings to **Enhanced** or **Full**. This feature controls what data Microsoft Edge sends to Microsoft 365 Analytics for enterprise devices with a configured commercial ID. Your options:
  - **Not configured**: Uses the OS default, which may not send any browsing history data
  - **Only send intranet data**: Allows the administrator to send intranet data history
  - **Only send internet data**: Allows the administrator to send internet data history
  - **Send intranet and internet data**: Allows the administrator to send intranet and internet data history

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Telemetry proxy server**: Enter the fully qualified domain name (FQDN) or IP address of a proxy server to forward Connected User Experiences and Telemetry requests, using a Secure Sockets Layer (SSL) connection. The format for this setting is *server*:*port*. If the named proxy fails, or if a proxy isn't entered when enabling this policy, the Connected User Experiences and Telemetry data isn't sent, and stays on the local device.

  Example formats:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

Select **OK** to save your changes.

## Search

These settings use the [search policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search), which also lists the supported Windows editions. 

- **Safe Search (mobile only)**: Control how Cortana filters adult content in search results. Your options:
  - **User defined**: Allow end users to choose their own settings.
  - **Strict**: Highest filtering against adult content.
  - **Moderate**: Moderate filtering against adult content. Valid search results aren't filtered.
- **Display web results in search**: When set to **Block**, users can't search, and web results aren't shown in Search. **Not configured** (default) allows users to search the web, and the results are shown on the device.

Select **OK** to save your changes.

## Start

These settings use the [start policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start), which also lists the supported Windows editions.  

- **Start menu layout**: Override the default start layout and customize the start menu on desktop devices. Upload an XML file that includes your customizations, including the order the apps are listed, and more. Users can't change the start menu layout you enter.
- **Pin websites to tiles in Start menu**: Import images from Microsoft Edge that are shown as links in the Windows Start menu for desktop devices.
- **Unpin apps from task bar**: **Block** prevents users from unpinning apps from the task bar. **Not configured** (default) allows users to unpin apps from the task bar.
- **Fast user switching**: **Block** prevents switching between users that are logged on simultaneously without logging off. **Not configured** (default) shows the **Switch user** on the user tile.
- **Most used apps**: **Block** hides the most used apps from showing on the start menu. It also disables the corresponding toggle in the Settings app. **Not configured** (default) shows the most used apps.
- **Recently added apps**: **Block** hides recently added apps from showing on the start menu. It also disables the corresponding toggle in the Settings app. **Not configured** (default) shows the recently added apps on the start menu.
- **Start screen mode**: Choose how the start screen is shown. Your options:
  - **User defined**: Doesn't force the size of Start. Users can set the size.
  - **Full screen**: Forces a fullscreen size of Start.
  - **Non-full screen**: Force non-fullscreen size of Start.
- **Recently opened items in Jump Lists**: **Block** hides recent jump lists from being shown on the start menu and taskbar. It also disables the corresponding toggle in the Settings app. **Not configured** (default) shows recently opened items in the jumplists.
- **App list**: Choose how the all apps lists are shown. Your options:
  - **User defined**: No setting is forced. Users choose how the app list is shown on the device.
  - **Collapse**: Hide all apps list.
  - **Collapse and disable the Settings app**: Hide all apps list, and disable **Show app list in Start menu** in the Settings app.
  - **Removes and disables the Settings app**: Hide all apps list, remove all apps button, and disable **Show app list in Start menu** in the Settings app.
- **Power button**: **Block** hides the power button from showing in the start menu. **Not configured** (default) shows the power button.
- **User Tile**: **Block** hides the user tile from showing in the start menu. **Not configured** (default) shows the user tile, and also sets the following settings:
  - **Lock**: **Block** hides the **Lock** option from showing in the user tile in the start menu. **Not configured** (default) shows the **Lock** option.
  - **Sign out**: **Block** hides the **Sign out** option from showing in the user tile in the start menu. **Not configured** (default) shows the **Sign out** option.
- **Shut Down**: **Block** hides the **Update and shut down** and **Shut down** options from showing in the power button in the start menu. **Not configured** (default) shows these options.
- **Sleep**: **Block** hides the **Sleep** option from showing in the power button in the start menu. **Not configured** (default) shows this option.
- **Hibernate**: **Block** hides the **Hibernate** option from showing in the power button in the start menu. **Not configured** (default) shows this option.
- **Switch Account**: **Block** hides the **Switch account** from showing in the user tile in the start menu. **Not configured** (default) shows this option.
- **Restart Options**:  **Block** hides the **Update and restart** and **Restart** options from showing in the power button in the start menu. **Not configured** (default) shows these options.
- **Documents on Start**: Hide or show the Documents folder in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **Downloads on Start**: Hide or show the Downloads folder in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **File Explorer on Start**: Hide or show File Explorer in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **HomeGroup on Start**: Hide or show the HomeGroup shortcut in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **Music on Start**: Hide or show the Music folder in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **Network on Start**: Hide or show Network in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **Personal folder on Start**: Hide or show Personal folder in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **Pictures on Start**: Hide or show the folder for pictures in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **Settings on Start**: Hide or show the Settings shortcut in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.
- **Videos on Start**: Hide or show the folder for videos in the Windows Start menu. Your options:
  - **Not configured** (default): No setting is forced. Users choose to show or hide the shortcut.
  - **Hide**: The shortcut is hidden, and disables the setting in the Settings app.
  - **Show**: The shortcut is shown, and disables the setting in the Settings app.

Select **OK** to save your changes.

## Windows Defender Smart Screen

- **SmartScreen for Microsoft Edge**: **Require** turns off Windows Defender SmartScreen and prevent users from turning it on. **Not configured** (default) turns on SmartScreen. Helps protect users from potential threats and prevent users from turning it off.

  Microsoft Edge uses Windows Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software.

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Malicious site access**: **Block** prevents users from ignoring the Windows Defender SmartScreen Filter warnings, and blocks them from going to the site. **Not configured** (default) allows users to ignore the warnings, and continue to the site.

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **Unverified file download**: **Block** prevents users from ignoring the Windows Defender SmartScreen Filter warnings, and block them from downloading unverified files. **Not configured** (default) allows users to ignore the warnings, and continue to download the unverified files.

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

Select **OK** to save your changes.

## Windows Spotlight

These settings use the [experience policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), which also lists the supported Windows editions.

- **Windows Spotlight**: **Block** turns off Windows spotlight on the lock screen, Windows Tips, Microsoft consumer features, and other related features. If your goal is to minimize network traffic from devices, set this to **Block**. **Not configured** (default) allows Windows spotlight features and may be controlled by end users. When enabled, you can also allow or block the following settings:

  - **Windows Spotlight on lock screen**: **Block** stops Windows Spotlight from showing information on the device lock screen. **Not configured** (default) enables this feature.
  - **Third-party suggestions in Windows Spotlight**: **Block** stops Windows Spotlight from suggesting content that isn't published by Microsoft. **Not configured** (default) allows app and content suggestions from partner software publishers in Windows spotlight features, like lock screen spotlight, suggested apps in the Start menu, and Windows tips.
  - **Consumer Features**: **Block** turns off experiences that are typically for consumers only, such as start suggestions, membership notifications, post-out of box experience app installation, and redirect tiles. **Not configured** (default) allows these features.
  - **Windows Tips**: **Block** disables pop-up Windows Tips. **Not configured** (default) allows the Windows Tips to show.
  - **Windows Spotlight in action center**: **Block** prevents Windows spotlight notifications from showing in the Action Center. **Not configured** (default) may show notifications in the Action Center that suggest apps or features to help users be more productive on Windows.
  - **Windows Spotlight personalization**: **Block** prevents Windows from using diagnostic data to provide customized experiences to the user. **Not configured** (default) allows Microsoft to use diagnostic data to provide personalized recommendations, tips, and offers to tailor Windows for the user's needs.
  - **Windows welcome experience**: **Block** turns off the Windows spotlight Windows welcome experience feature. The Windows welcome experience won't show  when there are updates and changes to Windows and its apps. **Not configured** (default) allows Windows welcome experience that shows the user information about new, or updated features.

Select **OK** to save your changes.

## Windows Defender Antivirus

These settings use the [defender policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender), which also lists the supported Windows editions.

- **Real-time monitoring**: **Enable** prevents real-time scanning for malware, spyware, and other unwanted software. **Not configured** (default) allows this feature.
- **Behavior monitoring**: **Enable** prevents Defender check for certain known patterns of suspicious activity on devices. **Not configured** (default) allows Windows Defender Behavior Monitoring.
- **Network Inspection System (NIS)**: NIS helps to protect devices against network-based exploits. It uses the signatures of known vulnerabilities from the Microsoft Endpoint Protection Center to help detect and block malicious traffic.
- **Scan all downloads**: Controls whether Defender scans all files downloaded from the Internet.
- **Scan scripts loaded in Microsoft web browsers**: **Not configured** (default) lets Defender scan scripts that are used in Internet Explorer. **Enable** prevents this scanning.
- **End user access to Defender**: **Block** hides the Windows Defender user interface from end users. All Windows Defender notifications are also suppressed. **Not configured** (default) allows user access to the Windows Defender UI. When this setting is changed, it takes effect the next time the end user's PC is restarted.
- **Signature update interval (in hours)**: Enter the interval that Defender checks for new signature files, from 0-24. Your options:

  - **Not configured** (default)
  - **Do not check**: Defender doesn't check for new signature files.
  - **1-24**: `1` checks every hour, `2` checks every two hours, `24` checks every day, and so on.
- **Monitor file and program activity**: Allows Defender to monitor file and program activity on devices.
- **Days before deleting quarantined malware**: Continue tracking resolved malware for the number of days you enter so you can manually check previously affected devices. If you set the number of days to **0**, malware stays in the Quarantine folder, and isn't automatically removed. When set to `90`, quarantine items are stored for 90 days on the system, and then removed.
- **CPU usage limit during a scan**: Limit the amount of CPU that scans are allowed to use, from **1** to **100**.
- **Scan archive files**: **Enable** prevents Defender from scan archived files, such as Zip or Cab files. **Not configured** (default) allows this scanning.
- **Scan incoming mail messages**: **Enable** prevents email scanning. **Not configured** (default) allows Defender to scan email messages as they arrive on the device.
- **Scan removable drives during a full scan**: **Enable** prevents full scans of removable drives. **Not configured** (default) lets Defender scan removable drives, such as USB sticks.
- **Scan mapped network drives during a full scan**: **Enable** lets Defender scan files on mapped network drives. **Not configured** (default) prevents the full scan. If the files on the drive are read-only, Defender can't remove any malware found in them.
- **Scan files opened from network folders**: **Not configured** (default) lets Defender scan files on shared network drives, such as files accessed from a UNC path. **Enable** prevents this scanning. If the files on the drive are read-only, Defender can't remove any malware found in them.
- **Cloud protection**: **Not configured** (default) allows the Microsoft Active Protection Service to receive information about malware activity from devices that you manage. **Enable** blocks this feature.
- **Prompt users before sample submission**: Controls whether potentially malicious files that might require further analysis are automatically sent to Microsoft. Your options:
  - **Not configured**
  - **Always prompt**
  - **Prompt before sending personal data**
  - **Never send data**
  - **Send all data without prompting**: Data is sent automatically

- **Time to perform a daily quick scan**: Choose the hour to run a daily quick scan. **Not configured** doesn't run a daily scan. If you want more customization, configure the **Type of system scan to perform** setting.

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

  > [!WARNING]
  > This setting in Intune in the Azure portal may show a Failed status. This is a bug with the reporting feature. After reproducing the behavior and troubleshooting, the Intune product group confirmed that the status is actually a Success. The reporting bug will be fixed in an upcoming release. There isn't a current ETA, as timelines change. Any updates to this feature are announced in [In development for Microsoft Intune](in-development.md).

- **Type of system scan to perform**: Schedule a system scan, including the level of scanning, and the day and time to run the scan. Your options:
  - **Not configured**: Doesn't schedule a system scan on the device. End users can manually run scans as needed or wanted on their devices.
  - **Disable**: Disables any system scanning on the device. Choose this option if you're using a partner anti-virus solution that scans devices.
  - **Quick scan**: Looks at common locations where there could be malware registered, such as registry keys and known Windows startup folders.
    - **Day scheduled**: Choose the day to run the scan.
    - **Time scheduled**: Choose the hour to run the scan.
  - **Full scan**: Looks at common locations where there could be malware registered, and also scans every file and folder on the device.
    - **Day scheduled**: Choose the day to run the scan.
    - **Time scheduled**: Choose the hour to run the scan.

  This setting may conflict with the **Time to perform a daily quick scan** setting. Some recommendations:

  - To run a daily quick scan, configure the **Time to perform a daily quick scan** setting.
  - To run a daily quick scan and a full scan every week, then configure the **Time to perform a daily quick scan**. Set **Type of system scan to perform** to a full scan with the day and time.
  - Don't configure the **Time to perform a daily quick scan** setting simultaneously with the **Type of system scan to perform** set to **Quick scan**. These settings may conflict, and a scan may not run.
  - To run a quick scan every Tuesday at 6 AM, configure the **Type of system scan to perform** setting.

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

  > [!WARNING]
  > This setting in Intune in the Azure portal may show a Failed status. This is a bug with the reporting feature. After reproducing the behavior and troubleshooting, the Intune product group confirmed that the status is actually a Success. The reporting bug will be fixed in an upcoming release. There isn't a current ETA, as timelines change. Any updates to this feature are announced in [In development for Microsoft Intune](in-development.md).

- **Detect potentially unwanted applications**: Choose the level of protection when Windows detects potentially unwanted applications. Your options:
  - **Not configured** (default): Windows Defender potentially unwanted applications protection is disabled.
  - **Block**: Windows Defender detects potentially unwanted applications, and detected items are blocked. These items show in history along with other threats.
  - **Audit**: Windows Defender detects potentially unwanted applications, but takes no action. You can review information about the applications Windows Defender would take action against. For example, search for events created by Windows Defender in the Event Viewer.

  For more information about potentially unwanted apps, see [Detect and block potentially unwanted applications](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).

- **Actions on detected malware threats**: Choose the actions you want Defender to take for each threat level it detects: low, moderate, high, and severe. Your options:
  - **Clean**
  - **Quarantine**
  - **Remove**
  - **Allow**
  - **User defined**
  - **Block**

Select **OK** to save your changes.

### Windows Defender Antivirus Exclusions

- **Files and folders to exclude from scans and real-time protection**: Adds one or more files and folders like **C:\Path** or **%ProgramFiles%\Path\filename.exe** to the exclusions list. These files and folders aren't included in any real-time or scheduled scans.
- **File extensions to exclude from scans and real-time protection**: Add one or more file extensions like **jpg** or **txt** to the exclusions list. Any files with these extensions aren't included in any real-time or scheduled scans.
- **Processes to exclude from scans and real-time protection**: Add one or more processes of the type **.exe**, **.com**, or **.scr** to the exclusions list. These processes aren't included in any real-time, or scheduled scans.

Select **OK** to save your changes.

## Next steps

For additional technical details on each setting and what editions of Windows are supported, see [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)
