🚀 Automated Upwork Job Scraper (AI-Powered)
An intelligent automated job-scraping and filtering system built using n8n, RapidAPI, Groq LLaMA model, and Airtable.
This workflow automatically fetches Upwork jobs, filters them for relevance using an LLM, and stores structured job data in Airtable.
&lt;p align="center"&gt;
  &lt;img src="https://cdn.worldvectorlogo.com/logos/upwork.svg" height="60"&gt;
  &lt;img src="https://n8n.io/img/logo-horizontal.svg" height="60"&gt;
  &lt;img src="https://seeklogo.com/images/A/airtable-logo-216B9AF35D-seeklogo.com.png" height="60"&gt;
  &lt;img src="https://avatars.githubusercontent.com/u/144002145?s=200&amp;v=4" height="60"&gt;
&lt;/p&gt;

📌 Features
✅ 1. Automated Upwork Job Scraping
Fetches fresh freelance job posts every hour (or manually) using:


RapidAPI – Upwork Jobs API


Custom search terms (e.g., "Python developer")


Up to 200 jobs per request


✅ 2. AI-Powered Job Relevance Filtering
Uses Groq LLaMA-3.3-70B to:


Analyze job title, description, skills, budget


Filter based on your criteria (skills, domain, task type)


Output JSON:


{
  "result": "true/false",
  "reason": "Why the job is/is not relevant",
  "icebreaker": "Custom intro message for applying"
}



          
            
          
        
  
        
    

✅ 3. Structured Data Extraction
n8n code node extracts:


Job title


Description


Skills


Budget (hourly/fixed)


Client location


Job URL


✅ 4. Airtable Auto-Insertion
All filtered jobs are inserted into Airtable with fields:


Job Title


Job description


Skills


Budget


Client Location &amp; Timezone


URL


Status ("found" by default)


✅ 5. Fully Automated
A Schedule Trigger runs the scraper every 3 days (modifiable).
Manual trigger also available during testing.

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
ComponentPurposen8n AutomationOrchestrates entire workflowRapidAPI – Upwork Jobs APISource for Upwork job dataGroq LLaMA-3.3-70BAI filtering modeln8n Code NodeConverts raw response to structured JSONAirtableStores filtered job listings

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
  "reason": "This is directly aligned with automation using Python &amp; Selenium.",
  "icebreaker": "Confident I’m the Python automation expert you’re looking for. I've built workflow automation systems and Selenium pipelines for real-world clients."
}


🛠 Setup Instructions


          
            
          
        
  
        
    

1. Clone this repo
git clone https://github.com/&lt;your-username&gt;/&lt;your-repo&gt;.git
cd your-repo

2. Import the workflow into n8n
Upload your JSON file: Upwork_Job_Scraper.json
3. Create Required API Keys
ServiceRequired KeyRapidAPIUpwork Jobs API keyGroqGroq API keyAirtablePersonal Access Token
Configure them in n8n Credentials.


4. Configure Search Term
In the HTTP Request node:
search = "Python developer"
limit = 200

Change to whatever job category you want.
5. Enable Schedule
The workflow runs every 3 days by default.
Modify in Schedule Trigger node.

📊 Airtable Output Example
TitleSkillsBudgetLocationURLStatusPython Automation ScriptPython, Selenium$20–$40/hrNew York, USlinkfound

🧪 Testing
Click “Test Workflow” or invoke via Manual Trigger.

📈 Future Improvements


🔍 Auto-apply to relevant jobs using Upwork API


📧 Email notifications for relevant filtered jobs


📊 Dashboard for job analytics


🤖 Multi-platform scraping (Fiverr, Freelancer, etc.)



🤝 Contributing
Feel free to open issues or submit PRs.

📄 License
MIT License.
