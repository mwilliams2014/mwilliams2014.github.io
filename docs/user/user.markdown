---
layout: page
title: User Guide
permalink: /user/quickstart/
---

# Connecting to Your ownCloud Server on Desktop and Mobile

While you can connect to ownCloud in your browser via the [Web interface](https://doc.owncloud.com/server/10.3/user_manual/files/webgui/overview.html),
the desktop and mobile clients provide additional features that can make the
process easier. This quickstart guide shows you how to connect to your ownCloud
server through these clients so you can get started using these features in no
time:

- [Connecting with the Desktop Client](#Connecting with the Desktop Client)
- [Connecting with Android](#connecting-to-owncloud-on-android)
- [Connecting with iOS](#connecting-to-owncloud-on-ios)

## Connecting with the Desktop Client

The Desktop Client provides these key benefits:

- Specify one or more directories on your computer that you want to synchronize
  to the ownCloud server.
- Always have the latest files synchronized, wherever they are located.

The Desktop Client is available for Windows, Mac OS, and Linux. Confirm that
your system meets the [requirements](https://doc.owncloud.com/desktop/2.5/installing.html#system-requirements),
then follow these steps to connect to the ownCloud Desktop client:

1.  Download the latest version of the ownCloud Desktop Synchronization Client
    from the [ownCloud download page](https://owncloud.com/download/#desktop-clients)
    for your OS, and follow any additional instructions provided.

2.  Run the [Installation Wizard](https://doc.owncloud.com/desktop/2.5/installing.html#installation-wizard)
    to install the Client.

      a. Enter the URL of your ownCloud server.

      ![step 1](../images/client-1.png)

      b. Next, enter your ownCloud login information.

      ![step 2](../images/client-2.png)

      c. On the *"Local Folder Option"* screen, choose whether to sync all of
         your files on the ownCloud server, or select individual folders. The
         default local sync folder is `ownCloud`, in your home directory, but
         you can change that here if you want.

      ![step 3](../images/client-3.png)

      d. Once your sync folders are configured, click the *"Connect"* button at
         the bottom right. The client attempts to connect to your ownCloud
         server, and when it is successful your files will start syncing, and
         you'll see two buttons:

      - one to connect to your ownCloud Web GUI
      - one to open your local folder

>**Note:** If on Linux, make sure you have a password manager enabled, such as
[GNOME Keyring](https://wiki.gnome.org/Projects/GnomeKeyring/) or [KWallet](https://utils.kde.org/projects/kwalletmanager/),
so that the sync client can login automatically.

>**Note:** By default, the ownCloud Client schedules a reboot after installation to
make sure the Explorer extension is correctly (un)loaded. If you need to
override this behavior, follow the instructions in the
[No Reboot After Installation](https://doc.owncloud.com/desktop/2.5/installing.html#no-reboot-after-installation)
section.

This quickstart guide merely touched the surface of what's available with the
Desktop client. See the [ownCloud Desktop Client documentation](https://doc.owncloud.com/desktop/2.5/)
for more information.

## Connecting with a Mobile Client

The ownCloud mobile Client is available for Android and iOS. Instructions for
both devices are shown below.

### Connecting to ownCloud on Android

The Android ownCloud app provides some notable advantages over the Web
interface:

- A simplified interface that fits nicely on a tablet or smartphone
- Automatic synchronization of your files
- Share files with other ownCloud users and groups, and create multiple public
  share links
- Upload of photos and videos recorded on your Android device
- Easily add files from your device to ownCloud
- Two-factor authentication

Follow these steps to access your ownCloud server on Android:

1.  Download the app from the [Google Play Store](https://play.google.com/store/apps/details?id=com.owncloud.android).

2.  Install the app.

    >**Note:** Users of customized ownCloud Android apps, for example from their
    employer, should follow their employer's instructions.

3.  The first time you run your ownCloud Android app, it opens to a
    configuration screen. Enter your server URL, login name, password, and click
    the **[Connect]** button. Click the **[eyeball]** to the right of your
    password to expose your password.

    ![Android Login](../images/android-2.png)

4.  Your ownCloud server should be [SSL-enabled](http://info.ssl.com/article.aspx?id=10241)
    so you can connect securely via HTTPS. If your server has a
    [self-signed SSL certificate](https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-16-04),
    you'll get a warning that you can't trust it. If this occurs, click the
    **[YES]** button to trust the certificate and complete your account setup.

    ![Trust Certificate](../images/android-3.png)

Great! Your account is set up and you can now sync files to your Android device
with your ownCloud server. See the [ownCloud Android app documentation](https://doc.owncloud.com/android/)
for more information.

![ownCloud Android App](../images/android-all-files-overview.png)

### Connecting to ownCloud on iOS

The iOS ownCloud app provides advantages over the Web interface that you should
consider:

- A simplified interface that fits nicely on an iPhone or iPad
- Automatic synchronization of your files
- Share files with other ownCloud users
- Easily upload files from your device to ownCloud
- Optional PIN for stronger security

Follow these steps to access your ownCloud server on iOS:

1.  Download the app from the [App Store](https://apps.apple.com/app/id1359583808?ls=1).

2.  Install the app.

3.  Open the app and provide your ownCloud server and login information.

4.  Once you're connected, your presented with your Files page.

    ![iOS Files Page](../images/ios-files-list.png)

Great! Your account is set up and you can now sync files to your iOS device
with your ownCloud server. See the [ownCloud iOS app documentation](https://doc.owncloud.com/ios/)
for more information.
