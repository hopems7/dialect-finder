# dialect-finder
# This project aims to find dialectal variants of the word "you" on a web page using Python

import urllib.request, urllib.parse, urllib.error
import re
import ssl
count = 0

#Creates the connection that will link to the url.

ctx=ssl.create_default_context()
ctx.check_hostname=False
ctx.verify_mode=ssl.CERT_NONE

#The user enters the url.

url=input('Enter - ')
html=urllib.request.urlopen(url).read()

#Matches the plurals "youse" and "y'all"

links=re.findall(b"\sy[o']\w\w\w\s", html)

#Prints each occurence and the total number of occurences

for link in links:
     count=count + 1
     print(link.decode())
print("Total Count: ", count)

