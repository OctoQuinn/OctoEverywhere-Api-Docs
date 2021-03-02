# App Connection Overview

### What is an App Connection?

An App Connection is a 3rd party app integration with OctoEverywhere that allows any OctoPrint app to leverage OctoEverywhere for remote access to user’s printers. App Connections enable a great partnership between 3rd party apps and OctoEverywhere for our users, allowing users to use the best OctoPrints apps for remote monitoring and control with a super easy and seamless setup.

#### Benefits to Your App:
- Apps that integrated App Connections will be advertised on the OctoEverywhere website as being integrated with OctoEverywhere.
- Many OctoEverywhere users now have the ability to monitor on-the-go where they hadn’t before and are looking for the best OctoPrint apps on all platforms to make that experience better.
- Your existing users will have a safe and secure remote access option that full works with your app.

#### OctoEverywhere Offers Your App:
- Very easy and straight forward developer intergration.
  - OctoEverywhere offers a fully ready to use portal, which handles user login, user account setup, user printer setup, and more.
  - Once setup, you can use all of your existing OctoPrint connection logic. OctoEverywhere simply gives you a unique hostname you can use to access the users's OctoPrint instance.
-	Full access to the OctoPrint instance, the exact same raw access you would have to all the APIs, web sockets, and webcam streams as you would have on a local connection. 
-	A full secure managed connection to OctoPrint. You can choose domain name security, basic http auth, or Bearer tokens for added security. 
-	OctoEverywhere app APIs that allow you to query information about the printer from OctoEverywhere, including it’s current local IP, it’s connection state to OctoEverywhere, and the user’s current limits.

### Cool! What does it look like?

[Give it a try!](https://octoeverywhere.com/appportal/v1/?appid=devtest&authType=none) 

Note that the experance is optimzied for mobile / tablet layouts.

### Cool Right? Let's Talk Intergration!

There are a few basic user states to consider:

- Users Who Are New To Your App
  - User's who have OctoEverywhere setup already
  - User's who don't have OctoEverwhere setup already
- Extisting Users Of Your App
  - User's who have OctoEverywhere setup already
  - User's who don't have OctoEverwhere setup already

With this intergration flow, we try to address all of these secnarios. Let's discuss each.

#### Users Who Are New To Your App

##### Who Already Have OctoEverywher Setup

Users might discovered your app either from the OctoEverywhere set
