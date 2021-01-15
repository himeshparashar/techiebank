 
#!/usr/bin/python

import requests
from bs4 import BeautifulSoup
import os
from colorama import Fore
import random

w = Fore.WHITE
g = Fore.GREEN
c = Fore.CYAN
y = Fore.YELLOW
b = Fore.BLUE
r = Fore.RED

colors = (w, g, c, y, b, r)
color = random.choice(colors)

banner = '''
 _____         _     _     ______             _    
|_   _|       | |   (_)    | ___ \           | |   
  | | ___  ___| |__  _  ___| |_/ / __ _ _ __ | | __
  | |/ _ \/ __| '_ \| |/ _ \ ___ \/ _` | '_ \| |/ /
  | |  __/ (__| | | | |  __/ |_/ / (_| | | | |   < 
  \_/\___|\___|_| |_|_|\___\____/ \__,_|_| |_|_|\_\
                                                                                           ©Bank of technology

     [+] Made by TechieBank
     [+] Instagram -: bank_of_technology (boy_himesh)
     [+] Whatsapp -: +1 (775) 665-6745
'''
print(color + banner + color)
titles = []
links = []
final_link = []
course = input(w + '     [+] ' + color + 'Enter the course name (eg: php,hacking,python,wifi,bussiness,design,development): ')
url = 'https://freeallcourse.com/?s=' + course
x = 0
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')
for i in soup.find_all('a', class_='post-title post-url'):
    title = i.get_text()
    link = i.get('href')
    titles.append(title)
    links.append(link)
for i in titles:
    print(w + '     [' + str(x) + '] ' + w + g + i + g)
    x += 1
print(' ')
choice = int(input(w + '     [+] ' + w + color + 'Select the course you want to download: ' + color))
_response = requests.get(links[choice])
_soup = BeautifulSoup(_response.content, 'html.parser')
description = _soup.find('div', class_='entry-content clearfix single-post-content')
print(' ')
print(w + '[+]' + w + g + '----------------' + g + y + ' What you will learn ' + y + g + '----------------' + g + w + '[+]' + w)
print(' ')
for i in description.find_all('li'):
    print(w + '     [+] ' + w + g + i.get_text() + g)
try:
    course_link = _soup.find('a', class_='wp-block-button__link has-white-color has-vivid-green-cyan-background-color has-text-color has-background')
    torrent_link = course_link.get('href')
    final_link.append(torrent_link)
except AttributeError as e:
    try:
        course_link = _soup.find('p', class_='has-text-align-center')
        torrent_link = course_link.find('a')
        final = torrent_link.get('href')
        final_link.append(final)
    except AttributeError as e:
        course_link = _soup.find('a', class_='btn btn-default btn-lg')
        final = course_link.get('href')
        final_link.append(final)
print(' ')
want = input(w + '      [+] ' + w + color + ' Do you want to download the course [y/n]: ' + color)
if want == 'y':
    download = os.system('wget ' + '"' + final_link[0] + '"')
    print(download)
else:
    print('Ok bye bye')
