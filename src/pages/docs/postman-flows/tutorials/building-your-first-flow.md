---
title: "Building your first flow"
updated: 2023-03-16
---

This page walks you through your first flow, calling the Pokémon API and printing out the list to the console. The Pokémon API returns over 1,000 results, but this flow will print two hundred at a time to the console until it reaches the end of the list.

## Contents

<!-- vale Postman.Spelling = NO -->

* [Creating a request and a collection](#creating-a-request-and-a-collection)
* [Making your first send request in Postman Flows](#making-your-first-send-request-in-postman-flows)
* [Logging the output to the console](#logging-the-output-to-the-console)
* [Checking for the next page of results](#checking-for-the-next-page-of-results)
* [Watching it run](#watching-it-run)

<!-- vale Postman.Spelling = YES -->

## Creating a request and a collection

Begin by creating a new collection and adding a GET request. You'll use this collection with the flow you'll create later.

1. In your workspace, select **New > Collection**. Name the collection **Pokemon API**.
1. [Add a GET request](/docs/getting-started/sending-the-first-request/) with this URL: `https://pokeapi.co/api/v2/pokemon?limit=200`.

    ![Add a request](https://assets.postman.com/postman-docs/v10/flow-first-request-v10.jpg)

1. Select **Send**, then select **Save as Example**.

    > Saving the response as an example enables Postman Flows to automatically detect the structure for easier access later.

1. Select the GET request and replace the URL `https://pokeapi.co/api/v2/pokemon?limit=200` with the variable `{{URL}}`.

    ![Replace the URL](https://assets.postman.com/postman-docs/v10/flow-replace-the-url-v10.jpg)

1. Select **Save**.

## Making your first send request in Postman Flows

1. Select **New > Flows**. Your new flow appears with a **Start** block already in place.

    > You can select and drag the canvas to reposition your flow.

    ![New flow](https://assets.postman.com/postman-docs/v10/flow-start-block-v10.jpg)

1. Right-click the canvas to the right of the **Start** block. From the list of blocks that opens, select **Send Request**.

    > You can type the block's name in the **Search** field to find it faster.

1. Connect the **Start** block to the **Send Request** block.

    ![Add Send Request block](https://assets.postman.com/postman-docs/v10/flow-add-send-request-v10.jpg)

1. In the **Send Request** block, select **Add request** and select **Pokemon API**. Then select the GET request you created earlier.
    ![Select request](https://assets.postman.com/postman-docs/v10/flow-select-request-v10.jpg)

1. Create a **String** block below the **Start** block and enter the URL `https://pokeapi.co/api/v2/pokemon?limit=200`.
1. Connect the **String** block to the port next to `{{URL}}` on the **Send Request** block.

    ![Add a String block](https://assets.postman.com/postman-docs/v10/flow-add-string-block-v10.jpg)

## Logging the output to the console

1. Create a **Select** block to the right of the **Send Request** block.
1. Connect the **Select** block to the port next to **Success** on the **Send Request** block.

    ![Add a Select block](https://assets.postman.com/postman-docs/v10/flow-add-select-1-v10.jpg)

1. In the **Select** block, select **Enter path...** and select `body.results`.

    > Because you saved an example earlier, the returned data's structure auto-populates in the block.

    ![Select body.results](https://assets.postman.com/postman-docs/v10/flow-body-results-v10.jpg)

1. Create a **Log** block and connect it to the right side of the **Select** block, then select **Run**.
1. Select **Console** to view the results.

    ![Add a Log block](https://assets.postman.com/postman-docs/v10/flow-add-log-v10.jpg)

## Checking for the next page of results

1. Create another **Select** block and connect it to the **Success** port on the **Send Request** block.

    ![Add another Select block](https://assets.postman.com/postman-docs/v10/flow-add-another-select-v10.jpg)

1. In the **Select** block you created, select **Enter path...** and select `next` to get the link to the next set of 200 results.
1. Create an **If** block to the right of the `body.next` **Select** block. Connect the **Select** block to the `key` port and the `Data` port on the **If** block.

    ![Add an Evaluate block](https://assets.postman.com/postman-docs/v10/flow-add-eval-block-2-v10.jpg)

1. In the **If** block, select `value1` and replace it with `has_next`. This assigns the `body.next` value from the **Select** block to the `has_next` variable in the **If** block.
1. Select **Write an FQL condition** and enter <code class="language-text">&#96;has_next&#96; != null</code>.

    > If `has_next` is null, then the flow has reached the last set of 200 results.

    ![Select body.next](https://assets.postman.com/postman-docs/v10/flow-enter-has-next-v10.jpg)

1. Connect the **If** block's TRUE port to the **Send Request** block's URL port. This passes the new `URL` variable to the **Send Request** block.
1. Also connect the **If** block's TRUE port to the **Send Request** block's Send port. This triggers the send event so it runs again.

    ![Connect the If block](https://assets.postman.com/postman-docs/v10/flow-connect-if-1-v10.jpg)

## Watching it run

<!-- vale Postman.Vocab = NO -->

After completing the above steps, select **Run**. The flow runs and logs all the Pokémon to the console.

<!-- vale Postman.Vocab = YES -->

![Watch it run](https://assets.postman.com/postman-docs/v10/flow-watch-it-run-1-v10.gif)
Congratulations, you've created your first flow!
