---
layout: post
title: UoE - Deciphering Big Data July 2024 - Web Scraping
subtitle: Identify and manage challenges, security issues and risks, limitations, and opportunities in data wrangling. Critically analyse data wrangling problems and determine appropriate methodologies, tools, and techniques (involving preparing, cleaning, exploring, creating, optimising and evaluating big data) to solve them. Systematically develop and implement the skills required to be effective member of a development team in a virtual professional environment, adopting real life perspectives on team roles and organisation.
categories: EL-Activities Wiki
tags: [UoE, coding, Module E-Portfolio Learning Activities]
---
---
## Web Scraping | Dinh Khoi Dang
---
### Coding Part

import requests

from bs4 import BeautifulSoup

import re

import json

url = 'https://www.discoverdatascience.org/ai-and-data-science/'

response = requests.get(url)

soup = BeautifulSoup(response.content, 'html.parser')

data_science_info = []

for tag in soup.find_all(text=True):

if re.search(r'data science', tag, re.IGNORECASE):

data_science_info.append(tag.strip())

for info in data_science_info:

print(info)

with open('data_science_info.json', 'w', encoding='utf-8') as json_file:

json.dump(data_science_info, json_file, ensure_ascii=False, indent=4)

save_to_json(data_science_info)

### Result

![image](/assets/images/banners/wiki3.jpg)

---
## Individual Reflecion
---

### Reflection

This assignment provided a hands-on experience in web scraping and data parsing using Python, with a specific focus on the BeautifulSoup4 and Requests libraries. The objective was to extract information related to the keyword “Data Scientist” and convert it into a structured JSON file. This task allowed me to strengthen my understanding of data extraction, HTTP requests, and the importance of well-structured data formats like JSON.

### Challenges and Approach

At the start, one of the key challenges was managing the large and often unstructured HTML data returned from the HTTP request. The Requests module allowed me to make a GET request to the URL and retrieve the web page content efficiently. However, navigating through the HTML tags to find relevant data was more complex than expected due to the diversity of web page structures. Here, BeautifulSoup became an essential tool, as it provided a powerful and flexible way to traverse the document tree and locate specific pieces of content.

I focused on finding the keyword “Data Scientist” using regular expressions (re.search) to refine my search, which proved crucial for filtering out irrelevant content. By targeting specific tags, I could extract meaningful text while discarding unnecessary HTML elements, such as scripts and advertisements. This process highlighted the importance of data cleaning during web scraping, as the raw data collected from websites is often cluttered with extraneous information.

### Parsing and Saving Data

Once I successfully extracted relevant information, the next step was converting the data into a structured format for further use. Initially, I considered both XML and JSON, but ultimately chose JSON due to its widespread use in modern data applications and its ease of integration with other data tools.

Writing the data to a JSON file was a crucial part of the project, where I used Python's json module to convert the list of extracted content into a structured JSON object. This process taught me the value of data serialization, which ensures that scraped data is not only readable but also easily transferable between applications or systems. The task also helped me appreciate the balance between data extraction and storage efficiency, as I needed to ensure that the resulting JSON file was well-organized and easy to interpret.

### Learning Outcomes

This assignment significantly improved my skills in handling HTML and HTTP responses through Python. I learned how to filter large amounts of web content and how to identify and extract only the relevant data. Additionally, working with regular expressions and understanding how different HTML elements are structured deepened my technical knowledge of web pages, which is critical for future web scraping projects.

I also had the opportunity to explore different methods of Inter-Process Communication (IPC), particularly as it pertains to data transfer between the scraping script and the JSON output. Parsing data correctly and transferring it into a standardized format like JSON is essential when working with large datasets that need to be processed or analyzed later.

### Engagement with Peer Work

In addition to my own project, I actively engaged with my peers’ work on the Module Wiki. Their approaches to similar tasks provided new perspectives, particularly regarding error handling and optimizing performance for web scraping. Through peer feedback, I gained insights into different ways to scrape data more efficiently, including how to handle issues like page timeouts or inconsistent HTML structures across web pages.

Overall, this project reinforced the importance of collaboration and continuous learning, as I was able to refine my techniques by learning from others in the course. By reviewing my peers’ work, I also discovered alternative approaches to structuring scraped data, some using XML instead of JSON, which helped me broaden my understanding of data formats.

### Conclusion

In conclusion, this assignment was a valuable experience in applying Python libraries for web scraping, data extraction, and parsing. It taught me how to navigate the complexities of HTML documents, clean and structure data effectively, and use JSON for data storage. I also gained a deeper understanding of the entire process from making HTTP requests to saving clean data into usable formats. Engaging with my peers and reflecting on their feedback further enhanced my learning, allowing me to improve my techniques and apply new strategies in future projects.






