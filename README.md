
# News Scraping Program

This Python program scrapes news articles from websites using the requests library and BeautifulSoup for web scraping. The data is then saved into a CSV file.

# Features
Web Scraping: Extracts news articles from specified websites.
Data Parsing: Uses BeautifulSoup to parse HTML and extract relevant information.
CSV Export: Saves the scraped data into a CSV file for further analysis.

#Requirements
Python 3.10
requests library
beautifulsoup4 library

#Installation
Clone the Repository:

bash
git clone https://github.com/aripardhana0/scraping-news.git
cd news-scraping-program
Create a Virtual Environment (optional but recommended):

bash

python -m venv venv
Activate the Virtual Environment:

Windows:
bash

venv\Scripts\activate
macOS and Linux:
bash

source venv/bin/activate
Install Dependencies:

bash

pip install requests beautifulsoup4

# Usage
Set User-Agent:
The program uses a custom user-agent to mimic a real browser request. Make sure to set the user-agent appropriately:

python

hades = {'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/537.36'}
Run the Script:
Execute the script to start scraping:

bash

python scrape-news.py
Output:
The scraped data will be saved into a CSV file named news_data.csv.

Example Code
python

import requests as req
from bs4 import BeautifulSoup as bs
from datetime import datetime
import csv

hades = {'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/537.36'}

# Function to scrape news
    def scrape_news():
        url = 'https://example.com/news'
        response = req.get(url, headers=hades)
        soup = bs(response.text, 'html.parser')
        
        articles = soup.find_all('div', class_='article')
        news_data = []
    
        for article in articles:
            title = article.find('h2').text
            date = article.find('time').get('datetime')
            summary = article.find('p').text
            
            news_data.append([title, date, summary])
    
        with open('news_data.csv', 'w', newline='', encoding='utf-8') as file:
            writer = csv.writer(file)
            writer.writerow(['Title', 'Date', 'Summary'])
            writer.writerows(news_data)
    if __name__ == '__main__':
    scrape_news()

# Contributing
Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

# License
This project is licensed under the MIT License. See the LICENSE file for details.
