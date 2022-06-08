---
layout: post
title:  "[Spring] Intro"
categories: tech
tags: spring
comments: true
---
# Spring framework
## eclipse에서 spring을 활용한 프로젝트 만들기
1. `create new Maven Project`를 통해 프로젝트를 생성한다.
    - Maven Project : build 도구로 maven을 사용하며 이 안에서 spring을 사용할 수 있다.- `create a simple project`를 체크한다.<br/>
    ![intro01](/assets/img/spring/intro01.JPG)
    - 프로젝트의 이름, 패키징 방식 등을 설정한다.
    ![intro02](/assets/img/spring/intro02.JPG)
        - `artifact id` : 프로젝트 이름
        - `packaging` : 패키징 방식. 일단은 jar을 사용하고 이후에 바꿀 예정
    - 프로젝트를 생성하면 다음과 같이 디렉토리가 구성된다.
    ![intro03](/assets/img/spring/intro03.JPG)
        - pom.xml : eclipse가 maven 프로젝트로 인식하기 위한 설정 파일
2. pom.xml 수정
    - pom.xml을 수정한 뒤 `update Maven`을 통해 설정을 적용해야한다.
    - 일반적으로 다음 3개의 설정을 수정/추가한다.
        1. **Maven 설정파일**
        2. **의존라이브러리**
            ```xml
            <!-- Spring framework 불러오기 -->

            <dependencies>
                <!-- https://mvnrepository.com/artifact/org.springframework/spring-context -->
                <dependency>
                    <groupId>org.springframework</groupId>
                    <artifactId>spring-context</artifactId>
                    <version>5.0.8.RELEASE</version>
                </dependency>
            </dependencies>
            ```
        3. **빌드설정**
            ```xml
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-compiler-plugin</artifactId>
                        <configuration>
                            <source>1.8</source>
                            <target>1.8</target>
                            <encoding>utf-8</encoding>
                        </configuration>
                    </plugin>
                </plugins>
            </build>
            ```
<br/>
<br/>

