
---
Allowing Headers from Source.md

To allow specific headers from the incoming message to be passed through the Integration Flow, you must **whitelist** them in the Runtime Configuration.

## **Steps**

1. Click on the **blank/empty space** of your iFlow (not on an object).
2. Go to **Runtime Configuration** (right-side panel).
3. Find the field **Allowed Headers**.
4. Add the headers you want to allow (whitelist).

### **Example**

If your source message sends headers like:

* `Country`
* `City`
* `Place`

Then add them in the Allowed Headers as:

```
Country|City|Place
```

### **Notes**

* Headers are case-sensitive.
* Multiple headers must be separated using the pipe symbol `|`.
* Only allowed headers can be accessed later using:

  ```
  ${header.<HeaderName>}
  ```

---
