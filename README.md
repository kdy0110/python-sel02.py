# python-sel02.py
from bs4 import BeautifulSoup
import requests
from selenium import webdriver
import time
import chromedriver_autoinstaller
driver = webdriver.Chrome()
url = 'https://www.melon.com/chart/index.htm'
driver.get(url)
time.sleep(2)
soup = BeautifulSoup(driver.page_source, 'html.parser')
# print(soup.prettify())
driver.quit()
tbody = soup.find('tbody')
trs = tbody.find_all('tr')
for tr in trs:
    tds = tr.find_all('td')
    rank = tds[1].select_one('span.rank').text
    a_tag = tds[5].find_all('a')
    title = a_tag[0].text
    singer = a_tag[1].text
    print(rank, title, singer)





# WebDriver를 종료합니다. (브라우저 창을 닫음)
driver.quit()

# BeautifulSoup을 사용하여 HTML 페이지의 tbody 태그를 찾습니다.
tbody = soup.find('tbody')

# tbody 태그 내의 모든 tr 태그를 찾아서 리스트로 저장합니다.
trs = tbody.find_all('tr')

# 각각의 tr 태그에 대해 반복문을 실행합니다.
for tr in trs:
    # 현재 tr 태그 내의 모든 td 태그를 찾아서 리스트로 저장합니다.
    tds = tr.find_all('td')

    # 두 번째 td 태그 내에 있는 span 태그의 클래스가 'rank'인 요소를 선택하고 텍스트를 가져옵니다.
    rank = tds[1].select_one('span.rank').text

    # 다섯 번째 td 태그 내에 있는 모든 a 태그를 찾습니다.
    a_tag = tds[5].find_all('a')

    # a 태그 리스트에서 첫 번째 a 태그의 텍스트를 음악 제목으로 가져옵니다.
    title = a_tag[0].text

    # a 태그 리스트에서 두 번째 a 태그의 텍스트를 가수로 가져옵니다.
    singer = a_tag[1].text

    # 결과를 출력합니다.
    print(rank, title, singer)














# res = requests.get(url)
# print(res.status_code)
# soup = BeautifulSoup(res.content, 'html.parser')
# print(soup.prettify())
