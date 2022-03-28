---
layout: post
title:  "[JAVA]기초 작업?"
subtitle: 설치하고,,뭐시깽이,,,,그런거 정리,,,
categories: tech
tags: java
comments: true
---
**Contents**
- [href에서의 절대경로, 상대경로](#절대경로-상대경로)



---
# Java 설치
## <span style="color:#da7c7c">1. JDK 설치</span>
- 현재 운영되는 사이트들은 대부분 v1.5 ~ v1.8 로 만들어져 있기 때문에 v1.8을 다운받아 설치하였다.

## <span style="color:#da7c7c">2. jdk 설치 확인</span>
JDK가 정상 설치 되었다면 cmd 창에서 `java -version`을 통해 버전을 확인할 수 있다.
![java_version_check](/assets/img/JAVA/jdk_version_check.JPG)


java 파일을 실행하기 위해서는 **C:\Program Files\Java\jdk1.8.0_321\bin**에 존재하는 **javac.exe**가 연결되어야 한다. <br/>
cmd 창에서 `javac -version`을 통해 javac의 버전을 확인해보자
![javac_version_1](/assets/img/JAVA/javac_version_1.JPG)
**javac.exe**가 설치되어있는 것을 확인했지만 다음과 같은 화면이 출력되는 이유는 환경 변수에 추가되어있지 않기 때문이다.

## <span style="color:#da7c7c">3. 환경 변수에 추가</span>
- 시스템 속성에 들어가서 오른쪽 하단에 있는 환경 변수에 들어간다.
    ![add_global_var](/assets/img/JAVA/global_var_1.JPG)

- 사용자 변수와 시스템 변수가 존재하는데 시스템 변수 하단에 새로 만들기를 눌러서 변수를 추가한다.
    - 변수 이름은 **JAVA_HOME**으로 하고 값은 javac.exe가 들어있는 bin 폴더의 상위 폴더까지의 값을 입력하고 확인을 누른다.
        ![add_sys_var](/assets/img/JAVA/add_sys_var.JPG)

- javac를 cmd 창에서 바로 실행할 수 있게 **PATH**에 추가한다.
    - 시스템 변수 중에 path 변수를 더블클릭해서 창을 연다.
    - 오른쪽 상단에 새로 만들기를 눌러서 `%JAVA_HOME%\bin`을 추가한다.

    - 모두 확인을 눌러 저장한 후 시스템 속성을 종료한다.

- 새로운 cmd 창을 열어서 javac의 버전을 확인한다.
    - 다음과 같이 나오면 환경 변수에 정상적으로 추가가 된 것이다. 
    ![check_javac_version](/assets/img/JAVA/javac_version_2.JPG)

## <span style="color:#da7c7c">4. java 파일 실행해보기</span>
- 다음 내용이 들어있는 HelloJava.java 파일을 생성한다.
    - 메모장을 통해 생성 가능
    ```java
    public class HelloJava {
	    public static void main(String[] args) {
		    System.out.println("안녀엉~");
    	}
    }
    ```

- cmd 창에서 해당 파일이 있는 디렉토리까지 이동한다.
- `javac HelloJava.java` 명령어를 통해 해당 파일을 OS에 상관 없이 JRE에서 실행할 수 있게 컴파일 한다.
    - 자바의 철학인 WORA(Write Once Run Anywhere)를 여기서 확인할 수 있다.
    - **HelloJava.class** 파일이 자동으로 생긴다.

- `java HelloJava` 명령어를 통해 HelloJava.class 가 실행되며 결과를 출력한다.

<br/>
<br/>
<hr>

# eclipse 다운
- [eclipse](https://www.eclipse.org/downloads/packages/) 에 들어가서 **2020년 6월의 Eclipse IDE for Enterprise Java Developers**를 운영체제에 맞게 다운받고 unzip한다.
    - java v1.8를 사용할 수 있는 가장 최근 버전의 eclipse가 2020년 6월 버전이다.

- 원하는 디렉토리에 Java 파일들을 저장할 workspace 폴더를 만들고 **eclipse.exe**를 실행하여 workspace로 해당 폴더를 지정한다.

- 프로젝트 하나를 생성한다.
    - 프로젝트를 하나의 프로그램이라고 생각하면 된다.  
    ![make_project](/assets/img/JAVA/start_project.JPG)

- 해당 프로젝트의 src 에 package를 하나 만들고 HelloJava라는 class를 생성한다.

- class의 내용은 다음과 같이 입력한다.
    ```java
    //package 정보를 알려준다. 이 파일은 examjava01 안에 있다는 정보
    package examjava01;

    //모든 java파일은 무조건 파일명과 동일한 class 명을 가져야 한다.
    public class HelloJava {
        public static void main(String[] args) {
            System.out.println("안녀엉~");
        }
    }
    ```
    - eclipse는 문서를 저장하면 자동으로 컴파일 해준다.

- 컴파일된 파일을 실행한다.
    - run : 코드 전체를 그냥 실행
    - debug : 코드를 한 줄 한 줄 실행하면서 에러가 존재하는지 출력한다.
        - 멈추는 지점을 설정하지 않으면 run과 동일하게 실행된다.
    - 결과는 console에 출력된다.


