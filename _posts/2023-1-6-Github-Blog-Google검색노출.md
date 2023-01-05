---
layout: post
title:  "[Github Blog] Google 검색노출"
date:   2023-01-06 00:00:00 +09:00
image:  '/assets/img/GithubPage.jpg'
tags:   [Github]
---

### **1. Google Search Console에 사이트 등록**
##### 1) 아래 사이트를 이용하여 Google Search Console에 접속
[Google Search Console](https://search.google.com/search-console/welcome?hl=ko)
##### 2) URL 접두어에 자신의 github io 주소를 입력
![](/assets/img/googleconsole.png)
##### 3) 소유권을 확인하는 절차 진행
(1) 제공하는 html을 다운받아서, 나의 github에서 _config.xml 파일과 동일한 위치 (root 위치)에 넣기.  
(2) 확인을 누르면 소유권이 확인되었다는 창이 뜸.
![](/assets/img/checkgoogle.png)

### **2. sitemap.xml생성**
아래 사이트에 있는  sitemap.xml 코드를 다운받은 google html 파일과 동일한 위치에 만들어주면 됨.  
[sitemap.xml](https://github.com/sosolnyunkim/sosolnyunkim.github.io/blob/main/sitemap.xml)

### **3. robots.txt 생성**
아래 robots.txt 코드를 sitemap.xml 파일과 동일한 위치에 만들어주면 됨.  
이때 Sitemap에 **자신의 github 주소/sitemap.xml**을 작성해주면 됨.
```text
User-agent: *
Allow: /
Sitemap: https://sosolnyunkim.github.io/sitemap.xml
```

### **4. Google Search Console에 sitemap등**
(1) 아래 그림처럼 Google Serach Console에서 **생인생성 > Sitemaps**에 들어가면 됨.  
(2) **새 사이트맵 추가**에 **sitmap**을 작성 후, 제출하면 됨. (이때 그림처럼 sitemap.xml을 적으면 fail이 뜸. 그러면 .xml을 제외하고 적으면 됨.)
![](/assets/img/sitemap.png)
![](/assets/img/sitemap2.png)














