# Content-Based Routing in SAP CPI (Simple Guide)

This guide explains how to perform **Content-Based Routing (CBR)** in SAP CPI (Integration Suite)
using a **Router** and **Terminate Message** endpoints.

---

## ✅ Pre-requisites
- An iFlow with:
  - HTTPS Sender
  - Router
  - Multiple end receivers
  - **Terminate Message** used as endpoints

- Input XML with multiple `<Country>` entries.

---

## ✅ Step 1: Configure Router Routes
1. Drag a **Router** into your iFlow.
2. Add **multiple routes** (one for each country).
3. For each route:
   - Click the route
   - Go to **Processing**
   - **Expression Type:** XML
   - **Condition:**  
     ```
     CountriesData/Country/Name = 'India'
     ```
   Replace `India` with any country you want.

---

## ✅ Step 2: Set the Default Route
1. After all country-specific routes, add **Terminate Message**.
2. Create one more route and point it to the Terminate shape.
3. Select the route → **Processing**
4. Enable: **Default Route**

This ensures:
- If no country matches the condition → the message will go to default terminate.

---

## ✅ Step 3: Test using Postman
POST your XML to your iFlow HTTPS endpoint.

You should see:
- Messages for India → India route
- Messages for Canada → Canada route
- Everything else → Default Route

---

## ✅ Sample XML Input (Use in Postman)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<CountriesData>
    <Country>
        <Name>India</Name>
        <Capital>New Delhi</Capital>
        <Currency>INR</Currency>
        <Language>Hindi</Language>
    </Country>

    <Country>
        <Name>Canada</Name>
        <Capital>Ottawa</Capital>
        <Currency>CAD</Currency>
        <Language>English</Language>
    </Country>

    <Country>
        <Name>Australia</Name>
        <Capital>Canberra</Capital>
        <Currency>AUD</Currency>
        <Language>English</Language>
    </Country>
</CountriesData>
