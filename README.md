# AI Nights Content - Beginner Track

## Maastricht specific content
Here is the slide deck used as an intro to Cognitive Services that was presented in record time: https://github.com/ilionx/AINights-cognitiveservices-workshop/blob/master/CognitiveServicesSlides.pdf

These slides are part of a talk I have done regularly which can be reviewed on my YouTube channel here: https://www.youtube.com/watch?v=tFF8T_AqnBM&list=PLfbOp004UaYUfXXNsMMbUAzr2pR8nfGf2&index=6

## Workshop for Attendees

## Session Information 
**Session Title:** Creating applications that can see, hear, speak or understand - using Microsoft Cognitive Services

**Session Abstract:** In this workshop you will be introduced to the [Microsoft Azure Cognitive Services](https://azure.microsoft.com/en-gb/services/cognitive-services/?WT.mc_id=ainights-github-amynic), a range of offerings you can use to infuse intelligence and machine learning into your applications without needing to build the code from scratch. 
We will cover pre-trained AI APIs, such as [computer vision](https://azure.microsoft.com/en-gb/services/cognitive-services/directory/vision/?WT.mc_id=ainights-github-amynic) and [text analytics](https://azure.microsoft.com/en-gb/services/cognitive-services/directory/lang/?WT.mc_id=ainights-github-amynic), that are accessed by REST protocol. Then look at how you can host these [models in containers](https://docs.microsoft.com/en-us/azure/cognitive-services/cognitive-services-container-support/?WT.mc_id=ainights-github-amynic), giving you the ability to run Cognitive Services offline and on edge devices. Finally we will dive into Custom AI that uses transfer learning - [Microsoft Azure Custom Vision](https://azure.microsoft.com/en-gb/services/cognitive-services/custom-vision-service/?WT.mc_id=ainights-github-amynic). This enables you to provide a small amount of your own data to train an image classification model. Wrapping the workshop up by building our custom trained AI into an application - using [Logic Apps](https://azure.microsoft.com/en-gb/services/logic-apps/?WT.mc_id=ainights-github-amynic), this technology is ideal for proof of concepts within machine learning


## Pre-requisites for your machine
* Clone this repository to your local machine to gain images and code samples you need for the demos: ```git clone https://github.com/amynic/AINights.git``` or choose 'Clone or Download' green button and then 'Download ZIP'
* [Microsoft Azure Subscription](https://azure.microsoft.com/en-gb/free/?WT.mc_id=ainights-github-amynic)
* Laptop with a modern web browser (Google Chrome, Microsoft Edge)
* [Postman, API Development Environment - available on Windows, Linux and macOS](https://www.getpostman.com/downloads/)

> *All demos and content have been tested on a Windows PC, however all options should run from macOS and Linux machines as well. Please provide information via an issue or pull request if you have feedback on other operating systems*  

## Go to sections:

* **Task 1:** Microsoft Azure Cognitive Services - Computer Vision [Go to Section](#task-1-microsoft-azure-cognitive-services---computer-vision)
* **Task 2:** Microsoft Azure Cognitive Services - Custom Vision [Go to Section](#task-2-microsoft-azure-cognitive-services---custom-vision)
* **Task 3:** Build Custom AI into an Application - Azure Logic Apps [Go to Section](#task-3-build-custom-ai-into-an-application---azure-logic-apps)

## Task 1: Microsoft Azure Cognitive Services - Computer Vision

In this task you will try out the Cognitive Services using the website demo options

Navigate to: [https://azure.microsoft.com/en-gb/services/cognitive-services/directory/vision/](https://azure.microsoft.com/en-gb/services/cognitive-services/directory/vision/?WT.mc_id=ainights-github-amynic)

![Computer Vision website Link highlighted](/docs-images/computer-vision-link.JPG)

There are lots of different demos to try in each section (Scene and Activity Recognition in Images, OCR, Face Detection, Emotion Detection, Video indexer etc)

Select the **Demo** link next to **Scene and activity recognition in images** under **Computer Vision**. There are also other demo links to explore the different services

![Computer Vision Example](/docs-images/computer-vision-demo.JPG)

Now select **Browse** button and upload the **cat.jpeg** or **city.jpeg** image from ```sample-images/computer-vision-web-browser/cat.jpeg```

![Computer Vision Cat Example](/docs-images/cat-sample.JPG)

## Task 2: Microsoft Azure Cognitive Services - Text Analytics via REST

Now you will try using the REST protocol as you would use to integrate these services into an application

First log into [Microsoft Azure](https://azure.microsoft.com/en-gb/?WT.mc_id=ainights-github-amynic) and choose **Portal** in the top right corner.

Once in the portal select **Create a resource** and search **Cognitive Services** and choose Enter. Then select **Create** on the Cognitive Services blade

![Create Cognitive Services Account](/docs-images/cognitive-azure.JPG)

Enter details to create an account:
* **Name:** enter a suitable name for the service (example: ainightscognitive)
* **Subscription:** Choose your subscription
* **Location:** Choose your closest Data Center available
* **Pricing Tier:** S0
* **Resource Group:** Select 'Create new', and provide a sensible name (example ainights)
* **select the checkbox after reading the terms below**
* **select 'Create'**

![Cognitive Services Details](/docs-images/cognitive-details.JPG)

Once created, in your notifications (top right corner) select **go to resource**
![Go to Resource](/docs-images/go-to-resource.JPG)

In the Cognitive Services page, select **Keys** and copy **KEY 1**
![Copy Key](/docs-images/keys.JPG)

Now select **Overview** in the left hand pane and copy the **Endpoint** variable
![Copy Endpoint](/docs-images/endpoint.JPG)

Download and open Postman, an API Development environment on your local machine. 
> Find the download in the [Pre-requisites section](#Pre-requisites-for-your-machine)

Select **Request**

![Create A Request](/docs-images/create-request.JPG)

Enter request details as below and choose the option **create a new collection** and name it "Text Analytics Samples"

![Enter Request Details](/docs-images/save-request.JPG)

Select the newly created collection and choose save

![Save Request](/docs-images/save.JPG)

Now create a request to call your text analytics API:
* Change from a GET request to a POST request in the top left
* Enter your endpoint URL and add ```text/analytics/v2.0/sentiment``` to the end
* Select Headers underneath the URL box
* In Key type ```Ocp-Apim-Subscription-Key``` and in Value add your KEY1 value
* In Key type ```Content-Type``` and in Value type ```application/json```
* ![Headers and URL](/docs-images/url-and-headers.JPG)
* Select Body underneath the URL box
* Select ```raw``` from the radio button options
* Copy JSON sample from ```sample-code/cognitive-services-api-task/sentiment-analysis-text.json``` into the box
* Select the ```Send``` button and review the Response
* ![Body and Submit REST Request](/docs-images/rest-body.JPG)

You can also try other options from the REST API - such as KeyPhrases function. Change the end of the URL from sentiment to keyPhrases and select send to view the key phrases for the example text.

* ![Key Phrases REST Request](/docs-images/keyphrases.JPG)

> Check out the language support for the Text Analytics API [here](https://docs.microsoft.com/en-gb/azure/cognitive-services/text-analytics/language-support/?WT.mc_id=ainights-github-amynic). If your language is supported please edit the JSON file to translate the text and show the functionality of the API above. There is an example of a French JSON file in ```sample-code/text-analytics-demo/sentiment-analysis-text-fr.json``` please edit this file as appropriate

> If you have any issues running Postman, API Development Environment you can always run the REST API requests within the API docs for [sentiment analysis](https://northeurope.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/operations/56f30ceeeda5650db055a3c9/?WT.mc_id=ainights-github-amynic) and [key phrase extraction](https://northeurope.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/operations/56f30ceeeda5650db055a3c6/?WT.mc_id=ainights-github-amynic). Select the data centre you are using and then enter your key in the box provided along with the sample body sample used in Postman

## Task 3: Microsoft Azure Cognitive Services - Custom Vision

Using Microsoft Azure Custom Vision service you can start to build your own personalised image classification and object detection algorithms with very little code. In this exercise we will create a dog-breed classification algorithm using Dog images from the [ImageNet open dataset created by Standford University](http://vision.stanford.edu/aditya86/ImageNetDogs/)

We have 7 Classes of dogs each with 30 images (available in a .zip file [here](sample-images/dogs.zip))
* Beagle
* Bernese Mountain Dog
* Chihuahua
* Eskimo Dog (aka Husky)
* German Shepherd 
* Golden Retriever
* Maltese

There is also a set of test images (not for training) in this [.zip folder](sample-images/dogs.zip).

First create a Custom Vision instance in your Azure account. 

* Go to the [Azure Portal](https://ms.portal.azure.com) main dashboard. 
* Click 'Create a Resource' in the top left
* Search for 'Custom Vision' 
* On the description pane for Custom Vision click Create.
* Enter details to create
    * a name for the service 
    * select your subscription 
    * **[IMPORTANT]** Please choose **SOUTH CENTRAL US** as the data centre
    * Choose the S0 tier for both 'Prediction pricing tier' and Training pricing tier
    * select the resource group you created previously for this project (e.g. ainights)
    * Click Create
* ![Custom Vision Blade Details](/docs-images/custom-vision-azure.JPG)

Now we can build our classifier, navigate to [https://www.customvision.ai](https://www.customvision.ai/?WT.mc_id=ainights-github-amynic) and choose sign in. Sign in with your Azure credentials account

> Accept the terms and conditions box to continue

Once loaded choose 'New Project' which opens a window to enter details

* Name: choose a suitable name
* Description: add a description of the classifier (example shown in image below)
* Resource Group: choose the resource group you created your custom vision service in (example: ainights[SO])
* Project Types: Classification
* Classification Types: Multiclass (Single tag per image)
* Domains: General
* ![Create Custom Vision Project](docs-images/create-project.JPG)

Choose 'Create Project' and you will land on an empty workspace like below
![Empty Custom Vision Project](docs-images/start-page.JPG)

Now we can start adding images and assigning them tags to create our image classifier

In the top left, select 'Add images', browse for the first folder of images from the [.zip folder](sample-images/dogs.zip) - Beagle - and select all 30 of the images in the folder.

Add the tag 'beagle' to the Beagle dog images and select 'Upload 30 files'

![Upload images of dogs](docs-images/add-class-images.JPG)

Once successful you receive a confirmation message and you should see your images are now available in the workspace

![Successful upload](docs-images/upload-successful.JPG)

Now complete the same steps of uploading and tagging images for the other 6 dog categories in the folder. For each type of dog:
* Click add images
* Select the 30 new dog images
* Add the class label (beagle, german-shepherd, maltese etc)
* choose upload
* confirm images uploaded into the workspace

Now you should have all categories uploaded and on the left hand side you can see your dog classes and you can filter depending on type of dog image

![All images uploaded and tagged](docs-images/all-categories-uploaded.JPG)

Now you are ready to train your algorithm on the dog image data you have uploaded. Select the green **'Train'** button in the top right corner

Once the training process is complete it will take you to the Performance tab. Here you will receive machine learning evaluation metrics for your model

![Evaluation Metrics](docs-images/train-metrics.JPG)

Now we have a model we need to test the model. Choose the 'Quick Test' button in the top right *(next to the train button)* this will open a window where you can browse for a local image or enter a web URL.

Browse for an image in the test folder (images the model have not been trained on) and upload. The image will be analysed and a result returned of what dog the model thinks it is (prediction tag) and the models confidence of its result (prediction probability)

![Quick Test](docs-images/quick-test.JPG)

> Repeat this process for other images in the test folder to see how the model performs

If you click on the **'Predictions'** tab on the top toolbar - you should see all the test images you have submitted. This section is for re-training, as you get new data you can add this to your model to improve its performance. The images are ordered by importance - the image, which if classified correctly, will add the most new information to the model is listed first. Whereas the last image might be very similar to other images already learnt by the model so this is less important to classify correctly.

![Re-training](docs-images/retraining.JPG)

To add these images to the model - select the first image, review the results the model provided and then in the 'My Tags' box enter the correct tag and click 'save and close'

![Add Re-training Tag](docs-images/add-tag.JPG)

This image will disappear from the  your predictions workspace and be added to the training images workspace. Once you add a few new images and tags you can re-train the model to see if there are improvements.

To use this model within applications you need the prediction details. Therefore, you have to go to the Performance tab from the top bar, click the **Publish** button and provide a name for this published iteration. 

![Prediction URL Location](docs-images/custom-vision-publish.JPG)

![Prediction URL Name](docs-images/custom-vision-publish-name.JPG)

You can now select the **Prediction URL** button to gain all information you need to create a Postman call to your API, by setting the URL, the Header and the Body (using both an image or an image URL)

![Prediction in Postman](docs-images/custom-vision-newpredictionurl.JPG)

**Great work!** you have created your specialised dog classification model using the Azure Custom Vision Service

## Task 3: Build Custom AI into an Application - Azure Logic Apps

In this section you will build an Azure Logic App to consume your Custom Vision AI dog classification application

First we need to create two Azure Storage Accounts.

Go to the azure portal and click create new resource in the top left corner. Select the section Storage and choose the first option Storage Account.

![Azure Storage Account](docs-images/storage-account.JPG)

We are going to create two storage accounts:
* one for the images to be dropped into to be processed (called ainightstor)
* another for the results after processing to be uploaded to (called resultainights)

> Complete the process below **twice** so you have two storage accounts in total

On the storage account creation page enter options to setup your storage account:s

* **Subscription:** choose your subscription
* **Resource Group:** choose the resource group you have been using for this workshop (e.g. ainights)
* **Storage Account Name:** (must be unique) enter an all lowercase storage account name. *Such as ainightsstor(yourname) or resultsainights(yourname) - append your name to the end of the storage account name so you know its unique (remove the brackets)*
* **Location:** your closest data center
* **Performance:** Standard
* **Account Kind:** Blob Storage
* **Replication:** Locally-redundant storage (LRS)
* **Access Tier:** Hot

Select **Review + create**, confirm validation is passed and then select **Create**

![Create Azure Storage Account](docs-images/create-storage-account.JPG)

Once your deployment is complete, got to the resource and review the account settings.
Select **Blobs** to review your empty blob storage account.

![Select Blob Storage Account](docs-images/select-blobs.JPG)
We need to add a container to the storage account to store our images and results.

Select the **+ Container** button and create a name for the container
> an example for the **ainightsstor** account would be **images** 

> an example for the **resultsainights** account would be **results** 

For the public access level setting select **Container (anonymous read access for containers and blobs)**
![Create a container](docs-images/create-stor-container.JPG)

> Complete the above for an image storage account and a results storage account with the same settings

Now we will create a Logic App - this will connect your image storage account to your AI classification service and put the results in your results storage account

Head to the Azure Portal Homepage. We are going to use Event Grid, a service that detects triggers in an Azure subscription (in our case, when a new blob is created in your Azure Storage account). Before we build with this - we must register it.

Got to subscriptions in the left panel, select your subscription and find Resource Providers in the left pane. Once the resource providers are listed - search "event" and select **Microsoft.EventGrid**.

![Register Event Grid](docs-images/subscriptions.JPG)

If this is not already status registered, select **register** from the toolbar

![Register Event Grid selection](docs-images/register-event-grid.JPG)

![Registered Event Grid](docs-images/registering.JPG)

Once registered with a green tick - go back to the Azure Portal Homepage. Select **Create a Resource**. Type Logic App and select the service

![Logic App](docs-images/logic-app.JPG)

Create the logic app by entering some setup detail like below:
* **Name:** suitable name for the dog classification application
* **Subscription:** Choose your subscription
* **Resource Group:** (use existing e.g. ainights) select the resource group you have been working for the whole workshop
* **Location:** choose the data center closest to you
* **Log Analytics:** off

Choose **Create**

![Logic App Option](docs-images/create-logic-app.JPG)

Once created, go to resource. From here we can create our logic process. Select **Logic app designer** from the left menu and then the  **When an Event Grid resource event occurs** option

![Logic App Trigger](docs-images/logic-app-trigger.JPG)

Connect to Azure event grid by signing in using your Azure credentials

![Event Grid Sign In](docs-images/event-grid-sign-in.JPG)

Once connected and you see a green tick, select continue.

Select the options below:
* **Subscription:** your subscription
* **Resource Type:** Microsoft.Storage.StorageAccounts
* **Resource Name:** choose your image storage account (e.g. ainightsstor)
* **Event Type Item - 1:** Microsoft.Storage.BlobCreated

![Event Grid Options](docs-images/event-grid-options.JPG)

Then choose next step. Type **Parse JSON** and select the parse JSON operator as part of the data Data Operations category

* **Content:** select the box and from the Dynamic Content box on the right, select **Body**
* **Schema:** select this box and enter the JSON schema provided in the [logic-app-schema1 file](sample-code/logic-app-task/logic-app-schema1.json)

![Parse JSON](docs-images/parse-json.JPG)

Then choose next step. Type **HTTP** and select the HTTP option as below

![HTTP Connection](docs-images/http-connector.JPG)

Now we need to fill in the details of the REST API request - similar to using Postman App.

* Method: POST
* URI: enter Prediction URL from Custom Vision Service
* Headers:
    * "Prediction-Key" : enter your prediction key from the custom vision service
    * "Content-Type" : "application/json"
* Queries: enter nothing
* Body: {"Url": "REPLACE WITH DYNAMIC CONTENT URL"}

![HTTP info](docs-images/http-request.JPG)

Choose next step

Then choose next step. Type **Parse JSON** and select the parse JSON operator again as part of the data Data Operations category

* **Content:** select the box and from the Dynamic Content box on the right, select **Body**
* **Schema:** select this box and enter the JSON schema provided in the [logic-app-schema2 file](sample-code/logic-app-task/logic-app-schema2.json) 

> the difference between the two parse JSON is, the first one parses the event grid response about the blob storage image URL, the second one parses the JSON from the custom vision service API call return

![Parse JSON](docs-images/parse-json-2.JPG)

Choose next step

type **for each** and select the grey control step called for each
Once selected in the output from previous step box, select the box and from Dynamic content select **predictions** from the Parse JSON 2 category

![For each prediction](docs-images/for-each-prediction.JPG)

Choose **Add an action**

Search Control, select the control icon and then from the results, select **Condition**

![If Statement](docs-images/control-condition.JPG)

In the Condition box, select choose a value. From Dynamic content find Parse Json 2 and then **probability**

Set the condition to be probability greater than 0.7 (as shown below)

![Condition value](docs-images/probability.JPG)

In the **If True** box select **Add an action**

Search for Azure Blob Storage and select the icon for Create Blob

In connection name enter **results** and select your results blob storage account name from the listed options and select create

![Connect to Result Blob Storage](docs-images/result-blob-connection.JPG)

In folder path, select the folder icon, far right, and choose the container name you created that is populated

Select the Blob name field and enter: result-(then from the Dynamic content box under Parse Json (1) select **id**)

Under Blob Content, select the field and in the Dynamic Content box on the right, select **see more** under the Parse Json 2 section. Then select **tagName**, enter a colon ":" and then select **probability**

![Azure Blob Storage results options](docs-images/create-blob-connector.JPG)

Finally save the logic app in the top action bar

Once saved, lets test the app for the desired outcome. Select **Run** from the top action bar

![Run Logic App to test](docs-images/run-logic-app.JPG)

Now navigate to your images storage account (easy to find from the resource group section). 
Choose Blob and select the images container. In there you should see an upload button. Upload one of the images from the Dogs data testset folder

![Upload Blob](docs-images/upload-blob.JPG)

Once uploaded, navigate back to your Logic App main page and review the  runs history section at the bottom of the page. Select the successful run and review the inputs and outputs from the

![Run History](docs-images/logic-app-run-history.JPG)

All sections should have a green tick and you can select each one to view the input and output between the layers (this is also a great way to debug if it doesn't run as expected)

![Logic app run successful](docs-images/explore-logic-app-run.JPG)

Finally navigate to your results blob storage account, select blob, enter the results container and review the file now created there. The contents of the file should show similar to the below - given the dog image input, the predicted class of the dog and also a confidence score

![Result](docs-images/result.JPG)

## Clean up resources	

Finally, If you don't expect to need these resources in the future, you can delete them by deleting the resource group. To do so, select the resource group for this workshop, select Delete, then confirm the name of the resource group to delete.
