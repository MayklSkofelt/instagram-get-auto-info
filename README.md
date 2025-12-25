# Instagram Info & Activity Scraper (Apify + Python)

🚀 **Automated platform that continuously collects Instagram profiles, new posts, and comments using Apify and Python**

This project is a Python-based automation platform powered by **Apify Actors** that continuously monitors Instagram accounts and automatically collects:

- Profile information  
- Newly published posts  
- Post comments (including new comments over time)

The system is designed to run repeatedly, ensuring that **new posts and comments are fetched automatically** without duplication.

## ✨ Features

- 🔍 Monitor public Instagram profiles
- 🆕 Automatically fetch **new posts**
- 💬 Automatically fetch **new comments** from posts
- 🔄 Continuous data updates (no duplicate data)
- 📊 Extract data such as:
  - Username
  - Bio
  - Followers / Following count
  - Posts count
  - Post captions
  - Likes & comments count
  - Comment text & author
- ⚡ Powered by **Apify Actors**
- 🐍 Written in **Python**
- 🤖 Fully automated & scalable
- 📁 Structured JSON output

## ▶️ How It Works

1. The platform receives a list of Instagram usernames
2. Apify Actors scrape profile data
3. New posts are detected automatically
4. Comments for each new post are collected
5. Previously collected data is skipped
6. Results are saved in structured JSON format

.
├── pycache/ # Python cache files
├── downloads/ # Downloaded media (images/videos)
│
├── api_token.json # Apify API token configuration
├── auto_skachat_req_we_comment.py # Auto-download requests & comments logic
├── instagram_monitor.py # Main monitoring & orchestration script
│
├── users.json # Tracked Instagram users
├── posts.json # All collected posts
├── downloaded_posts.json # Already processed/downloaded posts
├── new_items.json # Newly detected posts & comments


---

## 📄 File Descriptions

### `instagram_monitor.py`
Main controller script.  
Responsible for:
- Reading users from `users.json`
- Running Apify Instagram Actors
- Detecting **new posts**
- Triggering comment collection
- Updating JSON storage files

---

### `auto_skachat_req_we_comment.py`
Automation logic for:
- Fetching comments for posts
- Downloading post media (if enabled)
- Sending requests to Apify Actors
- Handling pagination and limits

---

### `api_token.json`
Stores the Apify API token.

Example:
```json
  {
  "APIFY_TOKEN": "your_apify_token_here"
  }


⚠️ Do not share this file publicly

users.json

List of Instagram usernames to monitor.

Example:

[
  "instagram",
  "natgeo",
  "openai"
]

posts.json

Contains all collected Instagram posts.

Stored data includes:

Post ID

Caption

Likes count

Comments count

Timestamp

downloaded_posts.json

Tracks posts that have already been processed or downloaded.
Used to prevent duplicates.

new_items.json

Stores newly detected content, such as:

New posts

New comments

This file is updated on each monitoring cycle.

downloads/

Optional directory for storing downloaded:

Images

Videos

Other media content

Usage

Run the monitoring script:

python instagram_monitor.py
