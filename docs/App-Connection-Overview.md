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

### Cool! What does it look like?

[Give it a try!](https://octoeverywhere.com/appportal/v1/?appid=devtest&authType=none) 

Note that the experience is optimized for mobile / tablet layouts.

#### A High Level User Experience
1) A user of your app want's to setup a remote connection to their printer with OctoEverywhere.
2) The user sees an in-app web view of the OctoEverywhere App Connection Portal
    1) The user sees a welcome message
    2) Optional flows depending on the user's state:
          1) If the user doesn't have an OctoEveywhere account... the portal will help them create one.
          2) If the user doesn't have a printer connected to OctoEverywhere... the portal will walk them through the 2 minute setup.
          3) If the user isn't an OctoEverywhere supporter... the portal will describe why a supporter role is required (for now) and will help them upgrade if they desire.
    5) The user confirms the printer they want to connect to and authorizes the app to connect.
6) The web portal closes and the user can now use the full app from anywhere!

#### A High Level Example App Integration
1) A user of your app want's to setup a remote connection to their printer with OctoEverywhere.
2) Your app opens a in-app web view and navigates to the OctoEverywhere App portal starting URL.
    1) Your app passes a few GET parameters to setup the App Connection portal
3) Your app watches the navigations of the web view until the portal navigates to the completion URL.
4) Your app reads the returned GET parameters from the completion URL
5) Your app uses the returned base URL to connect to the printer from anywhere!

### App Connection Life Cycle

An App Connection is created when a portal flow is successful. The credentials and context of an App Connections gives your app access to only a single printer for a given user. If a user want's set up multiple printers, they will all be unique sets of App Connection contexts.

Once created, an App Connection context and credentials remain valid until:
1) The user deletes their OctoEverywhere account.
2) The user removes the printer from their account.
3) The user revokes the App Connection from the OctoEverywhere website.

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

