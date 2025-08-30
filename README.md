# Day 1 — Orientation & First Run

## 🎯 Goal
Get familiar with the **n8n Editor UI**, basic triggers, executions, and credentials setup.

---

## 🛠️ Task
1. Create a workflow with:
   - **Manual Trigger**
   - **Set Node** (mock lead data: name + email)
   - **NoOp Node** (preview output only)
2. Run the workflow once and take a screenshot of the execution.
3. Export workflow as `01_first_run.json`.

---

## 📂 Deliverables
- `01_first_run.json` → exported workflow file  
- `screenshot.png` → screenshot of successful execution  

---

## 📖 Learning Resource
This task is based on **n8n official documentation**:  
👉 [n8n Level One — Chapter 1](https://docs.n8n.io/courses/level-one/chapter-1/)

---

## ✅ Outcome
By the end of Day 1:
- You understand the **Editor UI layout**.  
- You can add **nodes** and connect them.  
- You can execute and inspect workflows.  

---

📌 Next: Day 2 — Connect Google Sheets & Notion 🚀
<img width="1274" height="693" alt="image" src="https://github.com/user-attachments/assets/e9eb5b51-4d34-4702-a6da-628109a4b2e8" />
📌 Next: Day 2 — Connect Google Sheets & Notion 🚀
# 🚀 n8n Learning Journey - Day 2

## 📌 Task Overview
On **Day 2**, the focus was on integrating **Google Sheets** with n8n and learning how to pass data from one node (Set Node) into another (Google Sheets Node).

---

## ✅ Steps Completed

1. **Created Google Cloud Credentials**
   - Set up project in [Google Cloud Console](https://console.cloud.google.com/).
   - Created **OAuth Client ID** credentials.
   - Configured **OAuth Consent Screen** and added test users.
   - Connected the credentials to n8n.

   🔗 Guide: [Google OAuth Consent Screen Setup](https://developers.google.com/workspace/guides/configure-oauth-consent)

2. **Google Sheets Node Integration**
   - Created a **Google Sheet** with columns:
     ```
     Name | Email | Lead Source
     ```
   - In n8n:
     - Added a **Set Node** to generate mock data:
       ```json
       {
         "Name": "Shahood",
         "Email": "shahood@example.com",
         "Lead Source": "Website"
       }
       ```
     - Connected it to a **Google Sheets Node** (Append Row).
     - Mapped Set Node fields → Google Sheet columns.

   🔗 Guide: [Google Sheets Node Docs](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.googlesheets/)

3. **Expression Issue Debug**
   - Tried inserting values using expressions like:
     ```
     {{$json["Name"]}}
     {{$json["Email"]}}
     {{$json["Lead Source"]}}
     ```
   - Learned that values should be **mapped in the node field settings** instead of being written directly in Google Sheets.

---

## 📖 Resources Used
- [n8n Level 1 Course (Chapter 2 onwards)](https://docs.n8n.io/courses/level-one/chapter-1/)  
- [Google Cloud Console](https://console.cloud.google.com/)  
- [Google OAuth Consent Screen Guide](https://developers.google.com/workspace/guides/configure-oauth-consent)  
- [Google Sheets Node Docs](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.googlesheets/)  

---

## 📝 Learnings
- Understood **OAuth vs Service Accounts** for Google APIs.  
- Successfully created test credentials and connected Google Sheets.  
- Learned how to pass structured data from a **Set Node** to **Google Sheets Node**.  
- Realized the importance of **field mapping in n8n nodes** rather than putting expressions inside the sheet itself.
- <img width="1166" height="718" alt="image" src="https://github.com/user-attachments/assets/89502389-b9fa-4b4c-867d-af2d5558cbef" />


---

## 🔜 Next (Day 3 Preview)
- Explore **If / Switch Nodes**.  
- Learn **branching workflows** for conditional logic.  
- Work on handling **multiple inputs & data flow control**.  

---


