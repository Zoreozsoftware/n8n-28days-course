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

# 🚀 n8n Learning Journey - Day 3

## 📌 Task Overview
On **Day 3**, the focus was on learning **conditional branching** with the **IF node**.  
We used mock lead data and routed workflow execution based on the lead’s source.

---

## ✅ Steps Completed

1. **Created Mock Data**
   - Used a **Set Node** to generate lead information:
     ```json
     {
       "Name": "Shahood",
       "Email": "shahood@example.com",
       "LeadSource": "Facebook"
     }
     ```

2. **Added IF Node**
   - Condition: `LeadSource` equals `"Website"`.  
   - If **True** → run the “Website path”.  
   - If **False** → run the “Non-Website path”.

3. **Configured Website Path (True branch)**
   - For now, a simple **Set Node** to confirm workflow routing worked.  
   - Message example: `Welcome Website lead – {{$json["Name"]}}`.

4. **Configured Non-Website Path (False branch)**
   - Added a **Slack Node** to send an alert when a lead comes from another source.  
   - Slack message template:
     ```
     🚦 Non-Website Lead
     Name: {{$json["Name"]}}
     Email: {{$json["Email"]}}
     Source: {{$json["LeadSource"]}}
     ```

5. **Tested Workflow**
   - Case 1: `LeadSource = Website` → Website path executed.  
   - Case 2: `LeadSource = Facebook` → Slack notification triggered.

---

## 📖 Resources Used
- [IF Node Docs](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.if/)  
- [Slack Node Docs](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.slack/)  

---

## 📝 Learnings
- How to use **IF node** for conditional routing.  
- How to pass mock data into workflows with a **Set Node**.  
- How to trigger different outputs (Slack message vs Website path).
- <img width="1347" height="620" alt="image" src="https://github.com/user-attachments/assets/c0bf3dbc-2ffb-44c4-ad3d-a25ed38487f2" />
 

---
  

# Day 4 – Split Data into Batches  

## 🎯 Goal  
Understand how to use the **SplitInBatches node** in n8n to process data in smaller groups instead of all at once. This is essential when working with **large datasets** or **APIs that have rate limits**.  

---

## 🛠 What We Did  
1. Created **10 mock leads** using a Code node with fields:  
   - `Name`  
   - `Email`  
   - `LeadSource`  

2. Added a **SplitInBatches node**:  
   - Set **Batch Size** = `3`  
   - Connected Code → SplitInBatches  

3. Connected outputs:  
   - **Loop output** → NoOp node (to preview batch items)  
   - **Done output** → Finished node (to confirm workflow completion)  

4. Ran the workflow:  
   - First run showed **3 leads** in NoOp.  
   - Clicked **Continue Workflow** to process next 3 leads.  
   - Repeated until all 10 leads were processed.  
   - Finally, the **Done output** triggered the Finished node.  

---

## ✅ Key Learnings  
- **Loop output** runs once for every batch.  
- **Done output** runs **only once** after the last batch is processed.  
- This node is crucial for:  
  - Handling **APIs with rate limits** (send requests gradually).  
  - Breaking **large datasets** into smaller parts.  
  - Running workflows more **efficiently**.  

---

## 📸 Deliverables  
- Workflow file: `day04_split_batches.json`  
- Screenshot showing:  
  - Batch 1 (3 items)  
  - Batch 2 (3 items)  
  - Batch 3 (3 items)  
  - Batch 4 (1 item)  
  - Done output triggered  

---

## 📚 References  
- n8n Docs: [SplitInBatches Node](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.splitinbatches/)  
- 28-Day Roadmap → Day 4 Task  

---
<img width="1419" height="652" alt="image" src="https://github.com/user-attachments/assets/660b900c-64e4-4933-a224-f9860b104107" />

## 💡 Bonus  
In future workflows, this setup can be extended by connecting each batch to an **API call (HTTP Request node)**, making it ideal for bulk data processing.  
# Day 5 – API Requests with n8n  

## 🎯 Goal  
Learn how to use the **HTTP Request node** in n8n to send data to an external API and handle responses.  

---

## 🛠 What We Did  
1. Started with **10 mock leads** using a Code node (Name, Email, LeadSource).  
2. Added **SplitInBatches node** (batch size = 3) to process leads in groups.  
3. Connected **Loop output → HTTP Request node**.  
4. Configured HTTP Request:  
   - **Method**: `POST`  
   - **URL**: `https://jsonplaceholder.typicode.com/posts` (test API)  
   - **Body Content Type**: `JSON`  
   - **JSON Body**:  
     ```json
     {
       "name": "{{$json['Name']}}",
       "email": "{{$json['Email']}}",
       "leadSource": "{{$json['LeadSource']}}"
     }
     ```  
5. Connected HTTP Request → **NoOp node** to preview API responses.  

---

## ✅ Key Learnings  
- The **HTTP Request node** is the gateway to any API.  
- You can send dynamic data using **expressions** (`{{$json['FieldName']}}`).  
- **SplitInBatches** helps prevent hitting API rate limits by sending data gradually.  
- Fake APIs like [JSONPlaceholder](https://jsonplaceholder.typicode.com/) are perfect for testing.  

---

## 📸 Deliverables  
- Workflow file: `day05_api_requests.json`  
- Screenshot showing API responses with IDs.  

---

## 📚 References  
- n8n Docs: [HTTP Request Node](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/)  
- Test API: [JSONPlaceholder](https://jsonplaceholder.typicode.com/)  
<img width="1619" height="798" alt="image" src="https://github.com/user-attachments/assets/ed9eb72c-78d7-46d4-aafb-57b162a75781" />





