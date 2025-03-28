# My AWS Web App Project

## Project Overview

In this project, I built a static web app using HTML, CSS and JavaScript. I then deployed and hosted it on Amazon S3.

---

## Technologies Used

- **HTML**
- **CSS**
- **JavaScript**
- **Amazon S3**

---

## Prerequisites

- Bash 
- Visual Studio Code
- AWS Account
- Git
- Internet connection
  
---

## Project Setup

### Step 1: Project Initialisation

- I began by creating a project directory on my local machine to hold all the project files called "web-app-project."
- In this same directory, I created the following files: ```index.html```, ```style.css``` and ```script.js```.
- I used Visual Studio Code editor to edit these files.
     
### Step 2: HTML Structure

- I created the ```index.html``` file to structure the web page with a ```<header>``` ```<section>``` and ```<footer>```
- The ```<head>``` includes meta tags for character encoding and viewport, a title, and a link to the ```style.css``` file.
- The body contains a heading, a paragraph, a button, and footer text.
- I then linked the ```script.js``` file at the bottom to ensure JavaScript loads after the content.

### Step 3: Styling with CSS

- I created the ```style.css``` file to give the heading and footer a light blue background and white font
- I also gave the "Click Me" button a green colour which changes on hover.
  

### Step 4: Adding JavaScript

- I created a script.js file that allows visitors to interact with the "Click Me" button
- Once clicked, a JS event listener triggers an alert with "Hello, you clicked the button!"

---

## Deploying to Amazon S3

### Step 1: Create an S3 Bucket

- To deploy the web app, I created an S3 Bucket on AWS, giving it the unique name of "Static-Web-App-Project" and choosing my region.

### Step 2: Upload Project Files to S3

- I then dragged the project folder from my local machine to the S3 bucket
![Screenshot 2025-03-17 153704](https://github.com/user-attachments/assets/ee871ef0-82e6-4805-8b16-4f1d46d9dfc6)

### Step 3: Configuring S3 Bucket for Public Access and Static Hosting

- In the S3 Bucket, I enabled static web hosting by going to the "Properties" tab and selecting "Use this bucket to host a website." on the "Static website hosting" section.
- I then specified the index.html as the index document and error.html as the error document, ensuring visitors go to the right pages.
![Screenshot 2025-03-18 123144](https://github.com/user-attachments/assets/55f2bb8b-0e44-4c80-968c-6a2e1e34f2a3)

- I then configured the permissions to allow public access to the bucket by adding a bucket policy that grants ```s3:GetObject``` permission to everyone (public access):

``` {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::static-web-app-project/*"
    }
  ]
}
```


### Step 4: Testing and Verifying Deployment

- After deploying the project to S3, I tested it by copying the URL provided in the "Static Website Hosting" section of the bucket properties. I then pasted it into a web browser and succesfull accessed the web app as shown below:
![Screenshot 2025-03-18 155813](https://github.com/user-attachments/assets/50313cb0-aa74-47e4-a5ef-d9d1fe7ef4ef)

---

## Conclusion

This was a simple project to demonstrate my confidence with HTML, CSS and Javascript to create the web app and deploy and host it on Amazon S3. I learned the importance of structuring the files on S£ correctly, as I couldn't access the web app initially because the index.html file wasn't at the root of my S3 Bucket. Once I moved it to the root, I could then access the web app successfully.
