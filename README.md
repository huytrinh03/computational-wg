# Computational Work Group procedures

This repository contains the data files related to the procedures for different processes executed by the Computational Work Group. This file serves as a guide to execute these procedures, which include
- Collecting data: this process includes web scraping and data cleaning
- Creating application materials: creating CVs, Cover Letters, and other fake applicants' information

## System requirements
1. Google Chrome
2. Web Scraper (WS) Chrome extension
## Knowledge requirements
1. WS: [documentation](https://webscraper.io/documentation)
2. Python
3. Basic HTML/CSS/JavaScript

## 1. Collecting data
This process is different across differen job boards in India, as each site has a different webpage logic and thus requires a different approach to scrape and clean data from it. However, there are 2 common steps for every site:
- Scrape using WS
- Parse and clean the data using Python

### 1.1 General web scraping procedure:
1. [Open the WS Chrome extension](https://webscraper.io/documentation).
2. To get the Sitemap for the chosen job board A, copy the content inside the collecting-data/A/sitemap.json file.
3. To import the sitemap, click **Import Sitemap**, then paste the sitemap from Step 2. Enter a *Sitemap name*.
4. Click **Import Sitemap**. After that, you should be back to the WS's main menu with a new sitemap created.
5. Click on the sitemap that you just created.
6. To start scraping, click on the **Sitemap *sitemap name*** drop-down button and choose **Scrape**.
7. Configure the scraping settings, then click **Start scraping**. You will see that a new Chrome window is opened, and numerous site navigation manoeuvers are completed, all automatically done.
8. Optionally, to view the data extracted during the scraping, click on the **Sitemap [*sitemap name*]** drop-down button, choose **Browse**, and then click **Refresh data**.
9. Once the scraping is finished, to download the data, click on the **Sitemap [*sitemap name*]** drop-down button, choose **Export data**.

### 1.2. General data cleaning procedure
Configure and then run all cells in the collecting-data/A/A_parser.ipynb file (where A stands for the site you want to scrape from)

### 1.3. Website-specific scraping details
#### 1.3.1. Naukri
Between step 5 and 6 of section 1.1, one can configure the sitemap to fine-tune the scraping to their needs.
To only scrape jobs with specific filters (location, industry, etc.), you need to change the starting page from which the scraping is done by following the below steps:
1. Navigate to [Naukri's job search default landing page](https://www.naukri.com/jobs-in-india).
2. Add filters to your job search. After this is done, you will land in a new landing page with the applied filters.
3. Copy the URL of this landing page.
4. Navigate in WS **Sitemap *sitemap-name*** -> **Edit metadata**, and paste the URL in **Start URL 1**.

To change the number of websites being scraped, (for example, to 1000), you can add range to the start URL. Naukri uses numbering in page URL to specify the web pages that show the job postings. Each web page contains 20 postings. Thus, if we need to scrape 1000 postings, we will need to go through 50 web pages. Follow the below steps:
1. Navigate in WS **Sitemap *sitemap-name*** -> **Edit metadata**.
2. in the **Start URL 1** option, add the range "-[1-50]" after "jobs-in-india" in the Start URL.
3. Click **Save Sitemap**.
   
#### 1.3.2. Foundit
Foundit is a special case. Unlike other sites where we can retrieve the job posting's URL from the job search landing page, this is not possible on Foundit. The reason is that Foundit's job posting's URL is not embedded on the job search landing page but rather dynamically created when a job searcher click on the job posting in the landing page.<br>
Fortunately, we can still build the URL for Foundit's job posting by reverse engineering its creation. These URLs have the following formula:<br>
:*https://foundit.in/job/[Job Title]-[Company]-[Location]-[Job ID]*,:<br>
where each field in square brackets is hyphen separated (instead of space separated). Each field in the above formula can be scraped from the job search landing page.
<br>
The scraping procedure for Foundit is as follows:
1. Scrape the fields necessary for URL creation using WS.
2. Build the URLs using Python.
3. Access each of the built URL and scrape information using Python's Request and BeautifulSoup package.

Between step 5 and 6 of section 1.1, one can configure the sitemap to fine-tune the scraping to their needs.
To only scrape jobs with specific filters (location, industry, etc.), you need to change the starting page from which the scraping is done by following the below steps:
1. Navigate to [Foundit's job search default landing page](https://www.foundit.in/srp/results?sort=1&limit=100&query=%22%22).
2. Add filters to your job search. After this is done, you will land in a new landing page with the applied filters.
3. Copy the URL of this landing page, but exclude the "&searchId=..." section in the URL.
4. Navigate in WS **Sitemap *sitemap-name*** -> **Edit metadata**, and paste the URL in **Start URL 1**.

To change the number of websites being scraped, (for example, to 1000), you can change the *limit* parameter in the URL to "limit=1000".

#### 1.3.3. Shine
Between step 5 and 6 of section 1.1, one can configure the sitemap to fine-tune the scraping to their needs.
To only scrape jobs with specific filters (location, industry, etc.), you need to change the starting page from which the scraping is done by following the below steps:
1. Navigate to [Shine's job search configuration page](https://www.shine.com/new/job-search).
2. Add filters to your job search. After this is done, you will land in a new landing page with the applied filters.
3. Optionally, you can apply further filters in this landing page.
4. Copy the URL of this landing page.
5. Navigate in WS **Sitemap *sitemap-name*** -> **Edit metadata**, and paste the URL in **Start URL 1**.

To change the number of websites being scraped, (for example, to 1000), you can add range to the start URL. Naukri uses numbering in page URL to specify the web pages that show the job postings. Each web page contains 20 postings. Thus, if we need to scrape 1000 postings, we will need to go through 50 web pages. Follow the below steps:
1. Navigate in WS **Sitemap *sitemap-name*** -> **Edit metadata**.
2. in the **Start URL 1** option, add the range "-[1-50]" to the end of the start URL.
3. Click **Save Sitemap**.
