---
title: "왜 오류가 뜨는걸까???"
date: 2021-09-08 22:41:00 -0900
categories: Nodejs
---
사지방에서 GoormIDE로 개발을 하려고 npm으로 socket.io를 다운받으려고 하는데..   
   
```sh
npm ERR! typeerror Error: Missing required argument #1
...
```
이런 오류가 떴다...   
왜 떴을까 고민해보며 구글링을 해보니   
오래된 npm이 설치되었을 때의 문제란다...   
   
처음 컨테이너를 할당 받을 때 npm이 설치가 안되어있기 때문에   
apt install npm으로 설치를 먼저 했는데...   
   
다운받아지는 npm 버전이 낮았나보다   
   
```sh
# npm cache clean --force
# npm install -g n
# n stable
```
   
위의 코드를 차례대로 실행하면 최신 버전의 npm이 설치되고   
이후 다시   
   
```sh
# npm install socket.io
```
를 실행하니 정상적으로 작동하는 것을 발견~~~   
   
설치되어서 다행이다.. ㅠㅠ   

