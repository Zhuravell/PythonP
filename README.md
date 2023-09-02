# PythonP
#some python code and projects
#webscrapping project

from bs4 import BeautifulSoup
import requests
import pandas as pd

url="https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue"
url_get=requests.get(url).text
soup=BeautifulSoup(url_get, "html.parser")
#print(soup.prettify())

table_2=soup.find_all('table', class_='wikitable sortable')[1]
table_2_headers=table_2.find_all('th')
table_2_headers=[title.text.strip() for title in headers_table_2]
#print(table_2_headers)
df=pd.DataFrame(columns=[table_2_headers])
df

df.to_csv("/Users/interslavia/Desktop/webscrapping_python_project.csv")
