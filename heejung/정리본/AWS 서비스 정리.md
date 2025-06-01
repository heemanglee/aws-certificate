
---
- #### 컨테이너 서비스
- **Amazon ECS**
	- Elastic Container Service
	- AWS 제공하는 완전관리형 오케스트레이션 서비스
	- AWS에서 컨테이너를 쉽고 안정적으로 실행할 수 있게 해주는 서비스
	- EC2 또는 Fargate 위에서 실행 가능

- **Amazon EKS**
	- Elastic Kubernetes Service
	- 완전관리형 쿠버네티스 서비스

- **Amazon Fargate**
	- 컨테이너를 실행하기 위한 <mark style="background: #FFB8EBA6;">서버리스 컴퓨팅 엔진</mark>
	- EC2 인스턴스를 직접 만들거나 관리하지 않고도 컨테이너를 실행할 수 있게 해주는 서비스
	- 서버 없는 ECS/EKS 실행 방식
	- ECS 또는 EKS 둘다 Fargate에서 실행 가능
	- CPU, 메모리 자원만 지정하면 나머지는 AWS가 관리
	- "인프라 고민 없이 컨테이너만 실행하고 싶을 때 👍"


- 📌 **쿠버네티스**
	- <mark style="background: #FFB8EBA6;">컨테이너를 자동으로 배포하고, 운영하고, 관리해주는 시스템</mark>
	- 컨테이너 오케스트레이션 플랫폼
	- 수백 개, 수천 개의 컨테이너를 띄우고 업데이트하고 죽은 걸 다시 살리고 하려면 자동화가 필수, 이걸 도와주는게 쿠버네티스
- 📌 **오케스트레이션**
	- 컨테이너 여러 개를 통합 관리하는 자동화 시스템
	- 수많은<mark style="background: #FFB8EBA6;"> 컨테이너를 자동으로 조율하고 운영</mark>
	- 대표적인 오케스트레이션 도구: 쿠버네티스

- ##### ECS와 EKS의 차이
	- **ECS**
		- AWS 자체 시스템
		- 간단
		- AWS 전용
		- 유연성: 낮음
		- AWS 방식
		- "AWS만 쓸거야" →  간단하고 효율적
	- **EKS**
		- 오픈소스 Kubernetes
		- 설정이 복잡함
		- 유연성 높음
		- K8s의 지식이 필요
		- "쿠버네티스를 공부하며 쓸거야" →  멀티 클라우드 전략





---
- #### 부가적인 AWS 서비스

- ##### **상태 관리 서비스**
	- **AWS Service Health Dashboard**
		- <mark style="background: #FFB8EBA6;">전체 AWS</mark> 서비스의 <mark style="background: #FFB8EBA6;">상태(글로벌)</mark>
		- 전체 AWS 상태 확인용
		- "서울 리전의 EC2에 장애 발생" 등 AWS 공지성 이벤트
	- **AWS Management Console**
		- 모든 AWS 서비스에 접근하고 설정하는 웹 UI
		- AWS 사용 및 관리 인터페이스
	- **Amazon CloudWatch**
		- 사용자 계정의 리소스 상태, 지표, 로그
		- EC2 CPU 사용률, Lambda 에러, 커스텀 알람 설정
	- **AWS Personal Health Dashboard**
		- 내 계정에 영향을 주는 AWS 이벤트
	-  **AWS Config**
		- <mark style="background: #FFB8EBA6;">AWS 리소스의 구성 변경 기록</mark>을 추적하고, 규정 준수를 평가하는 서비스
		- 리소스 상태 기록, 변경 이력 추적, 규정 위반 감지
		- 규정 준수 관리, 자동 감사, 보안 점검 가능
	- **AWS X-Ray**
		- 애플리케이션의 <mark style="background: #FFB8EBA6;">요청 흐름을 시각화</mark>하고 성능 병목을 분석하는 도구
		- API 요청추적, 지연 분석, 오류 지점 파악
	- **AWS CloudTrail**
		- "누가 무엇을 했는가" ⇒️ <mark style="background: #FFB8EBA6;">API 호출 기록</mark>
		- AWS 리소스 전반
		- 보안, 감시, 변경 이력 감사
		- S3에 로그 저장

- ##### 컨설팅 서비스
	-  **AWS Trusted Advisor**
		- AWS <mark style="background: #FFB8EBA6;">리소스 상태를 진단하고 비용 절감/보안 개선</mark> 등을 추천하는 도우미 서비스
		- AWS 리소스 헬스 체크 + 최적화 가이드
	- **AWS Pricing  Calculator**
		- AWS 리소스 예상 요금을 계산할 수 있는 웹 기반 도구
		- EC2, S3, RDS 등 사용량 입력 시 예상 요금 계산
	- **AWS IQ**
		- AWS 공인 전문가와 고객을 연결해주는 전문가 매칭 플랫폼
		- AWS 관련 <mark style="background: #FFB8EBA6;">문제 해결을 위해 전문가와 연결</mark>하고, 프로젝트를 의뢰하거나 컨설팅을 받을 수 있는 서비스



- ##### 배포 서비스
	- **AWS CodeDeploy**
		- EC2, Lambda, 온프레미스 서버에 애플리케이션에 자동 배포해주는 서비스
		- GitGub, CodePipeline과 연동 가능
		- 지속적 배포(CD)를 위한 서비스
		- <mark style="background: #FFB8EBA6;">애플리케이션을 서버에 배포하는 도구</mark>
			- 실제 서버나 인스턴스에 코드를 올리는 작업만 담당
	- **AWS Elastic Beanstalk**
		- 애플리케이션을 자동 배포 및 운영하는 <mark style="background: #FFB8EBA6;">PaaS 서비스</mark>
		- Node.js, Python, Java 등 다양한 런타임 지원
		- 초보자가 쉽게 웹서비스 배포 가능
	- **AWS CodePipeline**
		- <mark style="background: #FFB8EBA6;">앱을 지속적으로 배포 또는 자동화</mark>
			- 자동화가 중요 🔴
		- 코드 변경 →  테스트 →  배포 자동화
		- 전문가용
		- CI/CD 통합 가능
		- →  "코드가 푸시되면 테스트 →  빌드 →  배포까지 자동화하고 싶어"
		- CI/CD 파이프라인을 구축하고 싶을 때
	- **AWS Amplify**
		- 프론트엔드 Git 연결로 자동 빌드 & 배포

- ##### 개발 환경 서비스
	- **Amazon Cloud9**
		- 웹 기반의 통합 개발 환경
		- 브라우저에서 바로 코드 작성, 실행, 디버깅이 가능한 개발도구
		- 웹 브라우저 기반 IDE
		- ex) AWS Lambda 함수 개발 및 디버깅, EC2 서버 자동 연결 후 SSH 없이 코드 작성, GitHub 연결하여 버전 관리
		- 요약: AWS에서 제공하는 클라우드 기반 개발환경으로, 브라우저에서 바로 코딩/디버깅/협업이 가능한 툴
	- **AWS SDK**
		- <mark style="background: #FFB8EBA6;">다양한 프로그래밍 언어</mark> 등에서 코드로 AWS 서비스를 호출할 수 있도록 해주는 라이브러리

	

- ##### **인프라 관련 서비스**
	- **AWS CloudFormation**
		- 인프라를 코드로 관리할 수 있는 서비스
		- 템플릿 파일로 EC2, S3, RDS 같은 리소스를 자동 생성
	- **Amazon AMI**
		- Amazon Machine Image
		- Amazon EC2 인스턴스를 만들기 위한 <mark style="background: #FFF3A3A6;">템플릿 이미지</mark>
		- EC2 가상 머신의 운영체제, 소프트웨어, 설정 값 등이 담긴 복제본
		- 한번 만들어준 환경을 여러 인스턴스로 빠르게 복제 가능
	- **AWS OpsWorks**
		- Chef나 Puppet 기반의 <mark style="background: #FFB8EBA6;">서버 구성 자동화 서비스</mark>
		- <mark style="background: #FFB8EBA6;">EC2 인스턴스의 구성 자동화</mark>
		- ex) 웹 서버에 Nginx 설치 →  포트 열기 →  앱 배포 과정을 자동화
	- **Amazon Snowball**
		- 물리적 데이터 전송 장치(오프라인)

- ##### 마이그레이션 서비스
	- **AWS Migration Hub**
		- 온프레미스 →  AWS <mark style="background: #FFF3A3A6;">마이스레이션 과정을 중앙에서 추적/관리</mark>
		- EC2, 데이터베이스 등의 마이그레이션 상태를 시각화
		- "이 서버는 복사중, 저 서버는 마이그레이션 완료" 등을 한눈에 확인 가능
		- 마이그레이션 진행 관리
	- **AWS Application Migration Service**
		- 전체 서버를 리프트 앤 시프트 마이그레이션
		- 기존 서버를 그대로 복제
	- **AWS Database Migration Service(DMS)**
		- 데이터베이스만 마이그레이션
	- **AWS Snow Family**
		- 초대용량 데이터를 물리적으로 AWS로 이동
	

- ##### 보안 관련 서비스
	- **Amazon Inspector.**
		- Inspector: 검사
		- 자동 보안 취약점 분석 서비스
		- EC2, 컨테이너, Lambda 등의 보안 취약점 자동 탐지
	-  **Amazon Macie**
		- S2 안의 민감한 정보(주민등록번호, 카드 번호) 를 자동 탐지하고 보호하는 보안 서비스
		- 머신러닝 기반으로 자동 탐지
		- 보안 사고 예방
	-  **Amazon Artifact**
		- AWS의 보안 및 규정 준수 관련 문서를 제공하는 서비스
	- **Penetration Testing** (AWS 서비스는 아님)
		- 보안 전문가가 해커처럼 시스템의 취약점을 찾는 보안 평가 방법
	- **AWS Service Catalog**
		- <mark style="background: #FFB8EBA6;">기업 내에서 승인된 AWS 리소스 모음(카탈로그) 을 정의</mark>하고 제공하는 서비스
		- 기업 내부 사용자가 표준화된 리소스를 셀프 서비스로 생성
		- 사용대상: 보안/거버넌스를 중요시하는 대기업, 조직 내 IT 부서
	- **AWS KMS** ~~(어떻게 맨날 까먹냐...)~~
		- Key Management Service
		- 암호화 키를 안전하게 생성, 저장, 관리하는 AWS 서비스
	- **AWS CloudHSM**
		- 하드웨어 보안 모듈(HSM)을 클라우드에서 제공하는 서비스
		- 암호화 키를 하드웨어 수준에서 안전하게 생성/저장/사용할 수 있도록 해줌



- ##### 메시지 관련 서비스
	- **Amazon SQS**
		- AWS에서 제공하는 완전관리형 메시지 큐 서비스
		- 시스템 간에 비동기적으로 메세지를 안전하게 전달할 수 있도록 도와주며, 분산 시스템이나 마이크로서비스 아키텍처에서 컴포넌트 간 decoupling에 매우 유용
		- 비동기 메시지 전달
	- **Amazon MQ**
		- Message Queue
		- 비동기 메시지 전달을 위한 중간 버퍼 역할
		- 관리형<mark style="background: #FFF3A3A6;"> 메시지 브로커 서비스</mark>
		- 오픈소스 브로커인 Apache AcriveMQ 또는 RabbitMQ를 기반으로 하며, 기존 애플리케이션에서 메시지 기반 통신을 AWS로 쉽게 이전할 수 있도록 돕는다.
		- 기능: 메시지 송수신 관리, 메시지 순서 및 내구성 보장
		- 용도: 기존 시스템 간 통신, 마이크로서비스 간 decoupling
		- AWS 이전할 때 변경 없이 사용 가능
		- 메시지 순서 보장, 트랜잭션, Durable Subscription 같은 고급 기능 필요 시 유용
		- SQS/SNS보다 복잡한 전통적인 메시지 브로커 기능이 필요한 경우
		- SQS/SNS는 AWS 네이티브 서비스지만 MQ는 기존 메시지 브로커와 호환가능
			-  ✅ **기존 ActiveMQ 시스템을 AWS로 옮길 때** → Amazon MQ
			- ✅ **새로운 서버리스 기반 메시징** → SQS/SNS 권장


- ##### 데이터 처리 관련 서비스
	- **AWS Neptune**
		- 그래프 데이터베이스
	-   **Amazon EMR(Elastic MapReduce)**
		 - 빅데이터 처리 및 분석 플랫폼
		 - 오픈소스 프레임워크를 자동으로 설치, 구성, 관리해주는 완전관리형 서비스
	- **Amzon QuickSight**
		- 클라우드 기반 BI(비즈니스 인텔리전스) 도구
		- 데이터 시각화하고 대시보드를 생성할 수 있음
		- 차트/그래프/대시보드 생성, ML 기반 분석
	- **Amazon Comprehend**
		-  **<mark style="background: #ADCCFFA6;">Comprehend</mark>** : 포괄
		- 자연어 처리를 위한 AWS의 <mark style="background: #FFF3A3A6;">완전관리형 머신러닝 서비스</mark>
		- 텍스트에서 의미, 감정, 키워드, 언어 등을 자동으로 분석해주는 서비스
	-  **Amazon Kinesis**
		- Kinesis: 운동
		- 실시간 스트리밍 데이터 처리 서비스
		- 실시간으로 발생하는 대규모 데이터를 수집, 처리, 분석할 수 있도록 도와줌
	- **Amazon Redshift**
		- 완전관리형 클라우드 기반 <mark style="background: #FFF3A3A6;">데이터 웨어하우스 서비스</mark>
		- 페타바이트급 데이터도 효율적으로 처리할 수 있음
		- 대규모 분석, 대용량 분석 최적화, 페타바이트 규모
	- **Amazon Personalize**
		- 기계 학습(ML) 기반의 개인화 추천 서비스
		- 실시간 <mark style="background: #FFB8EBA6;">추천</mark>, 사용자 행동 분석, 맞춤형 콘텐츠 제공
		- ML 지식 없이도 추천 시스템을 쉽게 구축 가능
		- AI 추천이 목적 - 맞춤형 상품/콘텐츠 추천
	- **AWS Batch**
		- 대량의 배치(일괄) 컴퓨팅 작업을 자동으로 실행/관리해주는 서비스
		- 대량 데이터 처리, 과학 연산, 영상 렌더링

- ##### 기타 서비스
	-  **AWS Service Control Policies (SCPs).**
		- AWS Organizations에서 사용하는 정책(Policy)으로, 조직 내의 계정들이 사용할 수 있는 AWS 서비스나 작업을 제한하거나 허용할 수 있게
	



---
- #### **AWS Elastic Beanstalk와 AWS CodePipeline의 차이**
	- **Elastic Beanstalk**
		- <mark style="background: #FFB8EBA6;">앱을 간단히 배포하고 운영</mark>
		- 인프라 + 배포까지 자동 구성
		- 코드 업로드만 하면 AWS가 구성해줌
		- 초보자용
		- 배포대상: EC2, ALB, Auto Scaling, RDS
		- CI/CD 통합 안됨 →  내장 배포만
		- →  "코드만 주면 내가 인프라도 만들고 배포도 해줄게" 쉽고 빠르게 배포 가능
	- **AWS CodePipeline**
		- <mark style="background: #FFB8EBA6;">앱을 지속적으로 배포 또는 자동화</mark>
		- 코드 변경 →  테스트 →  배포 자동화
		- 전문가용
		- CI/CD 통합 가능
		- →  "코드가 푸시되면 테스트 →  빌드 →  배포까지 자동화하고 싶어"
		- CI/CD 파이프라인을 구축하고 싶을 때


---
- #### **AWS CloudTrail과 AWS X-Ray 차이**
	- **CloudTrail**
		- "누가 무엇을 했는가" ⇒️ API 호출 기록
		- AWS 리소스 전반
		- 보안, 감시, 변경 이력 감사
		- S3에 로그 저장
	- **AWS X-Ray**
		- "요청이 애플리케이션 내부에서 어떻게 처리되었는가" ⇒️ 성능, 지연, 에러 분석
		- 애플리케이션 코드 실행 흐름(Lambda, API Gateway 등)
		- 애플리케이션 성능 분석, 병목 추적
		- "요청이 왜 느리지", "어디서 오류 났지"
		- X-Ray 콘솔에서 시각화
