# Facial recognition without code

![Blob](./media/blob.png) ![Right Arrow](./media/right.png) ![Event Grid](./media/event-grid.png) ![Right Arrow](./media/right.png) ![Logic App](./media/logic-app.png) ![Right Arrow](./media/right.png) ![Cognative Services](./media/cognative-services.png) ![Right Arrow](./media/right.png) ![SQL Database](./media/sql-database.png)

Today, we are going to build an event-driven application to consume photos, identify the photos by anonomous ID, and store basic data about each in a SQL database. In order to accomplish this, we are going to use the following parts of Azure's Serverless, AI platform, and managed services:

* Blob Storage
* Event Grid
* Logic Apps
* Cognitive Services
* SQL Database

The application we are building here gets all of the basic functionality up and running which provides a lot of opportunities to extend and expand upon it. At the end we'll provide some links and ideas of ways you can build on this.

## Prerequisites

* To accomplish this lab, you will need an Azure account. Make sure you are able to access Azure and provision resources before you move on.
* It may be helpful to have an empty text file, OneNote, or other place to note things down. We will be handling a lot of configuration details.

## Goal

We will upload images to Azure Blob Storage and use its built in events to emit an event to  Event Grid every time a new image is uploaded. Event Grid will be used to route these events to Logic Apps which will act as the integration engine with Cognitive Services. Based on the blob URL in the Event Grid event, Logic Apps will upload the image to Cognitive Services which will then return a `faceId` to uniquely identify each face as well as some data about the face such as age. This information will then be stored in a SQL Database for querying.

## Guide

### Setup Storage

![Blob](./media/blob.png) ![Right Arrow](./media/right.png) ![Event Grid](./media/event-grid-grey.png) ![Right Arrow](./media/right.png) ![Logic App](./media/logic-app-grey.png) ![Right Arrow](./media/right.png) ![Cognative Services](./media/cognative-services-grey.png) ![Right Arrow](./media/right.png) ![SQL Database](./media/sql-database-grey.png)

1. Go to the Azure Portal and provision a Storage Account of Kind `StorageV2 (general purposev2)`.

    ![Create Storage](./media/create-storage.png)

1. Add a blob container to the storage account

    ![Create Container](./media/create-container.png)

1. Generate a shared access signature for the Blob service. Store the `SAS token` for later.

    ![Create SAS](./media/create-sas.png)

### Add Cognitive Services Face API

![Blob](./media/blob.png) ![Right Arrow](./media/right.png) ![Event Grid](./media/event-grid-grey.png) ![Right Arrow](./media/right.png) ![Logic App](./media/logic-app-grey.png) ![Right Arrow](./media/right.png) ![Cognative Services](./media/cognative-services.png) ![Right Arrow](./media/right.png) ![SQL Database](./media/sql-database-grey.png)

1. In the portal, click "Create a resource" and search for `Face` to create a Cognative Services Face API.

    ![Create Face](./media/create-face.png)

1. Navigate to the overview for the new Cognative Services Face API instance and copy the `Endpoint` to be used in the Logic App.

    ![Get Endpoint](./media/get-endpoint.png)

1. Then click "Show access keys..." and copy the `NAME` and `KEY 1` for later.

    ![Get Name and Key](./media/get-keys.png)

### Setup SQL

![Blob](./media/blob.png) ![Right Arrow](./media/right.png) ![Event Grid](./media/event-grid-grey.png) ![Right Arrow](./media/right.png) ![Logic App](./media/logic-app-grey.png) ![Right Arrow](./media/right.png) ![Cognative Services](./media/cognative-services.png) ![Right Arrow](./media/right.png) ![SQL Database](./media/sql-database.png)

1. Create a SQL Database. When you create this, you will be asked to select a SQL Server to run it on. Unless you already have one running that you know you can use, you may create the SQL server directly here in the SQL Database create context. Make sure you note your logon information, you will need it later.

![Create SQL](./media/create-sql.png)

1. 

### Connect everything with Logic Apps and Event 

![Blob](./media/blob.png) ![Right Arrow](./media/right.png) ![Event Grid](./media/event-grid.png) ![Right Arrow](./media/right.png) ![Logic App](./media/logic-app.png) ![Right Arrow](./media/right.png) ![Cognative Services](./media/cognative-services.png) ![Right Arrow](./media/right.png) ![SQL Database](./media/sql-database.png)

### Test it out

![Upload](./media/upload.png) ![Right Arrow](./media/right-green.png) ![Blob](./media/blob.png) ![Right Arrow](./media/right-green.png) ![Event Grid](./media/event-grid.png) ![Right Arrow](./media/right-green.png) ![Logic App](./media/logic-app.png) ![Right Arrow](./media/right-green.png) ![Cognative Services](./media/cognative-services.png) ![Right Arrow](./media/right-green.png) ![SQL Database](./media/sql-database.png)

## Resources

### Documentation

### Extending this project

### Related sessions