## AWS (Amazon Web Service)
AWS는 클라우드 컴퓨팅 서비스입니다. 클라우드 컴퓨팅은 온디맨드(On-Demand) 방식으로 동작하기 때문에 사용한 만큼만 비용이 청구됩니다. 

기존의 온프레미스 방식에서는 기업이 직접 서버를 구매하고 유지 및 보수를 해야 했지만, 온디맨드 방식인 AWS를 사용하면 서버를 물리적으로 구입할 필요 없이 필요한 만큼만 컴퓨팅 리소스를 빌려 사용할 수 있습니다. 또한, 사용을 완료한 후 필요 없어진 리소스는 반납하기 때문에 비용이 발생하지 않습니다.

이를 통해 초기 투자 비용을 줄이고 운영 비용만으로 효율적인 IT 인프라를 구축할 수 있습니다.

## 가상화 기술을 사용하는 AWS EC2
### 가상화 (Virtualization)
가상화(Virtualization) 기술은 하이퍼바이저를 사용하여 하나의 물리 서버에서 여러 개의 가상 머신(VM, Virtual Machine)을 실행할 수 있도록 하는 기술입니다. 하이퍼바이저란 여러 개의 가상 머신을 생성하고 실행할 수 있도록 관리하는 소프트웨어입니다.
```bash
┌───────────┬───────────┐
│  VM 1     │  VM 2     │
│ [OS 1]    │ [OS 2]    │
│ App A     │ App B     │
└───────────┴───────────┘
	       │
[ 하이퍼바이저 (Hypervisor) ]
	       │
[ 물리 서버 (Hardware) ]
```

### AWS EC2는 KVM 가상화를 사용한다.
KVM(Kernel-based Virtual Machine)은 리눅스 커널이 자체적으로 하이퍼바이저 역할을 수행하는 가상화 기술입니다. KVM은 리눅스 커널 자체가 하이퍼바이저 역할을 수행하므로 Type-1 하이퍼바이저와 같은 성능을 제공합니다. 

하이퍼바이저는 Type-1(베어메탈), Type-2(호스트형)가 존재합니다.
- 베어메탈 하이퍼바이저
  - 하이퍼바이저가 물리 서버에 직접 설치되어 VM을 생성하고 관리합니다.
  - 하이퍼바이저가 물리 서버에 직접 접근할 수 있으므로 성능이 좋습니다.
```bash
┌───────────┬───────────────────────┐
│  VM 1     │          VM 2         │
│[Guest OS 1]    │ [Guest OS 2]     │
└───────────┴───────────────────────┘
       		│
[ 하이퍼바이저 (베어메탈 하이퍼바이저, Type 1) ]
	        │
[ 물리 서버 (Hardware) ]
```
- 호스트형 하이퍼바이저
  - 하이퍼바이저가 OS 위에서 실행되어 VM을 생성하고 관리합니다.
  - 하이퍼바이저가 물리 서버에 접근하지 못하고 OS를 거쳐야 하므로, 베어메탈 방식에 비해 성능이 좋지 않습니다.
```bash
┌───────────┬───────────┐
│  VM 1     │  VM 2     │
│ [OS 1]    │ [OS 2]    │
└───────────┴───────────┘
       │
[ 하이퍼바이저 (호스트형 하이퍼바이저, Type 2)]
       │
[ 운영체제 (Host OS) ]
       │
[ 물리 서버 (Hardware) ]
```

KVM은 하드웨어 가상화(CPU, 메모리, 디스크, 네트워크 인터페이스 등을 완전히 가상화(Full Virtualization))를 통해 Guest OS가 물리적 하드웨어에 직접 접근할 수 있도록 지원합니다.
일반적으로 가상 머신은 물리적 하드웨어에 직접 접근할 수 없어 반드시 하이퍼바이저를 거쳐 하드웨어 자원을 사용해야 합니다. 그러나 KVM은 하드웨어 가상화 기술을 활용하여 가상 머신이 물리 하드웨어 자원에 직접 접근하는 것처럼 동작할 수 있게 합니다.

### 일반적인 가상화
- Type-1, Type-2 하이퍼바이저 둘 다 소프트웨어 가상화 기술을 사용합니다.
- 하이퍼바이저가 하드웨어 자원을 제어하므로 Guest OS가 CPU, 메모리, 디스크, 네트워크 카드 등 하드웨어 자원에 직접 접근할 수 없습니다.
- 하이퍼바이저를 반드시 거쳐야 하므로 성능 저하가 발생할 수 있습니다.
### KVM 가상화
- KVM은 하드웨어 가상화 기술을 사용합니다.
- 하드웨어 가상화 기술을 사용하므로, VM 내의 Guest OS가 하드웨어 자원에 직접 접근하는 것처럼 동작합니다.
- 하이퍼바이저를 거치지 않고 직접 하드웨어 자원에 접근하게 되므로 성능이 향상됩니다.
```bash
+----------------------------------+
| 물리 서버 (Physical Server)       |
| - CPU, RAM, Disk, Network       |
+----------------------------------+
          │
          ▼
+----------------------------------+
| 리눅스 커널 (KVM 모듈 포함)           |  ← KVM이 하이퍼바이저 역할 수행
| - 하드웨어 가상화 기능 (VT-x)         |
+----------------------------------+
          │
          ▼
+----------------------------------+
| Guest OS (VM)                    |
| - CPU, RAM을 직접 사용 가능          |
| - 네트워크, 디스크 직접 접근 가능.      |
+----------------------------------+
```


KVM의 핵심 원리는 하드웨어 가상화 기술을 활용하여 Guest OS가 직접 하드웨어 자원(ex. CPU, RAM, 디스크)에 접근할 수 있도록 하는 것입니다. 이는 마치 Type-1(베어메탈 하이퍼바이저) 방식으로 동작하는 것이므로 성능이 향상됩니다.
```bash
+-------------------------------------+
| AWS 물리 서버 (Host Machine)          |
+-------------------------------------+
         │
         ▼
+-------------------------------------+
|  Nitro Hypervisor (KVM 기반)         |
|  - 가벼운 하이퍼바이저 구조               |
|  - 성능 최적화 및 보안 강화               |
+-------------------------------------+
         │
         ▼
+-------------------------------------+
|  AWS EC2 인스턴스 (Guest OS)          |
|  - Ubuntu, Windows, Amazon Linux 등  |
|  - 각 인스턴스는 독립적인 리소스 사용 	      |
+-------------------------------------+
```

## AWS EC2는 기본적으로 멀티 테넌시로 사용된다.
테넌시(Tenancy)는 하나의 물리 서버를 여러 사용자가 공유하는 방식을 의미합니다. 즉, 한 개의 물리 서버를 몇 명의 사용자가 사용할 것인지 결정하는 개념입니다.
| 유형                      | 설명                    | 특징                                                           |
|-------------------------|-----------------------|--------------------------------------------------------------|
| 싱글 테넌시 (Single Tenancy) | 한 사용자가 물리 서버를 독점      | - 물리 서버를 다른 사용자와 공유하지 않음 <br> - 한 사용자가 같은 물리 서버에 여러 개의 EC2 인스턴스를 생성할 수 있음<br> - 보안성이 높고 성능 예측 가능 <br> - 비용이 높음 |
| 멀티 테넌시 (Multi-Tenancy)  | 여러 사용자가 하나의 물리 서버를 공유 | - 서버 자원을 여러 사용자(VM)와 공유 <br> - 비용이 낮고 리소스 활용률 증가 <br> - 보안 정책 필요 |

AWS EC2는 기본적으로 멀티 테넌시 환경을 제공합니다. AWS EC2는 하나의 물리 서버를 가상화하여 여러 개의 EC2 인스턴스를 실행할 수 있습니다. 이 EC2 인스턴스들은 한 사용자에게만 제공되는 것이 아닌, 여러 사용자에게 제공될 수도 있습니다. 따라서 한 물리 서버를 여러 사용자가 공유할 수 있는 구조이므로 AWS EC2는 멀티 테넌시 환경으로 제공된다고 할 수 있습니다.

### AWS에서 제공하는 3가지 테넌시
- Shared Tenancy ( 공유 테넌시) - 기본값, 멀티 테넌시
  - 기본적으로 모든 EC2 인스턴스는 멀티 테넌시 환경에서 실행됩니다.
  - 여러 사용자가 사용하는 EC2 인스턴스가 하나의 물리 서버에서 동작할 수 있습니다.
  - 비용이 가장 저렴합니다.
- Dedicated Instance (전용 인스턴스) - 싱글 테넌시
  - 하나의 물리 서버가 다른 AWS 계정과 공유되지 않습니다.
  - 같은 계정 내의 여러 EC2 인스턴스가 같은 물리 서버에서 실행될 수도 있습니다.
  - EC2가 생성될 물리 서버는 AWS가 결정합니다.
  - 멀티 테넌시보다 비용이 높고, 전용 호스트보다 낮습니다.
- Dedicated Host (전용 호스트) - 싱글 테넌시
  - 사용자가 특정 물리 서버를 직접 예약하고 독점으로 사용합니다.
  - 같은 계정 내의 여러 EC2 인스턴스가 반드시 같은 물리 서버에서 실행됩니다.
  - 사용자가 사용할 물리 서버는 AWS가 아닌 사용자가 직접 결정합니다.
  - 비용이 가장 비쌉니다.
```bash
+-----------------------------------------------------+
|  AWS 데이터 센터 (물리 서버 그룹)                     |
+-----------------------------------------------------+
         │
         ├── [멀티 테넌시] Shared Tenancy (기본)  
         │       ├── 고객 A의 EC2 인스턴스
         │       ├── 고객 B의 EC2 인스턴스
         │       ├── 고객 C의 EC2 인스턴스
         │
         ├── [싱글 테넌시] Dedicated Instance 
         │       ├── 고객 A의 EC2 인스턴스
         │       ├── (같은 계정 내 다른 인스턴스와 공유될 수도 있음)
         │
         └── [완전한 싱글 테넌시] Dedicated Host 
                 ├── 고객 A의 EC2 인스턴스 전용 물리 서버
                 ├── 다른 고객과 절대 공유되지 않음

```

| 구분                     | 전용 인스턴스 (Dedicated Instance) | 전용 호스트 (Dedicated Host)             |
|------------------------|------------------------------|-------------------------------------|
| 물리 서버 선택 가능 여부         | AWS가 자동으로 물리 서버를 선택          | 사용자가 특정 물리 서버를 직접 선택                |
| 인스턴스 배치 방식             | AWS가 필요에 따라 여러 물리 서버에 배치 가능  | 사용자가 예약한 물리 서버에서만 실행                |
| AWS가 물리 서버를 변경할 수 있는가? | 가능 (AWS가 자동 관리)              | 불가능 (사용자가 직접 물리 서버 지정)              |
| 라이선스 관리 (BYOL)         | 라이선스 직접 관리 불가능               | 기존 Windows, Oracle 등의 라이선스 직접 적용 가능 |
| 비용                     | 전용 호스트보다 저렴                  | 가장 비쌈                               |

## EC2의 여러 가지 요금제 옵션
### 온디맨드 (On-Demand)
- 필요할 때 즉시 인스턴스를 생성하고, 사용한만큼만 비용을 지불합니다.
- 약정을 맺고 사용하는 것이 아닌, 필요할 때 생성하고 필요없을 때 반납합니다.
- EC2 인스턴스를 사용한 시간만큼만 비용이 발생합니다.

### Savings Plans
- 1년 또는 3년 단위로 약정하여 EC2 비용을 줄이는 방식입니다.
- 예약 인스턴스 요금제보다 유연하게 사용할 수 있습니다.
- 온디맨드 방식보다 최대 66% 비용을 절감할 수 있습니다.
#### Compute Savings Plans
- 완전한 유연성을 제공합니다.
- 사용하던 EC2 인스턴스의 리전과 패밀리를 변경할 수 있습니다.
  - ex. us-eash-1 -> ap-northeast-2
  - ex. m5.large -> c5.xlarge
- 테넌시 변경이 가능합니다.
#### EC2 Instance Savings Plans
- Compute Savings Plans보단 유연성이 낮지만, 예약 인스턴스보단 유연성이 높습니다.
- 사용하던 EC2의 리전은 변경할 수 없으나, 패밀리는 변경할 수 있습니다.
- 테넌시 변경이 가능합니다.

### 예약 인스턴스 (Reserved Instances)
- 1년 또는 3년 단위로 약정하여 EC2 비용을 줄이는방식입니다.
- 온디맨드 방식보다 최대 72% 비용을 절감할 수 있습니다.
#### 표준 RI (Standard Reserved Instances)
- 약정을 맺은 EC2 인스턴스의 리전과 유형을 변경할 수 없습니다.
  - ex. ap-northeast-2에서 m5.large 유형을 1년 약정으로 구매했다면, us-east-1이나 c5.large로 변경할 수 없습니다.
- 인스턴스 패밀리, OS, 리전, 테넌시를 변경할 수 없습니다.
- 온디맨드 방식 대비 최대 72%까지 비용을 절감할 수 있습니다.
#### 변동 RI (Convertible Reserved Instances)
- 약정을 맺은 EC2 인스턴스의 리전을 변경할 수 없으나, 유형은 변경할 수 있습니다.
  - ex. ap-northeast-2에서 m5.large 유형을 1년 약정으로 구매했다면, us-east-1으로 리전은 변경할 수 없으나, m5.xlarge로 변경은 가능합니다.
- 인스턴스 패밀리, OS, 테넌시를 변경할 수 있습니다.
- 온디맨드 방식 대비 최대 54%까지 비용을 절감할 수 있습니다.

### 스팟 인스턴스 (Spot Instances)
- AWS의 유후 EC2 인스턴스를 저렴한 가격에 구매할 수 있습니다.
- 구매한 EC2 인스턴스를 AWS가 필요하게 될 때 사전 예고 후 회수할 수 있습니다. 
  - 갑작스럽게 회수되어도 상관없는 작업을 실행하는 데 사용해야 합니다. 예를 들어, 배치 작업, CI/CD, 빅데이터 처리가 있습니다.
- 온디맨드 방식 대비 최대 90%까지 절감된 비용으로 구매할 수 있습니다.

### 전용 호스트 (Dedicated Host)
- 완전히 독립된 물리 서버를 할당받아 EC2 인스턴스를 실행합니다.
- 자체적으로 소유한 라이센스를 사용할 수 있으므로 라이센스 사용 비용이 발생하지 않습니다. 즉, AWS가 제공하는 라이센스를 사용하지 않으므로 비용이 발생하지 않습니다. (= BYOL, Bring Your Own License)
- 다수의 EC2 인스턴스를 물리적으로 격리하여 운영해야할 때 사용됩니다. 따라서 다른 EC2 인스턴스와 완전히 격리된 환경에서 실행됩니다. (= 싱글 테넌시)
  - 하이퍼바이저를 사용하여 같은 물리 서버에 여러 개의 가상 머신을 생성하여 여러 대의 EC2 인스턴스를 실행하는 것과 반대되는 개념입니다.

## 증가하는 트래픽을 ASG + ELB로 대응하는 방법
사용자가 증가하여 트래픽이 증가했을 때, 하나의 EC2 인스턴스로 운영할 경우 서버에 부하가 생겨 장애로 이어질 수 있습니다. ASG를 사용하지 않는다면 트래픽에 대응하기 위해 EC2 인스턴스를 직접 추가해야 하고, 부하가 줄어들 때는 다시 수동으로 삭제해야 합니다.

ASG(Auto Scaling Group)를 사용하면 설정한 임계치에 도달했을 대 자동으로 EC2 인스턴스를 추가로 생성합니다. 또한, 헬스 체크를 통해 생성되어 있는 EC2 인스턴스 중에서 비정상적인 인스턴스를 자동으로 교체하는 작업도 수행합니다. ASG에 생성할 EC2 인스턴스의 최소, 최대, 희망 개수를 입력할 수 있고, 평소에는 희망 개수만틈 유지되다가 트래픽에 따라 최소~최대 개수로 변경됩니다.

하지만 ASG만 사용하고 ELB(Elastic Load Balancer)를 사용하지 않을 경우, 아무리 EC2 인스턴스를 많이 생성하더라도 특정 인스턴스로 트래픽이 집중될 수 있습니다. 또한, ASG에 의해 추가된 EC2 인스턴스로 트래픽이 전달되지 않는 문제도 발생합니다. ELB는 트래픽을 여러 EC2 인스턴스에 분산하는 역할을 하므로, ASG를 사용할 경우 반드시 ELB를 함께 사용해야 합니다. ELB를 사용할 경우, ASG에 의해 EC2 인스턴스가 추가되었을 때 트래픽이 분산되는 대상으로 자동으로 추가됩니다. 

- ASG만 단독으로 사용했을 때
<img width="579" alt="스크린샷 2025-03-02 오후 2 18 59" src="https://github.com/user-attachments/assets/6d4cfc33-865d-4e1c-9152-e6a2750fe070" />

- ASG + ELB를 사용했을 때
<img width="765" alt="스크린샷 2025-03-02 오후 2 14 58" src="https://github.com/user-attachments/assets/d513d345-abe7-439f-a894-9ee8c2a097ac" />

## AWS 아키텍처 구성은 항상 “가용성”을 고려할 것
가용성(Availability)는 장애가 발생했을 때 서비스가 유지되는 것 뿐만 아니라, 서비스의 성능을 일정 수준 이상으로 보장하는 것입니다. 즉, 장애가 발생했을 때 죽지 않는 서비스가 아닌 사용자가 기대하는 성능을 계속 유지하는 서비스를 의미합니다.

가용성을 확보하기 위해서는 하나의 AZ에 모든 AWS 서비스를 배치하는 것이 아닌, 다중 AZ에 분산하여 배치해야 합니다. 단순히 분산 배치하는 것뿐만 아니라, 장애를 감지하고 자동으로 대응할 수 있어야 합니다.

### 가용성을 위한 요소들
- 다중 AZ 배포
  - EC2 : ASG를 사용하여 여러 AZ에 분산 배치해야 합니다.
  - RDS : Amazon RDS의 경우 다중 AZ를 사용하고, Aurora RDS의 경우  6중 스토리지 계층을 제공합니다.
  - ELB : 트래픽을 특정 인스턴스가 아닌, 여러 AZ에 분산되어 있는 EC2 인스턴스에게 분배해야 합니다.
  - 자동 복구 및 확장
    - ASG : 헬스 체크를 통해 비정상적인 인스턴스를 종료하고 새로운 인스턴스를 생성합니다.
    - Aurora RDS : 6중 스토리지 계층을 사용하여 특정 스토리지 노드에 장애가 발생해도 다른 스토리지 노드가 영향을 받지 않도록 설게되어 있습니다.
- 장애 감지 및 복구
  - ASG : 헬스 체크를 통해 비정상적인 EC2 인스턴스를 종료하고 새로운 인스턴스를 생성합니다.
  - ELB : 헬스 체크를 통해 비정상적인 EC2 인스턴스를 제외하고 정상적인 인스턴스로 트래픽을 전송합니다.

## AWS CloudFront를 사용하여 지연시간 줄이기
### CDN (Content Delivery Network)
CND은 정적 데이터(ex. 이미지, 동영상, 웹사이트)를 사용자에게 빠르게 전달하기 위해 사용됩니다. 

기본적으로 정적 데이터들은 서버를 운영하는 데이터 센터에 저장됩니다. 만약 데이터 센터가 서울에 있는데 미국에 있는 사용자가 정적 데이터를 요청할 경우 지연(Latency)이발생하게 될 것입니다. (지연 시간: 사용자가 요청을 보낸 후 응답을 받을 때까지 걸리는 시간) 

데이터 센터와 사용자 간의 지리적 거리가 멀어 지연 시간이 길어지는 문제를 해결하기 위해 CDN(Content Delivery Network)가 등장했습니다. CDN은 전 세계 여러 지역(엣지 로케이션)에 원본 데이터를 캐싱하여 사용자에게 더 가까운 서버에서 데이터를 제공하는 방식입니다. 
- 데이터 센터 : 서울(ap-northeast-2)
- 사용자의 위치 : 미국(us-east-1)
CDN 서버 덕분에 사용자는 서울에서 데이터를 받아오는 것이 아닌, 미국과 가까운 곳에 위치한 엣지 로케이션에서 데이터를 전달받습니다. 엣지 로케이션에 요청에 대한 데이터가 없을 경우 데이터 센터에서 원본 데이터를 가져와 캐싱한 후에 사용자에게 전달됩니다. 

CDN을 사용했을 때의 장점은 다음과 같습니다.
- 데이터 센터와 지리적으로 거리가 멀더라도 빠른 응답 가능
- 서버 부하 감소 (데이터 센터로 트래픽이 몰리지 않기 때문)
- 대역폭 비용 절감

### AWS CloudFront
<img width="1138" alt="스크린샷 2025-03-02 오후 3 41 33" src="https://github.com/user-attachments/assets/7bdd0aee-054c-4a5f-a7e7-71fe31f3255b" />

AWS CloudFront는 AWS에서 제공하는 CDN 서비스입니다. 

- CloudFront 사용 전
```bash
사용자(us-east-1) ───→ EC2(ap-northeast-2)
(응답 속도 느림, 네트워크 비용 증가)
```
- CloudFront 사용 후
```bash
사용자(us-east-1) ───→ 엣지 로케이션(미국) ───→ EC2(ap-northeast-2) (최초 요청)
                             └── (이후 요청) 캐싱된 데이터 제공
(응답 속도 빠름, 서버 부하 감소, 비용 절감)
```
1. 사용자가 정적 웹사이트를 요청합니다.
2. ClountFront가 사용자의 위치를 파악하여 가장 가까운 엣지 로케이션에 요청을 전달합니다.
3. 엣지 로케이션에 캐싱된 데이터가 있으면 해당 데이터를 응답으로 전달합니다.
4. 캐싱된 데이터가 없다면 데이터 센터가 위치한 원본 서버에서 콘텐츠를 가져옵니다.
5. 가져온 콘텐츠는 엣지 로케이션에 캐싱됩니다.
6. 이후 동일한 요청이 발생하면 엣지 로케이션에서 바로 응답이 가능합니다.

## 보안 그룹(Security Group)과 네트워크 ACL의 차이점
보안 그룹과 네트워크 ACL 둘 다 VPC 내에서 트래픽을 제어하는 데 중요한 역할을 합니다. 
각각의 차이점은 다음과 같습니다.
| 구분          | 보안 그룹 (Security Group)  | 네트워크 ACL (Network ACL)           |
|-------------|-------------------------|----------------------------------|
| 레벨(Level)   | 인스턴스(Instance) 단위       | 서브넷(Subnet) 단위                   |
| Stateful 여부 | Stateful (응답 트래픽 자동 허용) | Stateless (응답 트래픽도 명시적으로 허용해야 함) |
| 적용 대상       | EC2, RDS와 같은 개별 리소스     | 서브넷 내 모든 리소스                     |
| 규칙 적용 방식    | 허용(Allow) 규칙만 가능        | 허용(Allow) 및 거부(Deny) 규칙 모두 가능    |
| 기본 규칙       | 모든 트래픽 차단               | 기본적으로 모든 트래픽 허용 또는 차단 가능         |

### EC2(퍼블릭 서브넷) -> RDS(프라이빗 서브넷) 요청-응답 과정
EC2와 RDS는 동일한 VPC에 존재하되, 서브넷은 다릅니다.
- 애플리케이션(EC2) : 퍼블릭 서브넷에 존재
- RDS : 프라이빗 서브넷에 존재

1. EC2 -> RDS 요청
   1. TCP 3306 포트로 요청이 발생합니다.
   2. 퍼블릭 서브넷의 네트워크 ALC이 EC2의 아웃바운드 트래픽을 허용해야 합니다.
      1. 퍼블릭 서브넷의 네트워크 ACL에서 TCP 3306 포트 트래픽을 아웃바운드 트래픽으로 허용해야 합니다.
   3. 프라이빗 서브넷의 네트워크 ACL이 퍼블릭 서브넷에서 오는 트래픽을 인바운드로 허용해야 합니다.
      1. 프라이빗 서브넷의 네트워크 ACL에서 TCP 3306 포트 트래픽을 인바운드 트래픽으로 허용해야 합니다.
   4. RDS의 보안 그룹에서 퍼블릭 서브넷의 EC2에서 오는 트래픽을 인바운드로 허용해야 합니다.
      1. RDS 보안 그룹에서 TCP 3306 포트의 트래픽을 인바운드 트래픽으로 허용해야 합니다.
2. RDS -> EC2 응답
   1. TCP 3306 포트로 응답을 전송합니다.
   2. 보안 그룹은 stateful하므로, RDS 보안 그룹이 인바운드 트래픽으로 허용했다면 응답 또한 아웃바운드 트래픽으로 자동으로 허용됩니다.
   3. 프라이빗 서브넷의 네트워크 ACL이 RDS의 응답을 아웃바운드 트래픽으로 허용해야 합니다.
      1. 프라이빗 서브넷의 네트워크 ACL에서 TCP 3306 포트의 트래픽을 아웃바운드 트래픽으로 허용해야 합니다.
   4. 퍼블릭 서브넷의 네트워크 ACL이 프라이빗 서브넷에서 오는 응답을 인바운드 트래픽으로 허용해야 합니다.
      1. 퍼블렉 서브넷의 네트워크 ACL에서 TCP 3306 포트의 트래픽을 인바운드 트래픽으로 허용해야 합니다.

- EC2 -> RDS 요청 과정 요약
| 순서  | 적용 대상          | 동작                            |
|-----|----------------|-------------------------------|
| 1   | 퍼블릭 서브넷의 NACL  | 아웃바운드: TCP 3306 → 프라이빗 서브넷 허용 |
| 2   | 프라이빗 서브넷의 NACL | 인바운드: TCP 3306 ← 퍼블릭 서브넷 허용   |
| 3   | RDS 보안 그룹      | 인바운드: TCP 3306 ← EC2 보안 그룹 허용 |
- RDS -> EC2 응답 과정 요약
| 순서  | 적용 대상          | 동작                           |
|-----|----------------|------------------------------|
| 4   | RDS 보안 그룹      | Stateful: 응답 자동 허용           |
| 5   | 프라이빗 서브넷의 NACL | 아웃바운드: TCP 3306 → 퍼블릭 서브넷 허용 |
| 6   | 퍼블릭 서브넷의 NACL  | 인바운드: TCP 3306 ← 프라이빗 서브넷 허용 |

## AWS S3(Simple Storage Service)
AWS S3는 AWS에서 제공하는 객체 스토리지 서비스로, 데이터를 안전하게 저장하고 관리할 수 있는 기능을 제공합니다. S3는 버킷(Bucket)과 객체(Object)로 구성됩니다.
- 버킷 : 데이터를 저장하는 컨테이너
- 객체 : 개별 파일

S3는 99.999999999% 내구성을 보장합니다. 이는 데이터를 여러 개의 가용 영역에 복제하여 저장하기 때문에 가능합니다. 특정 AZ에 장애가 발생하더라도 다른 AZ에 저장된 복제본을 통해 데이터를 복구할 수 있습니다. 또한, S3는 주기적으로 손상된 데이터를 감지하여 복구하므로 데이터가 손상되거나 유실될 가능성이 낮습니다.

### S3는 증분 업데이트를 지원하지 않는다.
증분 업데이트(Incremental)란 전체 데이터를 다시 쓰는 것이 아닌, 변경된 부분만 업데이트하는 방법입니다. A 파일에 작성된 내용 일부를 수정했을 때, 증분 업데이트의 경우 수정된 부분만 업데이트하면 되지만, 전체 업데이트의 경우 전체 데이터를 다시 써야합니다. 증분 업데이트는 데이터 전송량을 감소시킨다는 장점이 있습니다.

- AWS S3 
  - 데이터를 하나의 객체(Object) 단위로 저장합니다.
    - ex. 1GB 크기의 데이터를 업로드하면 그 파일 자체가 하나의 객체로 S3에 저장됩니다.
  - 객체는 데이터 + 메타 데이터 + 고유한 키로 구성됩니다.
- AWS EBS
  - 데이터를 고정 크기의 블록 단위로 나누어 저장합니다.
    - ex. 1GB 크기의 데이터를 업도르하면 블록 단위로 여러 개로 쪼개어져서 EBS에 저장됩니다.

AWS S3는 객체 단위로 데이터를 관리하는 객체 스토리지(Object Storage)이므로 증분 업데이트를 지원하지 않습니다. 따라서 S3에서 객체가 변경되면 기존의 객체를 삭제하고 새로운 객체를 통째로 다시 저장해야 합니다. 즉, 기존 객체의 일부분만 수정했더라도 새로운 객체로 다시 저장해야 합니다.
반면에 AWS EBS(Elastic Block Store)는 데이터를 블록 단위로 저장하므로 증분 업데이트를 지원합니다. 따라서 전체 데이터를 다시 쓸 필요 없이, 변경된 블록만 업데이트하면 됩니다. 
<img width="945" alt="스크린샷 2025-03-02 오후 9 26 08" src="https://github.com/user-attachments/assets/e3ac47d2-3e78-488a-9e81-0932cf7aaac9" />

또한, EBS는 스냅샷을 사용하여 데이터를 백업할 수 있습니다. EBS 스냅샷도 마찬가지로 증분 업데이트를 통해 변경 사항을 저장합니다. 처음에는 EBS에 저장된 모든 데이터를 백업하고, 이후에는 변경 사항에 대해서만 백업됩니다.

## AWS EFS (Elsatic File System)
![image](https://github.com/user-attachments/assets/16f2c0ff-def9-4fe1-a5f2-7bf31f449f9d)

AWS EFS(Elastic File System)은 여러 EC2 인스턴스가 동시에 접근할 수 있는 공유 파일 시스템입니다. EFS는 리전 단위 서비스로서, 리전 내 여러 가용 영역(AZ)에 걸쳐 데이터를 자동으로 복제하여 저장합니다. 따라서 한 AZ에서 장애가 발생해도 다른 AZ에 저장되어 있는 복제본을 통해 데이터 접근이 가능하므로 내구성이 뛰어납니다. 또한, EFS는 완전 관리형 서비스로, 저장 공간이 부족하면 자동으로 확장됩니다.

반면에 EBS(Elsatic Block Store)는 EC2 인스턴스와 동일한 가용 영역(AZ)에서만 사용할 수 있는 블록 스토리지입니다. 따라서 EBS와 다른 AZ에 존재하는 EC2 인스턴스는 EBS에 접근할 수 없습니다. 또한, EBS가 존재하는 가용 영역에 장애가 발생하면 EBS 볼륨도 사용할 수 없게 됩니다. EBS는 EFS와 달리 용량이 부족할 때 자동으로 확장하지 않기 때문에 사용자가 수동으로 크기를 확장해야 합니다.

## 최소 권한 원칙 (Principle of Least Privilege)
최소 권한 원칙이란 사용자(User), 그룹(Group), 서비스(Service) 등이 수행해야 하는 작업에 필요한 최소한의 권한만 부여하는 것을 의미합니다.

최소 권한 원칙을 준수해야하는 이유는 보안을 위해서입니다.
- 모든 권한이 부여된 루트 사용자(root user) 또는 과도한 권한을 가진 사용자가 해킹을 당할 수 있습니다.
- 실수로 인한 데이터 손실 또는 중요한 설정 정보를 변경할 수 있습니다.
이를 방지하기 위해서 AWS에서는 IAM 정책(Policy)을 사용하여 AWS의 특정 리소스에 대한 접근 권한을 세밀하게 제어할 수 있습니다.

최소 권한 원칙을 준수하는 방법은 다음과 같습니다.
- 루트 사용자를 사용하지 않고, 사용할 권한만 부여된 IAM 사용자 및 역할(Role)을 사용합니다.
- IAM 정책을 통해 역할(Role)과 사용자(User)에게 필요한 권한만 부여합니다.

## 정책(Policy)와 역할(Role)
### 정책 (Policy)
정책(Policy)은 AWS 리소스에 대한 접근 권한을 정의하는 JSON 문서입니다. 정책은 IAM 사용자(User), 그룹(Group) 그리고 역할(Role)에 부여되어 특정 AWS 서비스에 대한 접근을 허용(Allow)하거나 거부(Deny)할 수 있습니다.

정책의 특징은 다음과 같습니다.
- 정책은 JSON 형식으로 작성되며, “Effect” 필드를 사용하여 AWS 서비스의 접근 권한을 정의합니다.
- 특정 AWS 서비스에 대한 읽기, 쓰기, 삭제 등 “Action”을 제어할 수 있습니다.
아래의 경우 `my-secure-bucket` 이름의 S3 버킷에 존재하는 객체들을 읽을 수 있는 권한을 부여한 정책입니다.
```bash
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-secure-bucket/*"
    }
  ]
}
```

### 역할(Role)
역할(Role)은 IAM 사용자(User) 또는 AWS 서비스가 특정 AWS 리소스에 접근할 수 있는 권한을 임시로 부여하는 방법입니다. 역할은 정책(Policy)를 통해 권한을 가지지만, IAM 사용자(User)에게 직접 할당되는 것이 아닌 `AssumeRole`을 통해 일시적으로 부여됩니다.

역할(Role)의 특징은 다음과 같습니다.
- IAM 사용자에게 직접 할당되는 것이 아닌, AssumeRole을 통해 부여됩니다.
- AWS 서비스가 다른 AWS 리소스에 접근할 수 있도록 할 수 있습니다.
- 임시 보안 자격 증명이므로, 만료 시간 이후에는 역할에 부여된 정책을 사용할 수 없습니다.

## IAM Group
AWS 계정 내에는 여러 IAM User가 존재할 수 있습니다. 각 User마다 개별적으로 정책(Policy)를 부여하여 AWS 리소스에 접근할 수 있도록 합니다. 동일한 정책이 여러 User에게 필요하다면 개별적으로 할당하는 것보단 IAM Group을 사용하여 효율적으로 정책을 부여할 수 있습니다. IAM Group에 정책을 부여하면 해당 Group에 속한 모든 User가 동일한 정책을 부여받게 됩니다. 

IAM Group을 사용하면 여러 User에게 일관된 접근 제어를 유지할 수 있고, 새로운 User가 생성되더라도 Group에 추가하는 것만으로도 자동으로 동일한 정책을 부여받게 됩니다.

## AWS Organizations
```bash
AWS Organizations
│
├── Management Account (ex: billing@example.com)
│
├── Organizational Unit (OU) - Development
│   ├── Dev Account (dev@example.com)
│   ├── QA Account (qa@example.com)
│
├── Organizational Unit (OU) - Production
│   ├── Staging Account (staging@example.com)
│   ├── Production Account (prod@example.com)
│
└── SCP 적용 가능 (ex: 특정 리전 사용 제한)
```
AWS Organizations는 여러 개의 AWS 계정을 중앙에서 통합 관리할 수 있는 서비스입니다. 특히, 보안, 결제, 정책 적용을 일괄적으로 관리할 수 있다는 점에서 중요한 서비스입니다.

AWS Organizations는 개별 계정의 IAM을 직접적으로 관리하는 서비스가 아닙니다. 즉, A 계정에 생성된 IAM User, Group, 정책 등을 Organizations에서 직접 제어할 수 없습니다. 하지만 서비스 제어 정책(SCP, Service Control Policy)을 사용해서 조직 내의 모든 계정에 대한 정책을 강제 적용할 수 있습니다. 예를 들어, 조직에 3개의 계정(A, B, C)가 존재할 때, A 계정은 ap-northesat-2 리전을 사용하지 못하도록 제한할 수 있습니다. 

또한, 각 계정의 비용이 개별적으로 청구되는 것보단, AWS Organizations의 통합 결제(Consolidated Billing) 기능을 통해 할인 혜택을 받을 수도 있습니다. 

### OU (Organizational Unit)
OU(Organizational Unit)는 AWS Organizations에서 여러 개의 AWS 계정을 그룹화하는 단위입니다. 즉, 비슷한 역할을 하는 계정들을 하나의 OU로 묶어서 관리할 수 있는 기능입니다.

OU의 역할은 다음과 같습니다.
- 계정 그룹화
  - OU를 사용하면 역할에 따라 여러 계정을 하나의 그룹으로 묶어서 관리할 수 있습니다.
  - 예를 들어, 개발과 관련된 `dev`, `staging`, `prod` 계정을 하나의 `Development OU`로 묶을 수 있습니다.
- SCP 적용
  - OU 단위로 보안 및 정책을 적용할 수 있습니다.
  - 예를 들어, `Development OU`에 `ap-northeast-2` 리전 사용 제한 정책(SCP)을 적용하면, 해당 Ou에 속한 모든 계정(dev, staging, prod)에서 ap-northeast-2 리전을 사용할 수 없게 됩니다.
  - SCP는 IAM 정책보다 상위 제한을 하기 때문에, IAM보다 우선 적용 됩니다.

### AWS Organizations 사용 전
- 개별 계정의 비용을 따로 확인해야 합니다.
- 여러 계정이 중복으로 사용하는 정책을 일관적으로 적용할 수 없습니다.
### AWS Organizations 사용 후
- 중앙 집중식 관리를 통해 여러 계정을 하나의 관리 계정으로 통합 관리할 수 잇습니다.
- 통합 결제(Consolidated Billing)로 비용 절감이 가능합니다.
- 서비스 제어 정책(SCP)을 통해 여러 계정에 보안 정책을 일관적으로 적용할 수 있습니다.
