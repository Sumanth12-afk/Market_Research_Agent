# 📊 Market Research Agent Workflow

## 🧾 Overview

This repository contains an **n8n workflow** (`Market_research_agent.json`) designed to automate market research by fetching trending topics from **Google Trends** and related **YouTube** video data using **SearchAPI** and **SerpAPI**. The data is appended to two **Google Sheets**:

- One for trending topics  
- One for YouTube video details

### Features

- 🔍 Retrieve trending search queries in India from Google Trends  
- 🔝 Filter the top 5 trending topics  
- 📺 Search YouTube for related videos  
- 📊 Store results in Google Spreadsheets for analysis  

---

## ✅ Prerequisites

To use this workflow, you’ll need:

- **n8n:** Installed (self-hosted or cloud). [Get started with n8n](https://n8n.io/).
- **Google Sheets API Access:**
  - A Google Cloud project with the Sheets API enabled  
  - OAuth2 credentials (configured in n8n)  
  - Two Google Sheets as described below  
- **API Keys:**
  - A **SearchAPI** key for Google Trends data  
  - A **SerpAPI** key for YouTube search  
- **GitHub account** and a repository to store the workflow  

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/your-repo-name.git  
cd your-repo-name
```

---

### 2. Prepare Google Sheets

#### A. Trending Topics Sheet

- **File name:** `trending topics`  
- **Tab name:** `Sheet1`  
- **Columns:**  
  ```
  Keyword | Search Volume | Percentage Increase | Categories | Related Keywords
  ```

#### B. YouTube Sheet

- **File name:** `Youtube`  
- **Tab name:** `Sheet1`  
- **Columns:**  
  ```
  Topic | title | url | Views | channel | uploaded
  ```

> 📌 **Important:** Share both sheets with the Google account linked to n8n (with Editor access).

---

### 3. Import Workflow into n8n

1. Open your n8n instance  
2. Go to **Workflows > Import from File**  
3. Import `Market_research_agent.json` from this repo  
4. The workflow will appear in your n8n workspace  

---

### 4. Configure Credentials

#### Google Sheets (OAuth2)

- Go to **Credentials > Add Credential > Google Sheets OAuth2 API**  
- Authenticate with your Google Cloud project  
- Link the credential to the **Google Sheets** and **Google Sheets1** nodes  

#### API Keys

- **SearchAPI Key:**  
  Update the `HTTP Request` node with your key  
  ```
  api_key=YipuyXF7fkyLUyTX1YboRfCf
  ```
- **SerpAPI Key:**  
  Update the `HTTP Request1` node with your key  
  ```
  api_key=91647d89330889486d3a58fd05978ec66af6423c9179ff4db5c4870f7c37725a
  ```

> 🔐 Replace placeholder keys with your actual API keys securely.

---

### 5. Verify Google Sheets

- Ensure the spreadsheet IDs in the nodes match the actual ones  
- Confirm both sheets use `Sheet1` as the tab name  

---

### 6. Test the Workflow

- Open the workflow in n8n  
- Click **Test Workflow** to trigger the execution  
- Monitor to ensure data is fetched and updated in both Google Sheets  

---

## 🧠 Workflow Details

This workflow includes:

| Node                | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `When clicking 'Test workflow'` | Manual trigger for testing workflow                             |
| `HTTP Request`      | Fetches top trends from Google Trends (India) using SearchAPI               |
| `Split Out`         | Splits response into individual trend items                                 |
| `If`                | Filters the top 5 trends by position (`position <= 5`)                      |
| `Google Sheets`     | Appends filtered trends into `Sheet1` of `trending topics` sheet            |
| `HTTP Request1`     | Searches YouTube for each trend using SerpAPI                               |
| `Split Out1`        | Splits YouTube search results                                               |
| `If1`               | Filters top 6 YouTube videos (`position_on_page < 6`)                       |
| `Google Sheets1`    | Appends video data into `Sheet1` of `Youtube` sheet                         |

---

## ▶️ Usage

- **Run Workflow:** Manually trigger or schedule using n8n  
- **Monitor Output:** Check Google Sheets `Sheet1` tabs  
- **Analyze:** Use the data for market insights, content planning, etc.  

---

## 🔒 Security Notes

- **API Keys:** Keep your API keys secure. Use n8n’s credential management.  
- **Google Sheets:** Only share with authorized users.  
- **Rate Limits:** Be mindful of API usage limits to prevent disruptions.  

---

## 🤝 Contributing

Contributions are welcome!  
Here’s how to get started:

```bash
# Fork and clone
git checkout -b feature/your-feature

# Make changes and commit
git commit -m "Add your feature"

# Push and open a PR
git push origin feature/your-feature
```

---

## 📄 License

This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for details.

---

## 📬 Contact

For support, please open an issue or contact:  
**sumanthnallandhigal@gmail.com**
