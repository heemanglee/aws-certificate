
##### S3 Transfer Acceleration
- S3에 파일을 더 빠르게 업로드할 수 있도록 도와주는 기능

##### Amazon S3 Intelligent-Tiering
- 접근 패턴 불규칙
- 접근 패턴 파악해서 가장 경제적 계층으로 자동 이동

##### Amazon S3 Gracier Flexible Retrieval
- 구 Gracier
- 장기보관
- 매우 저렴
- 접근 잘 안하는 장기 보관용 데이터
- 복원하는데 수분 ~ 수시간 소요

##### Amazon S3 Gracier Instant Retrieval
- 즉각적인 액세스 필요한 아카이브 데이터
	- 예시) 오래된 보고서, 규제 문서, 보관용 로그
- 몇 밀리 초 안에 검색
- 빨리 검색 유용

##### Amazon S3 Standard
- 자주 접근
- 빠른 접근 속도
- 가장 비쌈
- 자주 접근하는 데이터

##### Amazon S3 Standard-Infrequent Access
- Standard - IA
- 가끔 접근하는 데이터
- 저장기간이 짧을 수도
- 저장 비용 적음
- 중요하지만 가끔 접근 하는 데이터
	- 백업 파일, 월간 리포트, 비정기 조회 데이터

##### Gracier Deep Archive
- 가장 저렴한 객체 스토리지 클래스
- 12시간 내에 객체 검색
- 일년에 한 두번 액세스되는 데이터의 장기/디지털 보존 지원
- 모든 객체 최소 3개의 지리적 분산 가용 영역 복제 저장

##### Outposts
- S3 Outposts에 S3 버킷 생성