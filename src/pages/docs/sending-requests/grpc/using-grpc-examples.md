---
title: "Using gRPC examples"
updated: 2023-02-09
contextual_links:
  - type: section
    name: "Prerequisites"
  - type: link
    name: "Invoke your first gRPC request"
    url: "/docs/sending-requests/grpc/first-grpc-request/"
  - type: link
    name: "Specifying examples"
    url: "/docs/sending-requests/examples/"
  - type: link
    name: "Grouping requests in collections"
    url: "/docs/sending-requests/intro-to-collections/"
  - type: section
    name: "Additional Resources"
  - type: subtitle
    name: "Videos"
  - type: link
    name: "Working with gRPC | The Exploratory"
    url: "https://youtu.be/RbHOs2xchGE"
---
<!-- TODO: Add blog post link to front matter -->
You can save, edit, and share gRPC request-response pairs as [examples](/docs/sending-requests/examples/). You can even create gRPC examples from scratch.

APIs can be complex, and so can the guidelines for using them. Examples help you understand APIs by capturing the request sent from the client and the response received from the server in a single visual snapshot. You can combine these snapshots in a request and store the request in a collection to illustrate how the API functions under different scenarios. Examples help API producers tell the world beautifully what their API is about.

## Contents

* [Saving a gRPC example](#saving-a-grpc-example)
* [Editing a gRPC example](#editing-a-grpc-example)
* [Creating a gRPC example from scratch](#creating-a-grpc-example-from-scratch)
* [Creating example-specific documentation](#creating-example-specific-documentation)

## Saving a gRPC example

This walkthrough creates and executes a client streaming request, then saves the response as a gRPC example.

> If you are using the Postman web app, you must use the Postman Desktop Agent. See [About the Postman Agent](/docs/getting-started/about-postman-agent/) for more information.

1. In Postman, select  **New > gRPC Request** to open a request in a new tab.

1. Select **Enter Server URL** and enter `grpc.postman-echo.com`.

1. Select the **Select a method** dropdown list. When the list of methods has loaded, select **SayHello**.

    ![New gRPC request](https://assets.postman.com/postman-docs/v10/grpc-save-example-1request-1-v10.jpg)

1. Save the gRPC request to a collection.

    ![gRPC request](https://assets.postman.com/postman-docs/v10/grpc-save-example-2collection-1-v10.jpg)

    > gRPC examples can't be saved unless the request is in a collection.

1. Select **Invoke**. A `reply` message appears in the response section.

1. Select **Save as Example**.

    ![gRPC Save example button](https://assets.postman.com/postman-docs/v10/grpc-save-example-4saveExampleButton-1-v10.jpg)

    The saved example opens in a new tab and you can see the saved example under the request in the sidebar.

    ![gRPC example](https://assets.postman.com/postman-docs/v10/grpc-save-example-4savedExample-1-v10.jpg)

## Editing a gRPC example

1. [Create a gRPC request, save it to a collection, and save a gRPC example.](#saving-a-grpc-example)

1. Select the gRPC example in the sidebar.

    ![Select a gRPC example](https://assets.postman.com/postman-docs/v10/grpc-save-example-1select-example-1-v10.jpg)

1. In the response section, select the message you want to edit. The editor opens below the message.

    ![Select a message](https://assets.postman.com/postman-docs/v10/grpc-save-example-2select-message-1-v10.jpg)

1. Replace the `reply` response with `Not found` or any string.

1. Select the message again to close the editor.

1. Hover over a message. A handle appears to the left of the message. Select and drag the handle to reposition the message in the timeline.

    ![Reposition the message](https://assets.postman.com/postman-docs/v10/grpc-save-example-4reposition-2-v10.jpg)

1. Select **Save**.

## Creating a gRPC example from scratch

1. Create a gRPC request with the `LotsOfReplies` method (or any streaming method) and save it to a collection.

1. Hover over the gRPC request you created and select the more actions icon <img alt="More actions icon" src="https://assets.postman.com/postman-docs/icon-more-actions-v9.jpg#icon" width="16px">.

1. Select **Add example**.

    ![Select Add example](https://assets.postman.com/postman-docs/v10/grpc-create-example-1add-4-v10.jpg)

1. An empty example opens in the workbench and appears below the request in the sidebar.
    ![New example](https://assets.postman.com/postman-docs/v10/grpc-create-example-2save-4-v10.jpg)

1. Select the **Add a Message** dropdown and select **Message stream**.

    ![Select Message stream](https://assets.postman.com/postman-docs/v10/grpc-create-example-3stream-2-v10.jpg)

    This creates a sample message stream automatically using the message structure defined in the protobuf schema.

    ![Sample message stream](https://assets.postman.com/postman-docs/v10/grpc-create-example-4messages-1-v10.jpg)

1. Select **Save**.

## Creating example-specific documentation

1. [Create a gRPC request, save it to a collection, and save a gRPC example.](#saving-a-grpc-example)

1. Select the gRPC example in the sidebar.

    ![Select a saved example](https://assets.postman.com/postman-docs/v10/grpc-save-example-1select-example-1-v10.jpg)

1. In the right sidebar, select the the documentation icon <img alt="Documentation icon" src="https://assets.postman.com/postman-docs/documentation-icon-v8-10.jpg#icon" width="16px">.

1. Hover over **Add example description...** and select the edit icon <img alt="Edit icon" src="https://assets.postman.com/postman-docs/documentation-edit-icon-v8-10.jpg#icon" width="18px">.

    ![Select the edit icon](https://assets.postman.com/postman-docs/v10/grpc-doc-example-1edit-1-v10.jpg)

1. Enter your documentation for the gRPC example and select **Save**.

    ![Save documentation](https://assets.postman.com/postman-docs/v10/grpc-doc-example-1save-1-v10.jpg)