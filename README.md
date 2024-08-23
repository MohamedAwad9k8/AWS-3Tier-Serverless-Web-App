# AWS Serverless Web Application Project

# Overview

This project involves creating A  3-tier serverless web application hosted on AWS, leveraging various AWS services including S3, API Gateway, Lambda, and DynamoDB. The frontend is hosted on S3, API Gateway serves as the entry point for backend requests, Lambda functions handle the backend logic, and DynamoDB is used for data storage.

# Architecture Diagram
![image](https://github.com/user-attachments/assets/cef13d7e-32bf-4772-8535-b8b99ba868aa)

---
# AWS Services Used

- **Amazon S3**: Used to host the static frontend files.
- **Amazon API Gateway**: Acts as the API layer, routing requests to the appropriate Lambda functions.
- **AWS Lambda**: Executes backend logic in response to API Gateway requests.
- **Amazon DynamoDB**: NoSQL database used to store application data.
- **Amazon CloudFront**: Content Delivery Network (CDN) used to distribute the frontend files globally with low latency.
  

# Step-by-Step Setup  


## Step 1: Hosting Frontend on S3

First, head to S3 page on AWS Console, and create a new bucket
![image](https://github.com/user-attachments/assets/e377510b-8413-4310-9691-a8deb64e594e)
![image](https://github.com/user-attachments/assets/f664c5d3-8e08-4a1f-9b41-8ea3b374ac75)
Make sure to choose the desired region for your Web App, then choose a unique name for your S3 Bucket
![image](https://github.com/user-attachments/assets/7119417d-314a-4e50-acce-985d359f0d21)  

Scroll down and make the bucket publicly available  

![image](https://github.com/user-attachments/assets/655f9eda-7b0f-4151-b58e-56df9afa2c0b)  

Scroll down, add any desired Tags and Finally click on Create bucket  
![image](https://github.com/user-attachments/assets/2f597607-0ad9-4a43-b22c-2449acf00455)  


Navigate to Buckets, there you will see all your S3 buckets in this region.

Click on the bucket you just created  

![image](https://github.com/user-attachments/assets/dbc77ae7-9ab5-4e46-8f6b-ecdea3a4d51e)    

Click on Upload, to upload files, and folders
![image](https://github.com/user-attachments/assets/6ffb33f5-7094-45f4-a40f-a7f03a461e69)  

Add the required files (all at a time-possible), and the required folders (one at a time)
![image](https://github.com/user-attachments/assets/9416107e-8212-41a8-8aba-d13d3c8f6cf6)

Scroll down and press on upload
![image](https://github.com/user-attachments/assets/a34082e5-9db3-4455-9b6e-c0d186479c1b)

Note: The uploaded files should have API gateway endpoint in their code, to access it. So we will update it in the code later, and re-upload the updated files.

Now we will head to the Permissions tab

![image](https://github.com/user-attachments/assets/cd32c700-a90a-4fb3-8ff5-d541a722cfb5)

Scroll down to Bucket Policy and click edit
![image](https://github.com/user-attachments/assets/3bd8f6cc-0736-4ae0-8352-f2316e5c05e4)

Enter the policy, scroll down and press Save Changes

![image](https://github.com/user-attachments/assets/0ae980dc-398d-4b7a-bada-338649c6766c)

Finally head to properties, and scroll down to static website hosting

![image](https://github.com/user-attachments/assets/cf637f2c-afa2-4667-8684-51e4a8815604)

Click Edit

![image](https://github.com/user-attachments/assets/991e20af-3b27-43de-93a0-9ec62af10b0a)

![image](https://github.com/user-attachments/assets/0c8873b3-90e4-4738-a1ed-1db6c2adba3f)

Now head back to the properties tab, and scroll down to static web site hosting

![image](https://github.com/user-attachments/assets/629c6266-a945-4d79-98e3-8b577fc8723a)

Copy the link and paste it in a new tab, to test the hosted web app

This is the main page, index.html
![image](https://github.com/user-attachments/assets/d1357a0b-8892-48ac-a5ed-ee75e92861fc)


This is the error page
![image](https://github.com/user-attachments/assets/4768a4ce-8070-46ab-ba17-33d5e665a40a)

And this is the admin.html page, a page for admins to be able to change prices

Note: no security measures are implemented here, as it’s just a simple way to show the interaction with the database.
![image](https://github.com/user-attachments/assets/284ab527-e300-4f14-be93-1cf0937ddbb2)  

## Step 2: Configuring DynamoDB

Head to DynamoDB, and click on create table
![image](https://github.com/user-attachments/assets/148ab768-ce4d-4cda-8add-a654a68c8c7b)
![image](https://github.com/user-attachments/assets/b76014dd-7091-4250-ab6d-7b74bfa4a6c5)  

Enter the desired values for your use case
![image](https://github.com/user-attachments/assets/17724f8a-0e4f-47d1-abe7-bacc1782e26a)  

Add any desired Tags, and Press Create
![image](https://github.com/user-attachments/assets/874a8f52-69e4-48c9-8d38-02f2c524b998)


![image](https://github.com/user-attachments/assets/9dd44d39-b4f9-46f1-bf26-dcc4f371bb2c)

Click on Explore Items
![image](https://github.com/user-attachments/assets/4ab247ce-286c-4cf7-9760-5f776bb4a83a)  

It’s possible to query table Items from here

Note: choosing Scan, then Run will return all the table items
![image](https://github.com/user-attachments/assets/a4fa85a6-3c8e-4f25-963f-efddcfb20f50)  

Scroll Down, to see all the items

from here you can create a new item, or edit a current one

Click on Create Item
![image](https://github.com/user-attachments/assets/8f359e44-3665-440f-a4cf-963b7a342a6e)

![image](https://github.com/user-attachments/assets/b56793db-48aa-4d5a-b4a2-dfbb2b148299)  

## Step 3: Creating IAM Role for Lambda Functions

Head to IAM service
![image](https://github.com/user-attachments/assets/c2b69590-f061-4009-8ef5-e56888f16094)  

Select Roles from the sidebar
![image](https://github.com/user-attachments/assets/45a7b1e9-ebb6-448d-b7f8-18d3d0656c54)

Select Create Role
![image](https://github.com/user-attachments/assets/dc47998f-841c-4ea4-9904-7eb6a85ae7cc)
![image](https://github.com/user-attachments/assets/bc333eb1-10a9-45bd-8141-9073f2d7ac86)

Scroll Down and choose next,

Next we will attach the needed policies for the lambda function to be invoked and work properly

AmazonS3FullAccess, AmazonDynamoDBFullAccess, AWSLambda_FullAccess

After selecting all the desired policies, scroll down and select next
![image](https://github.com/user-attachments/assets/db2008b0-9e2e-4cba-8480-e3e9a606c4c5)
Enter name and description
![image](https://github.com/user-attachments/assets/c88ff6ec-4295-47ce-96fc-0f6af83123f2)
Review Selected Policies, and add any desired tags

then press Create Role
![image](https://github.com/user-attachments/assets/91a23d13-bc68-4114-b395-b837b831ae45)  


## Step 4: Creating Lambda Functions

navigate to the lambda service
![image](https://github.com/user-attachments/assets/37c527b7-408e-4d22-920d-4d4135e3dbb7)

Click on Create function
![image](https://github.com/user-attachments/assets/a002c9ca-e611-44a7-810b-31d683e79085)  

Enter a name for the function, and choose the desired language
![image](https://github.com/user-attachments/assets/fe5bab1b-0fc1-4194-8e03-a81bb0ff6471)  

Scroll down to permissions
![image](https://github.com/user-attachments/assets/661d70ad-7ce1-48db-ac03-2a2927e16657)  

Finally Press on Create Function
![image](https://github.com/user-attachments/assets/24ce70ca-c3f5-4620-b0c8-35d69c4008b9)

Here you can see an overview of the Lambda function

add the python code, and press deploy after
![image](https://github.com/user-attachments/assets/ea5ad41f-ddc7-4c0c-a69e-314bf0a3e7af)

Note: We will repeat the same steps for the other lambda function which is used to update prices.

Also note that, I will not discuss the python code here, since the main focus the it the deployment process on AWS.


## Step 5: Setting Up API Gateway

Next head to the API Gateway service and press Create API
![image](https://github.com/user-attachments/assets/779fefb7-f3fd-4628-aed6-96ec011db3fd)  

![image](https://github.com/user-attachments/assets/be908c8a-23c0-43d6-8b08-8c618473432b)  

Scroll down, till you reach REST API, and click create
![image](https://github.com/user-attachments/assets/c32a61e0-f518-43af-90c3-44bb88629bb6)


Choose new API, then enter a name and description, then click on Create API
![image](https://github.com/user-attachments/assets/52c1f559-164e-402e-8b12-2002c0a507aa)


Click on Create Resource
![image](https://github.com/user-attachments/assets/76c551d9-62d1-46a3-b0aa-51f0cdd0c23c)  

Enter the resource name,

Allow CORS If needed

and then create a new resource
![image](https://github.com/user-attachments/assets/29744c76-a89c-46b6-967d-ced97a6eb4e3)  

Press on Create Method
![image](https://github.com/user-attachments/assets/9d1e5f91-f4f5-4d51-864d-658c1cc07e6b)

![image](https://github.com/user-attachments/assets/5fde557e-ebec-4135-a17f-2809b3b7be87)

Choose the suitable lambda function, and click on Create Method
![image](https://github.com/user-attachments/assets/ebf05abb-c368-4e75-a0b6-970ce1dff62b)

Test the API, and deploy it from here
![image](https://github.com/user-attachments/assets/073fd6f8-dcd1-4bc4-b2b6-70e5a74115cc)  

Choose new stage and give it a name
![image](https://github.com/user-attachments/assets/0149e397-f1fb-4d58-8aa0-9a068818b0aa)

After Deploying the API, the API endpoint URL becomes available to use

Note: I have created a PATCH method under the update resource for the other lambda function, to handle the prices update process. It’s not shown here, but it’s the same steps as the GET method.
![image](https://github.com/user-attachments/assets/0ba1612d-37d4-43f7-943f-7e4676033544)

Now using the Full Invoke URL, we can copy it, and paste it in a new window to test it
![image](https://github.com/user-attachments/assets/1eeff322-6a2a-4e68-8d5a-c5dc4108b077)

![image](https://github.com/user-attachments/assets/44e04d91-22f4-40a6-b437-0320be34024b)

Finally, you will need to update your front end files, and add the API endpoints in them, then re-upload them in the S3 bucket.

Note: Only re-upload the modified files, which are probably the script.js files.

## Step 6: Cloud Front Integration

Why use Cloud Front?

Cloud Front is a Content Delivery Network service which allows for content caching leading to improved Improved Performance and Reduced Latency.

Another great benefit is it allows both http and https requests. While S3 bucket allows only http requests.

This improves security, and the web app more user friendly and easy to access

Note: Connecting to the web app on S3 using http protocol, will show the users an icon/message saying the connection isn’t secure, while trying to access the web app using https protocol will only result in an error.
![image](https://github.com/user-attachments/assets/b4459a8a-a305-422f-9f55-e32d672641d5)  

So let’s integrate Cloud Front to the Web App, first head to Cloud Front Page and click on Create Distribution
![image](https://github.com/user-attachments/assets/77d25f0b-7c41-41b5-ac5d-82296efcef90)
![image](https://github.com/user-attachments/assets/c9c8b30a-9232-4cbf-a21a-6f3b2be0739c)  

Choose the Origin for the CDN
![image](https://github.com/user-attachments/assets/e70416df-634b-4a04-8d20-9b99fae73f0d)


Enter a name 
![image](https://github.com/user-attachments/assets/a4e073bd-9533-4c5a-a227-d9b36d4b4f9d)  

Make sure to allow all HTTP methods
![image](https://github.com/user-attachments/assets/03d92fe4-7fa7-4e67-88ad-484346570b93)  

Choose the Cache Settings, I chose the legacy cache settings
![image](https://github.com/user-attachments/assets/910ef12e-0cee-4bcd-a53e-8bffcd9256f7)  

Scroll down and click Create
![image](https://github.com/user-attachments/assets/4a9524eb-f4c7-439e-9ef3-eeb759cd5035)

Go to Distributions, and wait for the status to become “Enabled”

After that click on the Distribution ID link
![image](https://github.com/user-attachments/assets/501fe106-d402-46eb-af29-8c184b8198d6)  

Copy the URL and test the web app.
![image](https://github.com/user-attachments/assets/ba87bc23-6c67-4202-b7f3-91812fedf5f0)  

# Testing the App

The web app now works on https!!!

Let’s try to update the price of Avocados
![image](https://github.com/user-attachments/assets/69631a72-85cd-4c32-b779-c3e9a4cb2fc8)  

We enter a new price, and click “Update Prices”
![image](https://github.com/user-attachments/assets/be7c64a6-fed4-487f-a307-8e6a121a3d3f)

A message shows up saying Prices were updated successfully 
![image](https://github.com/user-attachments/assets/0a4c6ae9-ad85-4b88-b676-5ce5197a5c83)  

Now let’s check the prices in the main page

Indeed, the Avocados prices have successfully been updated!!!
![image](https://github.com/user-attachments/assets/72551e38-60cb-4506-8e2b-52b0267e1717)  

We can even verify the change in DynamoDB table
![image](https://github.com/user-attachments/assets/6b47c0df-9eff-452a-9d81-5bb27c1da639)  


# Using a Custom domain (Optional)

Both AWS Route 53 and AWS Certificate Manager can be used to use a custom domain for the web app, which makes it more user friendly, easier to remember, and improves the SEO. More importantly it helps with emphasizing the business brand.

I will not get into that today, and I will leave it for another project, hopefully soon enough!!

### Thanks for reading and I hope you found my step-by-step guide to deploying a serverless web app on AWS enjoyable and informative. If you have any questions or feedback, feel free to reach out.

