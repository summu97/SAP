# Creating Dynamic Properties in SAP CPI Using Content Modifier (XPath Extraction)

This guide explains how to extract a value from an incoming XML payload using **XPath**, store it as an **Exchange Property** in a Content Modifier, and then reuse that property (for example, inside a Mail Adapter or any downstream step in your Integration Flow).

---

## 📌 Purpose  
Use an XML field (e.g., Country name) from the incoming request and dynamically insert it into email bodies, logs, script steps, or any CPI component using `${property.<name>}` notation.

---

## 📦 Example Input XML

```xml
<CountriesData>
    <Country>
        <Name>India</Name>
    </Country>
</CountriesData>
```


## ✅ Step 1: Add a Content Modifier  
1. Inside your IFlow, insert a **Content Modifier** before the step where you want to use the extracted value.  
2. Open the **Exchange Property** tab.  
3. Click **Add** and configure:

| Field | Value |
|-------|--------|
| **Action** | `Create` |
| **Name** | `Country` *(or any property name you prefer)* |
| **Source Type** | `XPath` |
| **Source Value** | `CountriesData/Country/Name` |
| **Data Type** | `java.lang.String` |

### ✔ Explanation  
- CPI will evaluate the XPath expression against the incoming XML.  
- Whatever value is found at `CountriesData/Country/Name` becomes the property **Country**.  
- The property stays available for the entire message execution.

---

## 📨 Step 2: Use the Property in Mail Adapter (or any step)

When configuring the **Mail Adapter → Processing → Mail Body**, you can reference your property:

```
Hello Team,

The country received from input is: ${property.Country}

Regards,
SAP CPI
```
