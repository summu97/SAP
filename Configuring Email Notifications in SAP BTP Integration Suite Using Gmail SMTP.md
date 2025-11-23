# Configuring Email Notifications in SAP BTP Integration Suite Using Gmail SMTP

This guide explains how to configure and send email notifications from an SAP BTP Integration Flow (IFlow) using Gmail SMTP.  
It includes prerequisites, SMTP configuration, credential setup, IFlow mail adapter configuration, and testing using Postman.

---

## 📌 Prerequisites

Before starting, make sure you have:

- **SMTP Host:** `smtp.gmail.com`  
- **SMTP Port:** `587`
- **Gmail Account:** `sumo1998sumanth@gmail.com(use your gmail)`
- **Gmail App Password** (required, regular Gmail password will NOT work)

### How to Generate a Gmail App Password
1. Log in to your Gmail account.
2. Go to **Google Account → Security**.
3. Enable **2-Step Verification** (mandatory).
4. Search for **App Passwords**.
5. Create a new app password (choose “Mail” and “Other” if needed).
6. Copy and save the generated password somewhere safe — you'll need it for SAP CPI.

---

## 🚀 Step 1: Create Gmail Credentials in Integration Suite

1. Navigate to:  
   **Monitor → Integrations & APIs → Security Material → Create**
2. Choose **User Credentials**.
3. Fill in the details:
   - **Name:** `Gmail`
   - **Description:** (any description)
   - **User:** `sumo1998sumanth@gmail.com(use your gmail)`
   - **Password:** `<your Gmail app password>`
4. Save and **Deploy**.

This creates secure credentials that your IFlow can use when sending emails.

---

## 🚀 Step 2: Test SMTP Connectivity

1. Go to:  
   **Monitor → Integrations & APIs → Test Connectivity**
2. Select **SMTP**.
3. Enter the following:

   | Field         | Value                    |
   |---------------|--------------------------|
   | Host          | `smtp.gmail.com`         |
   | Port          | `587`                    |
   | Proxy Type    | `Internet`               |
   | Protection    | `STARTTLS Optional`      |
   | Authentication| `Plain User/Password`    |
   | Credentials   | `Gmail` (created earlier) |

4. Click **Send**.

If everything is configured correctly, you will receive a **Success** response.

---

## 🚀 Step 3: Configure Mail Adapter in the IFlow

Inside your Integration Flow:

1. Add a **Mail** adapter as the **Receiver**.
2. Configure:

### **Mail — Connection**
- **Address:** `smtp.gmail.com:587`
- **Proxy Type:** `Internet`
- **Protection:** `STARTTLS Optional`
- **Authentication:** `Plain User/Password`
- **Credentials:** `Gmail` (same credentials created earlier)

### **Mail — Processing**
- **From:** `<your SAP login email>`
- **To:** `sumo1998sumanth@gmail.com(use your gmail)`
- **Mail Body:** Your custom message  
- (Other fields optional — set as needed)

3. **Save** and **Deploy** the iFlow.

---

## 🚀 Step 4: Test the IFlow Using Postman

1. Open Postman.
2. Use a **POST** request to your IFlow endpoint (HTTPS URL).
3. Set **Authentication** (e.g., Basic Auth with your BTP user).
4. Add **raw JSON or XML** in the body (sample payload).
5. Click **Send**.

If everything is correct, your Gmail inbox should receive the email triggered by the IFlow.

---

