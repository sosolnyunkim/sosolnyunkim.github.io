---
layout: post
title:  "[Github Blog] 시작하는 방법 - (2) 로컬 서버 활용"
date:   2022-12-18 00:00:00 +09:00
image:  '/assets/img/GithubPage.jpg'
tags:   [Github]
---

> 글이 제대로 써졌는 중간 주간 확인하면서 봐야겠죠?  
  매번 push하기에는 너무 오래 걸리기 때문에, 로컬 서버에서 확인하는 방법을 알려드릴게요!

### **1. Window에 Ruby설치**
window에 bundle을 설치하기 위해서는 반드시 ruby를 먼저 설치해야함.  
아래 사이트에서 ruby를 설치.  
[rubyinstaller.org](https://rubyinstaller.org/downloads/)
![](/assets/img/ruby.png)


### **2. Bundle 설치**
Ruby를 설치한 후, window powershell 창을 **다시 실행해야 함.**  
아래 command를 이용하여, git clone한 내 github.io 폴더 위치에서 bundle을 설치
```shell
bundle install
```
![](/assets/img/bundle install.png)


### **3. 로컬 서버에서 github 블로그 실행**
이제 로컬 서버에서 나의 github 블로그를 실행
##### 1) window powershell에서 아래의 command를 이용하여 서버를 실행
```shell
bundle exec jekyll server
```
##### 2) 크롬 창에는 아래의 주소를 주소 창에서 실행
```shell
http://127.0.0.1:4000/
```
![](/assets/img/localserver.png)


### **4. 파일을 수정할 때마다 제대로 업데이트 되는지 확인**
파일을 수정할 때마다 로컬 서버에 업데이트되는지 확인.  
파일의 최종 수정이 끝나면, 아래 command를 이용하여 push하면 실제 블로그에 동일하게 반영됨.
```shell
git add -all
git commit -m "first commit"
git push -u origin main
```

