---
title: "Setting up mock servers"
order: 84
page_id: "setting_up_mock"
contextual_links:
  - type: section
    name: "Prerequisites"
  - type: link
    name: "Sending requests"
    url: "/docs/sending-requests/requests/"
  - type: link
    name: "Grouping requests in collections"
    url: "/docs/sending-requests/intro-to-collections/"
  - type: section
    name: "Additional Resources"
  - type: subtitle
    name: "Videos"
  - type: link
    name: "Fake APIs for Real Developers"
    url: "https://www.youtube.com/watch?v=fgtDZPOPzLU"
  - type: subtitle
    name: "Related Blog Posts"
  - type: link
    name: "Mock responses in Postman by using Examples"
    url: "https://blog.postman.com/2017/05/17/mock-responses-in-postman-by-using-examples/"
  - type: link
    name: "Simulate a back end with Postman’s mock service"
    url: "https://blog.postman.com/simulate-a-back-end-with-postmans-mock-service/"
  - type: link
    name: "Team collaboration with Postman mock servers"
    url: "https://blog.postman.com/2017/09/20/team-collaboration-with-postman-mock-servers/"
  - type: link
    name: "Introducing Postman Mock Call Logs"
    url:  "https://blog.postman.com/introducing-postman-mock-call-logs/"
  - type: section
    name: "Next Steps"
  - type: link
    name: "Test scripts"
    url: "/docs/writing-scripts/test-scripts/"

warning: false
---

Mock Servers allow you to simulate your API data. By saving example responses for your requests, you can create a mock server that will return your example response instead of connecting to your actual API, for example in cases where you do not have a backend yet, or are experimenting and don't want to connect to your real data source.

You can create mock servers from Postman, from the web dashboard, and using the Postman API. You will need a Postman account to set up a mock server.

Each mock server in Postman is linked to a collection. Postman matches requests and generates responses for mocks from the examples saved for the collection requests. You can create a mock server even if you don't have an existing collection.

## Contents

* [Creating mock servers in-app](#creating-mock-servers-in-app)
    * [Mocking from the New button](#mocking-from-the-new-button)
    * [Mocking from the Launchpad](#mocking-from-the-launchpad)
    * [Mocking from an API](#mocking-from-an-api)
    * [Mocking from the Collections sidebar](#mocking-from-the-collections-sidebar)
    * [Mocking from history](#mocking-from-history)
        * [Mocking a single request](#mocking-a-single-request)
        * [Mocking all requests made on a specific date](#mocking-all-requests-made-on-a-specific-date)
* [Mocking from Collections in Browse view](#mocking-from-collections-in-browse-view)
* [Creating mock servers in the web dashboard](#creating-mock-servers-in-the-web-dashboard)
* [Making requests to mock endpoints](#making-requests-to-mock-endpoints)
* [Using HTTP access control for a mock](#using-http-access-control-for-a-mock)
* [Using free mock server calls](#using-free-mock-server-calls)
* [Editing and deleting mock servers](#editing-and-deleting-mock-servers)
    * [Editing mocks from the Collections pane](#editing-mocks-from-the-collections-pane)
    * [Deleting mocks from the Collections pane](#deleting-mocks-from-the-collections-pane)
    * [Editing mocks in Browse mode](#editing-mocks-in-browse-mode)
    * [Deleting mocks in Browse mode](#deleting-mocks-in-browse-mode)
    * [Editing mocks from the Dashboard](#editing-mocks-from-the-dashboard)
    * [Deleting mocks from the Dashboard](#deleting-mocks-from-the-dashboard)
* [Viewing mock calls](#viewing-mock-calls)
    * [Troubleshooting mock calls](#troubleshooting-mock-calls)
* [Next steps](#next-steps)

## Creating mock servers in-app

You can create a mock in several ways in the Postman app:

* Using the **New** button
* From the Launch screen
* Using [Examples in an existing collection](/docs/designing-and-developing-your-api/mocking-data/mocking-with-examples/)

### Mocking from the New button

The video below runs you through the steps in creating a mock server from the **New** button in the Postman app.

![Mock creation flow using New button](https://assets.postman.com/postman-docs/mock-creation-app-cnx.gif)

To create your mock server, click the **New** button in the top left of the header toolbar.

![Start by clicking the New button](https://assets.postman.com/postman-docs/mock-cnx-new-button.png)

Click **Mock Server** in the **Create New** tab.

![Choose "Mock Server" from the dialog box](https://assets.postman.com/postman-docs/mock-cnx-modal.png)

Choose whether you want to mock a new API or an existing collection. If you create a new API to mock, you will select a request method and enter the request path, response code, and response body. If you use an existing collection to mock, you will select a collection from a list of existing or team collections.

![Set request path and response body](https://assets.postman.com/postman-docs/mock-cnx-config.png)

When you have selected or created the request you want to mock, click **Next**.

In the **Set up the mock server** tab, you can configure your mock server.

1. Enter the name of the mock.
2. Select an environment (optional).
3. Check the checkbox if you want to make the mock server private.
4. Check the checkbox if you want to save the mock server URL as an environment variable.
5. Click **Next** to continue.

> If your mock server is private, you will need to add a Postman API key in the request header: `x-api-key:<Your-Postman-API-key>`. You can [share the collection](/docs/collaborating-in-postman/sharing/) and your collaborators can use their Postman API keys to consume the mock.

![Set mock server configuration](https://assets.postman.com/postman-docs/mock-cnx-config-continued.png)

> The number of calls made to mock servers may be limited by your Postman account. Check your [usage limits](https://go.postman.co/usage).

In the **Next steps** tab, you will see a list of suggested next steps to maximize the effectiveness of your mock server.

![Next steps after mock is created](https://assets.postman.com/postman-docs/mock-cnx-next-steps.png)

### Mocking from the Launchpad

**Launchpad** appears by default when you launch the Postman app. To create a mock server, open the Postman app, navigate to **Start something new** > **... View More** > **Create a mock server**.

Follow the process [outlined in the New Button section](#mocking-from-the-new-button) to complete the mock server setup steps.

> At the bottom, you can choose whether you want the Launchpad tab to display each time you open Postman by toggling the **Open Launchpad** option on or off.

### Mocking from an API

You can create a mock server from an existing API. Navigate to the API you'd like to add a mock server to, then click **Develop**. Select **Add Mock Server**, then choose between creating a new mock server or adding an existing one.

This will launch the **Create mock server** modal. Follow the process [outlined in the New button section](#mocking-from-the-new-button) to complete the mock server setup.

![Create mock from API Dev](https://assets.postman.com/postman-docs/githubusercontent3.png)

### Mocking from the Collections sidebar

You can create a mock server from an existing collection in the left sidebar. To do that, expand the collection details pane, switch over to the **Mocks** tab in the pane, and click **Create a mock server**.

![Create new mock server from collection sidebar](https://assets.postman.com/postman-docs/mock-cnx-collection-sidebar.png)

This will launch the **Create mock server** modal. Follow the process [outlined in the New Button section](#mocking-from-the-new-button) to complete the mock server setup steps.

If you already have mock servers created from the same collection, you will see an **Add mock** button instead of **Create a mock server**.

![Create new mock server from collection sidebar when there are existing mock servers](https://assets.postman.com/postman-docs/Adding+a+second+mock+from+sidebar.jpg)

### Mocking from history

You can create a mock server from the requests saved in the history of your Postman app.

#### Mocking a single request

You can mock a single request from the **History** tab in the left sidebar. Hover over an entry, and click **View more actions** (**...**) to expand the dropdown menu. Choose **Mock Request**.

![Create new mock server from history request](https://assets.postman.com/postman-docs/Mocking+a+single+request+from+history.jpg)

This will open the **Set up the mock server** modal. Pass the values outlined in the [New button section](#mocking-from-the-new-button). Click **Create Mock Server**.

This process of creating a mock server will also create a collection with the same title as the mock server. This collection will have a copy of the same request that you chose from the **History** sidebar. The mock server created is tied to this new collection.

![New collection created when creating mock server from history request](https://assets.postman.com/postman-docs/New+mocks+create+new+collections.jpg)

#### Mocking all requests made on a specific date

You can create a mock server from **History** for all the requests you made on a specific date, creating a new collection at the same time.

In the Postman app, click **History**.

![History tab](https://assets.postman.com/postman-docs/History+Mock+creation.jpg)

Next to the date you want to mock all the requests for, click the ellipsis **(...)** > **Mock Requests**.

![Ellipsis and mock requests](https://assets.postman.com/postman-docs/No+arrows+ellipsis+and+mocks.jpg)

The **Set up the mock server** modal will open.

In the modal, give your mock server a name. You also have the option to connect an environment to the mock server, make the mock server private, and to save the mock server's URL as an environment variable. Click **Create mock server**.

![Mocks modal](https://assets.postman.com/postman-docs/Second+step+modal.jpg)

> If you choose to make your mock server private, you'll have to [generate an API key](/docs/developer/intro-api/).

The "Next steps" modal will appear with an overview of your new mock server's details. Note the mock server's URL because you'll need it to make requests that return mock data.

![Mocks modal](https://assets.postman.com/postman-docs/Next+steps+modal+RS.jpg)

Creating the mock server will also create a collection with the same name as the server. The collection will have a copy of each request made on the date you chose in your **History**. All requests from this collection will be made to the server you just created.

![Mocks modal](https://assets.postman.com/postman-docs/New+mocks+create+new+collections.jpg)

### Mocking from Collections in Browse view

You can create a mock from an existing collection from the **Browse** view. Click the **Browse** toggle button on the bottom right of the Postman app. Change to the **Collections** tab for the current workspace. Click the **View more actions**  (**...**) button for the corresponding collection. Select **Mock Collection** from the dropdown.

![Create new mock server from browse view](https://assets.postman.com/postman-docs/mock-cnx-browse-view.png)

This will open the **Create mock server** modal. Follow the steps to finish creating the mock server.

## Creating mock servers in the web dashboard

You can create a mock server from the Web dashboard with existing collections and environments. Login to your [Postman team dashboard](https://go.postman.co), and navigate to your workspace by clicking your workspace name. In the workspace dashboard, click the **Mock servers** tab.

![Mock servers web dashboard](https://assets.postman.com/postman-docs/mock-web-dashboard.png)

Click the button to create a new mock server, and you will see the configuration screen. Set the relevant configuration.

![Mock servers web dashboard configuration](https://assets.postman.com/postman-docs/mock-web-config.png)

1. Enter the name of the mock.
2. Select a collection to mock.
3. Select a version tag of the collection to use for the mock. Leave it to **CURRENT** if you want to the mock server to use the latest version of your collection.
4. Select an environment to use with the mock (optional).
5. Select the checkbox if you want to make the mock server private.
6. Click **Create Mock Server** to create the mock and go back to the **Mock servers** dashboard.

## Making requests to mock endpoints

Once you've created your mock server, you can use the URL `https://{{mockId}}.mock.pstmn.io/{{mockPath}}` to make requests to it.

* `mockId`: The ID that you received when you created the mock. You can retrieve the ID using the [GET All Mocks endpoint](https://docs.api.getpostman.com/#018b5d62-f6fc-f752-597e-c1eb4bb98d24) in the [Postman API](https://www.getpostman.com/docs/pro/pro_api/intro_api).
* `mockPath`: The path of the request that you’d like to mock, for example <code>api/response</code>.

You will need to specify your [Postman API Key](https://app.getpostman.com/dashboard/integrations/pm_pro_api/list) as an `apikey` query parameter in the URL, or create an `X-API-Key` header.

You can save [example responses](/docs/designing-and-developing-your-api/mocking-data/mocking-with-examples/#step-3-saving-the-request-r1s-response-as-an-example-p1) for your mock server to use when responding to requests.

Your mock server will then pick a response based on the following criteria:

* `x-mock-response-code`: If this optional header is provided, the mock server will try to return an example response with the given status code.
* HTTP Method
* Request path

Learn more on [mocking with examples](/docs/designing-and-developing-your-api/mocking-data/mocking-with-examples/).

## Using HTTP access control for a mock

In addition to using the Postman app to make requests to mock endpoints, you can also make those requests in a browser.

A web browser makes a cross-origin HTTP request when it requests a resource from a domain, protocol, or port that's different from its own.

[Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) is a standard that defines a way in which a browser and server can interact securely, in this case referring to how a web browser interacts with the mock endpoints hosted on the Postman server.

CORS is enabled for Postman mock servers. As a result, you can stub your web apps with mocked data using the mock endpoints. Development or production web apps can then make requests to your Postman mock endpoint and receive an example response.

## Using free mock server calls

Your Postman account gives you a limited number of free mock server calls per month.

You can check your usage limits in the [Postman API](https://docs.api.getpostman.com) or [account usage page](https://go.pstmn.io/postman-account-limits).

## Editing and deleting mock servers

You can edit or delete existing mock servers in Postman. The following properties of a mock server can be updated through the Postman app and [Postman Dashboard](https://go.postman.co/):

* Name of the mock server
* Version tag of the underlying collection
* Environment associated with the mock server
* Private or public status of the mock server

![Postman Mock Server edit options](https://assets.postman.com/postman-docs/mocks/mock-edit-modal.png)

In the Postman app, you can edit or delete a mock server from the **Collections** pane or from the **Mocks** listed in **Browse** mode. You can also edit or delete a mock server from the [Postman Dashboard](https://the.postman.co/workspaces?type=personal).

### Editing mocks from the Collections pane

1. In the **Collections** pane, click the arrow **(>)** next to the name of the collection to expand the panel to the right.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Expanding+Collection+pane.jpg)
2. At the top of the panel, click the **Mocks** tab.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Mocks+tab.jpg)
3. Hover over the name of the mock server you want to edit and click **Edit**.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Edit+mock.jpg)

### Deleting mocks from the Collections pane

1. In the **Collections** pane, click the arrow **(>)** next to the name of the collection to expand the panel to the right.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Expanding+Collection+pane.jpg)
2. At the top of the panel, click the **Mocks** tab.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Mocks+tab.jpg)
3. Hover over the name of the mock server you want to delete and click **Delete**.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Deleting+mocks+from+Collections+pane.jpg)

### Editing mocks in Browse mode

1. At the top, click the **Mocks** tab.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Full+app+view+browse+mode.jpg)
2. Next to the name of the mock server, click the ellipsis **(...)** > **Edit**.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Edit+mocks+in+browse.jpg)

### Deleting mocks in Browse mode

1. At the top, click the **Mocks** tab.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Full+app+view+browse+mode.jpg)
2. Next to the name of the mocks server, click the ellipsis **(...)** > **Delete**.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Deleting+mocks+from+Browse.jpg)
3. Click **Delete**.
![Postman Mock Server edit options](https://assets.postman.com/postman-docs/Confirm+mock+deletion+modal+.jpg)

### Editing mocks from the Dashboard

> To open the [Dashboard](https://go.postman.co/), sign in to Postman from your browser.

1. Open the workspace or collection with the mock server you want to edit.
2. Click **Mocks** or **Mock Servers** at the top of the page.
3. Hover over the name of the mock server and click **Edit**.
![Edit mocks](https://assets.postman.com/postman-docs/Edit+mock+in+dashboard.jpg)

### Deleting mocks from the Dashboard

1. Open the workspace or collection with the mock server you want to edit.
2. Click **Mocks** or **Mock Servers** at the top of the page.
3. Hover over the name of mock server and click **Delete**.
![Delete mocks](https://assets.postman.com/postman-docs/Deleting+mocks+dashboard.jpg)
4. Click **Delete Mock Server**.
![Delete mocks](https://assets.postman.com/postman-docs/Delete+mock+server+modal.jpg)

## Viewing mock calls

You can view and search the details of calls to your mock servers using the mock call log. Open a mock from the Postman app by clicking it in __Collections__, in __APIs__, or by switching to __Browse__ &gt; __Mocks__ and clicking the mock name. Your mock call log will open in the web dashboard—you can also open it from the collection in the browser, by selecting __Mock Servers__.

![Mock List Browse View](https://assets.postman.com/postman-docs/mock-list-browse.jpg)

The mock call log lists an overview of calls made to the mock url, together with request and response details.

![Mock Call Log List](https://assets.postman.com/postman-docs/mock-call-log-list.jpg)

Mock call log entries indicate the time a request was sent, the request method and path, and a response overview. Click an entry to see more detail on request headers and body, or response headers and body. You can drill down into response data returned by a mock call.

![Mock Call Log](https://assets.postman.com/postman-docs/mock-call-log.jpg)

Use the search field to find particular calls, and the refresh button at the top of the list to view up to date requests.

### Troubleshooting mock calls

You can use the mock call log to troubleshoot your requests to mock servers.

<img alt="Mock Call Error" src="https://assets.postman.com/postman-docs/no-matching-requests.jpg" width="300px"/>

If you see `No matching requests` listed in the __Response__ column, this may mean that your mock server is not setup correctly. Make sure [you have an example saved for the request](/docs/designing-and-developing-your-api/mocking-data/mocking-with-examples/) in the collection you have the mock connected to.

In the case of a service outage, you will get a 502/503/504 response. Please subscribe and check the Postman [status page](https://status.postman.com/) for updates if you encounter this.

## Next steps

For more information about mock servers, see the following resources:

* [Mocking with examples](/docs/designing-and-developing-your-api/mocking-data/mocking-with-examples/)
* [Mocking with the Postman API](/docs/designing-and-developing-your-api/mocking-data/mock-with-api/)
* [Matching algorithm](/docs/designing-and-developing-your-api/mocking-data/matching-algorithm/)
