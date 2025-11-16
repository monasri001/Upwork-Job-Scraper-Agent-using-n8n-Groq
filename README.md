# 🚀 Automated Upwork Job Scraper (AI-Powered)

An intelligent **automated job-scraping and filtering system** built using **n8n**, **RapidAPI**, **Groq LLaMA model**, and **Airtable**.  
This workflow automatically fetches Upwork jobs, filters them for relevance using an LLM, and stores structured job data in Airtable.

---

## 📌 Features

### ✅ 1. Automated Upwork Job Scraping  
Fetches **fresh freelance job posts every hour** (or manually) using:
- **RapidAPI – Upwork Jobs API**
- Custom search terms (e.g., "Python developer")
- Up to **200 jobs per request**

### ✅ 2. AI-Powered Job Relevance Filtering  
Uses **Groq LLaMA-3.3-70B** to:
- Analyze job **title, description, skills, budget**
- Filter based on your criteria
- Output JSON:
      ```json
            {
              "result": "true/false",
              "reason": "Why the job is/is not relevant",
              "icebreaker": "Custom intro message for applying"
            }


### ✅ 3. Structured Data Extraction
n8n code node extracts:

Job title

Description

Skills

Budget (hourly/fixed)

Client location

Job URL

### ✅ 4. Airtable Auto-Insertion

All filtered jobs are inserted into Airtable with fields:

Job Title

Job Description

Skills

Budget

Client Location

URL

Status

### 5. ✅ Fully Automated

A Schedule Trigger runs the scraper every 3 days

Manual trigger available during testing

🧩 System Architecture
[Schedule Trigger / Manual Trigger]
                ⬇
         [HTTP Request Node]
                ⬇
        [Code Node — Format Data]
                ⬇
        [AI Filter — Groq LLaMA]
                ⬇
      [Structured Output Parser]
                ⬇
     [Airtable — Store Job Record]

⚙️ Technologies Used
Component	Purpose
n8n Automation	Orchestrates entire workflow
RapidAPI – Upwork Jobs API	Source for Upwork job data
Groq LLaMA-3.3-70B	AI-powered job filtering
n8n Code Node	Converts raw response into structured JSON
Airtable	Stores filtered job listings
📥 Input Example (Scraped Job)
{
  "title": "Python Automation Script Needed",
  "description_text": "Need an automation built using Selenium...",
  "skills": [{"name": "Python"}, {"name": "Selenium"}],
  "project_budget_hourly_min": 20,
  "project_budget_hourly_max": 40,
  "client_city": "New York",
  "client_country": "United States",
  "url": "https://www.upwork.com/job/12345"
}

📤 AI Output Example
{
  "result": "true",
  "reason": "This is directly aligned with automation using Python & Selenium.",
  "icebreaker": "Confident I’m the Python automation expert you’re looking for..."
}

🛠 Setup Instructions
1. Clone the Repository
git clone https://github.com/<your-username>/<your-repo>.git
cd your-repo

2. Import Workflow into n8n

Upload:

Upwork_Job_Scraper.json

3. Create Required API Keys
Service	Required Key
RapidAPI	Upwork Jobs API key
Groq	Groq API Key
Airtable	Personal Access Token

Configure these under n8n → Credentials.

4. Modify Search Terms

Inside HTTP Request Node:

search = "Python developer"
limit = 200

5. Enable Schedule Trigger

Runs automatically every 3 days.
You can also run manually for testing.

📊 Airtable Output Example
Title	Skills	Budget	Location	URL	Status
Python Automation Script	Python, Selenium	$20–$40/hr	New York, US	link	found
🧪 Testing

Use Manual Trigger for debugging the workflow before scheduling.

📈 Future Improvements

Auto-apply to relevant jobs

Email notifications

Multi-platform scraping

Dashboard analytics

AI-based job scoring

🤝 Contributing

Pull requests and issues are welcome!
Feel free to improve the scraping logic, LLM filtering, or Airtable schema.
