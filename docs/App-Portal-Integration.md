# App Connection Portal

Check out the [App Connection Overview](App-Connection-Overview.md) page for an overview of the App Connection entire system. 

The App Connection Portal has the following goals:

1)	Be a great and easy experience for users.
2)	Be an easy and complete app developer integration tool.
3)	Be robust and complete - able to handle all types user scenarios.

### Cool! What does it look like?

[Give it a try!](https://octoeverywhere.com/appportal/v1/?appid=devtest&authType=none) 

**Note:** The experience is optimized for mobile / tablet layouts.

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



### A Few Important Notes

- The portal is in it's early days and I would love feedback!
  - I would be happy to take any feedback relating to the portal flows or how I could change the process to help you achieve a more seamless intergration!
- The `appApiToken` and `auth*` parameters returned on the completion URL will only be given to you app once, and can not be queried from OctoEverywhere again. If they are lost, a new App Conneciton must be made.
- The portal **does not** return the OctoPrint Global API key.
  - I talked it over with the OctoPrint developers and since the global API key is deprecated and will be removed in future releases, they discouraged sending it. 
  - If your app doesn't already have access to the OctoPrint instance, you will need to do the OctoPrint App Key flow as you normally would when connecting locally.
    - More information on the OctoPrint App Key process can be [found here](https://docs.octoprint.org/en/master/bundledplugins/appkeys.html)
  - In the future, I will look into possibly auto creating App Keys on your behalf in OctoPrint, but that's not possible right now.

### Starting An App Connection Portal

To start a portal, you should open an in app web view and navigate to the following URL with the required and optiaonl GET parameters:
https://octoeverywhere.com/appportal/v1/

All of the required and optional GET parameters can be found in the [API doc for Starting An App Portal.](../reference/App-Connection.v1.yaml/paths/~1appportal~1v1/get)

Example: https://octoeverywhere.com/appportal/v1/?appid=devtest&authType=simple

### Handling Portal Completion

On successful or failure completion, the portal will navigate to `appportal/v1/complete` or the specified `returnUrl` with the resulting GET parameters. Your app should monitor the web view's navigation and when it sees the completion URL handle the portal result.

All of the return GET parameters can be found in the [API doc for the App Portal Completion URL.](../reference/App-Connection.v1.yaml/paths/~1appportal~1v1/get)

Remember that the `appApiToken` and `auth*` parameters will only be returned this one time and cannot be retrieved again. If you lose them, you must make a new App Connection.

<!-- ### Cool Right? Let's Talk Intergration!

There are a few basic user states to consider:

- Users Who Are New To Your App
  - User's who have OctoEverywhere setup already
  - User's who don't have OctoEverwhere setup already
- Extisting Users Of Your App
  - User's who have OctoEverywhere setup already
  - User's who don't have OctoEverwhere setup already
 -->