# Collecting Data - Assignment 2: Web Scraping 

## Overview
This project scrapes text from The Prophecies of Nostradamus hosted on the Internet Sacred Text Archive ([sacred-texts.com](https://www.sacred-texts.com/)).
The purpose is to build a structured corpus by automatically retrieving page content, extracting text, cleaning it, and saving it in a machine-readable format.

All scraping and cleaning procedures are documented in the Jupyter Notebook Assignment-3.ipynb, which concludes by exporting the corpus as a CSV file.
The corpus is suitable for Digital Humanities students and researchers interested in text analysis, or corpus linguistics work.

## Description of the Corpus
The corpus contains the following elements for each prophecy entry:

| Column     | Description                                                                               |
| ---------- | ----------------------------------------------------------------------------------------- |
| **ID**     | Unique identifier assigned to each prophecy (e.g., `nos_01`)                              |
| **TITLE**  | Work title (“The Prophecies of Nostradamus”)                                              |
| **AUTHOR** | The author of the text (Nostradamus)                                                      |
| **YEAR**   | Year of publication (1555/1558)                                                           |
| **URL**    | Direct link to the webpage scraped                                                        |
| **Text**   | Cleaned prophecy text extracted from HTML                                                 |
| **Chapter**  | Section or prophecy title extracted from the webpage (e.g., *Century I*, *Preface*, etc.) |

The data represents a structured collection of Nostradamus’ writings as reproduced on a publicly accessible archive website.

## Data Scraped
The scraping process retrieved:

- The HTML content of each prophecy page
- The prophecy text extracted from the main body of the webpage
- The chapter (e.g., Century I, Century II)
- Metadata from the initial metadata table 

## Cleaning Steps
1. Load metadata
  - Read the CSV file containing IDs, titles, authors, years, and URLs.
2. Loop through each URL and send a request
  - Retrieved the HTML content for each webpage.
  - Stored the full HTML temporarily for text extraction.
3. Parse HTML using BeautifulSoup
  - Converted the raw HTML into a navigable DOM structure.
4. Locate and extract the main text
  - Identified the primary text container within each page.
  - Extracted text using .get_text() to remove HTML tags automatically.
5. Strip and clean whitespace
  - Removed leading/trailing whitespace.

## Corpus File Format
The final file produced is: ``nostradamus_corpus.csv``
Format: CSV, UTF-8 encoded
Columns: ``ID``, ``TITLE``, ``AUTHOR``, ``YEAR``, ``URL``, ``Text``, ``Chapter``

## Terms and Conditions for Web Scraping and ``robots.txt``
The scraped texts come from the Internet Sacred Text Archive, a repository of public-domain works. Nostradamus' Prophecies are public domain, and the website republishes works that are legally free to use. 
Moreover, the ``robots.txt`` explicity allows user-agent to access the site.

  User-Agent: *
  
  Allow: /
  
  Content-signal: search=yes, ai-train=no
  
This means that all user agents (including Python, requests, etc) are allowed to fetch the data. I am only accessing those directories that permit it and I am not using it for AI training.
