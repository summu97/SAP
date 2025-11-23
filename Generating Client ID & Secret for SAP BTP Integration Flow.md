## 🔐 Generating Client ID and Secret for SAP BTP Integration Flow

---

## ✅ Step 1: Ensure “SAP Process Integration Runtime” is Available

### Check if the Service Exists
1. Go to **SAP BTP Cockpit → Subaccount → Instances**.
2. Click **Create**.
3. Search for **SAP Process Integration Runtime**.

### Case 1: Service NOT Available
If the service does not appear:

1. Go to **Global Account → Entitlements → Entity Assignments**.
2. Under **Subaccounts/Directories**, select your subaccount.
3. Click **Edit**.
4. Search for **SAP Process Integration Runtime**.
5. Add the following service plans:
   - `integration-flow`
   - `api`
6. Click **Save**.

Now the service will show up in your Subaccount.

---

## ✅ Step 2: Create an Instance of SAP Process Integration Runtime

Navigate to:

**BTP Cockpit → Subaccount → Instances → Create**

Use the following settings:

| Field                | Value                             |
|----------------------|------------------------------------|
| **Service**          | SAP Process Integration Runtime     |
| **Plan**             | integration-flow                    |
| **Runtime**          | Cloud Foundry                       |
| **Space**            | dev                                |
| **Instance Name**    | `CPI_SAMPLE_INSTANCE`               |

Click **Next**.

### Roles
- **ESBMessaging.send** (preselected automatically)

### Grant Type
- **Client Credentials**

Click **Next** → **Create**.

You now have an active OAuth-enabled instance.

---

## ✅ Step 3: Create a Service Key (Client ID + Secret)

1. Go to **BTP Cockpit → Subaccount → Instances**.
2. Select your instance, e.g., `CPI_SAMPLE_INSTANCE`.
3. Open the **Service Keys** tab.
4. Click **Create Service Key**.
5. Fill in:
   - **Name:** (your choice)
   - **Key Type:** Client ID / Secret
6. Click **Create**.

---

## 🎉 Step 4: Retrieve the OAuth Credentials

Open the newly created service key.  
You will see a JSON structure containing:

- `"clientid"`
- `"clientsecret"`
- `"tokenurl"`
- `"url"`

These credentials are used for OAuth 2.0 Client Credentials authentication in tools like:

- Postman  
- External Applications  
- SAP API Client  
- Backend Automations  

---


This completes the setup of OAuth Client Credentials with Client ID & Secret for SAP BTP Integration Suite.
