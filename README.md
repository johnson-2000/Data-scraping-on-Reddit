
# Reddit Data Scraping with Python

## Overview
This project aims to demonstrate the process of scraping data from Reddit using Python, leveraging the PRAW library, a Python wrapper for the Reddit API. The primary objective is to extract posts and comments from the Reddit platform, focusing on the "spotify" subreddit. The scraped data is then organized and stored for further analysis, providing insights into user interactions and discussions within the subreddit.

## Key Features
- **PRAW Integration**: Utilizes the PRAW library to interact with the Reddit API seamlessly.
- **Data Scraping**: Extracts top posts and comments from the "spotify" subreddit, providing a comprehensive view of user engagement and discussions.
- **Data Processing**: Processes the scraped data and structures it into a format suitable for analysis, enabling easy exploration and interpretation of the collected information.
- **Data Storage**: Stores the organized data in appropriate data structures, such as Pandas DataFrames, facilitating efficient retrieval and manipulation.

## Getting Started
To run the project locally, follow these steps:

1. **Install Dependencies**: Make sure to install the required dependencies using pip.
    ```bash
    pip install praw
    ```

2. **Configure Reddit API Credentials**: Obtain your Reddit API credentials (client ID, client secret, and user agent) and configure them in the provided Python script.

3. **Execute the Script**: Run the Python script to initiate the data scraping process. Ensure that you have appropriate permissions and adhere to Reddit's API usage guidelines.

4. **Explore the Data**: Once the data scraping process is complete, explore the collected data using data analysis tools or custom scripts tailored to your specific analysis requirements.

## Example Usage
Below is a snippet demonstrating the basic usage of the Reddit data scraping script:

```python
import praw
import pandas as pd

# Initialize Reddit instance with credentials
reddit = praw.Reddit(
    client_id="YOUR_CLIENT_ID",
    client_secret="YOUR_CLIENT_SECRET",
    user_agent="YOUR_USER_AGENT",
)

# Initialize an empty DataFrame
df = pd.DataFrame()

# Scraping top posts from the "spotify" subreddit
for submission in reddit.subreddit("spotify").top(limit=20):
    print(submission, submission.num_comments)

# Scraping comments from a specific submission
submission = reddit.submission(id="zlm0rp")
for top_level_comment in submission.comments:
    print(top_level_comment.author, top_level_comment.body, top_level_comment.score)
