# Step-by-Step Deployment Guide for PrecisionTakeAI on DigitalOcean

This guide will walk you through deploying the PrecisionTakeAI application on DigitalOcean App Platform. The instructions are designed to be easy to follow, even if you're not familiar with technical deployment processes.

## Prerequisites

- A DigitalOcean account (you've already signed up)
- Your domain name (precisiontake.ai)
- The PrecisionTakeAI codebase (provided in the zip file)

## 1. Preparing Your DigitalOcean Account

### 1.1 Log in to DigitalOcean

1. Go to [https://cloud.digitalocean.com/login](https://cloud.digitalocean.com/login)
2. Enter your email and password
3. Click "Log In"

### 1.2 Set Up Billing (if not already done)

1. In the left sidebar, click "Billing"
2. Add a payment method if you haven't already
3. DigitalOcean will charge based on your usage

## 2. Creating a Database

### 2.1 Create a PostgreSQL Database Cluster

1. In the left sidebar, click "Databases"
2. Click "Create Database Cluster"
3. Select "PostgreSQL" as the database engine
4. Choose the "Basic" plan
5. Select the "Starter" size ($15/month) - this is sufficient for starting out
6. Choose a datacenter region closest to your users (e.g., "New York" for US users)
7. Enter a name for your database cluster (e.g., "precisiontake-db")
8. Click "Create Database Cluster"

### 2.2 Set Up Database Access

1. Once the database is created (this may take a few minutes), click on it
2. In the "Connection Details" section, note down the following information:
   - Host (e.g., `db-postgresql-nyc1-12345-do-user-123456789.b.db.ondigitalocean.com`)
   - Port (usually `25060`)
   - Username (e.g., `doadmin`)
   - Password (click "View Password" to see it)
   - Database name (e.g., `defaultdb`)
3. Keep this information secure - you'll need it later

## 3. Deploying the Application

### 3.1 Create a New App

1. In the left sidebar, click "Apps"
2. Click "Create App"
3. Choose "Upload Source Code" as your source
4. Click "Next"

### 3.2 Upload the Application Code

1. Extract the `precisiontake_project.zip` file on your computer
2. Click "Browse" and select the extracted folder
3. Click "Upload" and wait for the upload to complete
4. Click "Next"

### 3.3 Configure the Application

1. On the "Configure your app" page:
   - Ensure the app name is set to "precisiontake-ai" (or your preferred name)
   - For "Environment Variables", click "Edit" and add the following:
     - `NODE_ENV`: `production`
     - `PORT`: `8080`
     - `SESSION_SECRET`: Create a random string (e.g., `precisiontake-secret-key-12345`)
     - `DATABASE_URL`: Use the format `postgresql://username:password@host:port/database` with the information from step 2.2
   - Click "Save"
2. Click "Next"

### 3.4 Review and Launch

1. Review all settings
2. Click "Create Resources"
3. Wait for the deployment to complete (this may take 5-10 minutes)

## 4. Connecting Your Domain

### 4.1 Add Your Domain to the App

1. Once the app is deployed, click on it
2. Click on the "Settings" tab
3. Scroll down to "Domains" and click "Add Domain"
4. Enter your domain: `precisiontake.ai`
5. Click "Add Domain"

### 4.2 Configure DNS Settings

1. DigitalOcean will provide you with DNS records to add
2. Go to your domain registrar's website (where you purchased precisiontake.ai)
3. Find the DNS settings or DNS management section
4. Add the CNAME record provided by DigitalOcean:
   - Type: `CNAME`
   - Name: `@` (or sometimes `www`)
   - Value: The DigitalOcean app URL (e.g., `precisiontake-ai-abcd1234.ondigitalocean.app`)
   - TTL: `3600` (or "1 hour")
5. Save the changes

### 4.3 Wait for DNS Propagation

1. DNS changes can take up to 48 hours to propagate, but often complete within a few hours
2. You can check the status in the DigitalOcean dashboard under your app's "Domains" section

## 5. Testing Your Deployment

### 5.1 Access Your Application

1. Once the deployment is complete and DNS is configured, visit your domain: `https://precisiontake.ai`
2. You should see the PrecisionTakeAI login page

### 5.2 Create an Admin Account

1. Click "Register" on the login page
2. Fill in your details to create the first admin account
3. Log in with your new account

## 6. Troubleshooting Common Issues

### 6.1 Application Not Loading

- Check if the deployment was successful in the DigitalOcean dashboard
- Verify that your DNS settings are correct
- Try accessing the app using the DigitalOcean URL directly

### 6.2 Database Connection Issues

- Verify that the `DATABASE_URL` environment variable is correct
- Check if the database is running in the DigitalOcean dashboard
- Ensure your app has network access to the database

### 6.3 Getting Help

- DigitalOcean has excellent documentation at [https://docs.digitalocean.com/](https://docs.digitalocean.com/)
- For specific issues with PrecisionTakeAI, refer to the README.md file in the codebase

## 7. Maintaining Your Application

### 7.1 Monitoring

1. In the DigitalOcean dashboard, click on your app
2. The "Insights" tab shows performance metrics
3. Set up alerts for important events by clicking "Create Alert"

### 7.2 Scaling

If you need more resources as your usage grows:
1. Go to your app in the DigitalOcean dashboard
2. Click "Settings" > "Resources"
3. Adjust the instance size or count as needed

### 7.3 Updates

To update your application in the future:
1. Make changes to the codebase
2. Go to your app in the DigitalOcean dashboard
3. Click "Settings" > "Source Code"
4. Click "Upload Source Code" and follow the prompts

## Conclusion

Congratulations! You've successfully deployed PrecisionTakeAI on DigitalOcean App Platform. Your application is now accessible at your custom domain and ready to use.

If you have any questions or need further assistance, please don't hesitate to reach out for support.
