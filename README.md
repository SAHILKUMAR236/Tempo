# Tempo
Project Setup
First, I cloned or downloaded the project code from GitHub.

Installed the required dependencies using:

bash
Copy
Edit
pip install -r requirements.txt
Created a .env file to store API keys securely. This file includes:

ini
Copy
Edit
REDDIT_CLIENT_ID=your_client_id
REDDIT_CLIENT_SECRET=your_client_secret
GEMINI_API_KEY=your_gemini_api_key
🧠 2. Understanding the Components
reddit_scraper.py: Scrapes Reddit user data (comments and posts) using PRAW and stores it in a local SQLite database.

persona_builder.py: Reads the stored data, sends it to Google Gemini (LLM) in chunks, and generates a complete user persona in Markdown format.

🚀 3. Running the Scraper
To scrape a Reddit user’s activity:

bash
Copy
Edit
python reddit_scraper.py <reddit_username>
For example:

bash
Copy
Edit
python reddit_scraper.py gallowboob
This will create a file named reddit_cache.db that stores the user's Reddit posts and comments.

🧾 4. Generating the Persona
After scraping is complete, I generated a persona file using:

bash
Copy
Edit
python persona_builder.py <reddit_username> --db reddit_cache.db
For example:

bash
Copy
Edit
python persona_builder.py gallowboob --db reddit_cache.db
This created a persona summary file inside the /output folder.
persona_builder.py
This project is designed to generate a detailed personality profile (persona) of a Reddit user based on their public posts and comments. The script connects to a local SQLite database (reddit_cache.db) which contains the user's Reddit activity. It extracts and cleans this text data, then splits it into smaller chunks to make it manageable for processing. Each chunk is analyzed using Google’s Gemini AI model, which summarizes the content to identify the user's behaviors, interests, and opinions. These AI-generated summaries are then combined and sent back to Gemini to generate a complete persona. The final persona includes key sections such as demographics, professional background, interests and motivations, communication style, personal needs, and even a representative quote—all backed by citations to the user's actual content. The output is saved in Markdown format in an output folder. This tool showcases how AI can be used to understand online behavior and build marketing-style personas from real social media data.
reddit_scraper.py
This Python script is designed to scrape public activity (posts and comments) from any Reddit user profile. You can either enter a Reddit username directly or provide a full profile URL, and the script will collect up to a specified number of submissions and comments using the Reddit API (via the praw library). The data is then stored in a SQLite database for further use, with an optional flag to create separate database files per user. Each entry is stored with useful details like the type (comment or post), subreddit name, author, creation date, content, and score. This scraper is useful for collecting and organizing Reddit data for further analysis, such as building user personas, behavioral studies, or content summaries.
This assignment focuses on creating a complete pipeline to generate a detailed user persona based on a Reddit user's activity. It is divided into two main parts: a Reddit scraper and a persona builder. The scraper extracts public posts and comments of any Reddit user using the Reddit API, and stores the data in a structured SQLite database. The second part uses this data and processes it with Google's Gemini AI model, which analyzes the user's writing patterns, interests, communication style, motivations, and other behavioral insights. The final output is a well-formatted persona report in Markdown, which includes demographics, professional background, pain points, and even a representative quote. This project is helpful in fields like marketing, user research, and product development where understanding audience behavior is important.
