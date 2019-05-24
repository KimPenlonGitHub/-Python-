# -Python-
Python笔记，记录相关爬虫学习过程
#第一种解法：
import requests,bs4

for x in range(10):
    url = 'https://movie.douban.com/top250?start=' + str(x*25) + '&filter='
    res = requests.get(url)
    bs = bs4.BeautifulSoup(res.text, 'html.parser')
    bs = bs.find('ol', class_="grid_view")
    for titles in bs.find_all('li'):
        num = titles.find('em',class_="").text
        title = titles.find('span', class_="title").text
        comment = titles.find('span',class_="rating_num").text
        url_movie = titles.find('a')['href']
        
        if titles.find('span',class_="inq") != None:
            tes = titles.find('span',class_="inq").text
            print(num + '.' + title + '——' + comment + '\n' + ' 推荐语：' + tes +'\n' + url_movie)
        else:
            print(num + '.' + title + '——' + comment + '\n' +'\n' + url_movie)


#第二种解法：
import requests
# 引用 requests 模块
from bs4 import BeautifulSoup
for x in range(10):
    url = 'https://movie.douban.com/top250?start=' + str(x*25) + '&filter='
    res = requests.get(url)
    bs = BeautifulSoup(res.text, 'html.parser')
    tag_num = bs.find_all('div', class_="item")
    # 查找包含序号，电影名，链接的 <div> 标签
    tag_comment = bs.find_all('div', class_='star')
    # 查找包含评分的 <div> 标签
    tag_word = bs.find_all('span', class_='inq')
    # 查找推荐语
    print(len(tag_word),len(tag_num))
    
    list_all = []
    for x in range(len(tag_num)-1):
        if tag_num[x].text[2:5] == '223' or tag_num[x].text[2:5] =='244':
            list_movie = [tag_num[x].text[2:5], tag_num[x].find('img')['alt'], tag_comment[x].text[2:5], tag_num[x].find('a')['href'] ]
        else:
            list_movie = [tag_num[x].text[2:5], tag_num[x].find('img')['alt'], tag_comment[x].text[2:5], tag_word[x].text, tag_num[x].find('a')['href']]
        list_all.append(list_movie)
    print(list_all)
