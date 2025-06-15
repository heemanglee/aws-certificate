# Aurora MysQL 버전 2 -> 3 메이저 버전 업그레이드 기술 문서

## 1. 개요

본 문서는 Amazon Aurora MysQL 버전을 `2.x(MySQL 5.7 호환)`에서 `3.x(MySQL 8.0)`로 업그레이드하는 절차와 주요 고려사항을 작성합니다.

- **기존 버전**: Aurora MySQL 2 (MySQL 5.7 호환)
- **대상 버전**: Aurora MySQL 3 (MySQL 8.0 호환)

업그레이드의 주된 목적은 `비용 최적화`입니다. Aurora MySQL 2에 대한 AWS의 표준 지원이 종료됨에 따라 발생하는 추가 비용을 제거하고, 최신 데이터베이스 엔진이 제공하는 성능과 보안을 활용하기 위함입니다.

## 2. 업그레이드 배경: RDS Extended Support와 비용 영향
Amazon Aurora MySQL 2 (MySQL 5.7 호환)는 2024년 10월 31일부로 표준 지원이 종료되었습니다. 표준 지원이 종료된 버전을 계속 사용할 경우, `Amazon RDS Extended Support`가 자동으로 활성화되어 추가 비용이 발생합니다. 
**RDS Extended Support는 vCPU-시간당 요금이 부과되고, 이는 인스턴스 사용 요금과는 별개로 청구되므로 전체 데이터베이스 비용이 크게 증가합니다.**

따라서 불필요한 비용을 제거하고, 최신 버전의 성능 및 보안을 활용하기 위해 Aurora MySQL 3로의 메이저 버전 업그레이드를 수행해야 합니다.

아래 사진의 경우 전체 데이터베이스 비용인데, **RDS Extended Support 비용($628.33)은 전체 Aurora MySQL 월별 비용($1.6k)의 약 `40%`를 차지**하고 있습니다. 

```math
$$
\text{비중}(\%) = \left( \frac{\text{Extended Support 비용}}{\text{총 비용}} \right) \times 100
$$
```
```math
$$
\left( \frac{628.33}{1600} \right) \times 100 \approx 39.27\%
$$
```

<img width="977" alt="전체_데이터베이스_비용" src="https://github.com/user-attachments/assets/044aa860-aaa6-4981-ab6c-20b980606143" />

Aurora MySQL 3으로 업그레이드하면 이 비용을 완전히 제거하여 데이터베이스 운영 비용을 최적화할 수 있습니다.

## 3. 고려사항 및 비용 영향
- **Amazon RDS Extended Support**
	- **비용 발생**: 표준 지원 종료일 이후, Extended Support는 vCPU-시간당 요금이 부과됩니다. 이는 온디맨드 인스턴스 요금과는 별개로 청구되는 추가 비용입니다. 

- **Aurora MySQL 3 주요 이점**
	- **성능 향상**: 향상된 쿼리 최적화, MySQL 8.0의 새로운 기능을 활용하여 쿼리 성능을 개선할 수 있습니다.
	- **보안 강화**: 최신 보안 패치 및 기능이 적용되어 데이터베이스 보안을 강화할 수 있습니다.

## 4. 주요 변경 사항
업그레이드를 진행하기 앞서, Aurora MySQL 3의 요구 사항을 검토하고 기존 리소스와의 호환성을 분석했습니다. 이 과정에서 엔진 버전뿐만 아니라 DB 인스턴스 클래스 변경이 필요함을 확인했습니다.

### 4-1. 변경 내역

| 구분 | 리소스 | 기존 (As-Is) | 변경 (To-Be) | 변경 사유 |
|------|--------|--------------|--------------|-----------|
| 엔진 | 모든 클러스터 | Aurora MySQL 2 (5.7 호환) | Aurora MySQL 3 (8.0 호환) | 표준 지원 종료 및 비용 최적화 |
| 인스턴스 | A | db.t3.small | db.t4g.medium | 최소 사양 미충족 |
| 인스턴스 | B | db.t3.medium | db.t4g.medium | 인스턴스 타입 표준화 및 성능 개선 |

### 4-2. 인스턴스 클래스 변경 상세

#### 1. 최소 사양 요구사항
Aurora MySQL 3은 `db.t3.small` 및 `db.t4g.small` 인스턴스 클래스를 지원하지 않습니다. 따라서 A 클러스터가 `db.t3.small`을 사용하고 있으므로, 업그레이드를 위해서는 상위 인스턴스 클래스 변경이 필요합니다.

#### 2. Graviton 기반 t4g 인스턴스로 표준화
업그레이드 시 인스턴스 클래스를 변경해야 한다면, AWS Graviton 프로세서기 기반의(`t4g`, `r6g`, `r7g` 등)로 전환하는 것을 권장합니다. Gravition 인스턴스는 동일 사향의 x86 기반 인스턴스(`t3`, `r5` 등) 대비 더 나은 가격 대비 성능을 제공하여 비용 절감 효과를 기대할 수 있습니다.

- 클러스터 A: `db.t3.small` -> `db.t4g.medium`으로 변경
- 클러스터 B: `db.t3.medium` -> `db.t4g.medium`으로 함께 변경

- **t3 계열 성능**:
<img width="1088" alt="db_t3_performance" src="https://github.com/user-attachments/assets/9edc7af3-d085-4852-b0fb-4864285a910e" />

- **t4 계열 성능**:
<img width="1076" alt="db_t4_performance" src="https://github.com/user-attachments/assets/cb936ecb-75bb-4421-ba74-ec4850784623" />

- **t3와 t4 계열 비용**:
<img width="958" alt="db_t3_t4_price" src="https://github.com/user-attachments/assets/bf5d6f10-1848-4391-8224-7d5f9677e34a" />

## 5. 업그레이드 전략: 블루/그린 배포 (Blue/Green Deployment)
다운타임을 최소화하고 배포 안정성을 확보하기 위해 AWS의 블루/그린 배포 기능을 사용하는 것이 가장 효과적입니다. 블루/그린 배포는 현재 운영 환경(블루)과 동일한 데이터를 갖는 스테이징 환경(그린)을 생성 후, 두 환경 간의 전환을 통해 신규 버전을 배포하는 전략입니다.

### 5-1. 사전 요구사항: 바이너리 로그(Binlog) 활성화
블루/그린 배포를 사용하기 위한 조건은 원본(블루) 클러스터에서 바이너리 로그를 활성화하는 것입니다.
1. **`binlog_format` 파라미터 변경**
    - 설정: DB 클러스터 파라미터 그룹에서 `binlog_format` 파라미터 값을 `ROW`로 설정해야 합니다.
    - 이유: 블루 환경의 변경 사항을 **그린 환경에 실시간으로 복제(Replication)**하기 위해 `ROW` 포맷의 바이너리 로그가 사용됩니다.
2. **파라미터 적용**
    - `binlog_format`은 정적(Static) 파라미터이므로, 변경 사항을 적용하려면 **DB 인스턴스의 재부팅이 필요**합니다.
    - 운영 중인 Writer 인스턴스의 재부팅을 피하기 위해 다음 절차를 수행합니다.
      1. `binlog_format`이 `ROW`로 설정된 새로운 DB 클러스터 파라미터 그룹을 생성합니다. 이는 기본으로 생성된 DB 클러스터 파라미터 그룹에 해당하며, 반대로 사용자 정의 파라미터 그룹을 사용한다면 `binlog_format` 값을 `ROW`로 설정하면 됩니다. 기존에 클러스터에 연결된 DB 인스턴스는 `biglog_format`이 `ROW`로 설정되지 않습니다. (재부팅 보류 상태)
      2. 클러스터에 새로운 Reader 인스턴스를 추가합니다. 단, 장애 조치 우선 순위를 `Tier- 0`으로 설정하여, Writer 인스턴스에 Failover 시에 새로 생성한 Reader 인스턴스가 Writer 인스턴스로 승격될 수 있도록 합니다. 새로 생성한 Reader 인스턴스는 `binlog_format`이 `ROW`로 동기화되어 있습니다.
      3. Writer 인스턴스에 Failover를 수동으로 트리거하여 2번에서 생성한 Reader 인스턴스를 Writer 인스턴스로 승격시킵니다.
      4. 🚨 이 과정을 통해 다운 타임을 최소화하여 Writer 인스턴스에 `binlog_format=ROW` 설정이 완료됩니다. Failover가 완료되면 MySQL 세션에 연결되어 있던 애플리케이션에서 DB 접속 오류가 발생할 수 있으므로, 반드시 애플리케이션 상태를 모니터링 해야합니다. 
      ```sql
      Exception: (MySQLdb._exceptions.OperationalError) (1290, 'The MySQL server is running with the --read-only option so it cannot execute this statement')
      ```

### 5-2. MySQL 8.0 호환성 검사 쿼리 
MySQL 5.7에서 8.0으로 업그레이드할 때, 현재 데이터베이스가 MySQL 8.0의 키워드 및 예약어를 사용하고 있는지 확인해야 합니다. 마이그레이션할 때 발생할 수 있는 예약어 충돌을 미리 방지해야 합니다.
> MySQL 8.0 Keywords and Reserved Words (공식 문서): https://dev.mysql.com/doc/refman/8.0/en/keywords.html

```sql
-- 데이터베이스 이름 검사
SELECT TABLE_SCHEMA, TABLE_NAME
FROM INFORMATION_SCHEMA.TABLES
WHERE UPPER(TABLE_NAME) IN ('CUBE', 'CUME_DIST', 'DENSE_RANK', 'EMPTY', 'EXCEPT', 'FIRST_VALUE', 'GROUPING', 'GROUPS', 'JSON_TABLE', 'LAG', 'LAST_VALUE', 'LEAD', 'NTH_VALUE', 'NTILE', 'OF', 'OVER', 'PERCENT_RANK', 'RANK', 'RECURSIVE', 'ROW', 'ROW_NUMBER', 'SYSTEM', 'WINDOW')
AND TABLE_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys'); -- 시스템 DB 제외

-- 테이블 이름 검사
SELECT TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE UPPER(COLUMN_NAME) IN ('CUBE', 'CUME_DIST', 'DENSE_RANK', 'EMPTY', 'EXCEPT', 'FIRST_VALUE', 'GROUPING', 'GROUPS', 'JSON_TABLE', 'LAG', 'LAST_VALUE', 'LEAD', 'NTH_VALUE', 'NTILE', 'OF', 'OVER', 'PERCENT_RANK', 'RANK', 'RECURSIVE', 'ROW', 'ROW_NUMBER', 'SYSTEM', 'WINDOW')
AND TABLE_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys'); -- 시스템 DB 제외

-- 프로시저 및 함수 이름 검사
SELECT ROUTINE_SCHEMA, ROUTINE_NAME, ROUTINE_TYPE
FROM INFORMATION_SCHEMA.ROUTINES
WHERE UPPER(ROUTINE_NAME) IN ('CUBE', 'CUME_DIST', 'DENSE_RANK', 'EMPTY', 'EXCEPT', 'FIRST_VALUE', 'GROUPING', 'GROUPS', 'JSON_TABLE', 'LAG', 'LAST_VALUE', 'LEAD', 'NTH_VALUE', 'NTILE', 'OF', 'OVER', 'PERCENT_RANK', 'RANK', 'RECURSIVE', 'ROW', 'ROW_NUMBER', 'SYSTEM', 'WINDOW')
AND ROUTINE_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys');

-- 트리거 이름 검사
SELECT TRIGGER_SCHEMA, TRIGGER_NAME
FROM INFORMATION_SCHEMA.TRIGGERS
WHERE UPPER(TRIGGER_NAME) IN ('CUBE', 'CUME_DIST', 'DENSE_RANK', 'EMPTY', 'EXCEPT', 'FIRST_VALUE', 'GROUPING', 'GROUPS', 'JSON_TABLE', 'LAG', 'LAST_VALUE', 'LEAD', 'NTH_VALUE', 'NTILE', 'OF', 'OVER', 'PERCENT_RANK', 'RANK', 'RECURSIVE', 'ROW', 'ROW_NUMBER', 'SYSTEM', 'WINDOW')
AND TRIGGER_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys');

-- 이벤트 이름 검사
SELECT EVENT_SCHEMA, EVENT_NAME
FROM INFORMATION_SCHEMA.EVENTS
WHERE UPPER(EVENT_NAME) IN ('CUBE', 'CUME_DIST', 'DENSE_RANK', 'EMPTY', 'EXCEPT', 'FIRST_VALUE', 'GROUPING', 'GROUPS', 'JSON_TABLE', 'LAG', 'LAST_VALUE', 'LEAD', 'NTH_VALUE', 'NTILE', 'OF', 'OVER', 'PERCENT_RANK', 'RANK', 'RECURSIVE', 'ROW', 'ROW_NUMBER', 'SYSTEM', 'WINDOW')
AND EVENT_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys');
```

### 5-3. 업그레이드 및 전환 절차
사전 요구사항이 충족된 후, 다음과 같은 절차로 업그레이드를 수행하였습니다.
1. **블루/그린 배포 생성**
    - 운영 중인 Aurora 클러스터(블루)를 소스로 지정하여 블루/그린 배포를 생성합니다.
    - AWS는 블루 환경과 동일한 구성의 스테이징 환경(그린)을 자동으로 프로비저닝하고, 바이너리 로그를 통해 데이터 동기화를 시작합니다.
2. **그린 환경 업그레이드 및 변경**
    - 데이터 동기화가 유지되는 상태에서 그린 환경에만 업그레이드를 진행합니다. 이 작업은 블루 환경(운영 서비스)에 어떠한 영향도 주지 않습니다.
    - 수행 작업:
        - Aurora MySQL 엔진 버전을 2에서 3으로 업그레이드
        - DB 인스턴스 클래스를 db.t3에서 db.t4g로 변경
3. **전환(Switchover)**
    - 그린 환경의 업그레이드와 테스트가 완료되면 '전환'을 실행합니다.
    - 전환이 시작되면 AWS는 블루와 그린 환경의 데이터가 완전히 동기화되도록 잠시 쓰기 작업을 차단한 후, DB 클러스터 엔드포인트가 그린 환경을 가리키도록 트래픽을 리디렉션합니다.
    - 전체 전환 과정은 일반적으로 1분 이내에 완료됩니다.
    - 🚨 전환 후에 실행 중인 애플리케이션에서 DB 접속 문제가 발생하지 않는지 반드시 모니터링해야 합니다.

### 5-4. 블루/그린 배포의 핵심 이점
- **다운타임 최소화**: 전환 중 발생하는 다운타임 시간이 매우 짧아 사용자 영향이 거의 없습니다.
- **기존 엔드포인트 유지**: 블루/그린 배포의 가장 큰 장점은 클러스터 엔드포인트와 Reader/Writer 엔드포인트가 변경되지 않는것입니다. 따라서 데이터베이스를 사용하는 애플리케이션의 코드나 설정 파일을 수정할 필요가 없습니다.
- **롤백 가능**: 전환 후 문제가 발생할 경우, 다시 블루 환경으로 롤백할 수 있어 배포 리스크를 낮출 수 있습니다.

## 6. 결론
업그레이드 완료 후 애플리케이션의 DB 세션 연결 및 기능이 모두 정상적으로 동작함을 확인하였고, 전체 DB 비용의 약 40%를 차지하던 RDS Extended Support 비용을 완전히 제거했습니다. 그리고 표준 지원이 종료된 Aurora MySLQ 2에서 최신 버전인 Aurora MySQL 3으로 전환하여 성능과 보안을 강화했습니다.
