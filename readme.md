## AWS 강의
### AWS 에서 오신 챔피언 등급 공인 강사 설수기 대표님
### <br/>

### 실습 없이 듣는 과정
### 강의 자료(향후 2년 동안 엑세스 가능)
#### https://online.vitalsource.com/reader/books/100-ACPEXX-30-KO-SG-E/pageid/0
![image](https://user-images.githubusercontent.com/62974484/186045517-77d8368d-eae4-49a1-956e-3f4d71fb0ec1.png)

### <br/><br/><br/>

### certification
#### https://aws.amazon.com/ko/certification/
![image](https://user-images.githubusercontent.com/62974484/186043593-5edd05b6-6db4-4d7d-881b-a040d8c2f979.png)

### <br/><br/><br/>

### 물리적인 서버가 수만대 있고(데이터 센터) 클러스터링 함 -> VM 으로 가상화하여 클라우드를 제공함
### 데이터 센터는 세계 주요 도시에 존재한다. 최대 6개를 묶어서 AZ (Available zone) 라고 하는 클러스터링 서버(논리적인 개념)를 만든다.
### 그런 AZ 를 2개 이상 묶어서 region 을 만든다. 그 중 하나가 Seoul region 이 있다.

### 클라우드는 대표적인 서비스로 EC2 가 있고 EC2 인스턴스(가상 서버)라고 함
### RDS : relational DB service (MySQL 등의 6개 관계형 DB) 를 지원해주는 서비스. 소개만 하고 이번 강의에서는 자세히 다루지는 않음
### <br/>

## 모듈 2. 클라우드 컴퓨팅이란
#### 서버에서 할당된 인스턴스의 CPU, 메모리를 말함
### on-premise 데이터 서버
### 퍼블릭 클라우드 : = 인터넷, AWS 와 같이 벤더들이 퍼블릭하게 제공하는 클라우드. 알리바바 등도 있음.
### 프라이빗 클라우드 : 개인
### 하이브리드 클라우드 : 퍼블릭 + 프라이빗
### AWS 에는 outposts 라고 퍼블릭 클라우드 말고 따로 서버를 데이터 센터 안에 서버를 들이는 서비스도 있다. 보안에 중요한 국방부 등에서 이용하기도 한다.
### <br/>

### 모듈 7. 모니터링 및 분석
#### 사용한 만큼 낼 수 있게 함
#### 시간마다 사용률 확인 -> 리소스에 맞게끔 스케일을 더 늘릴지 줄일지 결정 -> 오토스케일링한다 라고 함
#### 확장성, 가용성, 내구성 크게 3가지를 충족하게 함

### <br/><br/><br/>

## 모듈 1. AWS 소개
### 중요 키워드 : 온-디멘드, 온-프레미스
### on-demand : 사용한 만큼 과금, 사용할 만큼 제공
### on-premise : 애완동물과 같다? 프라이빗 서버
### 회사들은 특정 월마다 서버 사용률이 피크를 찍는 경우가 있다. 이 수요를 해결해주기 위해 AWS 가 지원해준다. -> 확장성. 
### AWS 는 API 로 소통한다.
![image](https://user-images.githubusercontent.com/62974484/186046258-3de7a808-733a-468a-865d-57960d0ea093.png)
![image](https://user-images.githubusercontent.com/62974484/186046315-573146d9-d891-43bd-a22b-9bc0a1df8472.png)
### 프로비저닝 : 온 디멘드와 같은 개념

### <br/><br/><br/>

## 클라우드 컴퓨팅의 이점

