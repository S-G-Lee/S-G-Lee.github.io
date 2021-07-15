---
layout: post
title:  "지킬(jekyll) 로 포스팅하기"
date:   2021-07-15 10:25:02 +0900
categories: jekyll update
tags: [blog, jekyll, github.io]
---
# Github 블로그 repository 만들기

1. Github에 reposit만들기

   - 반드시 username.github.io 이런 식으로 생성해야됨

2. >  git clone 복사한주소

3. clone한 폴더에 파일생성

   - > ex. cd username.github.io
     >
     > echo "hello world" > index.html

4. push

   > git add --all
   >
   > git commit -m "init"
   >
   > git push -u mygithub main

5. 브라우저에 username.github.io 쳐서 확인

# jekyll 적용

1. 로컬 cmd로 jekyll설치

   > gem install jekyll bundler

2. index.html 제거

3. github.io 폴더로 이동해서 jekyll 생성

   > jekyll new ./

4. > bundle install

5. jekyll을 로컬서버에 띄우기

   > bundle exec jekyll serve

   - 명령줄에 server adress: http://127.0.0.1:4000/ 이런식으로 뜨는 주소를 브라우저에 쳐보기

6. 원격에 push

   > git add .
   >
   > git commit -m '메시지'
   >
   > git push

# 테마 설정

1. 테마 사이트에서 테마 탐색

   **[jamstackthemes.dev](https://jamstackthemes.dev/ssg/jekyll/)**

   **[jekyllthemes.org](http://jekyllthemes.org/)**

   **[jekyllthemes.io](https://jekyllthemes.io/)**

   **[jekyll-themes.com](https://jekyll-themes.com/)**

2. 선택한 테마 링크로 이동

3. 다운로드

4. 다운받은 폴더의 파일들을 전체 복사 후 내 github.io 폴더에 복사(덮어쓰기)

5. > bundle install

6. > bundle exec jekyll serve

7. 설정 수정ㅠ

   1. _config.yml 열기
   2. 설정 추가

8. post 추가

   1. _posts폴더에 markdown형식으로 글쓰기

9. 원격에 push

# 문제 및 해결

1. jekyll 실행 시 `require': cannot load such file -- webrick (LoadError) 라는 오류 발생

   - webrick이라는 모듈이 없어서 오류 -> 설치하면 해결

     > bundle add webrick

2. 테마 설정 후 bundle install시 Bundler found conflicting requirements for the Ruby  version 에러 발생

   - ruby버전이 테마의 버전과 호환이 안되서 생기는 문제
