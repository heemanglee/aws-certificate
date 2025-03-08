
### EC2 요금제
1. <mark style="background: #BBFABBA6;">온디맨드</mark>
	1. <mark style="background: #FFF3A3A6;">중단할 수 없는 불규칙한 단기 워크로드가 있는 애플리케이션</mark>에 적합하다. 
	2. 선결제/최소 약정은 적용되지 않는다.
	3. 중지될때까지 <mark style="background: #FFF3A3A6;">계속 실행</mark>되며, <mark style="background: #FFF3A3A6;">컴퓨팅 시간에 대해서만 지불</mark>
	4. 앱 개발 및 테스트와 <mark style="background: #FFF3A3A6;">예측할 수 없는 사용 패턴</mark>이 있는 애플리케이션 실행이 포함된다.
2. <mark style="background: #BBFABBA6;">예약 인스턴스</mark>
	1. 1년 또는 3년 약정으로 구입 가능
	2. 유형
		1. **표준 예약 인스턴스**
			1. 가용 영역을 지정할 수 있다. 이 사양을 지정하면 EC2 용량이 예약된다.
		2. **컴버터블 예약 인스턴스**
			2. EC2 인스턴스를 <mark style="background: #FFF3A3A6;">여러 가용 영역 또는 다양한 인스턴스 유형</mark>에서 실행해야 하는 경우 유용하다.
			3. 유연성이 클 경우 혜택이 좋음
		3. **EC2 Instance Savings Plans**
			1. 특정 인스턴스 패밀리 및 리전에 대해 1년 또는 3년 기간동안 지출 약정을 할 경우 Ec2 인스턴스 비용을 절감시킬 수 있다. 
		4. **스팟 인스턴스**
			2. 시작 및 종료 시간이 자유롭거나 중단을 견딜 수 있는 워크로드에 적합
			3. 미사용 아마존 EC2 컴퓨팅 용량을 사용하며 온디맨드 요금의 90%까지 절감 가능
			4. 필요에 따라 시작 및 중지할 수 있는 백그라운드 처리 작업(고객 설문 조사 데이터 처리 작업)이 있다고 가정하면, 전반적인 비즈니스 운영에는 영향을 주지 않고 처리 작업을 시작하거나 중지하려고 할 때, 스팟 요청을 하고 용량을 사용할 수 있는 경우 스팟 인스턴스가 시작된다. 하지만 스팟 요청을 했는데 용량을 사용할 수 없는 경우 요청이 성공하지 못한다.
			5. 스팟 인스턴스를 시작한 후 용량을 더 이상 사용할 수 없거나 수요가 늘면 인스턴스가 중단될 수 있다. 이 경우 백그라운드 처리 작업에는 문제가 없을 수 있다. 하지만 앱 개발 및 테스트에서응 예기치 않은 중단을 방지하는 것이 좋다. 따라서 해당 작업에 더 적합한 다른 EC2 인스턴스를 선택할 것
		5. 전용 호스트
			1. 사용자 전용 EC2 인스턴스 용량을 갖춘 물리적 서버
			2. 기존 소켓당, 코어당 또는 VM당 소프트웨어 라이선스를 사용하여 라이선스 규정 준수를 유지할 수 있다.

---
# EC2 크기조정
### 확장성
1. 필요한 리소스만으로 시작하고 확장 및 축소를 통해 수요변화에 자동으로 대응하도록 아키텍처를 설계해야 한다. 이 기능을 제공하는 AWS 서비스가 Amazon EC2 Auto Scaling이다.

### Amazon EC2 Auto Scaling
1. 이를 사용하면 변화하는 애플리케이션의 수요에 따라 <mark style="background: #FFF3A3A6;">EC2 인스턴스를 자동으로 추가하거나 제거할 수 있다.</mark>  (즉, 수평확장)
2. 2가지 접근 방식
	1. **동적 조정** : 수요 변화에 대응
	2. **예측 조정**: 예측된 수요에 따라 적절한 수의 EC2 인스턴스를 자동으로 예약
3. 예시를 들자면, 애플리케이션을 준비할 때, 최소 인스턴스 수를 1로 설정할 수 있다. 즉, 하나 이상의 EC2 인스턴스가 항상 실행 중이어야 한다. 여기서 최소 인스턴스 수를 설정할 수 있다. <mark style="background: #BBFABBA6;">최소 용량</mark>은 auto scaling 그룹을 생성한 직후 시작되는 인스턴스의 수다. 그런 다음 최소 하나의 인스턴스가 필요하다하더라도 <mark style="background: #BBFABBA6;">희망용량</mark>을 EC2 인스턴스 2개로 설정할 수 있다. 세번째 구성은 <mark style="background: #BBFABBA6;">최대 용량</mark>이다. 예를 들어 수요 증가에 대응하여 확장하도록 Auto scaling 그룹을 구성하되 인스턴스 수를 최대 4개로 제한할 수 있다.
![[Pasted image 20250308205731.png]]
---
## Elastic Load Balancing(ELB)
1. 애플리케이션 트래픽을 EC2 인스턴스와 같은 <mark style="background: #FFF3A3A6;">여러 리소스에 자동으로 분산하는 AWS 서비스</mark>다.
2. 로드 밸런서는 Auto Scaling 그룹으로 들어오는 <mark style="background: #FFB8EBA6;">모든 웹 트래픽의 단일 점점 역할을 한다.</mark> 즉, 들어오는 트래픽의 양에 맞춰 EC2 인스턴스를 추가하거나 제거하므로 이러한 요청이 로드 밸런서로 먼저 라우팅된다. 그런 다음 요청을 처리할 <mark style="background: #FFF3A3A6;">여러 리소스로 분산</mark>된다. 예를 들어 EC2 인스턴스가 여러 개인 경우 ELB는 워크로드를 여러 인스턴스로 분산하므로 어느 한 인스턴스가 대량으로 워크로드를 처리 할 필요가 없다.
3. ELB와 EC2 Auto scaling은 별도의 서비스이지만 서로 연동하여 EC2에서 실행되는 애플리케이션이 뛰어난 성능과 가용서을 제공하도록 돕는다.
![[Pasted image 20250308211639.png]]


---
## 메시징 및 대기열

### 모놀리식 애플리케이션 및 마이크로서비스
1. 애플리케이션은 여러 구성요소로 구성되어 있는데, 밀결합된 애플리케이션이 있다고 가정하자. 이러한 구성요소에는 데이터베이스 서버, 사용자 인터페이스, 비즈니스 로직 등이 포함된다. 이러한 유형의 아키텍처를 <mark style="background: #BBFABBA6;">모놀리식 애플리케이션</mark>으로 볼 수 있다. 이 애플리케이션 아키텍처 접근 방식에서는 <mark style="background: #FFF3A3A6;">한 구성요소에서 장애가 발생하면 다른 구성 요소에도 장애가 발생하고 심지어 전체 애플리케이션에서 장애가 발생할 수도 있다.</mark>
2. <mark style="background: #BBFABBA6;">마이크로서비스 접근 방식</mark>에서는 애플리케이션 구성요소가 소결합되어 있다.<mark style="background: #FFF3A3A6;"> 단일 구성요소에서 장애가 발생해고 다른 구성요소들은 서로 통신하기 때문에 계속 작동된다. </mark>
3. <mark style="background: #BBFABBA6;">Amazon Simple Notification Service(Amazon SNS)</mark>는 게시 및 구독 서비스다. 게시자는 아마존 SNS 주제를 사용해서 구독자에게 메시지를 게시한다. 구독자는 웹 서버, 이메일 주소, AWS Lambda 함수 또는 여러 옵션이 될 수 있다.
4. <mark style="background: #BBFABBA6;"> Amazon Simple Queue Service(Amzon SQS)</mark>는 메시지 대기열 서비스다. 메시지 손실이나 다른 서비스 사용 없이 소프트 웨어 구성요소 간에 메시지를 전송, 저장, 수신할 수 있다. SQS에서는 애플리케이션이 메시지를 대기열로 전송한다. 사용자 또는 서비스는 대기열에서 메시지를 검색하여 처리한 후 대기열에서 삭제한다.

---
## 서버리스 컴퓨팅

1. EC2에서 실행하려는 애플리케이션이면 다음과 같이 해야 한다.
	1. 인스턴스(가상 서버)를 프로비저닝(생성하거나 설정)한다.
	2. 사용자 코드를 업로드한다.
	3. 실행되는 동안 계속해서 인스턴스를 관리한다.
2. <mark style="background: #BBFABBA6;">서버리스</mark>란 서버에서 실행되지만 이러한 <mark style="background: #FFF3A3A6;">서버를 프로비저닝하거나 관리할 필요가 없다</mark>는 뜻이다. 서버를 유지 관리하는 대신 새로운 제품과 기능을 혁신하는 데 더 집중할 수 있다. 또 다른 이점은 서버리스 애플리케이션을 자동으로 확장할 수 있는<mark style="background: #FFF3A3A6;"> 유연성</mark>이다. 서버리스 컴퓨팅은 처리량 및 메모리와 같은 소비 단위를 수정하여 용량을 조정할 수 있다. 이는 대표적으로 **AWS Lambda**이다.

### AWS Lambda
1. 서버를 프로비저닝하거나 관리할 필요 없이 코드를 실행할 수 있는 서비스다.
2. 람다를 사용하는 경우 <mark style="background: #FFF3A3A6;">사용한 컴퓨팅 시간에 대해서만 비용을 지불한다.</mark> 코드를 실행하는 동안에만 요금이 부과된다. 사실상 모든 유형의 애플리케이션 또는 백엔드 서버리스 코드를 실행할 수 있으며 이를 관리할 필요가 없다. 
3. 람다 함수로 업로드되는 이미지의 크기를 AWS 클라우드에 맞춰 자동으로 조정하는 함수가 있을 수 있다. 이경우 새 이미지를 업로드할 때 함수가 트리거된다.
> <mark style="background: #BBFABBA6;">트리거</mark>란?
>  람다 함수를 자동으로 실행시키는 이벤트 소스, 어떤 조건에서 람다 함수가 실행될지 결정하는 요소

- 작동 방식
	- 코드를 람다에 업로드한다.
	- 이벤트 소스에서 트리거되도록 코드를 설정한다.
	- 람다는 트리거된 경우에만 코드를 실행한다.
	- 사용한 컴퓨팅 시간에 대한 요금만 지불한다. 

### 컨테이너
- <mark style="background: #FFF3A3A6;">애플리케이션의 코드와 종속성을 하나의 객체로 패키징하는 표준방식을 제공한다.</mark>
- 보안성, 신뢰성, 확장성 요구 사항이 매우 중요한 프로세스 및 워크 플로에도 컨테이너를 사용한다.

### Amazon Elastic Container Service(Amazon ECS)
- AWS에서 컨테이너식 애플리케이션을 실행하고 확장할 수 있는 <mark style="background: #FFF3A3A6;">확장성이 뛰어난 고성능 컨테이너 관리 시스템</mark>이다.
- ECS는 <mark style="background: #FFB8EBA6;">도커 컨테이너를 지원</mark>한다. 도커는 애플리케이션을 신속하게 구축, 테스트, 배포할 수 있는 소프트웨어 플랫폼이다. AWS는 오픈소스 Docker Community Edition 및 구독 기반 Doker Enterprise Edition의 사용을 지원한다. ECS에서는 API 호출을 사용하여 도커 지원 애플리케이션을 시작 및 중지할 수 있다.

### Amazon Elastic Kubernetes Service(Amazon EKS)
- AWS에서 <mark style="background: #FFF3A3A6;">쿠버네티스를 실행하는데 사용할 수 있는 완전관리형 서비스다.</mark>
- <mark style="background: #BBFABBA6;">쿠버네티스</mark>는 <mark style="background: #FFF3A3A6;">컨테이너식 애플리케이션을 대규모로 배포하고 관리하는데 사용할 수 있는 오픈 소스 소프트웨어</mark>다. 자원자로 구성된 대규모 커뮤니티에서 쿠버네티스를 유지 관리하며, 쿠버네티스 커뮤니티와 적극적으로 협력한다. 즉, 컨테이너화된 애플리케이션을 자동으로 배포, 확장, 운영, 관리해주는 오픈소스 플랫폼이다. 컨테이너를 효율적으로 운영할 수 있도록 도와주는 시스템이다.
	- 코버네티스를 사용하면 자동으로 배포, 실행해 줄 수 있고, 트래핏이 증가하면 자동 확장, 컨테이너가 꺼지면 자동 복수, 컨테이너를 효율적으로 분배해주는 기능들이 있다.
	- 쿠버네티스의 핵심 개념에는
		- 클러스트: 쿠버네티스 전체 시스템
		- 노드: 컨테이너가 실행되는 서버
		- 파드: 실행단위
		- 디플로이먼트: 컨테이터 배포 / 관리 설정
		- 서비스: 네트워크 및 로드 밸런싱
		``
``` yaml
# 디플로이먼트로 배포하고 관리하는 설정 파일, Nginx 컨테이너 3개 실행하도록 설정 가능
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3  # 컨테이너 개수 (자동 확장 가능)
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80

```


> 이 두 가지는 컨테이너 오케스트레이션 도구!
> 컨테이너 오코스트레이션 도구란, 여러 개의 컨테이너를 자동으로 배포, 관리, 확장 및 운영할 수 있도록 도와주는 도구

### AWS Fargate
- <mark style="background: #BBFABBA6;">AWS Fargate</mark>는 <mark style="background: #FFF3A3A6;">컨테이너용 서버리스 컴퓨팅 엔진</mark>이다. Amazon ECS와 EKS에서 작동한다.
- 서버를 프로비저닝하거나 관리할 필요가 없다. AWS Fargate는 자동으로 서버 인프라를 관리한다. 