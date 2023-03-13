
## Scraping the CIA website by Maia Botek


### What This Code Does

The code I wrote is scraping the CIA’s country comparison webpage to gather information about 200+ countries. The information is written into a CSV file that allows users to see the real GDP per capita, GDP, total population, and population growth rate for each country. The only modification to my original proposal is the web page from which the links are scraped, which was modified from the original fact book list to the complete list of countries on the comparison page. 

### How Each Function Works

1. The first function I wrote is named get_urls_from_single_page, and it scrapes the CIA comparison page to find each country’s partial URL. It then adds the prefix of the CIA world fact book site to the partial link and adds each country’s link to a list, country_list.

2. The second function, scrape_one_country(url) scrapes the page for data from each link provided in the list, country_list. The function makes soup out of the url in the list and uses appropriate if/else statements to extract the real GDP, real GDP per capita, population and population growth rate values for each country, using next sibling. Additionally, it slices and strips the text to format values for the CSV file. There is also a condition to account for countries where all data is not present, which is the case for many small countries. Finally, it appends and returns the four values in the country_details list. 

3. The final function write_csv(url_list) writes the scraped data into the CSV file, ciainfo, with a python writer object. The function defines the sheet’s five-column headings and uses the indexes for the country_details list to write each country’s values to the corresponding row.

### Challenges and Solutions

The only unexpected issues I had pertained to the formatting of the CIA website’s content, specifically the variety between each country’s data. Some countries had all the necessary values listed whereas some of the smaller countries lacked data. Additionally, it was not enough to find specific years or text values as some countries have not had data updated since the early 2010s. To get around this, I wrote the function to slice the text after finding a specific or certain amount of characters (often the closed parentheses) and to write the text “No data provided” for countries that didn’t have it listed. I also changed the link from the world factbook list of pages to the country comparison page for populations as the starting point for my code to scrape the country URLs.

[^note]:
    Some of the code was modified and adapted from our actor/movie url scraping exercise, which has also been credited in the code itself.
