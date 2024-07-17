# Serverless Web Application Project

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


