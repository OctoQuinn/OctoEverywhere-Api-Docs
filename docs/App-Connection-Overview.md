# App Connection Overview

### What is an App Connection?

An App Connection is a 3rd party app integration with OctoEverywhere that allows any OctoPrint app to leverage OctoEverywhere for remote access to user’s printers. App Connections enable a great partnership between 3rd party apps and OctoEverywhere for our users, allowing users to use the best OctoPrints apps for remote monitoring and control with a super easy and seamless setup.

#### Benefits to Your App:
- Apps that integrated App Connections will be advertised on the OctoEverywhere website as being integrated with OctoEverywhere.
- Many OctoEverywhere users now have the ability to monitor on-the-go where they hadn’t before and are looking for the best OctoPrint apps on all platforms to make that experience better.
- Your existing users will have a safe and secure remote access option that full works with your app.

#### OctoEverywhere Offers Your App:
- Very easy and straight forward developer integration.
  - OctoEverywhere offers a fully ready to use portal, which handles user login, user account setup, user printer setup, and more.
  - Once setup, you can use all of your existing OctoPrint connection logic. OctoEverywhere simply gives you a unique hostname you can use to access the users' OctoPrint instance.
-	Full access to the OctoPrint instance, the exact same raw access you would have to all the APIs, web sockets, and webcam streams as you would have on a local connection. 
-	A full secure managed connection to OctoPrint. You can choose domain name security, basic http auth, or Bearer tokens for added security. 
-	OctoEverywhere app APIs that allow you to query information about the printer from OctoEverywhere, including it’s current local IP, it’s connection state to OctoEverywhere, and the user’s current limits.

### What Options Do I Have For Integration?

App Connections currently offer four integration points:

1) The App Connection - Gives you a secure and unique hostname to connect to your user's printer from anywhere.
2) [The App Connection Portal](App-Portal-Integration.md) - An "OAuth style" OctoEverywhere hosted portal developers can leverage for quick and easy App Connection creation.
3) [The App Connection OctoEverywhere APIs](App-OctoEverywhere-API.md) - A set of APIs from OctoEverywhere's service that return real-time information about the connected printer.
4) [The OctoEverywhere OctoPrint Plugin Local API](App-Local-Plugin-API.md)  - A simple API that allows local detection of the OctoEverywhere plugin and printer information.

### App Connection Life Cycle

An App Connection is created when a portal flow is successful. The credentials and context of an App Connections gives your app access to only a single printer for a given user. If a user want's set up multiple printers, they will all be unique sets of App Connection contexts.

Once created, an App Connection context and credentials remain valid until:
1) The user deletes their OctoEverywhere account.
2) The user removes the printer from their account.
3) The user revokes the App Connection from the OctoEverywhere website.
4) The user's account downgrades from being a supporter.

You can use the OctoEverywhere APIs described below to query OctoEverywhere for the state an App Connection at anytime.

### Authentication Types

App Connections support three types of authentication. Every app connection starts with a unique and high-entropy subdomain being generated. This keeps the connection secure, however the DNS name is transmitted in the clear for DNS resolution, so it can be sniffed during a man in the middle attack. For that reason, **we highly recommend you use either basic http auth or bearer token auth if possible.** These two systems are encrypted end-to-end and are 100% secure.

If you chose to use enhanced security, you will need to add **either** the basic http auth header or the bearer auth header to all of your HTTP and websocket calls. 

The authentication type is specified at the start of an App Connection Portal flow. For details see the [App Portal Integration](App-Portal-Integration.md) page.

### Give Me Feedback!

This entire thing was created for you, the developer, to make your life easier. If there are any changes or tweaks I can make to anything in this process, please let me know.

### Sounds Great! Let's Integrate!

#### Step 1 - Integrate the Portal

For all-of-the-details-you-could-ever-want about the portal integration, [look here](App-Portal-Integration.md).

#### Step 2 - (optional) - Integrate with OctoEverywhere APIs

The OctoEverywhere App APIs give you access to real-time details for a printer once it has been setup via the portal. This information can be used to make sure the App Connection is still valid, check if the printer is connected to OctoEverywhere, get the printer's local IP address, and get user usage limits. 
 
For all-of-the-details-you-could-ever-want about the poral integration, [look here](App-OctoEverywhere-API.md).

