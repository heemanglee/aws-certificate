---
layout:
---

# Practice Exam 1

1. AWS allows users to manage their resources using a web based user interface. What is the name of this interface?
    - A. AWS CLI.
	    - AWS를 명령어로 조작할 수 있는 도구
    - B. AWS API.
    - C. AWS SDK.
	    - Software Development Kit
	    - 프로그래밍 언어로 AWS를 제어할 수 있는 라이브러리
    - D. AWS Management Console.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

2. Which of the following is an example of horizontal scaling(수평확장) in the AWS Cloud?
    - A. Replacing an existing EC2 instance with a larger, more powerful one.
    - B. Increasing the compute capacity(용량) of a single EC2 instance to address the growing demands of an application.
    - C. Adding more RAM capacity to an EC2 instance.
    - D. Adding **more EC2 instances of the same size to handle** an increase in traffic.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

3. You have noticed that several critical Amazon EC2 instances have been terminated(종료된). Which of the following AWS services would help you determine(결정하다) who took this action?
    - A. Amazon Inspector.
	    - 보안 취약점 및 컴플라이언스 평가 도구
    - B. AWS CloudTrail.
	    - 로그 서비스
    - C. AWS Trusted Advisor.
	    - 리소스를 최적화하고 보안을 강화할 수 있도록 추천하는 서비스
    - D. EC2 Instance Usage Report.
	    - 사용량 데이터를 정리한 리포트

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

4. Which of the below options are related to the reliability(신뢰성) of AWS? (Choose TWO)
    - A. Applying the principle of least privilege(특권) to all AWS resources.
    - B. Automatically provisioning new resources to meet demand(요청) 🔴.
    - C. All AWS services are considered Global Services, and this design helps customers serve their international users.
    - D. Providing compensation(보상) to customers if issues occur.
    - E. Ability(능력) to recover quickly from failures 🔴.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, E
    </details>

5. Which statement(진술) is true regarding the AWS Shared Responsibility Model(공유 책임 모델)?
    - A. Responsibilities vary(바꾸다) depending(부수적인) on the services used.
    - B. Security of the IaaS services is the responsibility of AWS.
    - C. Patching the guest OS is always the responsibility of AWS.
	    - 번. 게스트의 운영체제 패치는 AWS에게 책임이다.
    - D. Security of the managed services is the responsibility of the customer.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

6. You have set up consolidated(통합된) billing for several AWS accounts. One of the accounts has purchased a number of reserved instances for 3 years. Which of the following is true regarding this scenario?
    - A. The Reserved(예약된) Instance discounts can only be shared with the master account.
	    - 예약된 인스턴스 비용은 오직 마스터 계정만 공유할 수 있다.
    - B. All accounts can receive the hourly cost benefit of the Reserved Instances 🔴.
    - C. The purchased instances will have better performance(성능) than On-demand instances.
    - D. There are no cost benefits from using consolidated billing; It is for informational purposes only.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

7. A company has developed an eCommerce web application in AWS. What should they do to ensure that the application has **the highest level of availability(고가용성)**?
	1. avaliablity Zone(AZ) : 같은 이전 내 물리적 데이터센터
    - A. Deploy(배치) the application across multiple Availability Zones and Edge locations.
	    - 엣지 로케이션은 CDN(CloudFront) 용도로 사용되며, 앱 전체 고가용성에는 관여 안함
    - B. Deploy the application across multiple Availability Zones and subnets.
	    - AZ 다중 배치는 좋지만 같은 Region이면 장애 대응 불가
    - C. Deploy the application across **multiple Regions and Availability Zones.**
    - D. Deploy the application across multiple VPC’s and subnets.
	    - VPC는 네트워크 단위라 물리적 인프라 이중화와는 무관

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

8. What does AWS Snowball provide? (Choose TWO)
- AWS Snowball: 대용량 데이터를 물리적으로 AWS로 옮기거나 가져오는 장치 및 서비스

    - A. Built-in(내장된) computing capabilities(성능) that allow customers to process data locally  🔴.
    - B. A catalog of third-party software solutions that customers need to build **solutions** and run their businesses.
    - C. A hybrid cloud storage between on-premises environments and the AWS Cloud.
    - D. An Exabyte-scale data transfer service that allows you to move extremely large amounts of data to AWS 🟡.
	    - 엑사바이트는 AWS snowmobile이고, Snowball은 테라바이트 ~ 페타바이트 규모
    - E. Secure transfer of large amounts of data into and out of the AWS 🔴.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, E
    </details>

9. A company has an AWS Enterprise Support plan. They want quick and efficient guidance with their billing and account inquiries(문의하다). Which of the following should the company use?
    - A. AWS Health Dashboard.
    - B. AWS Support Concierge(관리인) 🔴.
    - C. AWS Customer Service.
    - D. AWS Operations Support (운영지원).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

10. A Japanese company hosts their applications on Amazon EC2 instances in the Tokyo Region. The company has opened new branches in the United States, and the US users are complaining of high latency(지연시간). What can the company do to reduce latency for the users in the US while minimizing costs?
    - A. Applying the Amazon Connect latency-based routing policy.
    - B. Registering a new US domain name to serve the users in the US.
	    - 새로운 도메인 이름 등록하기
    - C. Building a new data center in the US and implementing(구현) a hybrid model.
	    - 새로운 데이터센터 구축? 
    - D. Deploying new Amazon EC2 instances in a Region located in the US.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

11. An organization has a large number of technical employees who operate(작동되다) their AWS Cloud infrastructure. What does AWS provide to help organize them into teams and then assign the appropriate(적절한) permissions for each team?
    - A. IAM roles.
    - B. IAM users.
    - C. IAM user groups 🔴.
    - D. AWS Organizations.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

12. A company has decided to migrate its Oracle database to AWS. Which AWS service can help achieve(성취하다) this **without** negatively(부정적으로) impacting the functionality of the source database?
    - A. AWS OpsWorks.
    - B. AWS Database Migration Service 🔴.
    - C. AWS Server Migration Service.
    - D. AWS Application Discovery Service.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

13. Adjusting compute capacity dynamically to reduce cost is an implementation of which AWS cloud best practice?
    - A. Build security in every layer.
	    - 모든 계층에 보안 구축
    - B. <mark style="background: #ADCCFFA6;">Parallelize</mark> tasks.
	    - 작업 병렬화
    - C. Implement elasticity 🔴
	    - Elasticity: 사용량 많으면 스케일 업, 적으면 스케일 다운
    - D. Adopt monolithic architecture.
	    - 모놀리식 아키텍처

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

14. What are the benefits of having infrastructure hosted in AWS? (Choose TWO)
    - A. Increasing speed and <mark style="background: #ADCCFFA6;">agility</mark>(민첩성). 🔴
    - B. There is no need to worry about security.
    - C. <mark style="background: #ADCCFFA6;">Gaining</mark>(이득) complete control over the physical infrastructure.
	    - 물리적 인프라에 대한 완전한 통제권 획득.
    - D. <mark style="background: #ADCCFFA6;">Operating</mark>(운영하다) applications on <mark style="background: #ADCCFFA6;">behalf</mark>(대신하여) of customers.
    - E. All of the physical security and most of the data/network security are taken care of for you. 🔴

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, E
    </details>

15. What is the advantage(장점) of the AWS-recommended practice of "<mark style="background: #ADCCFFA6;">decoupling</mark>(분리)" applications?
    - A. Allows treating an application as a single, cohesive unit.
    - B. Reduces inter-dependencies so that failures do not impact other components of the application 🔴.
    - C. Allows updates of any monolithic application quickly and easily.
	    - monolithic: 모든 기능을 한 프로젝트에 넣는 구조
    - D. Allows tracking of any API call made to any AWS service.
	    - 번) 모든 AWS 서비스에 대한 API 호출을 추적할 수 있다 ? 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

16. Which of the following helps a customer view the Amazon EC2 billing activity for the past month?
    - A. AWS Budgets.
	    - 예산을 설정하고 알림을 받을 수 있는 도구
    - B. AWS Pricing Calculator.
	    - 리소스 사용하기 전 비용을 미리 계산하는 도구
    - C. AWS Systems Manager.
	    - 리소스와 인프라를 운영, 관리, 자동화하는 통합도구
    - D. AWS Cost & Usage Reports 🔴.
	    - 비용 및 사용량 보고서를 CSV로 제공

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

17. What do you gain from setting up <mark style="background: #ADCCFFA6;">consolidated</mark>(통합된) billing for five different AWS accounts under another master account?
    - A. AWS services’ costs will be reduced to half the original price.
    - B. The consolidated billing feature is just for organizational purpose.
    - C. Each AWS account gets volume discounts.
	    - 볼륨 할인을 받는다? : 사용량이 많아질수록 할인을 받는다.
    - D. Each AWS account gets five times the free-tier services capacity.
	    - 번) 각 AWS 계정은 무료 계층 서비스 용량의 5배에 달한다.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

18. What should you do in order to keep the data on EBS volumes safe? (Choose TWO)
    - A. Regularly update firmware on EBS devices.
    - B. Create EBS snapshots. 🔴
    - C. <mark style="background: #ADCCFFA6;">Ensure</mark>(지키다) that EBS data is encrypted at rest. 🔴
	    - 정지된 상태에서 암호화되었는지 확인
    - D. Store a backup daily in an external drive (외부 드라이브).
    - E. Prevent any unauthorized access to AWS data centers.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, C
    </details>

19. One of the most important AWS best-practices to follow is the cloud architecture principle of elasticity(탄력성). How does this principle improve your architecture’s design?
    - A. By automatically scaling your on-premises resources based on changes in demand.
	    - 번) 자동으로 온프레미스 리소스를 스케일링. 
	    - AWS는 온프레미스 리소스를 직접 스케일링 하지 않음
    - B. By automatically scaling your AWS resources using an Elastic Load Balancer. 🟡
	    - ELB는 트래픽 분산 역할, 스케일링 자체는 Auto Scaling 담당
    - C. By reducing <mark style="background: #ADCCFFA6;">interdependencies</mark>(상호 의존) between application components wherever possible.
	    - 상호 의존 줄이기
    - D. By automatically provisioning the required AWS resources based on changes in demand. 🔴
	    - 수요에 따른 리소스를 자동 프로비저닝

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

20. A startup company is operating on limited funds and is extremely concerned about cost overruns(침략, 넘치다). Which of the below options can be used to notify the company when their monthly AWS bill exceeds $2000? (Choose TWO)
    - A. Setup a **CloudWatch** billing alarm that triggers an SNS notification when the threshold is exceeded. 🔴
    - B. Configure the Amazon Simple Email Service to send billing alerts to their email address on a daily basis.
    - C. Configure the **AWS Budgets Service** to alert the company when the threshold is exceeded. 🔴
    - D. Configure AWS CloudTrail to automatically delete all AWS resources when the threshold is exceeded.
    - E. Configure the Amazon Connect Service to alert the company when the threshold is exceeded.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, C
    </details>

21. What does Amazon CloudFront use to distribute content to global users with low latency?
    - A. AWS Global Accelerator.
    - B. AWS Regions.
    - C. AWS Edge Locations.
    - D. AWS Availability Zones.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

22. What does the "Principle of Least Privilege" refer to?
    - A. You should grant your users only the permissions they need when they need them and nothing more.
    - B. All IAM users should have at least the necessary permissions to access the core AWS services.
    - C. All trusted IAM users should have access to any AWS service in the respective AWS account.
    - D. IAM users should not be granted any permissions; to keep your account safe.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

23. Which of the following does NOT belong to the AWS Cloud Computing models?
    - A. Platform as a Service (PaaS).
    - B. Infrastructure as a Service (IaaS).
    - C. Software as a Service (SaaS).
    - D. Networking as a Service (NaaS).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

24. The identification process of an online financial services company requires that new users must complete an online interview with their security team. The completed recorded interviews are only required in the event of a legal issue or a regulatory compliance breach. What is the most cost-effective service to store the recorded videos?
    - A. S3 Intelligent-Tiering.
    - B. AWS Marketplace.
    - C. Amazon S3 Glacier Deep Archive.
    - D. Amazon EBS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

25. Which service provides DNS in the AWS cloud?
    - A. Route 53.
    - B. AWS Config.
    - C. Amazon CloudFront.
    - D. Amazon EMR.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

26. Hundreds of thousands of DDoS attacks are recorded every month worldwide. What service does AWS provide to help protect AWS Customers from these attacks? (Choose TWO)
    - A. AWS Shield.
    - B. AWS Config.
    - C. Amazon Cognito.
    - D. AWS WAF.
    - E. AWS KMS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, D
    </details>

27. A company is deploying a new two-tier web application in AWS. Where should the most frequently accessed data be stored so that the application’s response time is optimal?
    - A. AWS OpsWorks.
    - B. AWS Storage Gateway.
    - C. Amazon EBS volume.
    - D. Amazon ElastiCache.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

28. You want to run a questionnaire application for only one day (without interruption), which Amazon EC2 purchase option should you use?
    - A. Reserved instances.
    - B. Spot instances.
    - C. Dedicated instances.
    - D. On-demand instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

29. You are working on a project that involves creating thumbnails of millions of images. Consistent uptime is not an issue, and continuous processing is not required. Which EC2 buying option would be the most cost-effective?
    - A. Reserved Instances.
    - B. On-demand Instances.
    - C. Dedicated Instances.
    - D. Spot Instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

30. Which of the following can be described as a global content delivery network (CDN) service?
    - A. AWS VPN.
    - B. AWS Direct Connect.
    - C. AWS Regions.
    - D. Amazon CloudFront.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

31. Which of the following services allows customers to manage their agreements with AWS?
    - A. AWS Artifact.
    - B. AWS Certificate Manager.
    - C. AWS Systems Manager.
    - D. AWS Organizations.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

32. Which of the following are examples of AWS-Managed Services, where AWS is responsible for the operational and maintenance burdens of running the service? (Choose TWO)
    - A. Amazon VPC.
    - B. Amazon DynamoDB.
    - C. Amazon Elastic MapReduce.
    - D. AWS IAM.
    - E. Amazon Elastic Compute Cloud.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, C
    </details>

33. Your company has a data store application that requires access to a NoSQL database. Which AWS database offering would meet this requirement?
    - A. Amazon Aurora.
    - B. Amazon DynamoDB.
    - C. Amazon Elastic Block Store.
    - D. Amazon Redshift.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

34. As part of the Enterprise support plan, who is the primary point of contact for ongoing support needs?
    - A. AWS Identity and Access Management (IAM) user.
    - B. Infrastructure Event Management (IEM) engineer.
    - C. AWS Consulting Partners.
    - D. Technical Account Manager (TAM).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

35. How can you view the distribution of AWS spending in one of your AWS accounts?
    - A. By using Amazon VPC console.
    - B. By contacting the AWS Support team.
    - C. By using AWS Cost Explorer.
    - D. By contacting the AWS Finance team.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

36. Which of the following must an IAM user provide to interact with AWS services using the AWS Command Line Interface (AWS CLI)?
    - A. Access keys.
    - B. Secret token.
    - C. UserID.
    - D. User name and password.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

37. You have AWS Basic support, and you have discovered that some AWS resources are being used maliciously, and those resources could potentially compromise your data. What should you do?
    - A. Contact the AWS Customer Service team.
    - B. Contact the AWS Abuse team.
    - C. Contact the AWS Concierge team.
    - D. Contact the AWS Security team.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

38. Select TWO examples of the AWS shared controls.
    - A. Patch Management.
    - B. IAM Management.
    - C. VPC Management.
    - D. Configuration Management.
    - E. Data Center operations.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, D
    </details>

39. In order to implement best practices when dealing with a “Single Point of Failure,” you should attempt to build as much automation as possible in both detecting and reacting to failure. Which of the following AWS services would help? (Choose TWO)
    - A. ELB.
    - B. Auto Scaling.
    - C. Amazon Athen.
    - D. ECR.
    - E. Amazon EC2.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, B
    </details>

40. A company is planning to host an educational website on AWS. Their video courses will be streamed all around the world. Which of the following AWS services will help achieve high transfer speeds?
    - A. Amazon SNS.
    - B. Amazon Kinesis Video Streams.
    - C. AWS CloudFormation.
    - D. Amazon CloudFront.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

41. A developer is planning to build a two-tier web application that has a MySQL database layer. Which of the following AWS database services would provide automated backups for the application?
    - A. A MySQL database installed on an EC2 instance.
    - B. Amazon Aurora.
    - C. Amazon DynamoDB.
    - D. Amazon Neptune.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

42. What is the AWS service that enables AWS architects to manage infrastructure as code?
    - A. AWS CloudFormation.
    - B. AWS Config.
    - C. Amazon SES.
    - D. Amazon EMR.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
    </details>

43. Under the shared responsibility model, which of the following is the responsibility of AWS?
    - A. Client-side encryption.
    - B. Configuring infrastructure devices.
    - C. Server-side encryption.
    - D. Filtering traffic with Security Groups.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
    </details>

44. What does the AWS Health Dashboard provide? (Choose TWO)
    - A. Detailed troubleshooting guidance to address AWS events impacting your resources.
    - B. Health checks for Auto Scaling instances.
    - C. Recommendations for Cost Optimization.
    - D. A dashboard detailing vulnerabilities in your applications.
    - E. Personalized view of AWS service health.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A, E
    </details>

45. You have deployed your application on multiple Amazon EC2 instances. Your customers complain that sometimes they can’t reach your application. Which AWS service allows you to monitor the performance of your EC2 instances to assist in troubleshooting these issues?
    - A. AWS Lambda.
    - B. AWS Config.
    - C. Amazon CloudWatch.
    - D. AWS CloudTrail.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

46. Your company is developing a critical web application in AWS, and the security of the application is a top priority. Which of the following AWS services will provide infrastructure security optimization recommendations?
    - A. AWS Shield.
    - B. AWS Management Console.
    - C. AWS Secrets Manager.
    - D. AWS Trusted Advisor.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>

47. Which of the following is not a benefit of Amazon S3? (Choose TWO)
    - A. Amazon S3 provides unlimited storage for any type of data.
    - B. Amazon S3 can run any type of application or backend system.
    - C. Amazon S3 stores any number of objects, but with object size limits.
    - D. Amazon S3 can be scaled manually to store and retrieve any amount of data from anywhere.
    - E. Amazon S3 provides 99.999999999% (11 9’s) of data durability.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B, D
    </details>

48. In the AWS Shared responsibility Model, which of the following are the responsibility of the customer? (Choose TWO)
    - A. Disk disposal.
    - B. Controlling physical access to compute resources.
    - C. Patching the Network infrastructure.
    - D. Setting password complexity rules.
    - E. Configuring network access rules.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D, E
    </details>

49. What does AWS provide to deploy popular technologies such as IBM MQ on AWS with the least amount of effort and time?
    - A. Amazon Aurora.
    - B. Amazon CloudWatch.
    - C. AWS Quick Start reference deployments.
    - D. AWS OpsWorks.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
    </details>

50. An organization has decided to purchase an Amazon EC2 Reserved Instance (RI) for three years in order to reduce costs. It is possible that the application workloads could change during the reservation period. What is the EC2 Reserved Instance (RI) type that will allow the company to exchange the purchased reserved instance for another reserved instance with higher computing power if they need to?
    - A. Elastic RI.
    - B. Premium RI.
    - C. Standard RI.
    - D. Convertible RI.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
    </details>