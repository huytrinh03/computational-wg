# Computational Work Group procedures

This repository contains the data files related to the procedures for different processes executed by the Computational Work Group. This file serves as a guide to execute these procedures, which include
- Collecting data: this process includes web scraping and data cleaning
- Creating application materials: creating CVs, Cover Letters, and other fake applicants' information

## System requirements
1. Google Chrome
2. Web Scraper Chrome extension
## Knowledge requirements
1. Web Scraper Chrome extension: [documentation](https://github.com/user-attachments/assets/1ec9ea83-08af-4704-91d2-ca490cd5a260)
2. Python
3. HTML / CSS / JavaScript

## 1. Collecting data
This process is different across differen job boards in India, as each site has a different webpage logic and thus requires a different approach to scrape and clean data from it. However, there are 2 common steps for every site:
- Scrape using the Web Scraper Chrome extension
- Parse and clean the data using Python
### 1.1. Naukri
#### 1.1.1. Scraping from Naukri
1. To open the Web Scraper Chrome extension, click on the *3 vertical dots* symbol in the top right corner of your Google Chrome screen, then choose the **Web Scraper** tab.
2. To get the Sitemap for Naukri, copy the content inside the /scraping-data/naukri/sitemap.json file.
3. To import the sitemap, click **Import Sitemap**, then paste the sitemap from Step 2. Enter a *Sitemap name*.
4. Click **Import Sitemap**. After that, you should be back to the Web Scraper's main menu with a new sitemap created.
5. Click on the sitemap that you just created.
6. To start scraping, click on the **Sitemap [*sitemap name*]** drop-down button and choose **Scrape**.
7. Configure the scraping settings, then click **Start scraping**. You will see that a new Chrome window is opened, and numerous site navigation manoeuvers are completed, all automatically done.
8. Optionally, to view the data extracted during the scraping, click on the **Sitemap [*sitemap name*]** drop-down button, choose **Browse**, and then click **Refresh data**.
9. Once the scraping is finished, to download the data, click on the **Sitemap [*sitemap name*]** drop-down button, choose **Export data**.
### 1.2. Foundit
### 1.3. Shine

Related documentation:
Web Scraper Chrome extension
![image](https://github.com/user-attachments/assets/1ec9ea83-08af-4704-91d2-ca490cd5a260)

