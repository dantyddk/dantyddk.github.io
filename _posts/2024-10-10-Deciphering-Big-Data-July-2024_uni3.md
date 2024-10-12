---
layout: post
title: UoE - Deciphering Big Data July 2024 - Web Scraping
subtitle: Identify and manage challenges, security issues and risks, limitations, and opportunities in data wrangling. Critically analyse data wrangling problems and determine appropriate methodologies, tools, and techniques (involving preparing, cleaning, exploring, creating, optimising and evaluating big data) to solve them. Systematically develop and implement the skills required to be effective member of a development team in a virtual professional environment, adopting real life perspectives on team roles and organisation.
categories: EL-Activities, Wiki
tags: [UoE, assignment, essay, Module E-Portfolio Learning Activities]
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
