This ETL pipeline makes use of web scraping to clean and deliver it to AWS Services such as Amazon S3 and Amazon Athena. 
The pipeline fully cover the entire ETL process from extraction, transformation, and lastly loading.

Extraction: It makes use of several Python Libraries to web scrape such as requests, BeautifulSoup, and etc. The chosen website as a test for my workshop 
was "books.toscrape.com". The scrape function primarily focuses on getting the title, price, and rating of each book of each page. The maximum amount of pages to
scrape is up to the user.

Transformation: The scrape books needs to be formatted in such a way that is efficient and organized. The Python Library I used to do this is Pandas, which 
created a DataFrame for the data to be stored in. Clutter/Garbage data was also seen in the scraped data, so the clean function uses several commands in pandas such as .replace()
to format and clean the data (specifically the price in this case) to be functional when using mathematical functions for it. The rating column also had several issues with it such as
the data including the full array provided in the website that involved an unnecessary "star-rating" to it. I also utilized Python dictionaries to convert textual rating into an integer, 
making it viable for mathematical arithmetic/functions.

Loading:  Lastly, both cleaned and raw data is then loaded into an S3 bucket which acts as the storage for the data, then loaded into Athena for data analysis. 
This entire project is completely serverless as its main purpose was to use AWS services alongside it.
