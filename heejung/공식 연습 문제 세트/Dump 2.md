---
layout: exam
---

# Practice Exam 2

1. A global company with a large number of AWS accounts is seeking a way in which they can centrally manage billing and security policies across all accounts. Which AWS Service will assist them in meeting these goals?
    - A. AWS Organizations. ⭕️ 
    - B. AWS Trusted Advisor.
    - C. IAM User Groups.
    - D. AWS Config.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

2. Which service provides object-level storage(객체 스토리지) in AWS?
    - A. Amazon EBS.
    - B. Amazon Instance Store.
    - C. Amazon EFS.
    - D. Amazon S3. ⭕️ 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

3. A company is concerned that they are spending money on <mark style="background: #ADCCFFA6;">underutilized</mark>(활용도가 낮은) compute resources in AWS. Which AWS feature will help ensure that their applications are automatically adding/removing EC2 compute capacity to closely match the required demand?
    - A. AWS Elastic Load Balancer.
    - B. AWS Budgets.
    - C. AWS Auto Scaling. ⭕️ 
    - D. AWS Cost Explorer.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

4. Which S3 storage class is best for data with <mark style="background: #ADCCFFA6;">unpredictable</mark>(예측할 수 없는) access patterns?
    - A. Amazon S3 Intelligent-Tiering. ⭕️ 
	    - 접근 패턴이 불규칙일 때
	    - 접근 패턴을 자동으로 파악해서 가장 경제적인 계층으로 자동이동
    - B. Amazon S3 Glacier(빙하) Flexible Retrieval.
	    - 장기보관, 드물게 접근
	    - 장점: 매우 저렴하고, 거의 접근 안하는 장기 보관용 데이터
	    - 단점: 복원하는데 수 분에서 수시간 소요
    - C. Amazon S3 Standard.
	    - 자주 접근하는 데이터
	    - 매우 빠른 접근 속도
	    - 비용 가장 비쌈
	    - 웹 사이트, 앱, 실시간 데이터 처리에 자주 접근하는 데이터
    - D. Amazon S3 Standard-Infrequent(간헐적) Access.
	    - 가금 접근하는 중요 데이터
	    - 저장 비요은 낮고
	    - 요청 비용이 높고 최소 저장기간(30일) 있음
	    - 중요하지만 가끔만 접근하는 데이터

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

5. What is the AWS database service that allows you to upload data structured in **key-value format**?
    - A. Amazon DynamoDB. ⭕️ 
    - B. Amazon Aurora.
    - C. Amazon Redshift.
	    - 완전관리형 데이터 웨어하우스 서비스
    - D. Amazon RDS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

6. Which of the following is NOT correct regarding Amazon EC2 On-demand instances?
    - A. You have to pay a start-up fee when launching a new instance for the first time. ⭕️ 
    - B. The on-demand instances follow the AWS pay-as-you-go pricing model.
    - C. With on-demand instances, no longer-term <mark style="background: #ADCCFFA6;">commitments</mark>(약속) or <mark style="background: #ADCCFFA6;">upfront</mark>(미리) payments are needed.
    - D. When using on-demand Linux instances, you are charged per second based on an hourly rate.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

7. A company has moved to AWS recently. Which of the following AWS Services will help ensure that they have the proper security settings? (Choose TWO)
    - A. AWS Trusted Advisor. ⭕️ 
    - B. <mark style="background: #BBFABBA6;">Amazon Inspector</mark>(검사). ⭕️
	    - 자동 보안 평가 서비스
	    - 취약점, 잘못된 설정 등을 자동으로 스캔
	    - 보안 스캐너를 자동으로 돌려주는 서비스
	    - 소프트웨어 취약점, 패키지 업데이트 필요 여부, 네트워크 접근 설정, OS 구성 오류, EC2, Lambda, ECS, ECR 등 다양한 대산 지원
    - C. Amazon SNS.
    - D. Amazon CloudWatch.
    - E. Concierge Support Team.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, B
    </details>

8. What is the AWS feature that provides an additional level of security above the default authentication mechanism of usernames and passwords?
    - A. Encrypted keys.
    - B. Email verification.
    - C. AWS KMS.
	    - Key Management Service
	    - 암호화 키를 안전하게 생성, 저장, 관리, 사용하는 서비스
    - D. AWS MFA.
	    - Multi-Factor-Authentication
	    - 2단계 인증 (비밀번호 + 추가 인증 수단)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

9. A company is introducing a new product to their customers, and is expecting a <mark style="background: #ADCCFFA6;">surge</mark>(출현하다) in traffic to their web application. As part of their Enterprise Support plan, which of the following provides the company with architectural and scaling guidance?
	1. 트래픽이 많이 발생할거다
    - A. AWS Knowledge Center.
	    - 자주 묻는 질문과 설명 문서 제공
    - B. AWS Health Dashboard.
	    - 상태를 보여주는 대시보드 →  문제 탐지용
    - C. Infrastructure Event Management.
	    - 트래픽 급증이나 이벤트 대비를 위한 사전 아키텍처 및 확장 전략 지원
    - D. AWS Support <mark style="background: #ADCCFFA6;">Concierge</mark>(관리인) Service.
	    - 계정 및 결제 관련 도움 제공

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

10. You work as an on-premises MySQL DBA. The work of database configuration, backups, patching, and DR can be time-consuming and repetitive. Your company has decided to migrate to the AWS Cloud. Which of the following can help save time on database maintenance so you can focus on data architecture and performance?
    - A. Amazon RDS. ⭕️ 
    - B. Amazon Redshift.
    - C. Amazon DynamoDB.
    - D. Amazon CloudWatch.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

11. Which of the below is a best-practice when designing solutions on AWS?
	1. AWS의 Best Practice: 자동화, 탄력성, 비용 최적화, 빠른 실험 & 반복
    - A. Invest heavily in architecting your environment, as it is not easy to change your design later.
	    - 클라우드의 유연성을 무시한 문장
    - B. Use AWS reservations to reduce costs when testing your production environment. 🟡
	    - reservation은 장기 운영에 적합하고 테스트 환경엔 부적합
    - C. Automate wherever possible to make architectural (© ) experimentation easier. ⭕️ 
    - D. Provision(공급) a large compute(계산) capacity to handle any spikes in load
	    - 불필요한 비용 유발
	    - 오히려 Auto Scalling을 활용하여 탄력적으로 대응

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

12. According to the AWS Acceptable Use Policy, which of the following statements is true regarding penetration(침투) testing of EC2 instances?
	1. **<mark style="background: #FFB8EBA6;">Penetration Testing</mark>** : 보안 전문가가 해커처럼 시스템의 취약점을 탖는 보안 평가 방법
    - A. Penetration testing is not allowed in AWS.
    - B. Penetration testing is performed automatically by AWS to determine vulnerabilities(취약성) in your AWS infrastructure. 🟡
	    - 자동으로 AWS가 해줄 수 없음
    - C. Penetration testing can be performed by the customer on their own instances without prior authorization from AWS. ⭕️ 
	    - 고객은 자신의 인스턴스에 대해 AWS의 사전 승인 없이 침투 테스트를 실행할 수 있다.
    - D. The AWS customers are only allowed to perform penetration testing on services managed by AWS.
	    - AWs 고객은 오직 AWS가 허락하면 수행할 수 있다. →  ❌ 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

13. Which service is used to ensure that messages between software components are not lost if one or more components fail?
	1. - 소프트웨어 컴포넌트 간 메시지가, 일부 컴포넌트가 실행패도 유실되지 않도록 보장하려면 어떤 서비스를 사용해야 하는가
    - A. <mark style="background: #BBFABBA6;">Amazon SQS</mark>.
	    - Simple Queue Service
	    - 메시지를 큐에 저장하여 소비자가 나중에 처리 가능하게 함 →  메시지 유실 방지 최적
	    
    - B. <mark style="background: #BBFABBA6;">Amazon SES</mark>.
	    - Simple Email Service
    - C. AWS Direct Connect.
    - D. Amazon Connect.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

14. The principle “<mark style="background: #FFB8EBA6;">design for failure and nothing will fai</mark>l”(실패를 대비하면 실패하지 않는다) is very important when designing your AWS Cloud architecture. Which of the following would help adhere to this principle? (Choose TWO)
    - A. Multi-factor authentication.
	    - 보안 강화 기능
    - B. Availability Zones. ⭕️ 
	    - 다른 물리적 위치의 AZ에 리소스를 분산해 장애 발생 시에 고가용성 유지
    - C. Elastic Load Balancing. ⭕️ 
	    - 여러 인스턴스로 트래픽 분산
    - D. Penetration testing.
	    - 보안 취약점 탐지용
    - E. Vertical Scaling.
	    - 인스턴스 성능만 키우는 방법

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, C
    </details>

15. What is the AWS service that provides a virtual network <mark style="background: #ADCCFFA6;">dedicated</mark>(헌신하는) to your AWS account?
    - A. AWS VPN.
    - B. AWS Subnets.
    - C. AWS Dedicated Hosts.
    - D. Amazon VPC.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

16. According to the **AWS Shared responsibility model**, which of the following are the responsibility of the customer? (Choose TWO)
    - A. Managing environmental events of AWS data centers.
    - B. Protecting the confidentiality(기밀성) of data in transit in Amazon S3.
	    - HTTPS로 암호화 전송 설정은 고객이
    - C. Controlling physical access to AWS Regions.
    - D. Ensuring that the underlying(근본적인) **EC2 host** is configured properly.
	    - 호스트는 AWS가 관리
    - E. Patching applications installed on Amazon EC2.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, E
    </details>

17. Which of the following AWS services can be used as a compute(계산) resource? (Choose TWO)
    - A. Amazon VPC.
    - B. Amazon CloudWatch.
    - C. Amazon S3. 🟡
    - D. Amazon EC2.
    - E. AWS Lambda.

- 🔴 대표적인 AWS Compute 서비스 : 데이터를 처리하거나, 애플리케이션을 실행하거나, 연산을 수행할 수 있는 서버/실행 환경
	- Amazon EC2 : 가상 서버 인스턴스
	- AWS Lambda : 서버리스 함수 실행 서비스
	- ECS/EKS : 컨테이너 기반 애플리케이션 실행
	- <mark style="background: #BBFABBA6;">Fargate</mark> : 컨테이너 실행을 위한 서버리스 컴퓨트 엔진
	- Batch : 대규모 일괄 작업 실행용 컴퓨트 환경
	- <mark style="background: #BBFABBA6;">Lightsail</mark> : EC2 보다 간단한 가상 서버 서비스

- 컴퓨트가 아닌 예시
	- S3 : 저장소, 연산 수행 ❌
	- RDS: 데이터베이스 서비스
	- CloudFront : 데이터 전송 역할
	- DynamoDB : NoSQL DB, 연산보단 저장소

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D, E
    </details>

18. Your company is designing a new application that will store and retrieve photos and videos. Which of the following services should you recommend as the underlying storage mechanism?
    - A. Amazon EBS.
    - B. Amazon SQS.
    - C. Amazon S3.
    - D. Amazon Instance store.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

19. Which of the following is <mark style="background: #ADCCFFA6;">equivalent</mark>(동등한) to a user name and password and is used to authenticate your programmatic access to AWS services and APIs?
    - A. Instance Password.
    - B. Key pairs.
    - C. Access Keys.
    - D. MFA.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

20. What does Amazon <mark style="background: #BBFABBA6;">ElastiCache</mark> provide?
    - A. In-memory caching for read-heavy applications.
    - B. An Ehcache compatible in-memory data store.
	    - Encache는 자바용 캐시 라이브러리
    - C. An online software store that allows Customers to launch pre-configured software with just few clicks.
	    - <mark style="background: #BBFABBA6;">AWS Marketplace</mark>
    - D. A domain name system in the cloud.

- Elastic Cache
	- Redis 또는 Memcached를 사용하여 빠른 응답이 필요한 데이터를 메모리에 저장 (인메모리 캐시 서비스)
		- 인메모리 캐시란? 자주 사용하는 데이터를 RAM에 저장해두고 빠르게 꺼내쓰는 시스템
	- DB 호출 수를 줄이고, 애플리케이션 응답 속도를 향상
	- 읽기 작업이 많은 앱에 적합

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

21. What is the AWS service that enables you to manage all of your AWS accounts from a single master account?
    - A. AWS WAF.
    - B. AWS Trusted Advisor.
    - C. AWS Organizations.
    - D. Amazon Config.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

22. Which of the following EC2 instance purchasing options supports the Bring Your Own License (BYOL) model for almost every BYOL scenario?
    - A. Dedicated Instances.
	    - 다른 사용자와 물리 호스트 공유하지 않지만, 호스트 레벨 정보를 알 수 없음
    - B. Dedicated Hosts.
    - C. On-demand Instances.
    - D. Reserved Instances.

- BYOL : Bring Your Own License
	- 온프레미스에서 사용하던 소프트웨어 라이선스를 클라우드로 가져와 쓰는 것
- <mark style="background: #ADCCFFA6;">Dedicated</mark>(헌신하는) Host : 라이선스 조건을 세밀하게 맞출 수 있도록 물리 호스트 정보 제공 + 단독 사용

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

23. Which of the following is one of the benefits of moving infrastructure from an on-premises data center to AWS?
    - A. Free support for all enterprise customers.
    - B. Automatic data protection.
    - C. Reduced Capital Expenditure (CapEx). ⭕️ 
    - D. AWS holds responsibility for managing customer applications.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

24. Which of the following are important design principles you should adopt when designing systems on AWS? (Choose TWO)
    - A. Always use Global Services in your architecture rather than Regional Services.
    - B. Always choose to pay as you go.
    - C. Treat servers as fixed resources.
    - D. Automate wherever possible.
    - E. Remove single points of failure.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D, E
    </details>

25. Which AWS Service can be used to establish(설립하다) a dedicated, private network connection between AWS and your datacenter?
    - A. AWS Direct Connect.
    - B. Amazon CloudFront.
    - C. AWS Snowball.
    - D. Amazon Route 53.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

26. You are working on two projects that require completely different network configurations. Which AWS service or feature will allow you to isolate resources and network configurations?
    - A. Internet gateways.
    - B. Virtual Private Cloud.
    - C. Security Groups.
    - D. Amazon CloudFront.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

27. Which of the following services can help protect your web applications from SQL injection and other vulnerabilities in your application code?
    - A. Amazon Cognito.
    - B. AWS IAM.
    - C. Amazon Aurora.
    - D. AWS WAF.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

28. An organization needs to analyze and process a large number of data sets. Which AWS service should they use?
    - A. Amazon EMR.
    - B. Amazon MQ.
    - C. Amazon SNS.
    - D. Amazon SQS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

29. Based on the AWS Shared Responsibility Model, which of the following are the sole responsibility of AWS? (Choose TWO)
    - A. Monitoring network performance.
    - B. Installing software on EC2 instances.
    - C. Creating hypervisors.
    - D. Configuring Access Control Lists (ACLs).
    - E. Hardware maintenance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C, E
    </details>

30. What is the AWS service that provides you the highest level of control over the underlying virtual infrastructure?
    - A. Amazon Redshift.
    - B. Amazon DynamoDB.
    - C. Amazon EC2.
    - D. Amazon RDS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

31. What are the default security credentials that are required to access the AWS management console for an IAM user account?
    - A. MFA.
    - B. Security tokens.
    - C. A user name and password.
    - D. Access keys.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

32. In your on-premises environment, you can create as many virtual servers as you need from a single template. What can you use to perform the same in AWS?
    - A. IAM.
    - B. An internet gateway.
    - C. EBS Snapshot.
    - D. AMI.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

33. What are two advantages of using Cloud Computing over using traditional data centers? (Choose TWO)
    - A. Reserved Compute capacity.
    - B. Eliminating Single Points of Failure (SPOFs).
    - C. Distributed infrastructure.
    - D. Virtualized compute resources.
    - E. Dedicated hosting.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, C
    </details>

34. Which of the following aspects of security are managed by AWS? (Choose TWO)
    - A. Encryption of EBS volumes.
    - B. VPC security.
    - C. Access permissions.
    - D. Hardware patching.
    - E. Securing global physical infrastructure.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D, E
    </details>

35. Which statement best describes the operational excellence pillar of the AWS Well-Architected Framework?
    - A. The ability of a system to recover gracefully from failure.
    - B. The efficient use of computing resources to meet requirements.
    - C. The ability to monitor systems and improve supporting processes and procedures.
    - D. The ability to manage datacenter operations more efficiently.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

36. AWS has created a large number of Edge Locations as part of its Global Infrastructure. Which of the following is NOT a benefit of using Edge Locations?
    - A. Edge locations are used by CloudFront to cache the most recent responses.
    - B. Edge locations are used by CloudFront to improve your end users’ experience when uploading files.
    - C. Edge locations are used by CloudFront to distribute traffic across multiple instances to reduce latency.
    - D. Edge locations are used by CloudFront to distribute content to global users with low latency.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

37. What are the change management tools that helps AWS customers audit and monitor all resource changes in their AWS environment? (Choose TWO)
    - A. AWS CloudTrail.
    - B. Amazon Comprehend.
    - C. AWS Transit Gateway.
    - D. AWS X-Ray.
    - E. AWS Config.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, E
    </details>

38. Which of the following services allows you to run containerized applications on a cluster of EC2 instances?
    - A. Amazon ECS.
    - B. AWS Data Pipeline.
    - C. AWS Cloud9.
    - D. AWS Personal Health Dashboard.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

39. Which of the following services will help businesses ensure compliance in AWS?
    - A. CloudFront.
    - B. CloudEndure Migration.
    - C. CloudWatch.
    - D. CloudTrail.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

40. Which of the following procedures will help reduce your Amazon S3 costs?
    - A. Use the Import/Export feature to move old files automatically to Amazon Glacier.
    - B. Use the right combination of storage classes based on different use cases.
    - C. Pick the right Availability Zone for your S3 bucket.
    - D. Move all the data stored in S3 standard to EBS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

41. What are the AWS services/features that can help you maintain a highly available and fault-tolerant architecture in AWS? (Choose TWO)
    - A. AWS Direct Connect.
    - B. Amazon EC2 Auto Scaling.
    - C. Elastic Load Balancer.
    - D. CloudFormation.
    - E. Network ACLs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, C
    </details>

42. Which of the following activities may help reduce your AWS monthly costs?
    - A. Enabling Amazon EC2 Auto Scaling for all of your workloads.
    - B. Using the AWS Network Load Balancer (NLB) to load balance the incoming HTTP requests.
    - C. Removing all of your Cost Allocation Tags.
    - D. Deploying your AWS resources across multiple Availability Zones.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

43. What is the AWS service/feature that takes advantage of Amazon CloudFront’s globally distributed edge locations to transfer files to S3 with higher upload speeds?
    - A. S3 Transfer Acceleration.
    - B. AWS WAF.
    - C. AWS Snowmobile.
    - D. AWS Snowball.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

44. Which of the following AWS security features is associated with an EC2 instance and functions to filter incoming traffic requests?
    - A. AWS X-Ray.
    - B. Network ACL.
    - C. Security Groups.
    - D. VPC Flow logs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

45. Which AWS services can be used to improve the performance of a global application and reduce latency for its users? (Choose TWO)
    - A. AWS KMS.
    - B. AWS Global accelerator.
    - C. AWS Direct Connect.
    - D. AWS Glue.
    - E. Amazon CloudFront.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, E
    </details>

46. Using Amazon RDS falls under the shared responsibility model. Which of the following are customer responsibilities? (Choose TWO)
    - A. Building the relational database schema.
    - B. Performing backups.
    - C. Managing the database settings.
    - D. Patching the database software.
    - E. Installing the database software.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, C
    </details>

47. A company has a large amount of structured data stored in their on-premises data center. They are planning to migrate all the data to AWS, what is the most appropriate AWS database option?
    - A. Amazon DynamoDB.
    - B. Amazon SNS.
    - C. Amazon RDS.
    - D. Amazon ElastiCache.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

48. A company has created a solution that helps AWS customers improve their architectures on AWS. Which AWS program may support this company?
    - A. APN Consulting Partners.
    - B. AWS TAM.
    - C. APN Technology Partners.
    - D. AWS Professional Services.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

49. What is the AWS serverless service that allows you to run your applications without any administrative burden?
    - A. Amazon LightSail.
    - B. AWS Lambda.
    - C. Amazon RDS instances.
    - D. Amazon EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

50. Jessica is managing an e-commerce web application in AWS. The application is hosted on six EC2 instances. One day, three of the instances crashed; but none of her customers were affected. What has Jessica done correctly in this scenario?
    - A. She has properly built an elastic system.
    - B. She has properly built a fault tolerant system.
    - C. She has properly built an encrypted system.
    - D. She has properly built a scalable system.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>