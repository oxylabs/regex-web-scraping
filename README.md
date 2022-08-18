# regex-web-scraping
Web Scraping with RegEx 

```bash
python3 -m venv scrapingdemo
```

```bash
source ./scrapingdemo/bin/activate
```

```bash
pip install requests
```

```bash
pip install beautifulsoup4
```

```python
import requests
from bs4 import BeautifulSoup 
import re
```

```python
page = requests.get('https://books.toscrape.com/')
```

```python
soup = BeautifulSoup(page.content, 'html.parser')
content = soup.find_all(class_='product_pod')
content = str(content)

```

```python
re_titles = r'title="(.*?)">'
```

```python
re_prices = '£(.*?)</p>'
```

```python
titles_list = re.findall(re_titles, content)
price_list = re.findall(re_prices, content)

```

```python
with open("output.txt", "w") as f:
   for title, price in zip(titles_list, price_list):
       f.write(title + "\t" + price + "\n")
```

```python
# Importing the required libraries.
import requests
from bs4 import BeautifulSoup
import re

# Requesting the HTML from the web page.
page = requests.get("https://books.toscrape.com/")

# Selecting the data.
soup = BeautifulSoup(page.content, "html.parser")
content = soup.find_all(class_="product_pod")
content = str(content)

# Processing the data using Regular Expressions.
re_titles = r'title="(.*?)">'
titles_list = re.findall(re_titles, content)
re_prices = "£(.*?)</p>"
price_list = re.findall(re_prices, content)

#  Saving the output.
with open("output.txt", "w") as f:
   for title, price in zip(titles_list, price_list):
       f.write(title + "\t" + price + "\n")

```
