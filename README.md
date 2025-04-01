# Computational Work Group procedures

This repository contains the data files related to the procedures for different processes executed by the Computational Work Group. This file serves as a guide to execute these procedures, which include
- Collecting data: this process includes web scraping and data cleaning
- Creating application materials: creating CVs, Cover Letters, and other fake applicants' information

## System requirements
1. Google Chrome
2. Web Scraper Chrome extension
## Knowledge requirements
1. Web Scraper Chrome extension: [documentation](https://webscraper.io/documentation)
2. Python
3. HTML / CSS / JavaScript

## 1. Collecting data
This process is different across differen job boards in India, as each site has a different webpage logic and thus requires a different approach to scrape and clean data from it. However, there are 2 common steps for every site:
- Scrape using the Web Scraper Chrome extension
- Parse and clean the data using Python

### 1.1 General web scraping procedure:
1. [Open the Web Scraper Chrome extension](https://webscraper.io/documentation).
2. To get the Sitemap for the chosen job board A, copy the content inside the collecting-data/A/sitemap.json file.
3. To import the sitemap, click **Import Sitemap**, then paste the sitemap from Step 2. Enter a *Sitemap name*.
4. Click **Import Sitemap**. After that, you should be back to the Web Scraper's main menu with a new sitemap created.
5. Click on the sitemap that you just created.
6. To start scraping, click on the **Sitemap *sitemap name*** drop-down button and choose **Scrape**.
7. Configure the scraping settings, then click **Start scraping**. You will see that a new Chrome window is opened, and numerous site navigation manoeuvers are completed, all automatically done.
8. Optionally, to view the data extracted during the scraping, click on the **Sitemap [*sitemap name*]** drop-down button, choose **Browse**, and then click **Refresh data**.
9. Once the scraping is finished, to download the data, click on the **Sitemap [*sitemap name*]** drop-down button, choose **Export data**.

### 1.2. General data cleaning procedure
Configure and then run all cells in the collecting-data/A/A_parser.ipynb file (where A stands for the site you want to scrape from)
### 1.3. Website specific details
Between step 5 and 6 of section 1.1, one can configure the sitemap to fine-tune the scraping to their needs.
To only scrape jobs with specific filters (location, industry, etc.), you need to change the starting page from which the scraping is done by following the below steps:
1. Navigate to [Naukri's job search default landing page](https://www.naukri.com/jobs-in-india).
2. Add filters to your job search. After this is done, you will land in a new landing page with the applied filters
3. Copy the URL of this landing page
4. Navigate in Web Scraper **Sitemap *sitemap-name*** -> **Edit metadata**, and paste the URL in **Start URL 1**.

To change the number of websites being scraped, (for example, to 1000), you can add range to the start URL. Naukri uses numbering in page URL to specify the web pages that show the job postings. Each web page contains 20 postings. Thus, if we need to scrape 1000 postings, we will need to go through 50 web pages. Follow the below steps:
1. Navigate in Web Scraper **Sitemap *sitemap-name*** -> **Edit metadata**.
2. in the **Start URL 1** option, add the range "-[1-50]" after "jobs-in-india" in the Start URL.
3. Click **Save Sitemap**.
   
#### 1.3.1. Naukri
### 1.3.2. Foundit
### 1.3.3. Shine

Related documentation:
Web Scraper Chrome extension
![image](https://github.com/user-attachments/assets/1ec9ea83-08af-4704-91d2-ca490cd5a260)

