# 신한DS 금융SW 아카데미 :: 인터넷 서점 JAVA - ORACLE 구현

![_9a1c0224-81e6-44a3-8f3c-2addb0d7d34b](https://github.com/SHDS-5g-2324/JAVA/assets/29741156/1ad8ddd7-82c7-471f-bb77-dd4ae0bb681e)

## 1. 개발 환경
### 프로그래밍 언어 : Java 17
### 사용 라이브러리 : Lombok, Ojdbc
### 사용 DB : Oracle DB 11g
### 협업 툴 : Github, Slack

## 2. 기술 목표

### 객체지향 프로그래밍
#### 객체 지향 프로그래밍 (OOP): 
- Java는 객체 지향 프로그래밍 언어로, 이 코드는 객체 지향적인 설계 원칙을 따라 작성되었습니다. 클래스와 객체를 사용하여 코드를 구조화하고 각각의 객체는 데이터와 해당 데이터를 처리하는 메서드를 함께 캡슐화합니다.
#### 클래스와 객체: 
- 코드에서 다양한 클래스를 정의하고, 이 클래스들의 인스턴스인 객체를 생성하여 사용합니다. 예를 들어, Main, Login, RegisterMember, Purchase 등 다양한 기능을 제공하는 클래스가 있습니다.
#### 캡슐화 
- 클래스는 데이터와 해당 데이터를 조작하는 메서드를 함께 묶어 캡슐화합니다. 이를 통해 데이터의 무결성을 보호하고 관련 기능을 쉽게 관리할 수 있습니다.
#### 상속
- 상속을 사용하여 클래스 간에 코드를 재사용합니다. 예를 들어, Read 클래스에서 BookList 클래스를 상속하여 책 목록을 표시하는 메서드를 재사용합니다.
#### 다형성
- 다형성을 통해 같은 이름의 메서드를 다양한 방식으로 구현할 수 있습니다. 이 코드에서는 메뉴 처리를 위해 processMenu 메서드를 사용하며, 사용자의 선택에 따라 다양한 작업을 수행합니다.
#### 인터페이스
- Connection, ResultSet 등 JDBC(Java Database Connectivity) API를 사용하여 데이터베이스에 연결하고 데이터를 처리하는 인터페이스를 활용합니다.
  
### 디자인 패턴 방향성

#### MVC (Model-View-Controller)
- 이 코드에서는 모델 (데이터와 데이터를 처리하는 메서드를 캡슐화하는 클래스), 뷰 (사용자 인터페이스) 및 컨트롤러 (메뉴 처리 및 사용자 입력 처리)와 같은 MVC 패턴의 일부를 구현할 수 있습니다. 각 클래스는 특정 역할을 수행하며, 이들 간의 역할을 분리함으로써 코드의 유지보수성과 확장성을 향상시킬 수 있습니다.
#### 싱글톤 패턴 (Singleton Pattern)
- 코드에서는 DbConnect 클래스를 통해 데이터베이스 연결을 관리합니다. 이 클래스는 애플리케이션 전반에 걸쳐 단일 인스턴스로 유지될 수 있으며, 이는 싱글톤 패턴의 특성을 가질 수 있습니다.
#### 스트래티지 패턴 (Strategy Pattern)
사용자의 선택에 따라 다양한 작업을 수행하는 부분에서 스트래티지 패턴의 원칙을 따를 수 있습니다. 각 선택지마다 다른 전략(메서드 호출)을 사용하여 작업을 수행합니다.

### 예외 처리
- try-catch 블록을 사용하여 예외 상황을 처리합니다. 이를 통해 프로그램이 예기치 않은 상황에서도 안정적으로 동작할 수 있도록 합니다. 또한 의도하지 않은 입력으로 시스템에 문제가 생기는 것을 방지하기 위해, 문자열 가공 및 정제과정을 구현하고 자바가 제공하는 Exception을 활용

# 3. 프로젝트 설계과정

## ERD 다이어그램 
![image](https://github.com/SHDS-5g-2324/JAVA/assets/76528931/87155f96-c138-487f-9f26-fbe763de33a9)

## 기능구현
### 기본 기능
- 로그인
- 회원가입 및 회원 탈퇴 
- (DB저장 여부 확인 후 존재하면 로그인 / 없으면 회원가입)
- 책 리스트 출력
- 나가기기

### 구매 기능
- 책 리스트 출력
- 번호/이름 입력
- 구매대기 상태로 PURCHASE 테이블에 저장
- 내 구매내역에서 확인
- 구매 시 포인트 감소 , 구매내역 추가 , 판매 책 수량 감소 
- 로그인한 ID 구매 리스트 출력
- 상태 업데이트(장바구니 담기 / 결제제완료)
- 책 수량 0(품절) 일 때 구매불가능 


### 좋아요 기능 
- 책 번호/이름 입력
- LIKE_BOOK 테이블에 계정 아이디 + 책 아이디 저장 (이미 좋아요 한 책은 좋아요 실패)

---------

### 구분

### 로그인
		-아이디 비밀번호 일치시 로그인

### 회원가입
		-

### 마이페이지 
		-개인정보확인
		-비밀번호 변경
		-잔액조회
		-잔액추가
		-구매내역
		-좋아요목록
  		-장바구니 목록

### 책 구매하기 
		-판매중인 책 리스트 출력
		-베스트셀러 TOP 10 
		-책구매하기 
		-장바구니 담기
                   
### 회원탈퇴
		-탈퇴시 해당 ID로 가입 불가 
  
### 로그아웃
		- 로그아웃후 다시 로그인창으로 복귀 

## 예외처리 상세내용
- 입력값 String으로 받아 처리
- ...~~

## 이후 업데이트 사항
- 조인 테이블 각 키값 FK로 지정하여 아이디 삭제 시 내용 같이 삭제시키기(CASCADE)
- 회원가입 시 각 데이터 양식 제공하여 통과하지 못하면 회원가입 처리x
- DB 조회 인터페이스로 구현 + SQL문, 입력 형식이 달라도 오버라이딩 구현하기 [참고](https://velog.io/@ldevlog/13-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%9C-%EB%8B%A4%ED%98%95%EC%84%B1-%EA%B5%AC%ED%98%84-dao-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0)
- 
- 