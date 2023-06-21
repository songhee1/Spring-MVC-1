# Spring-MVC-1
Spring MVC 1편 강의를 보며 정리한 글입니다.

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>

- [Spring-MVC-1](#spring-mvc-1)
  * [섹션 1](#---1)
  * [I. 모든 것이 HTTP](#모든-것이-HTTP)
    + [1)웹 서버](#웹-서버)
    + [2) 웹 애플리케이션 서버](#웹-애플리케이션-서버)
    + [3) 이 둘의 차이](#이-둘의-차이)
    + [4) 웹 시스템 구성 - was, db](#4-------------was--db)
    + [5) 그래서 웹 시스템 구성하는 방법?](#5--------------------)
  * [II. 서블릿](#ii----)
    + [1) HTML FORM 데이터 전송](#1--html-form-------)
    + [2) 서블릿](#2-----)
  * [III. 동시요청 - 멀티 쓰레드](#iii--------------)
    + [서블릿 객체는 누가 호출하는가?](#-----------------)
    + [3) 쓰레드 풀 (요청마다 생성되는 스레드의 단점 보완)](#3------------------------------)
    + [4) 쓰레드 풀 - `실무팁`](#4---------------)
    + [5) 쓰레드 풀 - 적정 숫자](#5---------------)
    + [6) WAS 의 멀티 쓰레드 지원(핵심)](#6--was----------------)
  * [IV.  HTML, HTTP API, CSR, SSR](#iv--html--http-api--csr--ssr)
    + [1) 정적 리소스](#1--------)
    + [2) HTML 페이지(동적)](#2--html--------)
    + [3) HTTP API](#3--http-api)
    + [4) 서버사이드 레더링 SSR](#4------------ssr)
    + [5) 클라이언트 사이드 렌더링 CSR](#5----------------csr)
    + [6) 정리(백엔드 개발자 입장에서 UI 기술 어디까지 알아야 하는가)](#6------------------ui-----------------)
  * [V. 자바 백엔드 웹 기술 역사](#v---------------)
    + [1) 최신기술(스프링 웹 플럭스)](#1-----------------)
    + [2) 자바 뷰 템플릿 역사](#2-------------)
  * [섹션 2](#---2)
  * [I. Hello 서블릿](#i-hello----)
    + [서블릿 환경구성](#--------)
    + [서블릿 동작방식](#--------)
  * [II. HttpServletRequest-개요](#ii-httpservletrequest---)
  * [III. HttpServletRequest 기본 사용법](#iii-httpservletrequest-------)
    + [(1) start-line 정보](#-1--start-line---)
    + [(2) 헤더의 모든 정보를 출력하고자 할때](#-2---------------------)
    + [(3) Header 편리 기능을 조회할때](#-3--header------------)
    + [(4) Header 기타 정보를 조회하고자 할때](#-4--header----------------)
  * [III. HTTP 요청 데이터 - 개요](#iii-http------------)
    + [(1) Get방식의 쿼리 파라미터](#-1--get-----------)
    + [(2) Post- HTML Form](#-2--post--html-form)
    + [(3) HTTP message body](#-3--http-message-body)
    + [(1) HTTP 요청 데이터 중 GET 쿼리 파라미터](#-1--http----------get--------)
    + [(2) Post- HTML Form](#-2--post--html-form-1)
    + [(3) HTTP 요청 데이터 - API 메세지 바디- 단순 텍스트](#-3--http----------api---------------)
    + [(3) HTTP 요청 데이터 - API 메세지 바디- JSON](#-3--http----------api---------json)
  * [HttpServletResponse-  기본 사용법](#httpservletresponse---------)
    + [(1) Http 응답 데이터](#-1--http-------)
  * [섹션 3](#---3)
  * [I. 회원관리 웹 애플리케이션 요구사항](#i-------------------)
  * [II. 서블릿으로 회원 관리 웹 애플리케이션 만들기(MVC구현)](#ii--------------------------mvc---)
    + [(1) 회원 저장 폼에 대한 응답을 처리하는 서블릿(`MemberFormServlet`)](#-1----------------------------memberformservlet--)
    + [(2) 회원 저장 폼에 대한 요청과 응답을 처리하는 서블릿(`MemberSaveServlet`)](#-2--------------------------------membersaveservlet--)
    + [(3) 회원 목록 페이지에 대한 요청과 응답을 처리하는 서블릿(`MemberListServlet`)](#-3----------------------------------memberlistservlet--)
  * [III. JSP로 스프링 MVC 구현해내기](#iii-jsp------mvc------)
    + [(1) 회원 관리/회원 저장/회원 목록 웹 애플리케이션 생성](#-1-------------------------------)
  * [IV. MVC패턴](#iv-mvc--)
    + [**[MVC패턴을 사용해야하는 경우]**](#---mvc----------------)
    + [**[그럼 MVC패턴이란]**](#------mvc-------)
  * [V. MVC 패턴을 적용(JSP를 뷰, 서블릿을 컨트롤러로 사용)](#v-mvc--------jsp-------------------)
    + [(1) 회원 등록 폼 서블릿(컨트롤러), 회원 저장 서블릿, 회원 리스트 서블릿](#-1------------------------------------------)
  * [VI. MVC 패턴을 적용 후 한계(JSP를 뷰, 서블릿을 컨트롤러로 사용)](#vi-mvc-------------jsp-------------------)
  * [섹션 4](#---4)
  * [I. 프론트 컨트롤러 패턴 소개](#i---------------)
    + [(1) 프론트 컨트롤러 도입 전과 후 비교 그림](#-1------------------------)
    + [(2) 프론트 컨트롤러 패턴이란?](#-2----------------)
  * [II. 프론트 컨트롤러 도입-Version.1](#ii-------------version1)
    + [(1) Version 1의 구조](#-1--version-1----)
  * [III. View의 분리-Version.2](#iii-view-----version2)
    + [(1) 코드의 중복 발견](#-1-----------)
    + [(2) v2 구조](#-2--v2---)
  * [IV. Model의 분리-Version.3](#iv-model-----version3)
    + [(1) Version2의 문제점](#-1--version2-----)
    + [(2) Version3 구조](#-2--version3---)
  * [V. 단순하고 실용적인 컨트롤러 - Version4](#v------------------version4)
    + [(1) v4 구조](#-1--v4---)
  * [VI. 유연한 컨트롤러 - Version5](#vi------------version5)
  * [(1) 어댑터 패턴 등장](#-1-----------)
  * [(2) v5 구조](#-2--v5---)
  * [섹션 5](#---5)
  * [I. 스프링 MVC 전체 구조](#i-----mvc------)
    + [(1) 직접 만든 MVC 프레임워크 구조](#-1--------mvc---------)
    + [(2) Spring MVC 구조](#-2--spring-mvc---)
    + [(3) DispatcherServlet 구조 살펴보기](#-3--dispatcherservlet--------)
    + [(4) 동작과정](#-4------)
    + [(5) 주요 인터페이스 목록](#-5-------------)
  * [II. 핸들러 매핑과 핸들러 어댑터의 이해](#ii--------------------)
    + [(1) Controller인터페이스를 활용해 이해해보자](#-1--controller----------------)
    + [(2) HttpRequestHandler인터페이스를 사용해 이해해보자](#-2--httprequesthandler----------------)
  * [III. 뷰 리졸버의 이해](#iii----------)
    + [(1) 뷰 리졸버 동작 방식](#-1-------------)
  * [IV. 스프링 MVC 시작하기](#iv-----mvc-----)
    + [(1) `@RequestMapping` 의 이해](#-1----requestmapping------)
    + [(2) 스프링 MVC- 컨트롤러 통합](#-2------mvc---------)
    + [(3) 스프링 MVC- 실용적인 방식](#-3------mvc---------)
</a></i></small>




## 섹션 1

## I. 모든 것이 HTTP

다음은 모두 HTTP 기반으로 동작합니다.

### 1)웹 서버

- http 프로토콜로 주고 받을 수 있는 것을 웹 서버라고 하며 http 기반으로 동작합니다

### 2) 웹 애플리케이션 서버

- 사용자에 따라서 다른 화면들을 보여줄 수 있습니다
- **동적** html, http api(rest api) 등을 제공할 수 있습니다
- 서블릿, jsp, 스프링 mvc 모두 실행 가능합니다.

### 3) 이 둘의 차이

- 웹 서버 - 정적 리소스 파일 VS was는 웹 애플리케이션 로직이라고 보면 됩니다.
- 사실 이 둘의 경계는 모호하지만, 자바는 서블릿 컨테이너 기능을 제공하면 `was` 라고 하며, `was` 는 애플리케이션 코드를 실행하는데 더 특화되어있다고 구분하면 됩니다.

### 4) 웹 시스템 구성 - was, db

최소한으로 보면 이 둘로 구분할 수 있습니다. 

![Untitled (10)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/b9e18b6a-528d-4496-9daa-cdf5a09fe054)

- 하지만 `was` 가 너무 많은 일은 하나로 수행하게 되면 **서버 과부화**가 될 수 있습니다.
- **html/css/js** 같은 건 서빙하면 되어서 단순하지만, 애플리케이션 로직은 이들보다 매우 비쌉니다.
    - 파일을 불러다 보여주면 되지만 애플리케이션 로직은 비즈니스 로직이 들어가 있어서 가장 비쌉니다.
- 따라서, 정적 리소스 때문에 애플리케이션 로직이 수행이 어려울 수도 있습니다.
- `was` 장애시 오류 화면도 노출이 **불가능**하게 됩니다.

![Untitled (11)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/5d88b523-13e0-4c1f-b313-a3860432bd1f)

### 5) 그래서 웹 시스템 구성하는 방법?

웹 시스템 구성 - web, was, DB

![Untitled (12)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/932dc82b-6527-41f0-b951-03003d441c36)

장점

- 앞에 `web server`를 두고 정적 리소스를 처리 → 뒤에서 `was` 는 애플리케이션 로직만 담당하게 되어 중요 처리를 분담하게 됩니다.
- 효율적인 리소스 관리가 가능해집니다.
    - 정적 리소스가 많아지면 web 서버 증설하면 되고 반대로 애플리케이션 로직이 많아지면 `was` 를 증설하면 되기 때문입니다.

- 정적 리소스 제공하는 웹 서버는 잘 죽지 않지만,, `was` 서버는 잘 죽습니다.
    - `was` 또는 `db`가 제대로 응답을 못하면 web 서버에서 오류화면을 제공할 수 있습니다.
    - 데이터만 구축하게 될 경우에는 `was` 서버만 구축하면 됩니다.
    

## II. 서블릿

### 1) HTML FORM 데이터 전송

- METHOD = ‘POST’로 전송해 저장한다고 해봅시다.

![Untitled (13)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/ad048613-4d22-4f98-b1fd-3d9c479cd8fd)

- “서블릿” 은 비즈니스 로직 실행을 제외한 모든 기능을 모두 수행합니다.
    - HTTP 요청 메시지 파싱
    - …
    - 원래 서버에서 처리해야 할 업무들을 모두 비즈니스 로직 제외한 내용들을 수행합니다.

### 2) 서블릿

**특징**

- HTTP 요청 정보를 편리하게 사용할 수 있는 `HttpServletRequest` 가 있습니다.
- HTTP 응답 정보를 편리하게 제공하는 `HttpServletResponse` 가 있습니다.

- 서블릿 컨테이너 : 서블릿 객체를 생성, 호출하며, `WAS` 가 내려갈 때 서블릿 객체도 같이 내려줍니다.
- 톰캣처럼 서블릿 지원하는 `WAS` 를 `서블릿 컨테이너`라고 합니다.
- **서블릿 객체는 싱글톤으로** 관리합니다. (모두 공유해서 사용)
    - 최초 로딩 시점에 서블릿 객체를 미리 만들어두고 재활용합니다.
    - 모든 고객 요청은 동일 서블릿 객체 인스턴스에 접근하여 로직을 실행하게 됩니다.
    - **공유 변수에 주의해야**합니다. 싱글톤 객체는 멤버변수 사용할 때 주의해야 합니다.
    - 서블릿 컨테이너 종료할 때 서블릿 객체도 같이 종료됩니다.
- JSP도 서블릿으로 변환되어 사용됩니다.
- **동시 요청 위한 멀티 쓰레드 처리를 지원합니다.**
    - `WAS`가 자동으로 해결을 해줍니다.

## III. 동시요청 - 멀티 쓰레드

### 서블릿 객체는 누가 호출하는가?

- `쓰레드`가 호출합니다.
    - 애플리케이션 코드를 하나하나 내부에서 순차적으로 실행하는 것을 말합니다.
    - EX. 메인 메서드를 실행하면 MAIN 이름의 스레드가 실행되는 것입니다.
    - 스레드가 없으면 자바 애플리케이션 실행이 아예 불가능합니다.
    - 스레드는 한번에 하나의 코드 라인만 수행합니다.
    - 따라서, 동시처리가 필요하면 하나 이상이 필요합니다.

![Untitled (14)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/08e00edf-dbec-4cb0-8731-86322f25f049)

- 요청1에서 스레드를 사용하고 있으니(처리가 지연되는 중), 요청2는 계속해서 대기해야 합니다.

→ 요청마다 스레드를 생성해야 합니다.

![Untitled (15)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/fbcd998c-a275-4950-b3e4-ab25777a6567)

요청마다 스레드를 생성하는 것의 장단점

**장점**

- 동시 요청 처리가 가능하다.
- 하나의 쓰레드가 지연되어도, 나머지 스레드는 정상 동작합니다.

**단점**

- 스레드는 생성비용이 매우 비쌉니다.
- 스레드는 컨텍스트 스위칭 비용이 발생합니다.
    - cpu의 코어가 만약 하나라면, 코어 하나가 하나씩 수행, 전환할때 비용이 발생하는데 이를 ‘컨텍스트 스위칭 비용’ 이라고 합니다.

- 스레드 생성 제한이 없습니다.
    - 고객 요청이 너무 많이 오면, 메모리 임계점을 넘게되어 서버가 죽을 수도 있습니다. 못버티고 서버가 다운됩니다.
    

→ 내부에 스레드 풀이 있습니다.

![Untitled (16)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/364140dd-a2a7-4e00-b117-a4387c8702f7)

- 스레드 풀에서 갖다 쓰고 사용이 다 되면 스레드 풀에 반납을 합니다. 이런 식으로 스레드를 빌려쓰고 가져다 놓는 방식을 수행합니다.
- 스레드가 200개가 한계라고 한다면, 스레드가 없을 경우, 스레드를 대기하고, 거절합니다.
    - 너무 많이 밀리면 거절하게 됩니다.

### 3) 쓰레드 풀 (요청마다 생성되는 스레드의 단점 보완)

**특징**

- 필요 스레드를 스레드 풀에 보관하고 관리합니다.
- 톰캣은 최대 200개 기본으로 설정합니다.

**사용**

- 스레드가 필요하면 스레드 풀에서 가져다 사용하게 됩니다.
- 사용 종료시 해당 스레드를 스레드 풀에 반납합니다.
- 만약 스레드 풀에 스레드가 없다면 특정 숫자만큼 대기하도록 설정하게 됩니다.

### 4) 쓰레드 풀 - `실무팁`

- `was` 의 주요 튜닝 포인트는 **최대 쓰레드 수**입니다.
- 너무 낮게 설정하게 되면,,
    - 만약, 10개를 스레드 풀에 세팅을 한다고 하면, 동시 요청이 많게 되면 클라이언트는 응답 지연이 되게 됩니다.
- 너무 높게 설정하게 되면
    - 동시 요청이 많으면 임계점 초과되어 서버가 다운될 수 있습니다.

### 5) 쓰레드 풀 - 적정 숫자

- 상황에 따라 모두 다르기 때문에 `성능 테스트`를 해봐야합니다.
- 가급적이면 실제 서비스와 유사하게 성능 테스트를 시도하는 것도 좋습니다.
    - 툴 : 아파치 ab, 제이미터, nGrinder

### 6) WAS 의 멀티 쓰레드 지원(핵심)

- WAS가 멀티스레드를 지원한다는 것입니다. 개발자가 **스레드 관련 코드**를 신경쓰지 않아도 됩니다.
- 개발자는 비즈니스 로직만 작성하면 됩니다. 마치 **싱글 쓰레드 프로그래밍하듯** 편리하게 소스코드를 개발하면 됩니다.
- 대신, 어찌돼었든 멀티 쓰레드 환경이므로, 싱글톤(서블릿, 스프링 빈)은 주의해서 사용해야 합니다.
    - 멤버변수(공유변수)는 주의하기만 하면 잘 애플리케이션 개발할 수 있습니다.
    

## IV.  HTML, HTTP API, CSR, SSR

백엔드 개발자가 다음의 세 가지를 고민해야 합니다.(정적 리소스, html, http api)

### 1) 정적 리소스

### 2) HTML 페이지(동적)

![Untitled (17)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/a185caa6-0b0f-4f0f-9a8c-151009adf144)

- was가 db를 통해 주문정보를 조회 후 동적으로 html를 생성합니다.(jsp, 타임리프를 통해) 이후 웹 브라우저에 올려줍니다.

### 3) HTTP API

- html이 아니라 데이터를 전달합니다.
- 주로 거의 대부분 **JSON형식**을 사용합니다.
- 다양한 시스템에서 사용하게 됩니다. 다음과 같이
- 사용되는 상황
    - 데이터만 주고받는 경우에 사용합니다.
    - UI 화면이 필요한 경우에는 클라이언트가 별도로 처리합니다.
    - 웹 브라우저에서 HTML 렌더링을 위해 자바스크립트를 통해 AJAX, PATCH를 사용해서 API를 호출할 수 있습니다. WAS에서 필요한 내용을 보내줍니다.

- 웹 클라이언트 → 서버/ 서버 → 서버/ 앱 클라이언트 → 서버에서 사용됩니다.

### 4) 서버사이드 레더링 SSR

- 서버에서 동적 html까지 모두 생성해서 웹브라우저에서 보여주는 것입니다. 웹 브라우저는 보여주는 역할만 합니다.
- 서버에서 html까지 모두 생성해 렌더링하는 것을 말합니다.

### 5) 클라이언트 사이드 렌더링 CSR

- html 결과를 자바스크립트로 웹브라우저에서 동적으로 생성해서 적용하는 것을 말합니다.
- DOM 구조에 HTML 넣도록 하여 HTML를 건드는 것으로, 클라이언트쪽에서 HTML를 만진다고 하여 ‘클라이언트 사이드 렌더링’이라고 합니다.
- 필요 부분만 변경할 수 있습니다.
    - 구글 지도, 구글 캘린더 등

![Untitled (18)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/42b78d5d-45c5-4454-836d-581247e44083)

- 웹 브라우저에서 서버에 요청

→ HTML 내용이 없이 응답(자바스크립트 링크를 내려준다)

→ 자바스크립트 링크를 요청합니다.(`클라이언트 로직 + HTML 렌더링 코드`가 포함되어 있습니다.)

→ HTTP API로 데이터를 요청합니다.

### 6) 정리(백엔드 개발자 입장에서 UI 기술 어디까지 알아야 하는가)

**백엔드-SSR**

- 주로 정적 화면에 사용하며, HTML 최종 결과를 서버에서 만들어 웹브라우저에 전달합니다.
- JSP보다는, 타임리프를 공부하는 것을 권장합니다.
- 화면이 정적이고 복잡하지 않을 때 사용합니다.
- 백엔드 개발자는 **서버 사이드 렌더링 기술 학습이 필수적**입니다.

프론트엔드-CSR

- HTML 결과를 자바스크립트를 사용해 웹 브라우저에서 동적 생성하여 적용합니다.
- 필요 부분만 변경할 수 있고, 이 기술은 웹 프론트엔드 기술자들이 사용합니다.
- React, Vue.js를 사용하며 프론트엔드 개발자의 전문 분야입니다.

**선택과 집중**

- 웹 프론트엔드 기술 학습은 옵션입니다.
- 백엔드 개발은 서버, DB, 인프라 등등 배워야 할 기술이 많기 때문입니다.

## V. 자바 백엔드 웹 기술 역사

- 서블릿 …html 생성의 어려움 발견
- JSP … HTML 생성은 편하지만 비즈니스 로직까지 너무 많은 역할을 담당하게 됩니다.
- 서블릿, JSP 조합 MVC 패턴을 사용합니다..모델, 뷰, 컨트롤러로 나누어 개발합니다.

→ 비즈니스로직 부분(서블릿, 자바), 화면 렌더링 부분(JSP)을 나누게 됩니다.

이후 애노테이션 기반 스프링 MVC가 등장하게 됩니다.

- 스프링 부트 등장
    - 스프링 부트에는 서버를 내장하고 있고, 빌드 결과에 was 서버를 포함시켜 빌드 배포를 단순화시킵니다.
    

### 1) 최신기술(스프링 웹 플럭스)

- 최소 스레드로 최대 성능을 냅니다. 이는 컨텍스트 스위칭 비용을 효율화시킵니다.
- 함수형 스타일로, 동시처리 코드를 효율화시킵니다.
- 다만, 스프링 웹 플럭스는 기술적 난이도도 높으며 실무에서 많이 사용하지 않습니다.

### 2) 자바 뷰 템플릿 역사

jsp → 속도가 느리고 기능이 부족합니다.

타임리프 → 

내추럴 템플릿(html모양을 유지하면서 뷰 템플릿 적용이 가능합니다.) 되게 깔끔합니다. 

**최선의 선택**이라고 볼 수 있습니다.

스프링 mvc와 강력하게 기능 통합이 가능합니다.






## 섹션 2

**Q : 서블릿 사용하려고 스프링 부트 사용하려는 이유?** 

A : 스프링 부트에는 was 서버를 내장(톰캣)하고 있어서 스프링 부트로 프로젝트생성하는 것, 더불어 스프링 부트가 환경 설정하기 편하기 때문

(packaging : war 사용(JSP, SERVLET 사용을 위해))

## I. Hello 서블릿

**참고**

(기존)서블릿은 was 직접 설치 → 클래스 파일로 빌드 후 올린 후 톰캣 서버를 실행해야 합니다.

하지만 스프링 부트는 **톰캣 서버를 내장**하고 있으므로 톰캣 서버 설치 없이 편리하게 **서블릿 코드를 실행**할 수 있습니다.

### 서블릿 환경구성

- 스프링 부트에서 서블릿 사용하려면 `@ServletComponentScan` 을 작성합니다. 스프링 부트에서 자동으로 서블릿 등록해서 실행하도록 하는 어노테이션(서블릿 자동등록)입니다.

```java
package hello.servlet;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.web.servlet.ServletComponentScan;

@ServletComponentScan //서블릿 자동 등록
@SpringBootApplication
public class ServletApplication {

	public static void main(String[] args) {
		SpringApplication.run(ServletApplication.class, args);
	}

}
```

- http 요청을 보내면→ `was`가 request 객체를 만들어서 서버에 던져주게 됩니다.→ 응답을 위한 response 객체를 만들어서 서버에서 브라우저로 던지게 됩니다.

```java
package hello.servlet.basic;

import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet(name = "helloServlet", urlPatterns = "/hello")
// '/hello'로 오면 이 서블릿이 실행됩니다.
public class HelloServlet extends HttpServlet {

    // /hello로 오면 자동으로 해당 메서드 실행
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        System.out.println("HelloServlet.service");
        System.out.println("request = " + request);
        System.out.println("response = " + response);

        String username = request.getParameter("username");
        System.out.println("username = " + username);

        response.setContentType("text/plain");
        response.setCharacterEncoding("utf-8");//위 둘은 header에 들어간다
        response.getWriter().write("hello : "+ username); //http body에 들어가게 된다.
    }
}
```


![Untitled (19)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/69b0ea47-35e9-4f30-b6f5-b16cb08ffd2a)

- 쿼리 파라미터 = `?name=kim`

→ `request.getParameter("파라미터명")` 으로 http 파라미터에 담긴 내용을 받을 수 있습니다.

![Untitled (20)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/d465821a-9104-4ce5-8176-2eb8999d8f7f)

- `@WebServlet`

→ name :  서블릿 명으로 작성됩니다.

→ urlPatterns : URL 매핑에 활용됩니다.

reponse에 값을 넣으면, http 응답 메세지에 데이터가 담겨서 나가게 됩니다.

```java
response.setContentType("text/plain");
response.setCharacterEncoding("utf-8");//위 둘은 header에 들어간다
response.getWriter().write("hello : "+ username); //http body에 들어가게 된다
```

더불어, 서블릿 이름, urlPattern 은 이름이 겹쳐서는 안됩니다.

- **http 요청 메세지를 모두 눈으로 보고 싶을 때**

→ main>resources>application.properties

`logging.level.org.apache.coyote.http11=debug` 를 작성합니다.

- 이걸 운영서버에 모든 요청정보를 남기면 성능저하가 발생하므로 개발단계에서만 적용해야 합니다.

### 서블릿 동작방식

![Untitled (21)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/36799b33-abe1-46ff-99a0-831e2a112dbc)

스프링부트 실행 → 내장 톰캣서버를 띄워줍니다 → 톰캣 서버는 내부에 서블릿 컨테이너를 내장하고 있으므로, 서블릿을 모두 생성해줍니다.

→ `helloServlet` 생성

→HTTP 요청 시 Request 객체를 만들어서 서버 단에 던져줍니다. 

→ Response 객체를 만들어서 서버가 톰캣에 던지면 톰캣에서 브라우저에 던져줍니다.

![Untitled (22)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/cdf54b7b-babe-4236-a15b-18e57755fb0a)

**참고**

 http 응답에서 `Content-length` 는 웹 애플리케이션 서버가 자동으로 생성해줍니다.

## II. HttpServletRequest-개요

- http 요청 메시지를 매번 파싱해 사용하면 불편하기에 서블릿 기능 사용합니다.

→ HttpServletRequest 사용하면 http 요청 메세지 편리 조회할 수 있습니다.

→ 더불어 HTTP 요청 메시지 파싱 결과를 `HttpServletRequest` 객체에 담아서 제공하게 됩니다.

- httpServletRequest
    - 임시저장소 기능도 제공합니다. getAttribute로 값을 가져오고 setAttribute로 값을 저장할 수 있습니다.
        - 저장 : `request.setAttribute(name, value)`
        - 조회 : `request.getAttribute(name)`
    - 세션 관리 기능
        - `request.getSession(create:true)`
    
  ![Untitled (23)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/6fd57d7d-5c0b-4a8b-9396-af4794a53756)
    
    → 다음과 같이 HTTP 요청 메시지를 편리하게 조회할 수 있습니다.
    

- HttpServletRequst, HttpServlet Response를 사용하면서 **중요한 건 http 요청 메세지, http 응답 메세지 편리하게 사용하도록 도와주는 객체라는 점입니다.**
    
    → **http 스펙 메세지 자체를 이해하는게 중요**
    

## III. HttpServletRequest 기본 사용법

### (1) start-line 정보

`[localhost:8080/request-header](http://localhost:8080/request-header)` 에 접속하게 되면 나오는 정보에 대해 알아봅시다.

```java
package hello.servlet.basic.request;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Enumeration;

@WebServlet(name = "requestHeaderServlet", urlPatterns = "/request-header")
public class RequestHeaderServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //http 요청 메시지 첫 라인에 나오는 정보 가져오기
        printStartLine(request);
       
    }

    private static void printStartLine(HttpServletRequest request) {
        System.out.println("--- REQUEST-LINE - start ---");
        System.out.println("request.getMethod() = " + request.getMethod()); //GET
        System.out.println("request.getProtocol() = " + request.getProtocol()); //

				//http
        System.out.println("request.getScheme() = " + request.getScheme()); //http
       
				// http://localhost:8080/request-header
        System.out.println("request.getRequestURL() = " + request.getRequestURL());
        
				// '/request-header'
        System.out.println("request.getRequestURI() = " + request.getRequestURI());
       
			 //username=hi
        System.out.println("request.getQueryString() = " +
                request.getQueryString());
       
				//https사용 유무
				System.out.println("request.isSecure() = " + request.isSecure());
        
        System.out.println("--- REQUEST-LINE - end ---");
        System.out.println();
    }

   
    
}
```

![Untitled (24)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/61cc2286-9d81-44de-ac14-b3d3943c46fe)

### (2) 헤더의 모든 정보를 출력하고자 할때

```java
package hello.servlet.basic.request;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Enumeration;

@WebServlet(name = "requestHeaderServlet", urlPatterns = "/request-header")
public class RequestHeaderServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
       
        printHeaders(request);
        //http 요청 헤더 정보 모두 출력
    

    //Header 모든 정보 출력
    private void printHeaders(HttpServletRequest request) {
        System.out.println("--- Headers - start ---");

/*
        //헤더정보 가져오는 방법 1
        Enumeration<String> headerNames = request.getHeaderNames();
         while (headerNames.hasMoreElements()) {
         String headerName = headerNames.nextElement();
         System.out.println(headerName + ": " + request.getHeader(headerName));
         //값 출력

         }
*/

        //헤더 정보 가져오는 방법 2
        request.getHeaderNames()
                .asIterator()
                .forEachRemaining(headerName ->
                        System.out.println(headerName + ":" + request.getHeader(headerName)));
                        System.out.println("--- Headers - end ---");
        System.out.println();
    }

    
}
```
![Untitled (25)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/bb62028d-a6da-4ad7-b312-02696eda56e8)

### (3) Header 편리 기능을 조회할때

```java
package hello.servlet.basic.request;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Enumeration;

@WebServlet(name = "requestHeaderServlet", urlPatterns = "/request-header")
public class RequestHeaderServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
      
        printHeaderUtils(request);
        //http 요청 헤더 편의 정보
    }
    //Header 편리한 조회
    private void printHeaderUtils(HttpServletRequest request) {
        System.out.println("--- Header 편의 조회 start ---");
        System.out.println("[Host 편의 조회]");
        System.out.println("request.getServerName() = " +
                request.getServerName()); //Host 헤더
        System.out.println("request.getServerPort() = " +
                request.getServerPort()); //Host 포트
        System.out.println();
        System.out.println("[Accept-Language 편의 조회]");
        request.getLocales().asIterator()
                .forEachRemaining(locale -> System.out.println("locale = " +
                        locale));
        System.out.println("request.getLocale() = " + request.getLocale());
        System.out.println();
        System.out.println("[cookie 편의 조회]");
        if (request.getCookies() != null) {
            for (Cookie cookie : request.getCookies()) {
                System.out.println(cookie.getName() + ": " + cookie.getValue());
            }
        }
        System.out.println();
        System.out.println("[Content 편의 조회]");
        System.out.println("request.getContentType() = " +
                request.getContentType());
        System.out.println("request.getContentLength() = " +
                request.getContentLength());
        System.out.println("request.getCharacterEncoding() = " +
                request.getCharacterEncoding());
        System.out.println("--- Header 편의 조회 end ---");
        System.out.println();
    }

    
}
```

![Untitled (26)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/f2039a26-b7ab-4aac-b10f-f7c46479f72d)

- 언어 세팅하는 웹 브라우저에서 locale에서 제일 위에 있는게 가져올 수 있습니다. `request.getLocale()`
- 쿠키 정보도 넘어오게 됩니다. http 헤더에 담깁니다.

### (4) Header 기타 정보를 조회하고자 할때

```java
package hello.servlet.basic.request;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Enumeration;

@WebServlet(name = "requestHeaderServlet", urlPatterns = "/request-header")
public class RequestHeaderServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        
        printEtc(request);
    }
    //기타 정보
    private void printEtc(HttpServletRequest request) {
        System.out.println("--- 기타 조회 start ---");
        System.out.println("[Remote 정보]");
        System.out.println("request.getRemoteHost() = " +
                request.getRemoteHost()); //
        System.out.println("request.getRemoteAddr() = " +
                request.getRemoteAddr()); //
        System.out.println("request.getRemotePort() = " +
                request.getRemotePort()); //
        System.out.println();
        System.out.println("[Local 정보]"); //내 서버 정보를 보여줍니다.
        System.out.println("request.getLocalName() = " +
                request.getLocalName()); //
        System.out.println("request.getLocalAddr() = " +
                request.getLocalAddr()); //
        System.out.println("request.getLocalPort() = " +
                request.getLocalPort()); //
        System.out.println("--- 기타 조회 end ---");
        System.out.println();
    }
}
```

![Untitled (27)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/af8de7c4-d091-489c-8f4e-1727db10c17c)
실제 데이터 정보 조회하는 방법을 알아보겠습니다.

## III. HTTP 요청 데이터 - 개요

크게 3가지가 있고 이것만 알면 됩니다.

### (1) Get방식의 쿼리 파라미터

- 쿼리 파라미터로 **정보**를 전달합니다.
- ex. /url?username=hello&age=20
    
    → 검색, 필터, 페이징 등에서 많이 사용하는 방식입니다.
    

### (2) Post- HTML Form

- `Content-type` : body에 대한 설명으로 어떤 데이터인지 설명하는 용도로 사용됩니다.
- 메세지 바디에 쿼리 파라미터 형식으로 전달합니다. 쿼리파라미터와 유사한 방식으로 전달하게 됩니다.

ex. 회원가입, 상품주문 등 사용

### (3) HTTP message body

- 메세지 바디에 데이터를 직접 담아 요청하는 방법입니다.
- `HTTP API` 에서 주로 사용하며 데이터 형식은 주로 `JSON`을 사용하게 됩니다,
- `POST/PUT/PATCH` 방식이 있습니다.

하나씩 알아봅니다.

### (1) HTTP 요청 데이터 중 GET 쿼리 파라미터

- 메세지 바디 없이 **URL의 쿼리파라미터를 사용해 데이터를 전달**합니다.
    
    `?` 를 시작으로 추가 파라미터들은 `&` 로 구분합니다.
    

- `HttpServletRequest` 가 제공해주는 메서드를 사용하여 쿼리 파라미터를 편리하게 조회할 수 있습니다.

![Untitled (28)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/4dd2004d-59b0-42b6-93a7-10a59b939e2b)

```java
package hello.servlet.basic.request;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
/*
* 1. 파라미터 전송 기능 확인
* http://localhost:8080/request-param?username=hello&age=20
* */

@WebServlet(name = "requestParamServlet", urlPatterns = "/request-param")
public class RequestParamServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("[전체 파라미터 조회-start]");
        req
                .getParameterNames()
                .asIterator()
                .forEachRemaining(paramName->
                        System.out.println(paramName +" = " + req.getParameter(paramName)));
        System.out.println("[전체 파라미터 조회-end]");
        System.out.println();

        System.out.println("[단일 파라미터 조회]");
        String username = req.getParameter("username");
        String age = req.getParameter("age");

        System.out.println("username = " + username);
        System.out.println("age = " + age);
        System.out.println();

        System.out.println("[이름이 같은 복수 파라미터 조회]");
        String[] usernames = req.getParameterValues("username");
        for (String s : usernames) {
            System.out.println("s = " + s);

        }

        resp.getWriter().write("ok");
    }
}
```

- 복수 파라미터의 경우 단일 파라미터 조회 방법

: `username=hello&username=kim` 처럼 실무에서는 거의 사용되진 않지만, 파라미터 이름이 중복되는 경우엔 `request.getParamerter()` 를 사용하게 되면 `request.getParameterValues()` 의 첫번째 값을 반환하게 됩니다.

또한, `request.getParameter()` 는 하나의 파라미터에 대해 하나의 값만 있을 때 사용해야 합니다.

### (2) Post- HTML Form

- request.getParam() 메서드

get방식의 url 쿼리파라미터 형식과 post html form 형식 모두 지원한다. 따라서 파라미터 값을 가져올 수 있습니다.

- content-type 자체가 존재하지 않습니다(get방식의 url 쿼리 파라미터 형식)
- post html form 의 경우에는 무조건 conent-type을 작성해야합니다.

[포스트맨으로 테스트하는 경우]

![Untitled (29)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/c8a2555d-4f6e-4504-ba67-f807e232bbf6)

![Untitled (30)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/4445d72a-3de6-4c90-abdf-56495283a994)

### (3) HTTP 요청 데이터 - API 메세지 바디- 단순 텍스트

- 데이터를 직접 담아서 요청하는 방법
- 데이터 형식은 주로 JSON을 사용하고 있습니다.
- POST/PUT/PATCH에서 주로 사용됩니다.

- `getInputStream()` 으로 내용을 확인해볼 수 있습니다.

다음의 예시는 text 타입으로 데이터를 주고 받는 경우입니다.

### (3) HTTP 요청 데이터 - API 메세지 바디- JSON

- content-type : `application/json`  형식이어야 합니다.
- Body 타입을 raw-JSON 선택하고 JSON으로 바디 요청을 보내면 다음과 같습니다.

![Untitled (31)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/17ca099a-10a0-41fe-8264-66e2ec204b7d)

[Object Mapper를 사용하는 경우]

- json 결과를 파싱해서 사용하려는 자바 객체로 변환하려면 Jackson, Gson 같은 JSON 변환 라이브러리를 추가해서 사용해야 합니다.

```java
package hello.servlet.basic.request;

import com.fasterxml.jackson.databind.ObjectMapper;
import hello.servlet.basic.HelloData;
import org.springframework.util.StreamUtils;

import javax.servlet.ServletException;
import javax.servlet.ServletInputStream;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.nio.charset.StandardCharsets;

@WebServlet(name = "requestBodyJsonServlet", urlPatterns = "/request-body-json")
public class RequestBodyJsonServlet extends HttpServlet {

    private ObjectMapper objectMapper = new ObjectMapper();

    @Override
    protected void service(HttpServletRequest request, HttpServletResponse
            response)
            throws ServletException, IOException {

        ServletInputStream inputStream = request.getInputStream();
        String s = StreamUtils.copyToString(inputStream, StandardCharsets.UTF_8);
        //데이터를 인코딩으로 읽어옵니다.

        System.out.println("messageBody = " + s);

        HelloData helloData = objectMapper.readValue(s, HelloData.class);

        System.out.println("helloData.getUsername() = " + helloData.getUsername());
        System.out.println("helloData.getAge() = " + helloData.getAge());

        response.getWriter().write("ok");

    }
    }
```

## HttpServletResponse-  기본 사용법

- Http응답 메세지를 생성할 수 있습니다.
    - Http 응답 코드 지정/헤더 생성/바디 생성을 모두 수행할 수 있습니다.

강의 예제로 들었던 [`http://localhost:8080/response-header`](http://localhost:8080/response-header) 로 방문하게 되면 메세지 바디와 함께 설정한 헤더 정보를 확인할 수 있습니다.

```java
package hello.servlet.basic.response;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

@WebServlet(name="responseHeaderServlet", urlPatterns = "/response-header")
public class ResponseHeaderServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //응답코드 세팅 [status-line]
        resp.setStatus(HttpServletResponse.SC_OK);

        //[response-header] 세팅
        resp.setHeader("Content-Type","text/plain;charset=utf-8");
        resp.setHeader("Cache-Control", "no-cache, no-store, must-revalidate");
        resp.setHeader("Pragma", "no-cache");
        //위 두 줄은 캐시 초기화

        //[header 편의 메서드]
//        cookie(resp);
        redirect(resp);

        resp.setHeader("my-header", "hello");

        //메세지 바디
        PrintWriter writer = resp.getWriter();
        writer.println("안녕하세요"); //원하는 값을 넣으면 메세지 바디에 넣어진다.
    }

    private void cookie(HttpServletResponse resp){
        //쿠키 편의 메서드
        Cookie cookie = new Cookie("myCookie", "good");
        cookie.setMaxAge(600);
        resp.addCookie(cookie);
    }

    private void redirect(HttpServletResponse resp) throws IOException{
        //Status Code : 302
        //Location : /basic/hello-form.html

//        resp.setStatus(HttpServletResponse.SC_FOUND); //302
//        resp.setHeader("Location", "/basic/hello-form.html");

        resp.sendRedirect("/basic/hello-form.html");
    }
}
```

![Untitled (32)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/e8784a75-b8cd-409e-9937-bec4d254322e)

### (1) Http 응답 데이터

- 텍스트 응답/Html 응답/ Http API 응답 방법 3가지가 있습니다.

단순 텍스트 응답 데이터 같은 경우는 위에서 알아봤던 `writer.println("ok")` 가 해당됩니다. 

**[Html 응답]**

```java
package hello.servlet.basic.response;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

@WebServlet(name = "responseHtmlServlet", urlPatterns = "/response-html")
public class ResponseHtmlServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //content-type 먼저 설정
        //content-type : text/html;charset=utf-8
        resp.setContentType("text/html");
        resp.setCharacterEncoding("utf-8");

        PrintWriter writer = resp.getWriter();
        writer.print("<html>");
        writer.print("<body>");
        writer.print("  <div>안녕</div>");
        writer.print("</body>");
        writer.print("</html>");
    }
}
```

HTTP 응답으로 html 반환할 경우 `content-type:text/html` 로 지정을 해야 합니다.

![Untitled (33)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/934ee1ce-567c-4cfb-ade8-14b772982b29)

**[JSON 응답]**

```java
package hello.servlet.basic.response;

import com.fasterxml.jackson.databind.ObjectMapper;
import hello.servlet.basic.HelloData;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet(name = "responseJsonServlet", urlPatterns = "/response-json")
public class ResponseJsonServlet extends HttpServlet {

    private ObjectMapper objectMapper = new ObjectMapper();

    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //content-type : application/json

        resp.setContentType("application/json");
        resp.setCharacterEncoding("utf-8");

        HelloData helloData = new HelloData();
        helloData.setUsername("kim");
        helloData.setAge(20);

        //{"username":"kim", "age":20}
        //이렇게 바꾸려면 ObjectMapper 필요
        String result = objectMapper.writeValueAsString(helloData);
        resp.getWriter().write(result);

    }
}
```

![Untitled (34)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/450f4594-62e6-45e8-968c-583d0bd04f2f)



## 섹션 3

## I. 회원관리 웹 애플리케이션 요구사항

- 회원정보(이름 `username` , 나이 `age` )
- 기능요구사항(회원저장 , 회원 목록 조회)

- Member
    
    ```java
    package hello.servlet.domain.member;
    
    import lombok.Getter;
    import lombok.Setter;
    
    @Getter @Setter
    public class Member {
    
        private Long id;
        private String username;
        private int age;
    
        public Member(){
        }
        public Member(String username, int age) {
            this.username = username;
            this.age = age;
        }
    }
    ```
    

- MemberRepository
    
    ```java
    package hello.servlet.domain.member;
    
    import java.util.ArrayList;
    import java.util.HashMap;
    import java.util.List;
    import java.util.Map;
    
    public class MemberRepository {
        /*
         Map 사용시 동시성 문제가 발생할 수 있어서 실무에서는
         ConcurrentHashMap, Atomic Long 사용을 고려해야 한다.
        */
        private static Map<Long, Member> store = new HashMap<>();
        private static long sequence = 0L;
    
        //싱글톤 생성, 생성자로 막아주어야 한다.
        private static final MemberRepository instance = new MemberRepository();
    
        public static MemberRepository getInstance(){
            return instance;
        }
    
        private MemberRepository(){
    
        }
    
        public Member save(Member member){
            member.setId(++sequence);
            store.put(member.getId(), member);
            return member;
        }
    
        public Member findById(Long id){
            return store.get(id);
        }
    
        public List<Member> findAll(){
            return new ArrayList<>(store.values());
        }
    
        public void clearStore(){
            store.clear();
        }
    }
    ```
    

- 스프링은 기본적으로 싱글톤 패턴을 사용하지만, 스프링 없이 MVC패턴을 서블릿과 JSP로 구현하고자 하므로, `private` 예약어를 사용해 `MemberRepository` 접근을 제한합니다.

- MemberRepositoryTest
    
    ```java
    package hello.servlet.domain;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import org.junit.jupiter.api.BeforeEach;
    import org.junit.jupiter.api.Test;
    
    import java.util.List;
    
    import static org.assertj.core.api.Assertions.*;
    
    class MemberRepositoryTest {
        //junit5부터는 public 없어도 된다.
    
        MemberRepository memberRepository = MemberRepository.getInstance();
        //스프링 자체가 싱글톤이므로 나중에는 싱글톤을 쓸 필요가 없다.
    
        @BeforeEach
        void before(){
            memberRepository.clearStore();
        }
    
        @Test
        void save(){
            //given
            Member member = new Member("hello", 20);
    
            //when
            Member savedMember = memberRepository.save(member);
    
            //then
            Member findMember = memberRepository.findById(savedMember.getId());
            assertThat(findMember).isEqualTo(savedMember);
    
        }
    
        @Test
        void findAll(){
            //given
            Member member1 = new Member("member1", 20);
            Member member2 = new Member("member2", 30);
    
            memberRepository.save(member1);
            memberRepository.save(member2);
    
            //when
            List<Member> list = memberRepository.findAll();
    
            //then
            assertThat(list.size()).isEqualTo(2);
            assertThat(list).contains(member1, member2);
        }
    
    }
    ```
    

## II. 서블릿으로 회원 관리 웹 애플리케이션 만들기(MVC구현)

### (1) 회원 저장 폼에 대한 응답을 처리하는 서블릿(`MemberFormServlet`)

- MemberFormServlet
    
    ```java
    package hello.servlet.web.servlet;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.io.PrintWriter;
    
    @WebServlet(name="memberFormServlet", urlPatterns = "/servlet/members/new-form")
    public class MemberFormServlet extends HttpServlet {
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            resp.setContentType("text/html");
            resp.setCharacterEncoding("utf-8");
            PrintWriter w = resp.getWriter();
    
            w.write("<!DOCTYPE html>\n" +
                    "<html>\n" +
                    "<head>\n" +
                    " <meta charset=\"UTF-8\">\n" +
                    " <title>Title</title>\n" +
                    "</head>\n" +
                    "<body>\n" +
                    "<form action=\"/servlet/members/save\" method=\"post\">\n" +
                    " username: <input type=\"text\" name=\"username\" />\n" +
                    " age: <input type=\"text\" name=\"age\" />\n" +
                    " <button type=\"submit\">전송</button>\n" +
                    "</form>\n" +
                    "</body>\n" +
                    "</html>\n");
        }
    }
    ```
    
    - Content-Type : `text/html` , CharacterEncoding : `utf-8` 로 response 응답 객체로 설정합니다.
    
- **[서블릿의 동작원리 중 PrintWriter 정체]**
    
    클라이언트로부터 Servlet으로 요청이 들어오면, 요청(Request) 파악 후 응답(Response)을 전달합니다.
    
    Servlet으로 들어온 요청은 텍스트 즉, HTML 형태의 응답으로 표현할 수 있는데 이는 `PrintWriter w = resp.getWriter()` 로 객체를 생성하여 HTML 표현이 가능합니다.
    
    ```java
    PrintWriter w = resp.getWriter();
    ```
    
    이 코드에서 보는 것 처럼, HttpServletResponse 인터페이스인 getWriter()를 호출하고 있습니다. 
    
    PrintWriter 클래스는, 바이트를 문자의 형태를 가지는 객체로 바꾸는 역할을 합니다. 따라서 클라이언트에 대한 응답으로 텍스트를 제공하고 싶다면, PrinterWriter 클래스 객체를 정의하고 getWriter()를 통하여 인스턴스를 얻어오면 됩니다.
    
    **요약**
    
    - Servlet에서 클라이언트 요청에 대한 응답 형태는 문자 또는 바이트가 될 수 있다는 것
    - HttpServletResponse 인터페이스의 상위 인터페이스인 ServletResponse의 getWriter()메소드로 인스턴스를 생성해야만, 응답 페이지에 HTML을 그리는 것이 가능하다.

### (2) 회원 저장 폼에 대한 요청과 응답을 처리하는 서블릿(`MemberSaveServlet`)

- MemberSaveServlet
    
    ```java
    package hello.servlet.web.servlet;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.io.PrintWriter;
    
    @WebServlet(name="memberSaveServlet", urlPatterns = "/servlet/members/save")
    public class MemberSaveServlet extends HttpServlet {
    
        private MemberRepository memberRepository = MemberRepository.getInstance();
    
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            System.out.println("MemberSaveServlet.service");
            String username = req.getParameter("username");
            int age = Integer.parseInt(req.getParameter("age"));
    
            /*
            * get 요청의 url parameter 이든, http 데이터의 Form post 방식이든,
            * 해당 key와 value를 가져오려면 request.getParameter(key명)으로 가져온다.
            *
            * request.getParameter() 결과는 항상 문자열
            * */
    
            //회원 저장
            Member member = new Member(username, age);
            memberRepository.save(member);
    
            //결과 응답을 html코드로 내려본다
            resp.setContentType("text/html");
            resp.setCharacterEncoding("utf-8");
            PrintWriter w = resp.getWriter();
    
            //해당 html은 동적(중간에 프로그램 코드가 들어가기 때문)
            w.write("<html>\n" +
                    "<head>\n" +
                    " <meta charset=\"UTF-8\">\n" +
                    "</head>\n" +
                    "<body>\n" +
                    "성공\n" +
                    "<ul>\n" +
                    " <li>id="+member.getId()+"</li>\n" +
                    " <li>username="+member.getUsername()+"</li>\n" +
                    " <li>age="+member.getAge()+"</li>\n" +
                    "</ul>\n" +
                    "<a href=\"/index.html\">메인</a>\n" +
                    "</body>\n" +
                    "</html>");
    
        }
    }
    ```
    
![Untitled (37)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/13dbd4cf-3055-4e74-a0d2-ad331cb467cf)

- html Form으로 작성한 결과를 어떻게 `req.getParameter()` 로 받을 수 있는 것인지??

Post방식의 HTML Form이든, Get요청의 URL Params 든, 두 가지 방법 모두 `req.getParameter()` 로 키 값에 대한 value를 받아올 수 있다.

```java
 String username = req.getParameter("username");
int age = Integer.parseInt(req.getParameter("age"));
```

### (3) 회원 목록 페이지에 대한 요청과 응답을 처리하는 서블릿(`MemberListServlet`)

- MemberListServlet
    
    ```java
    package hello.servlet.web.servlet;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.io.PrintWriter;
    import java.util.List;
    
    @WebServlet(name = "memberListServlet", urlPatterns = "/servlet/members")
    public class MemberListServlet extends HttpServlet {
        private MemberRepository memberRepository = MemberRepository.getInstance();
    
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            List<Member> members = memberRepository.findAll();
    
            //응답 html을 만드는 방법(저장된 회원 목록 조회)
            resp.setContentType("text/html");
            resp.setCharacterEncoding("utf-8");
    
            PrintWriter w = resp.getWriter();
    
            w.write("<html>");
            w.write("<head>");
            w.write(" <meta charset=\"UTF-8\">");
            w.write(" <title>Title</title>");
            w.write("</head>");
            w.write("<body>");
            w.write("<a href=\"/index.html\">메인</a>");
            w.write("<table>");
            w.write(" <thead>");
            w.write(" <th>id</th>");
            w.write(" <th>username</th>");
            w.write(" <th>age</th>");
            w.write(" </thead>");
            w.write(" <tbody>");
    /*
    정적 html이 작성되게 된다.
     w.write(" <tr>");
     w.write(" <td>1</td>");
     w.write(" <td>userA</td>");
     w.write(" <td>10</td>");
     w.write(" </tr>");
    
     동적으로 돌리는 방법은 멤버 리스트를 하나씩 꺼내와서 html태그로 묶는 방법이다.
    */
            for (Member member : members) {
                w.write(" <tr>");
                w.write(" <td>" + member.getId() + "</td>");
                w.write(" <td>" + member.getUsername() + "</td>");
                w.write(" <td>" + member.getAge() + "</td>");
                w.write(" </tr>");
            }
            w.write(" </tbody>");
            w.write("</table>");
            w.write("</body>");
            w.write("</html>");
        }
    }
    ```
    

위의 (1)~(3) 으로 서블릿을 통하여 스프링 MVC를 모방해보았습니다. 서블릿만으로 뷰를 그려내고 자바 코드를 작성할 수 있다는 특징이 있으나,

복잡하고 비효율적입니다.

따라서 **HTML문서만 템플릿 엔진**에서 그려내도록 하고, **자바코드는 서브릿**에서 처리하도록 변경해봅니다.

- 템플릿엔진 종류

JSP, Thymeleaf, …

## III. JSP로 스프링 MVC 구현해내기

- 서블릿 / JSP / MVC패턴 에 이어 스프링까지의 페이지 확인할 수 있도록 페이지를 설정합니다.
- index.html
    
    ```java
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
    </head>
    <body>
    <ul>
        <li><a href="basic.html">서블릿 basic</a></li>
        <li>서블릿
            <ul>
                <li><a href="/servlet/members/new-form">회원가입</a></li>
                <li><a href="/servlet/members">회원목록</a></li>
            </ul>
        </li>
        <li>JSP
            <ul>
                <li><a href="/jsp/members/new-form.jsp">회원가입</a></li>
                <li><a href="/jsp/members.jsp">회원목록</a></li>
            </ul>
        </li>
        <li>서블릿 MVC
            <ul>
                <li><a href="/servlet-mvc/members/new-form">회원가입</a></li>
                <li><a href="/servlet-mvc/members">회원목록</a></li>
            </ul>
        </li>
        <li>FrontController - v1
            <ul>
                <li><a href="/front-controller/v1/members/new-form">회원가입</a></li>
                <li><a href="/front-controller/v1/members">회원목록</a></li>
            </ul>
        </li>
        <li>FrontController - v2
            <ul>
                <li><a href="/front-controller/v2/members/new-form">회원가입</a></li>
                <li><a href="/front-controller/v2/members">회원목록</a></li>
            </ul>
        </li>
        <li>FrontController - v3
            <ul>
                <li><a href="/front-controller/v3/members/new-form">회원가입</a></li>
                <li><a href="/front-controller/v3/members">회원목록</a></li>
            </ul>
        </li>
        <li>FrontController - v4
            <ul>
                <li><a href="/front-controller/v4/members/new-form">회원가입</a></li>
                <li><a href="/front-controller/v4/members">회원목록</a></li>
            </ul>
        </li>
        <li>FrontController - v5 - v3
            <ul>
                <li><a href="/front-controller/v5/v3/members/new-form">회원가입</a></
                li>
                <li><a href="/front-controller/v5/v3/members">회원목록</a></li>
            </ul>
        </li>
        <li>FrontController - v5 - v4
            <ul>
                <li><a href="/front-controller/v5/v4/members/new-form">회원가입</a></
                li>
                <li><a href="/front-controller/v5/v4/members">회원목록</a></li>
            </ul>
        </li>
        <li>SpringMVC - v1
            <ul>
                <li><a href="/springmvc/v1/members/new-form">회원가입</a></li>
                <li><a href="/springmvc/v1/members">회원목록</a></li>
            </ul>
        </li>
        <li>SpringMVC - v2
            <ul>
                <li><a href="/springmvc/v2/members/new-form">회원가입</a></li>
                <li><a href="/springmvc/v2/members">회원목록</a></li>
            </ul>
        </li>
        <li>SpringMVC - v3
            <ul>
                <li><a href="/springmvc/v3/members/new-form">회원가입</a></li>
                <li><a href="/springmvc/v3/members">회원목록</a></li>
            </ul>
        </li>
    </ul>
    </body>
    </html>
    ```
    

### (1) 회원 관리/회원 저장/회원 목록 웹 애플리케이션 생성

- `main/webapp/jsp/members/new-form.jsp`
    
    ```java
    <%@ page contentType="text/html;charset=UTF-8" language="java" %>
    <html>
    <head>
        <title>Title</title>
    </head>
    <body>
    <form action="/jsp/members/save.jsp" method="post">
        username: <input type="text" name="username" />
        age: <input type="text" name="age" />
        <button type="submit">전송</button>
    </form>
    </body>
    </html>
    ```
    
- `main/webapp/jsp/members/save.jsp`
    
    ```java
    <%@ page import="hello.servlet.domain.member.MemberRepository" %>
    <%@ page import="hello.servlet.domain.member.Member" %>
    <%@ page contentType="text/html;charset=UTF-8" language="java" %>
    <%
        //request, response는 자동으로 변환되므로 바로 그냥 사용 가능(지원)
        MemberRepository memberRepository = MemberRepository.getInstance();
        System.out.println("MemberSaveServlet.service");
        String username = request.getParameter("username");
        int age = Integer.parseInt(request.getParameter("age"));
    
        Member member = new Member(username, age);
        memberRepository.save(member);
    
    %>
    <html>
    <head>
        <title>Title</title>
    </head>
    <body>
    성공
    <ul>
        <li>id=<%=member.getId()%></li>
        <li>username=<%=member.getUsername()%></li>
         <li>age=<%=member.getAge()%></li>
    </ul>
    <a href="/index.html">메인</a>
    </body>
    </html>
    ```
    
- `main/webapp/jsp/members.jsp`
    
    ```java
    <%@ page import="java.util.List" %>
    <%@ page import="hello.servlet.domain.member.MemberRepository" %>
    <%@ page import="hello.servlet.domain.member.Member" %>
    
    <%@ page contentType="text/html;charset=UTF-8" language="java" %>
    <%
       MemberRepository memberRepository = MemberRepository.getInstance();
       List<Member> members = memberRepository.findAll();
    %>
    <html>
    <head>
     <meta charset="UTF-8">
     <title>Title</title>
    </head>
    <body>
    <a href="/index.html">메인</a>
    <table>
     <thead>
     <th>id</th>
     <th>username</th>
     <th>age</th>
     </thead>
     <tbody>
    <%
         for (Member member : members) {
             out.write(" <tr>");
             out.write(" <td>" + member.getId() + "</td>");
             out.write(" <td>" + member.getUsername() + "</td>");
             out.write(" <td>" + member.getAge() + "</td>");
             out.write(" </tr>");
     }
    %>
     </tbody>
    </table>
    </body>
    </html>
    ```
    

→ 앞서서 JSP에서 자바 코드와 뷰 영역을 표현해내는 것은 서블릿만으로 웹 애플리케이션을 구현해내는 것 만큼이나 복잡합니다. 

→ 비즈니스 로직(회원 저장), 레포지토리를 통해 데이터 조회 등을 수정하려면 JSP를 건드려야 하고 계속해서 노출되는 상황입니다.

## IV. MVC패턴

- 비즈니스 로직은 서블릿에, JSP는 HTML로 화면을 그리는 것에만 집중하도록 한 것이 MVC패턴입니다.
- 아래에 나오는 내용들은 서블릿과 JSP를 통해 직접 MVC패턴을 적용, 리팩터링하는 과정입니다.

### **[MVC패턴을 사용해야하는 경우]**

- 코드 그룹 중에 변경의 **라이프 사이클이 다른 경우**, 이들을 분리해서 각각 따로 하나의 코드로 관리해야 합니다. 왜냐하면 불필요한 부분에 대해서도 노출이 잦아지고 유지보수에도 어렵기 때문

- 업무에 따라 다른 코드가 사용되는 경우, 해당하는 코드들을 각각 분리해내야 합니다.

### **[그럼 MVC패턴이란]**

- 웹 애플리케이션은 보통 MVC패턴을 사용하고 있습니다.

구성은 컨트롤러/모델/뷰입니다.

- 컨트롤러
    - **HTTP 요청**을 받아서 파라미터를 검증하고, **비즈니스 로직을 실행**합니다.(Service를 호출한다는 말을 표현, service 계층에서 비즈니스 로직 실행)
    - 뷰에 전달할 결과 데이터를 조회해서 **모델에 담습니다.**
- 모델
    - 뷰에 출력할 데이터를 담아둡니다.
    - 뷰가 필요한 데이터를 모두 모델에 담아서 전달해주는 덕분에 **뷰는 비즈니스 로직이나 데이터 접근을 몰라도 되고, 화면을 렌더링 하는 일에 집중**할 수 있습니다.
- 뷰
    - 모델에 담겨있는 데이터를 사용해서 화면을 그리는 일에 집중합니다.
    

- MVC패턴을 사용하기 전과 후의 개략도
    - 전
        
        ![Untitled (35)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/cb605dc5-e7f3-40c1-a849-a58ffe504b03)
        
    
    - 후
        
       ![Untitled (36)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/5a45eba7-088f-47e9-a2e8-fe5da566f4e9)
        

## V. MVC 패턴을 적용(JSP를 뷰, 서블릿을 컨트롤러로 사용)

### (1) 회원 등록 폼 서블릿(컨트롤러), 회원 저장 서블릿, 회원 리스트 서블릿

- `MvcMemberFormServlet`
    
    ```java
    package hello.servlet.web.servletmvc;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    @WebServlet(name = "mvcMemberFormServlet", urlPatterns = "/servlet-mvc/members/new-form")
    public class MvcMemberFormServlet extends HttpServlet {
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            //jsp 경로 호출(제어권을 넘겨준다)
            String viewPath = "/WEB-INF/views/new-form.jsp";
            RequestDispatcher requestDispatcher = req.getRequestDispatcher(viewPath);
            requestDispatcher.forward(req, resp); 
    				// 다른 서블릿 or jsp로 이동할 수 있는 기능
            //서버 내부에서 다시 호출 발생한다.
    
            /*
            * 클라이언트 -> 서블릿 -> JSP(리다이렉트x) -> 클라이언트
            *
            * 컨트롤러 거쳐서 JSP를 호출하고 싶을 때는
            * [WEB-INF>폴더]에 넣어 호출,
            * 외부에서는 바로 호출 불가(항상 서블릿 거쳐서 forward로 호출해야 나온다.)
            *
            * mvc패턴은 항상 컨트롤러 거치고 뷰로 간다
            *
            * redirect : 실제 클라이언트에게 응답 가고, 리다이렉트 경로로 다시 요청
            * forward : 서블릿에서 JSP 호출해도 클라이언트가 인지하지 못한다.
            * */
    
        }
    }
    ```
    

**[사용된 메서드의 의미]**

- `dispatcher.forward()` - 서블릿에서 다른 서블릿 or JSP로 이동할 수 있는 기능입니다. 서버에서 재호출이 발생하며, 클라이언트는 이를 모릅니다.

- 경로 중 `/WEB-INF/`

```java
String viewPath = "/WEB-INF/views/new-form.jsp";
```

이 경로를 작성하게 되면, 외부에서 바로 해당 링크로 접속할 수 없습니다. 컨트롤러를 통해서만 해당 경로로 이동시킵니다.

(/WEB-INF/views/new-form.jsp 내용 생략)

- `MvcMemberSaveServlet`
    
    ```java
    package hello.servlet.web.servletmvc;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    @WebServlet(name = "mvcMemberSaveServlet", urlPatterns = "/servlet-mvc/members/save")
    public class MvcMemberSaveServlet extends HttpServlet {
        private MemberRepository memberRepository = MemberRepository.getInstance();
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            String username = req.getParameter("username");
            int age = Integer.parseInt(req.getParameter("age"));
            Member member = new Member(username, age);
            memberRepository.save(member);
            
            **//Model에 데이터를 보관한다.
            req.setAttribute("member", member);**
    
            String viewPath = "/WEB-INF/views/save-result.jsp";
            RequestDispatcher dispatcher = req.getRequestDispatcher(viewPath);
            //Servlet에서 JSP의 해당 경로로 넘어가겠다는 의미
            dispatcher.forward(req,resp);
        }
    }
    ```
    

- 위 코드에서 확인할 수 있듯이, HttpServletRequest을 모델로 활용했습니다.
- request내의 `setAttribute()` 로 request 객체에 데이터를 넣어 보관하며, 이를 뷰에 전달합니다.
- 뷰에서는 `getAttribute()` 로 데이터를 확인할 수 있습니다.

- MvcMemberListServlet
    
    ```java
    package hello.servlet.web.servletmvc;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.List;
    
    @WebServlet(name= "mvcMemberListServlet", urlPatterns = "/servlet-mvc/members")
    public class MvcMemberListServlet extends HttpServlet {
        private MemberRepository memberRepository = MemberRepository.getInstance();
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    
            List<Member> members = memberRepository.findAll();
            req.setAttribute("members",members); //model에 담는다.
    
            String viewPath = "/WEB-INF/views/members.jsp";
            RequestDispatcher dispatcher = req.getRequestDispatcher(viewPath);
            dispatcher.forward(req, resp);
    
        }
    }
    ```
    

## VI. MVC 패턴을 적용 후 한계(JSP를 뷰, 서블릿을 컨트롤러로 사용)

- V의 서블릿들 내용을 충실히 확인했다면 알 수 있는 내용은 다음과 같다.

→ 포워드의 중복이 발생합니다.

```java
RequestDispatcher dispatcher = request.getRequestDispatcher(viewPath);
dispatcher.forward(request, response);
```

매번 직접 메서드를 생성해서 호출해야한다는 중복이 발생합니다.

→ viewPath를 매번 prefix, suffix를 동일하게 설정해야 합니다.

```java
prefix : /WEB-INF/views/
sffix : .jsp
```

→ 서블릿 내용 중 어떤 서블릿은 HttpServletRequest, HttpServletResponse를 사용하지도 않습니다. 

- 서블릿을 매번 사용한다면 테스트 코드 작성도 어렵고 공통처리 또한 어렵습니다.

**⇒ 프론트 컨트롤러 패턴을 도입해 한번만 서블릿 코드를 작성하고 그 이외 컨트롤러들은 공통 인터페이스를 구현하는 형태로 작성해볼 수 있습니다.**

**⇒ 스프링 MVC핵심 또한 프론트 컨트롤러를 사용한다는 점에 주목해야 합니다.**






## 섹션 4

## I. 프론트 컨트롤러 패턴 소개

### (1) 프론트 컨트롤러 도입 전과 후 비교 그림

![Untitled (44)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/d640e6d8-6c81-4c74-837f-6c71a330edf3)

![Untitled (43)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/71166e93-6b5f-4b91-9b31-18f73958c4b3)

### (2) 프론트 컨트롤러 패턴이란?

각 클라이언트들은 Controller A, B, C 사용하기 위해 각각을 호출하는 것이 아니라, Front Controller에 요청을 보내고, FrontController에서 요청에 맞게 컨트롤러를 찾아 호출시켜주는 패턴을 말합니다.

공통코드에 대해 Front Controller 에서 처리 후, 다른 코드에 대해서만 각 Controller를 호출해 처리할 수 있도록 하는 패턴을 말합니다.

(3) 프론트 컨트롤러 패턴의 특징

- 프론트 컨트롤러 서블릿 하나로 클라이언트 요청을 모두 받아낸다는 점
- 프론트 컨트롤러에서 요청에 알맞는 컨트롤러를 호출해준다는 점
- 나머지 컨트롤러에서는 서블릿을 굳이 사용하지 않아도 된다는 점
- **공통 처리가 가능하다는 점**

## II. 프론트 컨트롤러 도입-Version.1

이전까지 사용했던 웹 애플리케이션을 리펙토링해봅시다.

### (1) Version 1의 구조

![Untitled (42)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/c7687f8f-6de0-4741-9994-bdba438b0978)

- ControllerV1
    
    ```java
    package hello.servlet.web.frontController.v1;
    
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    public interface ControllerV1 {
        void process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException;
        //service와 유사하게 작성
    }
    ```
    
- MemberFormControllerV1 - 회원등록 컨트롤러
    
    ```java
    package hello.servlet.web.frontController.v1.controller;
    
    import hello.servlet.web.frontController.v1.ControllerV1;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    public class MemberFormControllerV1 implements ControllerV1 {
    
        @Override
        public void process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            //jsp 경로 호출(제어권을 넘겨준다)
            String viewPath = "/WEB-INF/views/new-form.jsp";
            RequestDispatcher requestDispatcher = request.getRequestDispatcher(viewPath);
            requestDispatcher.forward(request, response); // 다른 서블릿 or jsp로 이동할 수 있는 기능
        }
    }
    ```
    

→ 구체 컨트롤러에서 바로 view 경로를 생성해서 `JSP forward`를 지정해줍니다.

- MemberSaveControllerV1 - 회원저장 컨트롤러
    
    ```java
    package hello.servlet.web.frontController.v1.controller;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.v1.ControllerV1;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    public class MemberSaveControllerV1 implements ControllerV1 {
        private MemberRepository memberRepository = MemberRepository.getInstance();
        @Override
        public void process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            String username = request.getParameter("username");
            int age = Integer.parseInt(request.getParameter("age"));
            Member member = new Member(username, age);
            memberRepository.save(member);
    
            //Model에 데이터를 보관한다.
            request.setAttribute("member", member);
    
            String viewPath = "/WEB-INF/views/save-result.jsp";
            RequestDispatcher dispatcher = request.getRequestDispatcher(viewPath);
            //Servlet에서 JSP의 해당 경로로 넘어가겠다는 의미
            dispatcher.forward(request,response);
        }
    }
    ```
    
- MemberListControllerV1- 회원 목록 컨트롤러
    
    ```java
    package hello.servlet.web.frontController.v1.controller;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.v1.ControllerV1;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.List;
    
    public class MemberListControllerV1 implements ControllerV1 {
        private MemberRepository memberRepository = MemberRepository.getInstance();
        @Override
        public void process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            List<Member> members = memberRepository.findAll();
            request.setAttribute("members",members); //model에 담는다.
    
            String viewPath = "/WEB-INF/views/members.jsp";
            RequestDispatcher dispatcher = request.getRequestDispatcher(viewPath);
            dispatcher.forward(request, response);
        }
    }
    ```
    
- FrontControllerServletV1 - 프론트 컨트롤러
    
    ```java
    package hello.servlet.web.frontController.v1;
    
    import hello.servlet.web.frontController.v1.controller.MemberFormControllerV1;
    import hello.servlet.web.frontController.v1.controller.MemberListControllerV1;
    import hello.servlet.web.frontController.v1.controller.MemberSaveControllerV1;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.HashMap;
    import java.util.Map;
    
    @WebServlet(name="frontControllerServletV1", urlPatterns = "/front-controller/v1/*")
    public class FrontControllerServletV1 extends HttpServlet {
        private Map<String, ControllerV1> controllerV1Map = new HashMap<>();
    
        public FrontControllerServletV1() {
            controllerV1Map.put("/front-controller/v1/members/new-form", new MemberFormControllerV1());
            controllerV1Map.put("/front-controller/v1/members/save", new MemberSaveControllerV1());
            controllerV1Map.put("/front-controller/v1/members", new MemberListControllerV1());
        }
    
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            System.out.println("FrontControllerServletV1.service");
    
            String requestURI = req.getRequestURI();
    
            ControllerV1 controller = controllerV1Map.get(requestURI);
    
            /*
            * URI 문자열을 받아와서 해당하는 컨트롤러를 호출한다.
            *
            * 다형성에 의해 인터페이스를 받을 수 있는 것이다.
            * */
    
            if(controller == null){
                resp.setStatus(HttpServletResponse.SC_NOT_FOUND);
                return;
            }
    
            controller.process(req, resp);
            //오버라이드 된 메서드가 호출된다.
    
        }
    }
    ```
    

- `urlPatters`

```java
@WebServlet(name="frontControllerServletV1", urlPatterns = "/front-controller/v1/*")
```

이렇게 작성되어있는데, 이는 해당 경로 하위의 모든 경로를 서블릿을 통해 해당 프론트 컨트롤러 서블릿과 연결된다는 의미입니다.

- `protected void service()`

```java
@Override
protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    System.out.println("FrontControllerServletV1.service");

    String requestURI = req.getRequestURI();

    ControllerV1 controller = controllerV1Map.get(requestURI);

    /*
    * URI 문자열을 받아와서 해당하는 컨트롤러를 호출한다.
    *
    * 다형성에 의해 인터페이스를 받을 수 있는 것이다.
    * */

    if(controller == null){
        resp.setStatus(HttpServletResponse.SC_NOT_FOUND);
        return;
    }

    controller.process(req, resp);
    //오버라이드 된 메서드가 호출된다.

}
```

URI를 가져오고 해당 경로에 맞는 v1 컨트롤러를 매칭시킵니다. 이후엔 인터페이스 오버라이딩 됐던 메서드 process를 호출하면 알맞는 로직이 수행되는 것을 확인할 수 있습니다.

## III. View의 분리-Version.2

### (1) 코드의 중복 발견

- 중복되는 코드
    
    `MemberFormController.java`
    
    ```java
    //jsp 경로 호출(제어권을 넘겨준다)
    String viewPath = "/WEB-INF/views/new-form.jsp";
    RequestDispatcher requestDispatcher = request.getRequestDispatcher(viewPath);
    requestDispatcher.forward(request, response); // 다른 서블릿 or jsp로 이동할 수 있는 기능
    ```
    
    `MemberSaveController.java`
    
    ```java
    String viewPath = "/WEB-INF/views/save-result.jsp";
    RequestDispatcher dispatcher = request.getRequestDispatcher(viewPath);
    //Servlet에서 JSP의 해당 경로로 넘어가겠다는 의미
    dispatcher.forward(request,response);
    ```
    
    `MemberListController.java`
    
    ```java
    String viewPath = "/WEB-INF/views/members.jsp";
    RequestDispatcher dispatcher = request.getRequestDispatcher(viewPath);
    dispatcher.forward(request, response);
    ```
    

컨트롤러 → 뷰 로 넘어가는 위의 코드부분이 매번 중복이 발생하고 깔끔하지 못하다는 v1의 단점입니다. 이를 별도로 뷰를 처리하는 객체를 만듭니다.

### (2) v2 구조

![Untitled (41)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/a5703e94-da34-4fc2-b9ae-cc06515a2145)

- MyView
    
    ```java
    package hello.servlet.web.frontController;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import javax.sql.rowset.serial.SerialException;
    import java.io.IOException;
    import java.util.Map;
    
    public class MyView {
        private String viewPath;
        public MyView(String viewPath){
            this.viewPath = viewPath;
        }
    
        public void render(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {
            RequestDispatcher dispatcher = request.getRequestDispatcher(viewPath);
            dispatcher.forward(request, response);
        }
    }
    ```
    

같은 코드가 반복되는 이 부분을 MyView라는 뷰 처리 클래스에 따로 보관하고 호출되면 자동으로 특정 JSP를 호출하도록 리펙토링되었습니다.

```java
RequestDispatcher dispatcher = request.getRequestDispatcher(viewPath);
//Servlet에서 JSP의 해당 경로로 넘어가겠다는 의미
dispatcher.forward(request,response);
```

- ControllerV2
    
    ```java
    package hello.servlet.web.frontController.v2;
    
    import hello.servlet.web.frontController.MyView;
    
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    public interface ControllerV2 {
        MyView process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException;
        //service와 유사하게 작성
    }
    ```
    

→ v1과 달리진 점 : 반환타입이 void에서 MyView로 바뀌었다는 점

- MemberFormControllerV2 - 회원등록폼
    
    ```java
    package hello.servlet.web.frontController.v2.controller;
    
    import hello.servlet.web.frontController.MyView;
    import hello.servlet.web.frontController.v2.ControllerV2;
    
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    public class MemberFormControllerV2 implements ControllerV2 {
        @Override
        public MyView process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
          return  new MyView("/WEB-INF/views/new-form.jsp");
        }
    }
    ```
    
- MemberSaveControllerV2- 회원저장
    
    ```java
    package hello.servlet.web.frontController.v2.controller;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.MyView;
    import hello.servlet.web.frontController.v2.ControllerV2;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    public class MemberSaveControllerV2 implements ControllerV2 {
        private MemberRepository memberRepository = MemberRepository.getInstance();
        @Override
        public MyView process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            String username = request.getParameter("username");
            int age = Integer.parseInt(request.getParameter("age"));
            Member member = new Member(username, age);
            memberRepository.save(member);
    
            //Model에 데이터를 보관한다.
            request.setAttribute("member", member);
    
            return new MyView("/WEB-INF/views/save-result.jsp");
        }
    }
    ```
    
- MemberListControllerV2- 회원목록
    
    ```java
    package hello.servlet.web.frontController.v2.controller;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.MyView;
    import hello.servlet.web.frontController.v2.ControllerV2;
    
    import javax.servlet.RequestDispatcher;
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.List;
    
    public class MemberListControllerV2 implements ControllerV2 {
        private MemberRepository memberRepository = MemberRepository.getInstance();
        @Override
        public MyView process(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            List<Member> members = memberRepository.findAll();
            request.setAttribute("members",members); //model에 담는다.
    
            return new MyView("/WEB-INF/views/members.jsp");
        }
    }
    ```
    

→ v1과 달라진 점 : `dispatcher.forward()` 호출은 MyView에 책임을 넘기고 오직 view 경로만 생성해서 MyView를 반환한다는 점

- FrontControllerV2
    
    ```java
    package hello.servlet.web.frontController.v2;
    
    import hello.servlet.web.frontController.MyView;
    import hello.servlet.web.frontController.v2.controller.MemberFormControllerV2;
    import hello.servlet.web.frontController.v2.controller.MemberListControllerV2;
    import hello.servlet.web.frontController.v2.controller.MemberSaveControllerV2;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.HashMap;
    import java.util.Map;
    
    @WebServlet(name="frontControllerServletV2", urlPatterns = "/front-controller/v2/*")
    public class FrontControllerServletV2 extends HttpServlet {
        private Map<String, ControllerV2> controllerV2Map = new HashMap<>();
    
        public FrontControllerServletV2() {
            controllerV2Map.put("/front-controller/v2/members/new-form", new MemberFormControllerV2());
            controllerV2Map.put("/front-controller/v2/members/save", new MemberSaveControllerV2());
            controllerV2Map.put("/front-controller/v2/members", new MemberListControllerV2());
        }
    
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            System.out.println("FrontControllerServletV2.service");
    
            String requestURI = req.getRequestURI();
    
            ControllerV2 controller = controllerV2Map.get(requestURI);
    
            /*
             * URI 문자열을 받아와서 해당하는 컨트롤러를 호출한다.
             *
             * 다형성에 의해 인터페이스를 받을 수 있는 것이다.
             * */
    
            if(controller == null){
                resp.setStatus(HttpServletResponse.SC_NOT_FOUND);
                return;
            }
    
            MyView view = controller.process(req, resp);
            view.render(req, resp);
    
        }
    }
    ```
    

→ v1와 달라진 점 : JSP를 dispatcher하는 MyView가 사용됬다는 점 + MyView 클래스에 `render()` 호출부가 생성되어 이를 호출하기만 하면 된다는 점

## IV. Model의 분리-Version.3

### (1) Version2의 문제점

- 서블릿 종속성이 존재합니다.

v2의 구체 컨트롤러 코드에는 `HttpServletRequest, HttpServletResponse` 가 들어가 있습니다. 사용하지 않는데 계속 포함되어있어서 문제가 됩니다

**v3에서의 해결방법**

→ 가끔 사용할 때도 있지만 서블릿 요청으로 온 파라미터 정보(username, age)를 저장하고 목록을 보여주기 위해 쓰입니다. 따라서, `Map` 만 넘겨주도록 하고 해당 중복을 제거해야 합니다. 

→ 서블릿 종속성을 없애면 당연히 `request, response` 도 없어지기 때문에, 데이터 정보를 담는 `Model` 객체를 만들어서 사용하도록 하면 됩니다.

- 뷰 경로(이름)이 중복되고 있습니다.

```java
return  new MyView("/WEB-INF/views/new-form.jsp"); 
return new MyView("/WEB-INF/views/save-result.jsp");
return new MyView("/WEB-INF/views/members.jsp");
```

**v3에서의 해결방법**

→ 컨트롤러에서 논리이름만 반환하고 나머지 물리 위치는 프론트컨트롤러에서 해결합니다.

### (2) Version3 구조

![Untitled (40)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/be68a1a3-db64-4ecf-baff-49b70c18c7b7)

- 이 구조의 특징

서블릿 종속성 제거를 위해 ModelView라는 데이터를 담는 객체를 사용합니다.

- ModelView
    
    ```java
    package hello.servlet.web.frontController;
    
    import java.util.HashMap;
    import java.util.Map;
    
    public class ModelView {
        private String viewName; //뷰의 논리적 이름
        private Map<String, Object> model = new HashMap<>(); //데이터를 담을 모델
    
        public ModelView(String viewName) {
            this.viewName = viewName;
        }
    
        public String getViewName() {
            return viewName;
        }
    
        public void setViewName(String viewName) {
            this.viewName = viewName;
        }
    
        public Map<String, Object> getModel() {
            return model;
        }
    
        public void setModel(Map<String, Object> model) {
            this.model = model;
        }
    } 
    ```
    
- ControllerV3
    
    ```java
    package hello.servlet.web.frontController.v3;
    
    import hello.servlet.web.frontController.ModelView;
    
    import java.util.Map;
    
    public interface ControllerV3 {
        ModelView process(Map<String, String> paramMap);
        //v2랑 비교해보면 서블릿에 종속적이지 않다는 점이 특징
    }
    ```
    

→ v2와 달라진 점 : v2에서는 물리위치까지 전달하는 MyView가 반환되었다면,  v3에서는 서블릿 종속성을 없애기 위해 ModelView를 반환, 논리이름만 전달하는 것이 차이점

- MemberFormControllerV3 - 회원등록 폼
    
    ```java
    package hello.servlet.web.frontController.v3.controller;
    
    import hello.servlet.web.frontController.ModelView;
    import hello.servlet.web.frontController.v3.ControllerV3;
    
    import java.util.Map;
    
    public class MemberFormControllerV3 implements ControllerV3 {
        @Override
        public ModelView process(Map<String, String> paramMap) {
            return new ModelView("new-form"); //논리이름 저장
        }
    }
    ```
    
- MemberSaveControllerV3 - 회원저장
    
    ```java
    package hello.servlet.web.frontController.v3.controller;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.ModelView;
    import hello.servlet.web.frontController.v3.ControllerV3;
    
    import java.util.Map;
    
    public class MemberSaveControllerV3 implements ControllerV3 {
    
        private MemberRepository memberRepository = MemberRepository.getInstance();
        @Override
        public ModelView process(Map<String, String> paramMap) {
            String username = paramMap.get("username");
            int age = Integer.parseInt(paramMap.get("age"));
    
            Member member = new Member(username, age);
            memberRepository.save(member);
    
            ModelView mv = new ModelView("save-result");
            mv.getModel().put("member", member);
    
            return mv;
    
        }
    }
    ```
    

→ v2와 달라진 점 : 직접 서블릿의 `request.setAttribute` 로 데이터를 담지 않고 Map에 담아 ModelView를 리턴한다는 점

- MemberListControllerV3- 회원목록
    
    ```java
    package hello.servlet.web.frontController.v3.controller;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.ModelView;
    import hello.servlet.web.frontController.v3.ControllerV3;
    
    import java.util.List;
    import java.util.Map;
    
    public class MemberListControllerV3 implements ControllerV3 {
    
        private MemberRepository memberRepository = MemberRepository.getInstance();
    
        @Override
        public ModelView process(Map<String, String> paramMap) {
    
            List<Member> members = memberRepository.findAll();
            ModelView mv = new ModelView("members");
            mv.getModel().put("members", members);
    
            return mv;
        }
    }
    ```
    

- FrontControllerServletV3
    
    ```java
    package hello.servlet.web.frontController.v3;
    
    import hello.servlet.web.frontController.ModelView;
    import hello.servlet.web.frontController.MyView;
    import hello.servlet.web.frontController.v2.ControllerV2;
    import hello.servlet.web.frontController.v3.controller.MemberFormControllerV3;
    import hello.servlet.web.frontController.v3.controller.MemberListControllerV3;
    import hello.servlet.web.frontController.v3.controller.MemberSaveControllerV3;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.HashMap;
    import java.util.Map;
    
    @WebServlet(name="frontControllerServletV3", urlPatterns = "/front-controller/v3/*")
    public class FrontControllerServletV3 extends HttpServlet {
        private Map<String, ControllerV3> controllerV3Map = new HashMap<>();
    
        public FrontControllerServletV3() {
            controllerV3Map.put("/front-controller/v3/members/new-form", new MemberFormControllerV3());
            controllerV3Map.put("/front-controller/v3/members/save", new MemberSaveControllerV3());
            controllerV3Map.put("/front-controller/v3/members", new MemberListControllerV3());
        }
    
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            System.out.println("FrontControllerServletV3.service");
    
            String requestURI = req.getRequestURI();
    
            ControllerV3 controller = controllerV3Map.get(requestURI);
    
            /*
             * URI 문자열을 받아와서 해당하는 컨트롤러를 호출한다.
             *
             * 다형성에 의해 인터페이스를 받을 수 있는 것이다.
             * */
    
            if(controller == null){
                resp.setStatus(HttpServletResponse.SC_NOT_FOUND);
                return;
            }
    
            //Param map을 넘겨줘야 한다. forEach로 하나하나 다 꺼내서 Map으로 새로 생성
            Map<String, String> paramMap = createParamMap(req);
    
            ModelView mv = controller.process(paramMap);
    
            String viewName = mv.getViewName();//논리이름만 나온다.
            MyView view = viewResolver(viewName);
            //뷰를 찾아주는 해결자 역할(논리이름->물리이름)
    
            view.render(mv.getModel(), req, resp);
    
        }
        private MyView viewResolver(String viewName){
            return new MyView("/WEB-INF/views/"+viewName+".jsp");
            //논리이름->물리이름으로 바꿔주는 역할을 하며 실제 위치를 MyView에서 가져온다.
        }
    
        private static Map<String, String> createParamMap(HttpServletRequest req) {
            /*
            * paramMap을 넘겨줘야 한다.
            * request에서 파라미터 이름을 다 꺼내줘야 한다.
            *
            * 맵을 만들고, 파라미터 이름을 모두 가져와서, 키와 값을 맵에 저장한다.
            * 파라미터 맵에 값을 집어넣는다.
            * */
            Map<String, String> paramMap = new HashMap<>();
            req.getParameterNames().asIterator()
                    .forEachRemaining(paramName -> paramMap.put(paramName, req.getParameter(paramName)));
            return paramMap;
        }
    }
    ```
    
- MyView
    
    아래 코드를 추가한다. ModelView에서 넘어온 해쉬맵과 req, resp를 통해 응답 정보를 구성하는 과정이다.
    
    ```java
    public void render(Map<String, Object> model, HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        modelToRequestAttribute(model, req);
        RequestDispatcher dispatcher = req.getRequestDispatcher(viewPath);
        dispatcher.forward(req, resp);
    }
    
    private static void modelToRequestAttribute(Map<String, Object> model, HttpServletRequest req) {
        model.forEach((key, value)-> req.setAttribute(key, value));
        //jsp는 attribute로 값을 넣어 꺼내 쓸 수 있다.
        //map의 루프를 다 돌린다. req에 값을 다 담는다
    }
    ```
    

→ v2와 달라진 점 

- `createParamMap()` 의 추가 : HttpServletRequest에서 넘어온 Param 정보를 Map으로 반환하는 역할
    - 코드
        
        ```java
         private static Map<String, String> createParamMap(HttpServletRequest req) {
          /*
          * paramMap을 넘겨줘야 한다.
          * request에서 파라미터 이름을 다 꺼내줘야 한다.
          *
          * 맵을 만들고, 파라미터 이름을 모두 가져와서, 키와 값을 맵에 저장한다.
          * 파라미터 맵에 값을 집어넣는다.
          * */
          Map<String, String> paramMap = new HashMap<>();
          req.getParameterNames().asIterator()
                  .forEachRemaining(paramName -> paramMap.put(paramName, req.getParameter(paramName)));
          return paramMap;
        }
        ```
        
- `viewResolver()` 의 추가 : 직접 MyView에서 물리 위치로 바꾸는게 아니라 프론트컨트롤러에서 변환 후 최종적으로 MyView 객체에 저장
- `view.render(mv.getModel(), req, resp)` 의 호출 : HTML 화면을 렌더링하며 데이터 정보도 따로 받는다는 점

## V. 단순하고 실용적인 컨트롤러 - Version4

항상 뷰 생성과 ModelView 반환의 번거로움을 단순화, 편리성을 강화하기 위해 v4를 작성합니다.

### (1) v4 구조

![Untitled (39)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/367db36b-76e9-4b7a-bd10-2f53bbb64132)

v3와 다르게 ModelView를 매 컨트롤러마다 반환하지 않습니다. 다만 viewname만 반환하며 이를 뷰 리졸버에서 처리합니다.

- ControllerV4
    
    ```java
    package hello.servlet.web.frontController.v4;
    
    import java.util.Map;
    
    public interface ControllerV4 {
        /**
         *
         * @param paramMap
         * @param model
         * @return viewName
         */
        String process(Map<String, String> paramMap, Map<String, Object> model);
    }
    ```
    
- MemberFormControllerV4
    
    ```java
    package hello.servlet.web.frontController.v4.controller;
    
    import hello.servlet.web.frontController.v4.ControllerV4;
    
    import java.util.Map;
    
    public class MemberFormControllerV4 implements ControllerV4 {
        @Override
        public String process(Map<String, String> paramMap, Map<String, Object> model) {
            return "new-form";
        }
    }
    ```
    
- MemberSaveControllerV4
    
    ```java
    package hello.servlet.web.frontController.v4.controller;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.ModelView;
    import hello.servlet.web.frontController.v3.ControllerV3;
    import hello.servlet.web.frontController.v4.ControllerV4;
    
    import java.util.Map;
    
    public class MemberSaveControllerV4 implements ControllerV4 {
    
        private MemberRepository memberRepository = MemberRepository.getInstance();
            @Override
            public String process(Map<String, String> paramMap, Map<String, Object> model) {
                String username = paramMap.get("username");
                int age = Integer.parseInt(paramMap.get("age"));
    
                Member member = new Member(username, age);
                memberRepository.save(member);
    
              model.put("member", member);
              return "save-result";
            }
        }
    }
    ```
    

→ 파라미터로 model이 전달되므로 따로 직접 생성하지 않아도 됩니다.

- MemberListControllerV4
    
    ```java
    package hello.servlet.web.frontController.v4.controller;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.v4.ControllerV4;
    
    import java.util.List;
    import java.util.Map;
    
    public class MemberListControllerV4 implements ControllerV4 {
        private MemberRepository memberRepository = MemberRepository.getInstance();
    
        @Override
        public String process(Map<String, String> paramMap, Map<String, Object> model) {
            List<Member> members = memberRepository.findAll();
            model.put("members",members);
    
            return "members";
        }
    }
    ```
    
- FrontControllerV4
    
    ```java
    package hello.servlet.web.frontController.v4;
    
    import hello.servlet.web.frontController.ModelView;
    import hello.servlet.web.frontController.MyView;
    import hello.servlet.web.frontController.v2.ControllerV2;
    import hello.servlet.web.frontController.v3.ControllerV3;
    import hello.servlet.web.frontController.v3.controller.MemberFormControllerV3;
    import hello.servlet.web.frontController.v3.controller.MemberListControllerV3;
    import hello.servlet.web.frontController.v3.controller.MemberSaveControllerV3;
    import hello.servlet.web.frontController.v4.controller.MemberFormControllerV4;
    import hello.servlet.web.frontController.v4.controller.MemberListControllerV4;
    import hello.servlet.web.frontController.v4.controller.MemberSaveControllerV4;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.HashMap;
    import java.util.Map;
    
    @WebServlet(name="frontControllerServletV4", urlPatterns = "/front-controller/v4/*")
    public class FrontControllerV4 extends HttpServlet {
        private Map<String, ControllerV4> controllerV4Map = new HashMap<>();
    
        public FrontControllerV4() {
            controllerV4Map.put("/front-controller/v4/members/new-form", new MemberFormControllerV4());
            controllerV4Map.put("/front-controller/v4/members/save", new MemberSaveControllerV4());
            controllerV4Map.put("/front-controller/v4/members", new MemberListControllerV4());
        }
    
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
            System.out.println("FrontControllerServletV4.service");
    
            String requestURI = req.getRequestURI();
    
            ControllerV4 controller = controllerV4Map.get(requestURI);
    
            /*
             * URI 문자열을 받아와서 해당하는 컨트롤러를 호출한다.
             *
             * 다형성에 의해 인터페이스를 받을 수 있는 것이다.
             * */
    
            if(controller == null){
                resp.setStatus(HttpServletResponse.SC_NOT_FOUND);
                return;
            }
    
            //Param map을 넘겨줘야 한다. forEach로 하나하나 다 꺼내서 Map으로 새로 생성
            Map<String, String> paramMap = createParamMap(req);
            Map<String, Object> model = new HashMap<>(); //추가
    
            String viewName = controller.process(paramMap, model);
    
            MyView view = viewResolver(viewName);
            //뷰를 찾아주는 해결자 역할(논리이름->물리이름)
    
            view.render(model, req, resp);
    
        }
        private MyView viewResolver(String viewName){
            return new MyView("/WEB-INF/views/"+viewName+".jsp");
            //논리이름->물리이름으로 바꿔주는 역할을 하며 실제 위치를 MyView에서 가져온다.
        }
    
        private static Map<String, String> createParamMap(HttpServletRequest req) {
            /*
             * paramMap을 넘겨줘야 한다.
             * request에서 파라미터 이름을 다 꺼내줘야 한다.
             *
             * 맵을 만들고, 파라미터 이름을 모두 가져와서, 키와 값을 맵에 저장한다.
             * 파라미터 맵에 값을 집어넣는다.
             * */
            Map<String, String> paramMap = new HashMap<>();
            req.getParameterNames().asIterator()
                    .forEachRemaining(paramName -> paramMap.put(paramName, req.getParameter(paramName)));
            return paramMap;
        }
    }
    ```
    

→ v3와 다른 점 : 모델 객체 `Map<String, Object>` 를 미리 생성해놓고 컨트롤러 호출시 해당 해쉬맵만 전달하도록 해 중복을 없앤 점 + 논리이름만 반환해서, `ViewResolver` 에서 처리하도록 한 점

## VI. 유연한 컨트롤러 - Version5

## (1) 어댑터 패턴 등장

이전 버전의 큰 문제점은 인터페이스 하나만 정해야한다는 점이었습니다.

```java
 public FrontControllerServletV3() {
    controllerV3Map.put("/front-controller/v3/members/new-form", new MemberFormControllerV3());
    controllerV3Map.put("/front-controller/v3/members/save", new MemberSaveControllerV3());
    controllerV3Map.put("/front-controller/v3/members", new MemberListControllerV3());
}
```

 

예로 v3 프론트컨트롤러만 해도 경로가 v3로 지정되어있었고 다른 인터페이스 컨트롤러는 꿈도 못꿨습니다.

그래서 나온 것이 어뎁터 패턴이고, 프론트컨트롤러에서 다양하게 컨트롤러를 처리할 수 있도록 합니다.

## (2) v5 구조

![Untitled (38)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/32ceee26-b190-40de-bc2e-d73facf58798)

- MyHandlerAdapter(어댑터는 이렇게 구현해야한다는 구조의 코드)
    
    ```java
    package hello.servlet.web.frontController.v5;
    
    import hello.servlet.web.frontController.ModelView;
    
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    
    public interface MyHandlerAdapter {
        boolean supports(Object handler); //컨트롤러 넘어왔을때 핸들러 지원가능?여부
        ModelView handle(HttpServletRequest request, HttpServletResponse response,Object handler)
            throws ServletException, IOException; //지원가능하다면 해당 ModelView 반환
    }
    ```
    
    `supports` : 여기서 handler는 컨트롤러를 말하고, 해당 어댑터가 받아온 컨트롤러를 처리할 수 있는지 여부를 판단한다. 
    
    `handle` : 실제 컨트롤러를 호출, 결과로 ModelView 반환
    
    (이전까지는 프론트 컨트롤러에서 실제 컨트롤러를 호출했지만, 어댑터를 통해 실제 컨트롤러를 호출하게 됩니다.)
    
- ControllerV3HandlerAdapter
    
    ```java
    package hello.servlet.web.frontController.v5.adapter;
    
    import hello.servlet.web.frontController.ModelView;
    import hello.servlet.web.frontController.v3.ControllerV3;
    import hello.servlet.web.frontController.v5.MyHandlerAdapter;
    
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.HashMap;
    import java.util.Map;
    
    public class ControllerV3HanlderAdapter implements MyHandlerAdapter {
        @Override
        public boolean supports(Object handler) {
            return (handler instanceof ControllerV3);
            //v3 인터페이스야? 맞다면 true
        }
    
        /**
         *
         * handle메서드
         *어댑터의 역할 : 핸들러를 호출해주고 반환타입을 ModelView로 맞춰서 반환해주어야 한다.
         */
    
        @Override
        public ModelView handle(HttpServletRequest request, HttpServletResponse response, Object handler) throws ServletException, IOException {
            ControllerV3 controller = (ControllerV3)handler;
            //supports로 걸러진 애를 찾아서 casting해서 쓸 수 있다.
    
            Map<String, String> paramMap = createParamMap(request);
            ModelView mv = controller.process(paramMap);
    
            return mv;
        }
    
        private static Map<String, String> createParamMap(HttpServletRequest req) {
            /*
             * paramMap을 넘겨줘야 한다.
             * request에서 파라미터 이름을 다 꺼내줘야 한다.
             *
             * 맵을 만들고, 파라미터 이름을 모두 가져와서, 키와 값을 맵에 저장한다.
             * 파라미터 맵에 값을 집어넣는다.
             * */
            Map<String, String> paramMap = new HashMap<>();
            req.getParameterNames().asIterator()
                    .forEachRemaining(paramName -> paramMap.put(paramName, req.getParameter(paramName)));
            return paramMap;
        }
    }
    ```
    
- FrontControllerServletV5
    
    ```java
    package hello.servlet.web.frontController.v5;
    
    import hello.servlet.web.frontController.ModelView;
    import hello.servlet.web.frontController.MyView;
    import hello.servlet.web.frontController.v3.ControllerV3;
    import hello.servlet.web.frontController.v3.controller.MemberFormControllerV3;
    import hello.servlet.web.frontController.v3.controller.MemberListControllerV3;
    import hello.servlet.web.frontController.v3.controller.MemberSaveControllerV3;
    import hello.servlet.web.frontController.v4.ControllerV4;
    import hello.servlet.web.frontController.v4.controller.MemberFormControllerV4;
    import hello.servlet.web.frontController.v4.controller.MemberListControllerV4;
    import hello.servlet.web.frontController.v4.controller.MemberSaveControllerV4;
    import hello.servlet.web.frontController.v5.adapter.ControllerV3HanlderAdapter;
    import hello.servlet.web.frontController.v5.adapter.ControllerV4HandlerAdapter;
    
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    import java.util.ArrayList;
    import java.util.HashMap;
    import java.util.List;
    import java.util.Map;
    
    @WebServlet(name= "FrontControllerV5", urlPatterns = "/front-controller/v5/*")
    public class FrontControllerV5 extends HttpServlet {
    
        //이전 버전과 비교
    //    private Map<String, ControllerV4> controllerMap = new HashMap<>();
        private final Map<String, Object> handlerMappingMap = new HashMap<>();
        private final List<MyHandlerAdapter>handlerAdapters = new ArrayList<>();
    
        public FrontControllerV5() {
            initHandlerMappingMap();
            initHanlderAdapters();
        }
    
        private void initHanlderAdapters() {
            handlerAdapters.add(new ControllerV3HanlderAdapter());
            handlerAdapters.add(new ControllerV4HandlerAdapter());
        }
    
        private void initHandlerMappingMap() {
            handlerMappingMap.put("/front-controller/v5/v3/members/new-form", new MemberFormControllerV3());
            handlerMappingMap.put("/front-controller/v5/v3/members/save", new MemberSaveControllerV3());
            handlerMappingMap.put("/front-controller/v5/v3/members", new MemberListControllerV3());
    
            //v4 추가
            handlerMappingMap.put("/front-controller/v5/v4/members/new-form", new MemberFormControllerV4());
            handlerMappingMap.put("/front-controller/v5/v4/members/save", new MemberSaveControllerV4());
            handlerMappingMap.put("/front-controller/v5/v4/members", new MemberListControllerV4());
        }
    
        @Override
        protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    
            //1. 핸들러 매핑정보 조회
            //MemberFormControllerV4 반환됨
            Object handler =  getHandler(req);
    
            /*
             * URI 문자열을 받아와서 해당하는 컨트롤러를 호출한다.
             *
             * 다형성에 의해 인터페이스를 받을 수 있는 것이다.
             * */
    
            if(handler == null){
                resp.setStatus(HttpServletResponse.SC_NOT_FOUND);
                return;
            }
    
            //2. 핸들러 어댑터 찾기
            //ControllerV4HandlerAdapter
            MyHandlerAdapter adapter = getHandlerAdapter(handler);
    
            //3. handle 호출(실제 컨트롤러가 호출, 모델 뷰를 반환)
            ModelView mv = adapter.handle(req,resp, handler);
    
            //4. 뷰 리졸버 호출, 뷰 랜더 호출
            String viewName = mv.getViewName();//논리이름만 나온다.
            MyView view = viewResolver(viewName);
            //뷰를 찾아주는 해결자 역할(논리이름->물리이름)
    
            view.render(mv.getModel(), req, resp);
        }
    
        private MyHandlerAdapter getHandlerAdapter(Object handler) {
            MyHandlerAdapter a;
            //handler = MemberFormController
            for (MyHandlerAdapter adapter : handlerAdapters) {
                if(adapter.supports(handler)){
                   return adapter;
                }
                //v3어댑터를 찾고 있다면 v3 어댑터인 것을 찾으면 리턴
                //없으면 for문 돈다.
            }
    
            throw new IllegalArgumentException("handler adapter를 찾을 수 없습니다 handler = "+ handler);
        }
    
        private Object getHandler(HttpServletRequest req) {
            String requestURI = req.getRequestURI();
            return handlerMappingMap.get(requestURI);
            //핸들러를 찾는다.
    
        }
    
        private MyView viewResolver(String viewName){
            return new MyView("/WEB-INF/views/"+viewName+".jsp");
            //논리이름->물리이름으로 바꿔주는 역할을 하며 실제 위치를 MyView에서 가져온다.
        }
    }
    ```



## 섹션 5

## I. 스프링 MVC 전체 구조

### (1) 직접 만든 MVC 프레임워크 구조

![Untitled (46)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/47be7165-e9f8-4379-85eb-aa5fb1144feb)

### (2) Spring MVC 구조


![Untitled (45)](https://github.com/songhee1/Spring-MVC-1/assets/96781855/3f6addd7-f91c-4227-a0b8-94a6087bbe03)

비교해보면 다음과 같습니다.

FrontController → Dispatcher Servlet

handlerMappingMap → HandlerMapping

MyHandlerAdater → HandlerAdapter

ModelView → ModelAndView

viewResolver → ViewResolver

MyView→ View

### (3) DispatcherServlet 구조 살펴보기

`org.springframework.web.servlet.DispatcherServlet` 해당 경로입니다.

스프링 MVC 패턴 또한 프론트 컨트롤러 패턴으로 이뤄져있고, 그것이 바로 DispatcherServlet입니다. 이는 곧 스프링 MVC의 핵심입니다.

- 디스패처 서블릿의 등록과정

HttpServlet을 상속받고, 서블릿으로 동작하게 됩니다.

→ 따라서 디스패처 서블릿이 서블릿으로 자동으로 등록되어 **모든 경로에 대해 매핑**되는 원리입니다. `urlPatters="/"` 

(참고) 자세한 경로가 더 우선순위가 높은 규칙이 있습니다.

- DispatcherServlet.doDispatch()
    
    ```java
    protected void doDispatch(HttpServletRequest request, HttpServletResponse 
    response) throws Exception {
    HttpServletRequest processedRequest = request;
    HandlerExecutionChain mappedHandler = null;
    ModelAndView mv = null;
    // 1. 핸들러 조회
    mappedHandler = getHandler(processedRequest);
    if (mappedHandler == null) {
    noHandlerFound(processedRequest, response);
    return;
    }
    // 2. 핸들러 어댑터 조회 - 핸들러를 처리할 수 있는 어댑터
    HandlerAdapter ha = getHandlerAdapter(mappedHandler.getHandler());
    // 3. 핸들러 어댑터 실행 -> 4. 핸들러 어댑터를 통해 핸들러 실행 -> 5. ModelAndView 반환
    mv = ha.handle(processedRequest, response, mappedHandler.getHandler());
    processDispatchResult(processedRequest, response, mappedHandler, mv,
    dispatchException);
    }
    private void processDispatchResult(HttpServletRequest request,
    HttpServletResponse response, HandlerExecutionChain mappedHandler, ModelAndView 
    mv, Exception exception) throws Exception {
    // 뷰 렌더링 호출
    render(mv, request, response);
    }
    protected void render(ModelAndView mv, HttpServletRequest request,
    HttpServletResponse response) throws Exception {
    View view;
    String viewName = mv.getViewName();
    // 6. 뷰 리졸버를 통해서 뷰 찾기, 7. View 반환
    view = resolveViewName(viewName, mv.getModelInternal(), locale, request);
    // 8. 뷰 렌더링
    view.render(mv.getModelInternal(), request, response);
    }
    ```
    

서블릿 URL이 호출되면 HttpServlet이 제공하는 `service()` 가 호출

→ DispatcherServlet은 부모인 FrameworkServlet의 service() 오버라이드를 작성하게 됩니다.

→ FrameworkServlet의 service()를 시작으로 해서 위의DispatcherServlet.doDispatch()가 호출됩니다.

### (4) 동작과정

1. 핸들러 조회

```java
// 1. 핸들러 조회
mappedHandler = getHandler(processedRequest);
if (mappedHandler == null) {
noHandlerFound(processedRequest, response);
return;
}
```

핸들러 매핑을 통해 요청 URL에 매핑된 핸들러(컨트롤러)를 조회합니다.

1. 핸들러 어댑터 조회

```java
// 2. 핸들러 어댑터 조회 - 핸들러를 처리할 수 있는 어댑터
HandlerAdapter ha = getHandlerAdapter(mappedHandler.getHandler());
```

핸들러(컨트롤러)를 실행할 수 있는 어댑터를 찾아옵니다.

1. 핸들러 어댑터 실행

```java
// 3. 핸들러 어댑터 실행 -> 4. 핸들러 어댑터를 통해 핸들러 실행 -> 5. ModelAndView 반환
mv = ha.handle(processedRequest, response, mappedHandler.getHandler());
processDispatchResult(processedRequest, response, mappedHandler, mv,
dispatchException);
}
```

```java
private void processDispatchResult(HttpServletRequest request,
HttpServletResponse response, HandlerExecutionChain mappedHandler, ModelAndView 
mv, Exception exception) throws Exception {
// 뷰 렌더링 호출
render(mv, request, response);
}
protected void render(ModelAndView mv, HttpServletRequest request,
HttpServletResponse response) throws Exception {
View view;
String viewName = mv.getViewName();
// 6. 뷰 리졸버를 통해서 뷰 찾기, 7. View 반환
view = resolveViewName(viewName, mv.getModelInternal(), locale, request);
// 8. 뷰 렌더링
view.render(mv.getModelInternal(), request, response);
}
```

핸들러 어댑터를 실행해서 반환한 ModelAndView 객체에서 뷰 이름을 가져옵니다. 이후엔, 뷰 리졸버를 통해서 뷰의 논리이름 변경합니다. 이후엔 뷰 객체를 반환하고 뷰를 렌더링합니다.

### (5) 주요 인터페이스 목록

- 핸들러 매핑

org.springframework.web.servlet.HandlerMapping

- 핸들러 어댑터

org.springframework.web.servlet.HandlerAdapter

- 뷰리졸버

org.springframework.web.servlet.ViewResolver

- 뷰

org.springframework.web.servlet.View

## II. 핸들러 매핑과 핸들러 어댑터의 이해

핸들러 매핑과 핸들러 어댑터를 이해하기 위해 `Controller` 인터페이스를 직접 사용하고 이해해봅시다.

### (1) Controller인터페이스를 활용해 이해해보자

- Controller 인터페이스
    
    ```java
    package org.springframework.web.servlet.mvc;
    
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    
    import org.springframework.lang.Nullable;
    import org.springframework.web.servlet.ModelAndView;
    @FunctionalInterface
    public interface Controller {
    	@Nullable
    	ModelAndView handleRequest(HttpServletRequest request, HttpServletResponse response) throws Exception;
    
    } 
    ```
    
- OldController(인터페이스 구현체)
    
    ```java
    package hello.servlet.web.springmvc.old;
    
    import org.springframework.stereotype.Component;
    import org.springframework.web.servlet.ModelAndView;
    import org.springframework.web.servlet.mvc.Controller;
    
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    @Component("/springmvc/old-controller") //스프링 빈의 이름을 url 패턴으로 맞춘것
    public class OldController implements Controller {
        @Override
        public ModelAndView handleRequest(HttpServletRequest request, HttpServletResponse response) throws Exception {
            System.out.println("OldController.handleRequest");
            return new ModelAndView("new-form");
        }
    }
    ```
    
    - `@Component` 컨트롤러에 경로를 작성해줌으로써 /springmvc/old-controller 경로로 URL이 매핑됩니다.
    - 또한 스프링 빈에는 해당 경로를 이름으로 하여 등록됩니다.

앞선 핸들러 매핑으로 컨트롤러를 찾고, 핸들러 어댑터로 해당 컨트롤러의 메서드를 제어하는 과정이 있었습니다.

- **HandlerMapping**

따라서 핸들러 매핑으로 해당 스프링 빈 이름을 찾을 수 있도록 해야합니다. 핸들러 매핑은 기본적으로 컨트롤러를 찾을 수 있습니다. 

이 예제에서는 스프링 빈으로 등록했기 때문에 핸들링 매핑시, 스프링 빈 이름을 찾아야합니다.

- 기본적인 우선순위 목록
    
    0번째 : `RequestMappingHandlerMapping`  - 애노테이션 기반 컨트롤러 `@RequestMapping` 에서 사용하며, 이를 기반으로 핸들러를 찾습니다.
    
    1번째 : `BeanNameUrlHandlerMapping` - 스프링 빈 이름으로 매핑 대상인 핸들러를 찾습니다.
    

- **HandlerAdapter**

핸들러 매핑으로 찾은 핸들러를 실행하고 제어할 수 있는 핸들러 어댑터를 찾아야 합니다. 

이 예제에서는 `Controller` 인터페이스 실행하는 어댑터를 찾아야합니다.

- 기본적인 우선순위 목록
    
    0번째 : `RequestMappingHandlerAdapter` - 애노테이션 기반 컨트롤러 `@RequestMapping` 에서 사용하고, 이것을 통해 어댑터를 찾고 메서드 실행합니다.
    
    1번째 : `HttpRequestHandlerAdapter` - `HttpRequestHandler` 를 처리합니다.
    
    2번째 : `SimpleControllerHandlerAdapter` - `Controller` 인터페이스를 처리하며 어노테이션을 의미하는 것이 아닙니다. 해당 인터페이스가 위치한 핸들러일 경우, 이를 다루는 어댑터입니다.
    

💫**웹 브라우저가 해당경로로 이동하면서 어떻게 동작하는가?**

따라서 위의 핸들러 매핑과 어댑터들로 인해 

1. **핸들러 매핑으로 핸들러를 찾습니다.** - 빈 이름으로 찾아야하기 때문에 첫번째 순위인 `BeanNameUrlHandlerMapping` 실행으로 성공합니다. 따라서 OldController반환됩니다.

1. **핸들러 어댑터를 찾습니다.** - supports메서드를 호출해, 지원여부를 체크하고 Controller 지원 어댑터인 `SimpleControllerHandlerAdapter` 가 어댑터가 됩니다.

1. **핸들러 어댑터의 실행** - 어댑터 실행 + 핸들러 정보를 넘기고, 핸들러가 내부에서 동작하게 됩니다.

### (2) HttpRequestHandler인터페이스를 사용해 이해해보자

- HttpReqeustHandler
    
    ```java
    @FunctionalInterface
    public interface HttpRequestHandler {
    
    	/**
    	 * Process the given request, generating a response.
    	 * @param request current HTTP request
    	 * @param response current HTTP response
    	 * @throws ServletException in case of general errors
    	 * @throws IOException in case of I/O errors
    	 */
    	void handleRequest(HttpServletRequest request, HttpServletResponse response)
    			throws ServletException, IOException;
    
    }
    ```
    
- MyHttpRequestHandler(인터페이스 구현체)
    
    ```java
    package hello.servlet.web.springmvc.old;
    
    import org.springframework.stereotype.Component;
    import org.springframework.web.HttpRequestHandler;
    
    import javax.servlet.ServletException;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.io.IOException;
    @Component("/springmvc/request-handler")
    public class MyHttpRequestHandler implements HttpRequestHandler {
        @Override
        public void handleRequest(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    
        }
    }
    ```
    

💫**웹 브라우저가 해당경로로 이동하면서 어떻게 동작하는가?**

따라서 위의 핸들러 매핑과 어댑터들로 인해 

1. **핸들러 매핑으로 핸들러를 찾습니다.** - 빈 이름으로 찾아야하기 때문에 첫번째 순위인 `BeanNameUrlHandlerMapping` 실행으로 성공합니다. 따라서 MyHttpRequestHandler가 반환됩니다.

1. **핸들러 어댑터를 찾습니다.** - supports메서드를 호출해, 지원여부를 체크하고  MyHttpRequestHandler컨트롤러 지원 어댑터인 `HttpRequestHandler` 가 어댑터가 됩니다.

1. **핸들러 어댑터의 실행** - 어댑터 실행 + 핸들러 정보를 넘기고, 핸들러가 내부에서 동작하게 됩니다.

## III. 뷰 리졸버의 이해

- OldController 추가
    
    ```java
    package hello.servlet.web.springmvc.old;
    
    import org.springframework.stereotype.Component;
    import org.springframework.web.servlet.ModelAndView;
    import org.springframework.web.servlet.mvc.Controller;
    
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    @Component("/springmvc/old-controller") //스프링 빈의 이름을 url 패턴으로 맞춘것
    public class OldController implements Controller {
       @Override
     public ModelAndView handleRequest(HttpServletRequest request,
    		HttpServletResponse response) throws Exception {
    		 System.out.println("OldController.handleRequest");
    		 return null;
    		 }
    }
    ```
    

### (1) 뷰 리졸버 동작 방식

- 기본적인 우선순위 목록
    
    0번째 : `BeanNameViewResolver`- 빈 이름 기반 뷰를 찾아 반환합니다. 
    
    1번째 : `InternalResourceViewResolver` - JSP 처리하는 뷰를 반환하게 됩니다.
    

💫**웹 브라우저가 해당경로로 이동하면서 ‘뷰 리졸버’는 어떻게 동작하는가?**

따라서 위의 핸들러 매핑과 어댑터들로 인해 어댑터를 찾고 핸들러 메서드를 실행하게 됩니다. 이 다음은 이후의 뷰 리졸버에 대한 과정입니다.

1. 핸들러 어댑터로 논리 뷰를 가져옵니다.- OldContorller에서 논리 이름만 반환된 것처럼, 논리이름만을 추출합니다.

1. ViewResolver 호출 

뷰이름을 활용해 앞선 우선순위목록에서 매칭되는 뷰 리졸버를 찾습니다. 따라서, 0순위부터 차례로 찾아보며 `InternalResourceViewResolver` 를 호출하게 됩니다.

1. `InternalResourceViewResolver` 을 통하여 `InternalResourceView` 을 반환하고 forward() 호출해 처리할 수 있는 경우라면 이를 사용합니다.
2. view.render() 를 통해 뷰를 랜더링해 JSP를 실행합니다.

(참고)

JSP에서는 forward()를 통해서만 렌더링이 되지만, 이외 뷰 템플릿들은 forward()없이도 렌더링이 된다는 특징이 있습니다.

## IV. 스프링 MVC 시작하기

### (1) `@RequestMapping` 의 이해

이 어노테이션은 핸들러 매핑과 핸들러 어댑터로 각각 `RequestMappingHandlerMapping`, `RequestMappingHandlerAdapter` 를 호출할 수 있습니다.

**실무의 대부분이 이 방식을 통해 컨트롤러를 제어합니다.(99.9%)**

`@RequestMapping` 을 사용해서 앞서 만든 웹애플리케이션 컨트롤러를 변경해봅시다.

- SpringMemberFormControllerV1
    
    ```java
    package hello.servlet.web.springmvc.v1;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.servlet.ModelAndView;
    
    @Controller
    /**
     * 컨트롤러 어노테이션에는 컴포넌트 애노테이션이 들어가있다.
     * = 컴포넌트 스캔 대상이 되고 스프링 빈에 등록된다.
     *
     * 스프링mvc에서 애노테이션 기반 컨트롤러로 인식한다. (RequestMappingHandlerMapping에서 인식)
     *
     * 해당 url이 호출되면 process메서드 호출
     *
     * RequestMappingHandlerMapping은 @Controller 또는 RequestMapping 어노테이션이 클래스 레벨에
     * 붙어있어야 해당 클래스를 찾아낼 수 있다.
     */
    @RequestMapping
    public class SpringMemberFormControllerV1 {
        @RequestMapping("/springmvc/v1/members/new-form")
        public ModelAndView process(){
            return new ModelAndView("new-form");
        }
    }
    ```
    
    | @Controller | - 스프링이 자동으로 빈에 등록시켜줍니다.
    - 자동으로 컴포넌트 스캔 대상이 됩니다.
    - 스프링 MVC에서 애노테이션 기반 컨트롤러로 인식하게 됩니다. |
    | --- | --- |
    | @RequestMapping | - 요청 정보를 매핑합니다.
    - 요청 URL이 해당 경로와 똑같다면 해당 메서드 process() 가 호출됩니다. |

RequestMapping의 핸들러 매핑으로 소개한 `RequestMappingHandlerMapping` 은 원래 `@RequestMapping` 또는 `**@Controller` 가 클래스 레벨에 있어야 매핑정보로 인식**할 수 있었습니다.

하지만, 스프링 3.0이상부터 클래스 레벨에 `@RequestMapping` 만 있는다면 매핑정보로 인식하지 못하고 오직 `@Controller` 가 있어야만 스프링 컨트롤러로 인식할 수 있습니다.(주의)

→ `@RestController` 는 `@Controller` 도 포함하므로 이 또한 인식됩니다.

- SpringMemberSaveControllerV1
    
    ```java
    package hello.servlet.web.springmvc.v1;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.ModelView;
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.servlet.ModelAndView;
    
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.util.Map;
    
    @Controller
    public class SpringMemberSaveControllerV1 {
        /**
         *
         */
        private MemberRepository memberRepository = MemberRepository.getInstance();
    
        @RequestMapping("/springmvc/v1/members/save")
        public ModelAndView process(HttpServletRequest request, HttpServletResponse response) {
            String username = request.getParameter("username");
            int age = Integer.parseInt(request.getParameter("age"));
    
            Member member = new Member(username, age);
            memberRepository.save(member);
    
            ModelAndView mv = new ModelAndView("save-result");
            mv.addObject("member", member);
            return mv;
    
        }
    }
    ```
    
- SpringMemberListControllerV1
    
    ```java
    package hello.servlet.web.springmvc.v1;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import hello.servlet.web.frontController.ModelView;
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.servlet.ModelAndView;
    
    import java.util.List;
    import java.util.Map;
    @Controller
    public class SpringMemberListControllerV1 {
        private MemberRepository memberRepository = MemberRepository.getInstance();
    
        @RequestMapping("/springmvc/v1/members")
        public ModelAndView process(){
    
            List<Member> members = memberRepository.findAll();
    
            ModelAndView mv = new ModelAndView("members");
            mv.addObject("members", members);
    
            return mv;
        }
    }
    ```
    

### (2) 스프링 MVC- 컨트롤러 통합

- 클래스 단위가 아닌 메서드 단위에만 `@RequestMapping` 이 적용되었으므로 이를 하나의 컨트롤러로 통합해 작성해볼 수 있습니다.

- SpringMemberControllerV2
    
    ```java
    package hello.servlet.web.springmvc.v2;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.servlet.ModelAndView;
    
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import java.util.List;
    
    @Controller
    @RequestMapping("/springmvc/v2/members")
    public class SpringMemberControllerV2 {
        private MemberRepository memberRepository = MemberRepository.getInstance();
    
        @RequestMapping("/new-form")
        public ModelAndView newForm(){
            return new ModelAndView("new-form");
        }
    
        @RequestMapping("/save")
        public ModelAndView save(HttpServletRequest request, HttpServletResponse response) {
            String username = request.getParameter("username");
            int age = Integer.parseInt(request.getParameter("age"));
    
            Member member = new Member(username, age);
            memberRepository.save(member);
    
            ModelAndView mv = new ModelAndView("save-result");
            mv.addObject("member", member);
            return mv;
    
        }
    
        @RequestMapping //주소를 더할게 없는 경우 경로 제거하고 작성
        public ModelAndView members(){
    
            List<Member> members = memberRepository.findAll();
    
            ModelAndView mv = new ModelAndView("members");
            mv.addObject("members", members);
    
            return mv;
        }
    }
    ```
    

V1 컨트롤러를 확인해보면 경로의 중복이 발생합니다.

```java
@RequestMapping("/springmvc/v1/members")
public ModelAndView process(){...}

@RequestMapping("/springmvc/v1/members")
public ModelAndView process(){...}

@RequestMapping("/springmvc/v1/members/new-form")
public ModelAndView process(){...}
```

중복되는 경로인 `"/springmvc/v1/members"` 이 부분을 클래스 레벨에서 `@RequestMapping` 에 두면 중복을 해결할 수 있습니다.

```java
@RequestMapping("/springmvc/v2/members")
```

→ 클래스 레벨 경로 + 메서드 경로가 조합되서  호출된다고 볼 수 있습니다.

### (3) 스프링 MVC- 실용적인 방식

스프링 MVC에서는 개발자를 위해 편의기능을 다양하게 지원하고 있고 그것들에 대하여 알아봅시다.

- SpringMemberControllerV3
    
    ```java
    package hello.servlet.web.springmvc.v3;
    
    import hello.servlet.domain.member.Member;
    import hello.servlet.domain.member.MemberRepository;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.*;
    
    import java.util.List;
    
    @Controller
    @RequestMapping("/springmvc/v3/members")
    public class SpringMemberControllerV3 {
        private MemberRepository memberRepository = MemberRepository.getInstance();
    
    //    @RequestMapping(value = "/new-form", method = RequestMethod.GET) //get요청인 경우만 호출
        @GetMapping("/new-form")
        public String newForm(){
            return "new-form";
        }
    
        /**
         * 애노테이션 기반 컨트롤러는 모델앤뷰를 반환해도되고, 문자를 반환해도 된다.
         * 뷰 이름으로 알고 프로세스가 진행되기 때문
         *
         */
    
    //    @RequestMapping(value  = "/save", method = RequestMethod.POST)
        @PostMapping("/save")
        public String save(
                @RequestParam("username") String username,
               @RequestParam("age") int age, /*타입 변환도 지원해준다*/
                Model model
                /**
                 * 스프링이 제공하는 모델
                 */
        ) {
            Member member = new Member(username, age);
            memberRepository.save(member);
    
           model.addAttribute("member", member);
            return "save-result";
    
        }
    
    //    @RequestMapping(method = RequestMethod.GET)
        @GetMapping
        //주소를 더할게 없는 경우 경로 제거하고 작성
        public String members(
                Model model
        ){
    
            List<Member> members = memberRepository.findAll();
            model.addAttribute("members", members);
    
            return "members";
        }
    
    }
    ```
    
    ****편의 기능****
    
    | Model 파라미터 | Model을 파라미터로 받을 수 있는데, 이는 Spring이 제공하는 모델로, 데이터를 넣기가 가능하다. |
    | --- | --- |
    | ViewName 이름 직접 반환 | 논리이름으로 반환해도 되고 ModelAndView를 반환해도 된다. |
    | @RequestParam | HTTP 요청 파라미터 정보를 받을 수 있다.
    파라미터로 쓰인 변수이름을 “”로 받을 수 있고 변수명도 작성할 수 있다.  |
    | @RequestMapping
    = @GetMapping +
    @PostMapping | URL 매칭 + method도 모두 구분 할 수 있다.
    더불어 method까지 구분하기 번거로운 경우 @GetMapping이나 @PostMapping을 사용하면 된다. |
