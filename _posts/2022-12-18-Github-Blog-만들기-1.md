---
layout: post
title:  "[Github Blog] 시작하는 방법 - (1)"
date:   2022-12-18 00:00:00 +09:00
image:  '/assets/img/GithubPage.jpg'
tags:   [Github]
---

> :bulb: window powershell인지 git bash인지 혼동하지 말 것!

### **1. 전제조건**
Window에 powershell은 이미 install 되어있어야 함.


### **2. Window에 git 설치하기**
window에서 글을 자유롭게 쓰기 위해서는 에디터인 vim이 사용가능해야 함. git은 vim을 사용가능하도록 함.  
**window powershell**에서 아래 command를 이용하여 git을 설치할 수 있음.
```shell
winget install --id Git.Git -e --source winget 
```
![](/assets/img/WindowGit.png)


### **3. Driver 설치하기**
##### 1) Github에서 사용할 repository를 생성
![](/assets/img/WindowGit2.png)
##### 2) repository 이름은 반드시 **username.github.io**로 해야함. (username과 정확히 일치하지 않으면 작동하지 않음.)
![](/assets/img/WindowGit3.png)


### **4. Repository와 연동할 폴더 생성 및 선택**
repository와 연동할 폴더를 생성하고, 해당 폴더를 우클릭하여 "더 많은 옵션 보기 > Git Bash Here"로 Git Bash를 실행
![](/assets/img/WindowGit4.png)
![](/assets/img/WindowGit5.png)

### **5. Repository clone**
**git bash**에서 Respoitory를 clone 함. 아래 command를 이용하여 clone할 수 있음.
```shell
git clone <생성한 github 주소>
```
이때 github 주소는 아래 그림에서 표시된 빨간색 부분을 눌러서 얻을 수 있음.
![](/assets/img/WindowGit6.png)
![](/assets/img/WindowGit7.png)
![](/assets/img/WindowGit8.png)

### **6. 페이지 생성**
**git bash**에서 test 파일 생성
```shell
echo "Hello" > index.html
```

### **7. Push**
**window powershell**에서 아래 command를 이용하여 repository에 올리기 (이를 push라고 함.)
```shell
git add -all
git commit -m "first commit"
git push -u origin main
```

