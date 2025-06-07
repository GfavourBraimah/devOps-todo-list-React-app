# 📋 DevOps To-Do List React App (Manual Deployment via AWS Console)

This project demonstrates how to manually deploy a React application to **AWS** using the **AWS Management Console**.

I manually deployed my React app by building it locally and uploading the build folder to an S3 bucket configured for static website hosting. I applied a bucket policy for public access and created a CloudFront distribution pointing to the S3 endpoint. I tested and confirmed the React app was accessible through the CloudFront URL.

---

## 📌 Week 2: Manual Deployment via AWS Console

### 🎯 Objective
Gain hands-on experience configuring and deploying AWS services **without automation tools**, using only the AWS Console.

---

## 🚀 Local App Build

```bash
npm install
npm run build
```

---

## 📋 Deployment Steps

### Step 1: Create and Configure S3 Bucket

**Create S3 Bucket**
* Created an S3 bucket named: `devops-todo-list346.`

**Enable Static Website Hosting**
* Navigate to **Properties** tab
* Enable **Static Website Hosting**
* Configure settings:
  * **Index document**: `index.html`
  * **Error document**: `index.html`

**Configure Public Access**
* Disable "Block all public access"
* Add the following bucket policy for public read access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::devops-todo-list346./*"
    }
  ]
}
```

📸 **Screenshot**:  ![Screenshot](/images/S31.png)


---

### 📁 Step 2: Upload Build Files to S3

1. **Build the React application locally:**
   ```bash
   npm run build
   ```

2. **Upload all files from the `build/` directory using the AWS Console**

📸 **Screenshot**:  ![Screenshot](/images/s3bucket.png)

3. **Verify files are publicly accessible via S3 Static Website Endpoint**

---

### 🌐 Step 3: Configure CloudFront Distribution

**Create CloudFront Distribution** with the following configuration:
* Uses the S3 website endpoint as its origin
* Redirects HTTP to HTTPS
* Sets **index.html** as the default root object

📸 **Screenshot**:![CloudFront Setup](/images/cloudfront.png)

---

## 🔗 Live Application

* **CloudFront URL**: 👉 https://d2cse1w212ycna.cloudfront.net/ 


![CloudFront URL](/images/react3.png)

---

## 📝 Summary of Manual Steps

1. ✅ Built the React app locally using `npm run build`
2. ✅ Created an S3 bucket and enabled static hosting
3. ✅ Uploaded the `build/` folder to the S3 bucket
4. ✅ Applied a public-read bucket policy
5. ✅ Created a CloudFront distribution with the S3 website as origin


---

## 🛠️ Technologies Used

* **AWS S3** - Static website hosting
* **AWS CloudFront** - Content Delivery Network
* **React** - Frontend framework

---

## 📚 Additional Resources

* [AWS S3 Static Website Hosting Guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
* [AWS CloudFront Documentation](https://docs.aws.amazon.com/cloudfront/)
* [AWS Route 53 Documentation](https://docs.aws.amazon.com/route53/)

---

## 🤝 Contributing

Feel free to submit issues and enhancement requests!

---
