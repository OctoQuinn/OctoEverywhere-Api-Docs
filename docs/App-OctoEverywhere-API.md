# App Connection API

Check out the [App Connection Overview](App-Connection-Overview.md) page for an overview of the App Connection entire system. 

The OctoEverywhere App API allows apps to get information from the OctoEverywhere service relating to an existing App Connection they have established.

Right now the information that can be queried is limited, but it can be expanded in the future. If there's any functionatliy of information you would like to see added to better your app, please reachout and we can discuss it. 

### The Info API

[Documentation](../reference/App-Connection.v1.yaml/paths/~1appportal~1v1/get)

The `info` API returns you all kinds of good stuff about the current state of the printer. There are two main uses:

1) Determine the state of an App Connection
2) Get real-time info about the printer.

#### App Connection State

If your app can't connect to the printer from the app connection URL, it's helpful to know why. Using the `info` API you can determine the state of the app connection, which can be one of three states.

1) The App Connection is **valid** and the printer **is** connected OctoEverywhere.
2) The App Connection is **valid** and the printer **isn't** connected to OctoEverywhere.
3) The App Connection is **no longer valid**.

You can determin the state based on the GET return type and the returned JSON body. For details