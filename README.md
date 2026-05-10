
# n8n Automation Workflows: WordPress Social Poster & LinkedIn Job Hunt

This repository contains two automation workflows built in n8n:
1. **WordPress Social Poster** – Automatically generates platform-specific social media captions and posts them whenever a WordPress blog is published.
2. **LinkedIn Job Hunt** – Automates LinkedIn job discovery, scoring, and resume generation for job seekers.

All workflows are designed to save time, improve consistency, and increase reach or application efficiency.

---

## Workflow 1: WordPress Social Poster

### Overview
Automatically create and post unique captions for Facebook, Instagram, Twitter/X, and LinkedIn whenever a WordPress blog post goes live. This ensures content reaches all platforms effectively without manual effort.

### Who Is This For?
- Bloggers, agencies, and businesses publishing content regularly.  
- Digital marketing and SEO teams looking to maximize post engagement.  
- Anyone wanting to automate social media promotion with platform-optimized captions.

### How It Works
1. **Trigger:** Webhook fires when a WordPress post is published.  
2. **Filter:** Ensures only published blog posts (not drafts, pages, or products) are processed.  
3. **HTML → Markdown:** Converts post content for clean AI processing.  
4. **AI Caption Generation:** OpenRouter (GPT-4o or other supported models) generates four platform-specific captions.  
5. **Publish:** Captions are simultaneously posted to Twitter/X, Facebook, Instagram, and LinkedIn using the respective APIs.

### Setup Requirements
- WordPress with WP Webhooks (or equivalent) plugin.  
- n8n instance with a public webhook URL.  
- API credentials for OpenRouter, Twitter/X, Facebook, Instagram, LinkedIn.

### Customization Options
- Adjust AI model or caption style.  
- Add additional platforms (e.g., TikTok, Pinterest).  
- Filter posts by category or tag.  
- Enable delayed or scheduled posting.

---

## Workflow 2: LinkedIn Job Hunt

### Overview
Automates job search by scraping LinkedIn listings, evaluating relevance, generating tailored resumes and cover letters, and logging applications.

### Who Is This For?
- Job seekers aiming to streamline LinkedIn applications.  
- Professionals who want to receive only relevant job opportunities and automatically create application documents.

### How It Works
**Stage 1 – Scrape & Filter:**  
- Schedule Trigger fires at defined intervals.  
- Apify scraper collects job listings based on keywords and location.  
- Filter nodes remove irrelevant recruiters or locations.  
- HTML content is converted to Markdown.  
- Quick AI GateKeeper filters out unsuitable listings.  
- Results saved in the **Gatekeeper Results** Google Sheet.

**Stage 2 – Score & Notify:**  
- Detailed AI scoring evaluates job fit.  
- Matching roles above threshold added to **Roles to Apply** Google Sheet.  
- Telegram notifications alert you to new opportunities.

**Stage 3 – Generate Resume & Apply:**  
- Triggered by updating a row in the “Roles to Apply” sheet.  
- AI Resume Writer fills Google Docs templates with personalized resumes and cover letters.  
- Documents saved to Google Drive, application status updated in Google Sheets.

### Setup Requirements
- n8n instance, Apify account, OpenRouter/OpenAI API keys.  
- Google Workspace (Sheets, Docs, Drive) with OAuth2 credentials.  
- Telegram bot token.

### Customization Options
- Modify LinkedIn search URLs and filters.  
- Adjust AI scoring and GateKeeper thresholds.  
- Add more languages or resume templates.  
- Configure Telegram chat for notifications.

---

## Nodes Used (Both Workflows)

- **Webhook / Schedule Trigger**  
- **Filter / IF / Switch / Merge**  
- **Markdown Conversion**  
- **Set / Clean Data**  
- **AI Agent (OpenRouter, OpenAI)**  
- **HTTP Request / API Calls**  
- **Google Sheets / Docs / Drive**  
- **Telegram Notification**  
- **Twitter/X, Facebook, Instagram, LinkedIn nodes**

---

## Support
For questions or template files, please contact the workflow maintainer. Both workflows are ready for customization and use in your own accounts.
