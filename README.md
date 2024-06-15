**Python Script for Web Scraping Largest African Companies by Revenue**
This Python script scrapes data from the Wikipedia page listing the Largest Companies in Africa by Revenue https://en.wikipedia.org/wiki/List_of_largest_companies_in_Africa_by_revenue. It extracts the table containing company information and creates a CSV file named "Companies.csv" in your Documents folder (you can modify the path).

**Here's what the script does:**

1.**Imports necessary libraries:**

* requests: Used to fetch website content.
* BeautifulSoup: Parses HTML content for easy data extraction.
* pandas: Enables creating and manipulating DataFrames (fancy tables in Python).

2.**Defines the target URL:**

* Stores the Wikipedia page URL in a variable named url.

3.**Fetches and parses the webpage:**

*  requests to grab the webpage content and stores it in page.
* Employs BeautifulSoup to parse the HTML content (page.text) into a more navigable format (soup).

4.**Targets the relevant table:**

* We're interested in the table containing company data. The script tries different approaches to find it:
.Looks for the first table (soup.find('table')). This might not always be the correct one.
.Retrieves the second table (soup.find_all('table')[1]), assuming indexing starts from 0.
.Attempts to find the table with specific class attributes ('wikitable' and 'sortable').

5.**Extracts table headers:**

* Once the desired table is found, it grabs all header elements (<th>) and stores them in a list named world_titles.
*Loops through these headers, cleans any leading/trailing spaces from their text content using .strip(), and creates a new list (world_table_titles) containing these cleaned titles.

6.**Creates a pandas DataFrame:**

* Initializes a DataFrame named df using pandas. This DataFrame will hold the scraped data in a structured format (like a spreadsheet).
* Sets the column names of df to the cleaned table header titles extracted earlier (world_table_titles).

7.**Extracts table data:**

* Finds all table row elements (<tr>) within the target table and stores them in column_data.
* Iterates through each row (skipping the first one, which is likely the header) and extracts the text content from each table data cell (<td>).
* Cleans the extracted data (removing extra spaces) and stores it in a list named individual_row_data.
* Appends this data as a new row to the DataFrame df.

8.**Saves the data:**

* Saves the DataFrame df as a CSV file named "Companies.csv" in the specified location (C:\Users\personal\Documents\Web_Scraping\Companies.csv).
* Uses index=False to prevent the row index from being saved as a separate column in the CSV.
**Disclaimer**
Please note that websites can change their structure and layout over time. This script relies on the current format of the Wikipedia table. If the website structure changes, you might need to adjust the code to target the relevant elements for successful scraping.
