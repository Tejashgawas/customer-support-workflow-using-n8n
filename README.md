# Customer Support AI Workflow

This project describes an **automated Customer Support AI workflow** that categorizes incoming emails, applies appropriate labels, and generates intelligent replies using a knowledge base.  
The system streamlines customer service operations by delivering **fast, accurate responses** to common inquiries.

---

## 📜 Overview
The workflow processes incoming customer emails end-to-end, using AI to classify queries and craft responses.  
It consists of the following key components:

1. **Email Ingestion** – Automatically detects and captures new emails.  
2. **Email Categorization** – Uses AI to classify the type of inquiry.  
3. **Intelligent Response Generation** – Leverages a knowledge base to create detailed replies.  
4. **Action Automation** – Labels and responds to emails without human intervention.

---

## ⚙️ Workflow Breakdown

### 1. Gmail Trigger
- A **Gmail Trigger** detects a new incoming email.
- This event initiates the workflow, ensuring that every new customer message is processed immediately.

### 2. Text Classifier
- The email’s **subject and body** are sent to a **Text Classifier** powered by an **OpenAI Chat Model**.  
- The classifier categorizes the email. Example categories:
  - `Customer Support`
  - `Others` (spam, newsletters, personal emails)
  - Optional extensions: `Billing Inquiry`, `Technical Issue`, `Product Feedback`, etc.

### 3. AI Agent (Customer Support Path)
If the email is classified as **Customer Support**, the workflow activates an AI Agent to generate a response.

- **Knowledge Base**  
  A **Pinecone Vector Store** contains company policies, FAQs, and other relevant documents.

- **Embeddings**  
  The customer query is converted into a **vector representation** using **OpenAI Embeddings**, enabling semantic search within the knowledge base.

- **Model**  
  An AI chat model (e.g., **4o-mini-chat**) processes:
  - The customer’s message
  - The retrieved knowledge base content  
  It then formulates a **context-rich and accurate reply**.

### 4. Automated Actions
Once the AI Agent generates a response, two automated actions occur:

- **Add Label to Message**  
  A Gmail label such as `"Customer Support Handled"` or `"Auto-Replied"` is applied for easy tracking.

- **Reply to Message**  
  An **automated email reply** is sent to the customer, providing an immediate response that may fully resolve the issue.

### 5. “Do Nothing” Path (Others)
If the email is categorized as **Others** (spam, newsletters, etc.), the workflow routes it to a **No Operation** node.  
This ensures irrelevant messages are ignored.

---

## 🚀 How to Use and Customize

### 1. Integration
The workflow requires:
- **Gmail API** – Detects new emails and sends replies.
- **OpenAI API Key** – Powers the text classifier and embeddings.
- **Pinecone API Key** – Manages the knowledge base vector store.

### 2. Customization
- **Categorization**  
  Train or fine-tune the classifier to detect more granular categories such as:
  - `Refund Request`
  - `Order Status`
  - `Account Access`

- **Knowledge Base**  
  Populate the Pinecone Vector Store with:
  - Company policies
  - Product documentation
  - Detailed FAQs  
  The quality and breadth of this data directly influence the AI’s response accuracy.

- **AI Model**  
  Swap **4o-mini-chat** with other language models to balance **performance**, **latency**, and **cost**.

- **Workflow Actions**  
  Extend the automation to:
  - Create support tickets in **CRM systems** (Salesforce, Zendesk, etc.)
  - Notify human agents for complex or high-priority cases
  - Trigger follow-up workflows such as order tracking or escalation

---

## ✅ Conclusion
This **Customer Support AI workflow** delivers a powerful, scalable solution for handling routine customer inquiries.  
By using AI to classify emails, retrieve information, and generate responses, the system:
- Reduces manual workload  
- Accelerates response times  
- Frees human agents to focus on **complex, high-value interactions**
