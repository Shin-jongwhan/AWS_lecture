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
### 전세계 region 26개, AZ 86개가 있다.
### <br/>

### region 을 구성하기 전에 AZ 를 묶는 게 중간에 하나 더 있는데, VPC 라는 사설망이 있다. 
### IPv4 xxx.xxx.xxx.xxx 가 있다. VPC 는 기본적으로 IPv4 로 구성한다. 프라이빗 IP 이다.
#### A 클래스 : 첫 8비트(xxx.)를 고정한다. 그리고 나머지 24 비트를 사용한다.
#### B 클래스는 16 비트(xxx.xxx)를 고정, C 는 24 비트(xxx.xxx.xxx)를 고정한다.
#### 10.0.0.0/24 로 표현되어 있으면 24 비트는 고정되어 있다는 말이다.
#### 이렇게 구성한 다음 subnet 을 구성할 수 있다. 예를 들어 subnet 이 4개 있으면 IP 를 잘라서 각 subnet 4개에 할당해준다.
#### VPC 는 프라이빗, 퍼블릭 망 이렇게 나눌 수 있다. 외부와 소통할 수 있는 건 퍼블릭. DB 와 같이 개발자들이 볼 수 있는 건 프라이빗.
#### 프라이빗 서브넷 - 라우팅 테이블에 in-bound 를 거부하게 하는 룰을 만든다. 그리고 NAT 를 설정하여 프라이빗과 퍼블릭이 소통할 수 있게 만든다. 
#### NAT 설명
##### 단일 주소 변환 라우터의 변경 내용을 중앙 집중식으로 관리하여 도메인 내의 사용자에게 이 유형의 변경 내용을 숨길 수 있습니다. NAT는 로컬 호스트가 공용 인터넷에 액세스할 수 있게 하고 외부에서는 직접 액세스할 수 없도록 보호합니다. 네트워크를 주로 내부용으로 사용하는 조직에서는 이 체계를 사용하는 경우에도 가끔 외부 액세스가 필요합니다.
##### NAT 지원 라우터는 공용 네트워크와 개인 네트워크 사이에 설치됩니다. NAT 지원 라우터의 역할은 내부 비공개 IPv4 주소와 할당된 공용 IPv4 주소 간에 변환하는 것이므로 개인 네트워크의 모든 디바이스는 동일한 공용 IPv4 주소를 공유할 수 있습니다.
https://docs.microsoft.com/ko-kr/azure/rtos/netx-duo/netx-duo-nat/chapter1
![image](https://user-images.githubusercontent.com/62974484/186080370-8acc407e-abaf-434a-8514-ce4d5cb332ff.png) <br/> 
### <br/>

### IGW (internet gateway) 를 통해 VPC 바깥과 소통한다. 나가는 것을 out-bound, 들어오는 것을 in-bound 라고 한다.
### ELB : 고객이 트래픽을 발생시키면 IGW 로 들어와서 ELB 가 그 트래픽(요청)을 중앙관리해주고 각각의 서비스(DB, app...)를 가진 인스턴스가 잘 켜져 있는지 체크한 후 트래픽을 넘겨준다.
### ELB 는 인스턴스가 잘 켜져 있는지 주기적으로 체크한다.
### 또한 ELB 는 사용률을 체크하여 autoscaling 을 해준다.
### VGW : virtual gateway. AWS의 사설망이다.
### CGW : 개인 서버의 인터넷 망이며 CGW 라고 한다.
### 하이브리드 클라우드를 만드려면 VGW, CGW 를 연결하는데 VPN 으로 연결한다.
[EC2 autoscaling](#EC2-autoscaling)
![image](https://user-images.githubusercontent.com/62974484/186070658-10aaf5bb-e21e-4d89-bfb5-0e45c4dee0e5.png) <br/>
![image](https://user-images.githubusercontent.com/62974484/186077957-1a40ad04-4218-4b67-9f79-716bcaf23f4b.png)
### response 200 이 뜨는지 체크한다.
### <br/>

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
### CDN : content delivery network. 네트워킹 및 컨텐츠 전송
### SQL : 정형, 관계형 DB (RDS). 6개의 관계형 DB - 오라클, MS 의 msequal, MySQL, 마리아DB, AWS 의 오로라 등...
### NoSQL : 비정형, 비관계형 DB. 몽고DB
### 빅데이터는 비관계형 DB 를 선호한다.
![image](https://user-images.githubusercontent.com/62974484/186051686-6067599b-b4f4-4b80-9a3e-571fcfbec6ec.png) <br/>
![image](https://user-images.githubusercontent.com/62974484/186051697-d02a8e7f-3f91-4236-950c-480eab21e427.png) <br/>


### <br/><br/><br/>

## 모듈 2. 클라우드 컴퓨팅
### 다이나모 데이터베이스
#### 아마존을 생각해보자. 장바구니 넣는 거 insert, 바꾸는 거 update, 장바구니에서 없애는 거 delete. 수많은 사람들이 이렇게 하는데 이거를 latency 를 해결해야 한다.
#### 지연 시간을 해결해주는 방법? 이 다이나모 데이터베이스이다.
#### 작은 것은 지연 시간을 1 ms (1000분의 1초) 이내로 구현한다.
#### 서비스당 지연 시간, 사이즈 당 지연 시간 등을 구현한다.
#### <br/>
### EC2 cloud (elastic computing 2 cloud)
#### elastic : 융통성과 비슷함. 붙였다가 뗐다가 할 수 있는 것.
#### 가상 서버
#### IOPS : input output per sec. 읽기 - input / 쓰기 - output. EC2 cloud 를 사용할 때 고려해야 할 점이다.
#### AMI : amazon machine image. VM 의 image 와 같다. 크게 리눅스나 윈도우 image 가 있다. 
#### 그리고는 인스턴스 유형을 고른다. t 타입 r 타입 ...
##### 범용은 t, m 타입. 컴퓨팅(CPU 가 더 많음)은 c. 메모리가 더 많은 건 r. 스토리지는 d.
#### 사이즈를 고른다. micro, 2XL .... CPU core 몇 개와 메모리 얼마를 쓸 것인지 고르는 것이다.
#### region 을 AZ 2개 이상으로 하는 이유 : 한 개 AZ 에서 DB 가 망가지면 안 되니까,, 백업용. 두 개 이상의 AZ 에 동시에 복사하는 미러링도 가능하다. 리소스가 없을 때 다른 AZ 를 쓴다.
#### region 의 가격은 해당 도시의 땅값, 전기세 등으 고래하기 때문에 가격이 달라진다.
#### 계약은 온-디멘드와 스팟이 있고, 전용 호스트가 따로 있다.
##### 스팟은 놀고 있는 region 을 90% 할인해서 해주지만, 컴퓨팅 파워가 부족하면 그냥 뺏어버린다. 돌고 있는 프로세스도 다 죽여버림. ㅋㅋ
##### 온-디멘드는 일반적인 AWS 클라우드이다.
##### 전용 호스트는 물리적 서버를 처음부터 혼자 점유해서 쓰는 것이고 전용 인스턴스는 켤 때부터 점유하는 것.
![image](https://user-images.githubusercontent.com/62974484/186058095-c47c79c3-11ed-4605-bb0b-496b829514d0.png)

### <br/><br/><br/>

## EC2 autoscaling
### 점유를 할 때 사용률마다 조절할 수 있는 기능
### 동적 조정을 한다.
### scale up / down : 수직적 확장으로 이렇게 할 때는 인스턴스를 다시 생성할 때 다시 켜야 하는 downtime 이 발생한다.
### scale in / out : 수평적 확장으로 downtime 이 없다. 
### core / memory - min, desired, max 를 설정할 수 있다. cpu / mem 점유율에 따라 룰을 정하고 변경하는 방법으로 함. 보통 20%, 50%, 70% 로 한다.

### <br/><br/><br/>

## 메세징 서비스
### 모놀리식 : 각각의 어플리케이션이 독립적이지 않고 상호의존적인 비즈니스적 운영 방법. 움... 그러니까 비동기적이지 않다는 것. 
#### 카페에서 고객 - 주문 - 제품 - 공급 이러한 각각의 업무들이 각각 상호의존적으로 작용하는 것과 같다. 주문이 많으면 공급을 늘리고 적으면 줄이고...
### 파이썬, C#, java 어느 언어로 개발해도 되는데 각각의 언어에 독립적이지 않은 소통 방식이 필요하다. 
### 그래서 이 소통(또는 이벤트)을 표준화된 restAPI 로 쓴다.

### <br/><br/><br/>

## 큐 서비스
### 프로듀서가 작업을 생산하고, 컨슈머가 작업을 소비하는 것을 관리해주는 큐 서비스

### <br/><br/><br/>

## 서버리스 컴퓨팅 서비스
### 람다 함수로 실행한다. 파이썬의 람다 함수도 이 함수.
### 람다 함수는 꼭 누군가가 실행을 해줘야 발생한다.
![image](https://user-images.githubusercontent.com/62974484/186072836-c14dfa86-188e-4daa-ba8f-42cfff03d897.png) <br/>
![image](https://user-images.githubusercontent.com/62974484/186072875-143794cf-44e0-4ae1-a3f7-5e9dc3923bea.png)

### <br/><br/><br/>

## 컨테이너 서비스
### 도커 컨테이너 지원 서비스이다.
### ECS 는 도커 컨테이너를 직접 실행하는 것이고, 각각의 컨테이너를 수동으로 관리해주는 것이다.
### EKS 는 수많은 도커 컨테이너를 자동으로 관리해주는 완전 관리형 서비스이다.
#### ECS, EKS 모두 오픈 소스이고, AWS 에서 사용 가능하도록 하는 것이다.
![image](https://user-images.githubusercontent.com/62974484/186072940-a0c6178a-f03a-422f-b553-8654a107d9c5.png) <br/>
![image](https://user-images.githubusercontent.com/62974484/186072972-d2eb3a20-3570-4743-bbea-b4a7e57c6676.png)

### <br/><br/><br/>

## 글로벌 인프라 및 안정성
### cloudfront : CDN, chaching
#### 오리지널 region 에 컨텐츠가 있고, 각 region 에 캐싱하여 어디에 오리지날 데이터가 있다고 알려주는 '배포'를 해준다.
#### Amazon CloudFront는 .html, .css, .js 및 이미지 파일과 같은 정적 및 동적 웹 콘텐츠를 사용자에게 더 빨리 배포하도록 지원하는 웹 서비스입니다.
#### 엣지 로케이션 : 더 가까운 지역의 region 을 사용하게 해서 더 빠르게 전송
https://docs.aws.amazon.com/ko_kr/AmazonCloudFront/latest/DeveloperGuide/Introduction.html
### WAF : 보안. 파이어월
### shield : DDOS 공격 완화
### Route53 : AWS 전용 랜선. 한국에는 5개 통신사와 제휴해서 전용선을 깔았다고 한다.
### API 로 통신 : 관리 콘솔, CLI, SDK 등 어느 것으로 써도 소통할 수 있게 함

### <br/><br/><br/>

## 네트워킹
### 프라이빗 서브넷 소통
#### DX : 다이렉트 커넥트
#### AWS 전용선으로 네트워킹한다.
![image](https://user-images.githubusercontent.com/62974484/186082887-aee36d58-fad5-43c8-8b9d-8f85278f289c.png)
### VPC 가 만들어질 떄 디폴트 라우팅 테이블이 있다.
### 근데 subnet 을 만들 떄 퍼블릭과 피라이빗으로 나누는데 다 디폴트 라우팅 테이블을 사용하면 활용도가 안 좋다.
### 그래서 적어도 퍼블릭과 프라이빗은 나누어서 쓰길 적극 권장한다.
### 그리고 인바운드, 아웃바운드 허용을 어느 포트 번호에서만 허용해줄지 설정한다.
### 그리고 트래픽이 들어올 때 인바운드 / 아웃바운드 허용 범위에서 들어오면 시큐리티 그룹에서 또 필터링 해주고 그 다음에 허용된 것만 어플리케이션, DB 를 건드린다.
### <br/>
### SG : 시큐리티 그룹은 mendatory 이고 상태를 저장해서 인바운드로 들어온 정보를 저장한다.
#### 상태 저장은 인바운드로 들어왔으면 아웃바운드로 나가는 것도 허용할 수 있게 해주는 개념
### <br/>
### NACL : SG (securityy group) 말고 NACL 이 있는데 얘는 상태를 비저장한다.
#### NACL 은 상태가 비저장되기 때문에 인바운드로 들어왔는데, 아웃바운드로는 못 나간다.

### <br/><br/><br/>

## 스토리지
### filesystem, block level, object level 스토리지 타입이 있다.
### object 에는 S3 가 포함된다. 한 파일을 object 라고 하며 한 object 당 5 TB 미만이어야 하고, 최대 용량은 정해지지 않았다. 다만 자주 엑세스하지 않아도 다른 스토리지보다 요금이 비싸다.
### block 은 인스턴스 내에서 EBS 라는 외장하드와 같은 스토리지를 할당하며 최대 16 TB 를 할당해준다. 저장된 용량 당 과금하고 write, read 할 때 요금이 싸다.
#### EBS 는 인스턴스가 설치된 AZ 안에서만 엑세스할 수 있다.
### filesystem 은 네트워크로 연결되어 있어 다른 AZ 에서도 이용가능하다.
### 그래서 데이터 볼륨에 따라, 사용 용도에 따라 filesystem 을 쓸지 결정한다.
### 리눅스 AMI 를 고르면 EFS 파일시스템, 윈도우 AMI 를 고르면 FSX 파일시스템을 선택한다.

### <br/><br/><br/>

