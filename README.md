# My AWS Web App Project

## Project Overview

This project enhances a basic AWS S3 static website deployment by integrating CloudFront for global distribution, AWS Certificate Manager (ACM) for SSL encryption, and CloudWatch for logging. It is designed for a real-world production setup, ensuring security, scalability, and monitoring.

---

## Technologies Used

- **AWS S3**
- **CloudFront**
- **AWS Certificate Manager**
- **Cloudwatch**
- **Cloudflare**

---

## Prerequisites

- Bash 
- Visual Studio Code
- AWS Account
- Git
  
---

## Project Setup

### Step 1: Create an S3 Bucket

1. I began by creating a bucket, naming it the same domain I intend to use: ***static.damiadeprojects.uk***
2. I ensured that ```Block all public access``` was left unchecked
3. Enabled static website hosting
   ![Screenshot 2025-03-27 140137](https://github.com/user-attachments/assets/c9cccd96-f8bf-4762-84be-e5b889f9d74e)

### Step 2: Upload Webapp Files to S3

1. I dragged and dropped the files from my local machine to the S3 Bucket
![Screenshot 2025-03-28 013307](https://github.com/user-attachments/assets/9a5bc116-a888-4255-b6ce-01296c291f5b)

### Step 3: Configure Bucket Policy for Public Access

1. I added the following policy to enable public access:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::static.damiadeprojects.uk/*"
        }
    ]
}
```
### Step 4: Set Up CloudFront Distribution

1. To enable the app to reach globally, I created a CloudFront web distribution
2. I made the Origin Domain Name my S3 bucket
3. I enabled and created an Origin Access Control
4. I set the Viewer Protocol Policy to "redirect HTTP to HTTPS"
   ![Screenshot 2025-03-27 140938](https://github.com/user-attachments/assets/0bacf7d9-97fc-4230-a61b-77c9177a53c9)


### Step 5: Configured DNS for CloudFront

1. Since I manage my domain on Cloudflare instead of Route53, I created a CNAME record with the name being ```static.damiadeprojects.uk``` and the target being the CloudFront distribution domain provided to me
   ![Screenshot 2025-03-27 140402](https://github.com/user-attachments/assets/8470a116-b7ef-411c-9217-e31959722b6c)

### Step 6: Enable SSL Certificate on CloudFront

1. I went to AWS Certificate Manager and requested a new certificate for static.damiadeprojects.uk
2. I went back to Cloudflare to validate the certificate, adding CNAME records provided by ACM
3. After being issued, I attached the certificate to my CloudFront distribution 

### Step 7: Enable CloudWatch Logs for CloudFront

1. On CloudWatch, i created a new log group called ```/aws/cloudfront/static-damiadeprojects-logs```
2. I then went back to the Logging tab of my distribution and chose ```CloudWatch Logs```
![Screenshot 2025-03-28 012853](https://github.com/user-attachments/assets/54afb006-a0bf-4de4-99c1-89aeda1c54b5)


### Project Completed

When I navigated to ```static.damiadeproejcts.com```, I can now see the secured icon
![Screenshot 2025-03-27 143322](https://github.com/user-attachments/assets/10e42b55-86d2-44c6-8346-951d604760d5)

---

## Conclusion

This project demonstrates a comprehensive approach to deploying static websites on AWS S3, tailored for real-world production use. By incorporating security, scalability, and monitoring, it goes beyond simple hosting to provide a robust, high-performance solution for clients.
