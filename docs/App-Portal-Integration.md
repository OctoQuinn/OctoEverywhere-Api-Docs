# App Connection Portal Integration

### Overview

Check out the [App Connection Overview](App-Connection-Overview.md) page for an overview of the entire system. 

The App Connection portal has the following goals:

1)	Be a great and easy experience for users.
2)	Be an easy and complete app developer integration tool.
3)	Be robust and complete, able to handle all types user scenarios.


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

To start a portal, you should open an in app web view and navigate to the following URL with the required and optiaonl GET parameters.
https://octoeverywhere.com/appportal/v1/

For types and syntax of the GET parameters, see [this API doc](../reference/App-Connection.v1.yaml/paths/~1appportal~1v1/get)

#### Portal Starting Page GET Parameters

#### appId
The App ID is a string that's assinged to your app by OctoEverywhere. This is used to track which App Connections are created by which apps, and also used to add your app name to the UI. Please contact Quinn if you need an App ID assinged. 

#### authType
The authenciation type determins what type of auth will be required for this app connection. There are three possible values of which you can choose one.

1) `none`
    1) **NOT RECOMENDED** - Should only be used if you can't support basic http auth or a bearer token.

Example: https://octoeverywhere.com/appportal/v1/?appid=devtest&authType=none

The types 


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

#### authType

Info abobut hte auth type

Users might discovered your app either from the OctoEverywhere set