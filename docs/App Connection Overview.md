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


#### A High Level Example App Intergration/Flow
1) A user of your app want's to setup a remote connection to their printer with OctoEverywhere.
2) Your app opens a in-app web view and navigates to the OctoEverywhere App portal URL.
3) The OctoEverywhere Portal will handle...
   1) Show the user a biref welcome message
   2) Optional flows depending on the user's state:
      1) If the user doesn't have an OctoEveywhere account... the portal will help them create one.
      2) If the user doesn't have a printer conneted to OctoEverywhere... the portal will walk them through the 2 minute setup.
      3) If the user isn't an OctoEverywhere supporter... the portal will describe why a supporter role is required (for now) and will help them upgrade if they desire.
   3) The portal will show a message allowing the user to confirm which printer they want to connect and asking the user to authorize and finish the connection.
4) The conneciton will be created and the details will be passed back to the app as GET parameters on the requested final URL.
5) Your app reads the parameters, sets the correct remote hostname, optionally set the correct authenction systems, and is done!

### App Connection Life Cycle

An App Connection is created when a portal flow is successful. The credentails and context of an App Connections gives your app access to only a single printer for a given user. If a user want's set up multipe printers, they will all be unique sets of App Connection contexts.

Once created, an App Connection context and credentails remain valid until:
1) The user deletes their OctoEverywhere account.
2) The user removes the printer from their account.
3) The user revokes the App Connection from the OctoEverywhere website.

You can use the OctoEverywhere APIs described below to query OctoEverywhere for the state an App Connection at anytime.

### Sounds Great! Let's Integrate!

There's one intergration you need to do and one intergration that's optional.

#### Step 1 - Intergrate the Portal

For all-of-the-details-you-could-ever-want about the portal intergration, go here.

#### Step 2 - (optional) - Intergrate with OctoEverywhere APIs

The OctoEverywhere App APIs give you access to realtime details for a printer once it has been setup via the portal. This information can be used to make sure the App Connection is still valid, check if the pritner is connected to OctoEverywhere, get the printer's local IP addreess, and get user usage limits. 
 
For all-of-the-details-you-could-ever-want about the poral intergration, go here.

