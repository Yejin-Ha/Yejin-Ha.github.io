---
layout: post
title: "[Git]Github blog 만들기"
subtitle: "Github blog 설정하는 방법"
categories: git
tags: Github
comments: true
---
### **Github blog를 만들어보자.**
Github blog를 만들기 위해서는 다음의 조건들이 필요하다.
1. 자신의 Github 계정
2. [repository 생성](#span-style"colorda7c7c"githubio-repository-만들기span)
3. Ruby 설치 
4. [Jekyll 다운받기](#span-style"colorda7c7c"jekyll-다운받기span)
    - jekyll 테마를 적용하는 것은 선택<br/>

<br/>
<br/>
<hr/>
<br/>

# <span style="color:#da7c7c">Github.io repository 만들기</span>
## 1. 자신의 Github에 repository 생성
- repository의 이름은 무조건 `{사용자이름}.github.io` 가 되어야 한다.
- 사용자의 이름과 정확히 일치하지 않으면 작동하지 않을 수 있다.

## 2. Local에 clone 받기
- 생성한 repository를 자신의 컴퓨터에 clone 받는다.

## 3. index.html 파일 push
- index.html을 간단하게 생성한다.
    - index.html : 블로그의 시작 화면
- main에 push한다.
    ```
    git add .
    git commit -m "create index.html"
    git push -u origin main
    ```

## 4. 확인하기
- `{username}.github.io` 에 접속해서 index.html 파일이 잘 적용되었는지 확인한다.
    - Ex) [https://yejin-ha.github.io/](https://yejin-ha.github.io/) 
- 파일이 적용되려면 10분 정도의 시간이 걸리므로 적용이 안되었다고 조급해하지 말자 :smiley:

<br/>
<br/>
<br/>

# <span style="color:#da7c7c">Ruby 설치</span>
Jekyll는 Ruby 기반이므로 Jekyll 테마를 적용하려면 Ruby가 설치되어있어야 한다.  
만약 Jekyll 테마를 적용하지 않는다면 이 과정은 무시해도 괜찮다.

<br/>
<br/>
<br/>

# <span style="color:#da7c7c">Jekyll 다운받기</span>
## 1. jekyll 설치
- `Start command prompt with Ruby`를 실행한다.
- 그 후 다음의 명령어를 실행한다.
    ```
    gem install jekyll bundler
    ```
    - bundler - jekyll와 사용하기 좋은 도구이다.
        - 프로젝트에 따라 다른 버전의 Jekyll를 사용해야 하거나 Jekyll를 시스템 레벨이나 사용자 레벨에 설치하고 싶지 않을 때 유용하다.

## 2. Jekyll project 생성
- 프로젝트를 생성하기 전에 무조건 clone한 dir로 이동해야 한다.
    ```
    <!-- clone 받은 dir로 이동 -->
    cd Yejin-Ha.github.io

    <!-- 새로운 jekyll 프로젝트 생성 -->
    jekyll new ./
    ```
- 다음과 같은 에러가 발생하는 경우가 있다. 
    ![Image Alt 텍스트](/assets/img/Gitblog/gitblog_jekyllerr1.png)
    - 이런 error가 나올 경우 `jekyll new ./ --force`를 통해 해결할 수 있다.
    - 아마 이미 프로젝트가 존재하는 경우에 이런 error가 발생한다.

## 3. jekyll 테마 적용
- 원하는 jekyll 테마를 정한다.
- github에서 zip으로 다운받고 unzip한 뒤 local에 clone 받은 자신의 repository(Yejin-Ha.github.io)에 복사한다.
- gemfile들을 빼고는 다 복사한 후 __config.yml을 보고 gemfile을 수정한다.  

__config.yml             |  Gemfile
:-----------------------:|:-----------------------:
![Image Alt 텍스트](/assets/img/Gitblog/config1.JPG) | ![ML_decision_tree_3_0](/assets/img/Gitblog/genfile1.JPG)

## 4. bundle install
- Genfile에 설정한 내용을 토대로 프로젝트에 사용될 bundle들을 설치한다.
    ```
    bundle install
    ```

## 5. 서버 실행
- 이전의 과정에서 아무런 문제가 없었다면 서버를 실행했을 때 아무 error가 생기지 않을 것이다.
- 다음 명령을 통해 서버를 실행시킨다.
    ```
    bundle exec jekyll serve
    ```