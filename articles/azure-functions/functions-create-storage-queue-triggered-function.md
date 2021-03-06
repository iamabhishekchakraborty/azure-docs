---
title: Create a function in Azure triggered by queue messages | Microsoft Docs
description: Use Azure Functions to create a serverless function that is invoked by a messages submitted to an Azure Storage queue.
services: azure-functions
documentationcenter: na
author: ggailey777
manager: erikre
editor: ''
tags: ''

ms.assetid: 361da2a4-15d1-4903-bdc4-cc4b27fc3ff4
ms.service: functions
ms.devlang: multiple
ms.topic: get-started-article
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 04/25/2017
ms.author: glenga

---
# Create a function triggered by Azure Queue storage

Learn how to create a function triggered when messages are submitted to an Azure Storage queue.  

![View message in the logs.](./media/functions-create-storage-queue-triggered-function/function-app-in-portal-editor.png)

It should take you less than five minutes to complete all the steps in this topic.

## Prerequisites

[!INCLUDE [Previous quickstart note](../../includes/functions-quickstart-previous-topics.md)]

You also need to download and install the [Microsoft Azure Storage Explorer](http://storageexplorer.com/). 

[!INCLUDE [functions-portal-favorite-function-apps](../../includes/functions-portal-favorite-function-apps.md)] 

## <a name="create-function"></a>Create a Queue triggered function

Expand your function app, click the **+** button next to **Functions**, click the **QueueTrigger** template for your desired language. Then, use the settings as specified in the table, and then click **Create**.

![Create the storage queue triggered function.](./media/functions-create-storage-queue-triggered-function/functions-create-queue-storage-trigger-portal.png)
    
| Setting      |  Suggested value   | Description                                        |
| ------------ |  ----------------- | -------------------------------------------------- |
| **Queue name**   | myqueue-items    | Name of the queue to connect to in your Storage account. |
| **Storage account connection** | AzureWebJobStorage | You can use the storage account connection already being used by your function app, or create a new one.  |
| **Name your function** | Unique in your function app | Name of this queue triggered function. |  

Next, you connect to your Azure Storage account and create the **myqueue-items** storage queue.

## Create the queue

1. In your function, click **Integrate**, expand **Documentation**, and copy both **Account name** and **Account key**. You use these credentials to connect to the storage account. If you have already connected your storage account, skip to step 4.
 
    ![Get the Storage account connection credentials.](./media/functions-create-storage-queue-triggered-function/functions-storage-account-connection.png)v

2. Run the [Microsoft Azure Storage Explorer](http://storageexplorer.com/) tool, click the connect icon on the left, choose **Use a storage account name and key**, and click **Next**.

    ![Run the Storage Account Explorer tool.](./media/functions-create-storage-queue-triggered-function/functions-storage-manager-connect-1.png)
    
3. Enter the **Account name** and **Account key** from step 1, click **Next** and then **Connect**. 
  
    ![Enter the storage credentials and connect.](./media/functions-create-storage-queue-triggered-function/functions-storage-manager-connect-2.png)

4. Expand the attached storage account, right-click **Queues**, click **Create queue**, type `myqueue-items`, and then press enter.
 
    ![Create a storage queue.](./media/functions-create-storage-queue-triggered-function/functions-storage-manager-create-queue.png)

Now that you have a storage queue, you can test the function by adding a message to the queue.  

## Test the function

1. Back in the Azure portal, browse to your function expand the **Logs** at the bottom of the page and make sure that log streaming isn't paused.

2. In Storage Explorer, expand your storage account, **Queues**, and **myqueue-items**, then click **Add message**. 

    ![Add a message to the queue.](./media/functions-create-storage-queue-triggered-function/functions-storage-manager-add-message.png)

2. Type your "Hello World!" message in **Message text** and click **OK**.
 
3. Wait for a few seconds, then go back to your function logs and verify that the new message has been read from the queue. 

    ![View message in the logs.](./media/functions-create-storage-queue-triggered-function/functions-queue-storage-trigger-view-logs.png)

4. Back in Storage Explorer, click **Refresh** and verify that the message has been processed and is no longer in the queue.

## Clean up resources

[!INCLUDE [Next steps note](../../includes/functions-quickstart-cleanup.md)]

## Next steps

You have created a function that runs when a message is added to a storage queue. 

[!INCLUDE [Next steps note](../../includes/functions-quickstart-next-steps.md)]

For more information about Queue storage triggers, see [Azure Functions Storage queue bindings](functions-bindings-storage-queue.md). 



