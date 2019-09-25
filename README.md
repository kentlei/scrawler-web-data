# scrawler-web-data

import requests
import pandas as pd

url = "http://www.etnet.com.hk/www/tc/stocks/realtime/quote_shortsell.php?code=2778"
response = requests.get(url) #用get 取得網頁資料

import io
f = io.StringIO(response.text) #將資料存成檔案f
dfs = pd.read_html(f) #我們將此文件利用pd.read_html(f)來分析網頁f中的表格，將所有的表格存成 a list of dataframe
world_index = dfs[0] #我們將第一張dataframe給拿出來



#用Selector 找網頁的資料

# Import a scrapy Selector
from scrapy import Selector

# Import requests
import requests

url = 'https://www.datacamp.com/courses/tech:python'

# Create the string html containing the HTML source
html = requests.get(url).content

# Create the Selector object sel from html
sel = Selector( text = html )

# Print out the number of elements in the HTML document
print( "There are 1020 elements in the HTML document.")
print( "You have found: ", len( sel.xpath('//*') ) )
