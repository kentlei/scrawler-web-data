# scrawler-web-data

import requests
import pandas as pd

url = "http://www.etnet.com.hk/www/tc/stocks/realtime/quote_shortsell.php?code=2778"
response = requests.get(url) #用get 取得網頁資料

import io
f = io.StringIO(response.text) #將資料存成檔案f
dfs = pd.read_html(f) #我們將此文件利用pd.read_html(f)來分析網頁f中的表格，將所有的表格存成 a list of dataframe
world_index = dfs[0] #我們將第一張dataframe給拿出來
