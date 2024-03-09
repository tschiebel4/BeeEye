**Project Name:** X HAR Scraper

**Installation Instructions:** You will need Python and PowerBI to run your own use-cases here

**1. Problem Statement**
I've recently moved into a townhouse close to train tracks, not realizing the frequency of passing trains, which often disrupt my nights. To understand their patterns, as freight train schedules aren't publicly available, I turned to a social media page, 'NoCo Train Alerts,' that monitors train activity in northern Colorado: https://twitter.com/NoCoTrainAlert. Lacking access to an API key, I manually gathered data from this page by exporting a HAR file, converting it into a CSV format with a Python script developed through ChatGPT prompts, and analyzing it in Power BI, I aimed to gain insights into the train schedules that impact my daily life.

**2. HAR File Export from X**
Right click anywhere on page -> inspect -> now its recording -> go to network tab -> export har file
https://www.youtube.com/watch?v=LcqVDfueb8g&t=229s
"A HAR (HTTP Archive) file is a JSON-formatted log of a web browser's interactions with a site. It records the web browser's requests and responses in detail, including URLs, headers, and timing information. This makes HAR files incredibly useful for understanding the behavior of web pages and for manual web scraping when API access is not available or feasible. 
--In this project, I used a HAR file to capture data from the 'NoCo Train Alerts' social media page. 
--This process involved navigating the page while the browser recorded all the data exchanges. 
--The resulting HAR file provided a comprehensive snapshot of the page's data, which I then processed to extract relevant information about train schedules."

**3. Python Script**
--Import Libraries: The script begins by importing necessary libraries: json for working with JSON data, and pandas (as pd) for data manipulation.
--Defining extract_tweets_from_har Function: This function loads the HAR file, iterates through its entries, and extracts tweet data, handling potential JSON structure variations and decoding errors.
--Defining json_extract Helper Function: A recursive function that fetches values from nested JSON based on a specified key.
--Defining tweets_to_dataframe Function: Converts the extracted tweets into a Pandas DataFrame and adds a binary flag to indicate the presence of the word "Train" in the tweet.
--Executing the Script: The script extracts tweets from the HAR file, converts them to a DataFrame, and exports the data to a CSV file for further analysis.

**4. ChatGPT Prompts**
Make sure to mention that I provided a targeted sample from the HAR file

**5. Power BI Data Transformations and Visualizations**
--Date = TRIM(RIGHT(LEFT(har_text[tweet_body], SEARCH(" @ ", har_text[tweet_body])), LEN(LEFT(har_text[tweet_body], SEARCH(" @ ", har_text[tweet_body]))) - SEARCH(", ", LEFT(har_text[tweet_body], SEARCH(" @ ", har_text[tweet_body])))))
--Month = Month(har_text[Date])
--Day of Week = LEFT(har_text[tweet_body], 3)
--Hour = HOUR(har_text[Time])
--Mulberry Flag = IF(CONTAINSSTRING(har_text[tweet_body], "Mulberry") = TRUE(), 1, 0)
--Direction = IF(CONTAINSSTRING(har_text[tweet_body], "Northbound") = TRUE(), "Northbound", IF(CONTAINSSTRING(har_text[tweet_body], "Southbound") = TRUE(), "Southbound", "Other"))
(Might be good to explain how ChatGPT can help here as well)

**6. Analysis and Insights**
--371 Tweets
--More Northbound than Southbound
--In general, they don't come through as often during the weekend
--they tend to come Between 10am and 12am
--Higher volume in July
--More-so Monday and Wednesday in July
--Skewed later in July
--6pm would be a good time to meditate...wed, thurs, sat

**Credits:**
https://youtu.be/LcqVDfueb8g?si=tneejn5lug0rHr77&t=119
