## 인스턴스 관리 웹페이지
TencentDB for MySQL를 초기화하면 인스턴스 리스트에서 인스턴스명을 클릭하거나 조작 리스트에서 [관리]를 클릭하면 인스턴스 관리 웹페이지에 접속합니다. 인스턴스 더 알아보기, 인스턴스 모니터링, 데이터베이스 관리 등 작업을 지원합니다.

### 인스턴스 더 알아보기
[인스턴스 더 알아보기] 웹페이지에서 데이터베이스의 다양한 메시지를 조회할 수 있습니다. 다음 이미지에 명시한 것처럼 <img src="https://main.qcloudimg.com/raw/071659c8118f8c9b94d4ab90cebbd955.png"  style="margin:0;"> 클릭 시 인스턴스의 기본 메시지를 수정할 수 있습니다. 광역 통신망의 주소는 기본적으로 종료된 상태이며, 필요하실 경우 매뉴얼로 오픈하십시오.
![](https://main.qcloudimg.com/raw/be7a1916b3cba0932a015b95fa857d2d.png)

### 인스턴스 모니터링
[인스턴스 모니터링] 웹페이지에서 기존 데이터베이스가 작동한 다양한 핵심 메트릭의 모니터링을 조회할 수 있습니다. 액세스, 부하, 캐시 쿼리, 테이블, InnoDB、MyISAM 등에 대해 모니터링합니다.
인스턴스 모니터링과 알람 기능에 대한 디테일한 소개는 [모니터링 기능](https://cloud.tencent.com/document/product/236/8455)과 [알람 기능](https://cloud.tencent.com/document/product/236/8457)을 참조하십시오.

### 데이터베이스 관리
#### 데이터베이스 리스트
[데이터베이스 관리]>[데이터베이스 리스트] 웹페이지에서 SQL 파일을 지정 데이터베이스에 추가할 수 있습니다. 
1. [데이터 액세스]를 클릭하여 데이터 액세스 웹페이지에 접속합니다.
2. [신규 추가 파일]을 클릭하여 로컬 SQL 파일을 선택하고 업로드를 확인합니다.

#### 파라미터 설정
[데이터베이스 관리]>[파라미터 설정] 웹페이지에서 데이터베이스의 여러 수정 가능한 파라미터를 설정하고 조회하며 히스토리를 수정할 수 있습니다. [파라미터 실행값] 옆의 <img src="https://main.qcloudimg.com/raw/071659c8118f8c9b94d4ab90cebbd955.png"  style="margin:0;"> 클릭하여 파라미터값을 수정할 수 있으며, 상세내역은 [파라미터 템플릿 소개](https://intl.cloud.tencent.com/document/product/236/8461).를 참조하십시오.

#### 계정 관리
[데이터베이스 관리]>[계정 관리] 웹페이지에서 시스템의 기본 root 계정을 관리할 수 있습니다. 예를 들면 권한을 수정하고 비밀번호를 재설정할 수 있으며, 계정을 생성하거나 삭제할 수 있습니다. 

### 보안 그룹
[보안 그룹] 웹페이지에서 데이터베이스에 보안 그룹을 설정할 수 있습니다. 디테일한 설명은 [클라우드 데이터베이스 보안 그룹](https://cloud.tencent.com/document/product/236/9537)을 참조하십시오.

### 백업 복구
[백업 복구] 웹페이지에서 binlog를 다운로드하고 콜드 백업할 수 있습니다. 상세내역은 [백업 방식](https://intl.cloud.tencent.com/document/product/236/7513).을 참조하십시오.

### 조작 로그
[조작 로그] 웹페이지에서 슬로우 쿼리 로그, 에러 로그, 롤백 로그를 조회하고 다운로드할 수 있습니다.

### 읽기 전용 인스턴스
[읽기 전용 인스턴스] 웹페이지에서 읽기 전용 인스턴스를 1개 혹은 여러 개 생성할 수 있습니다. 사용자의 읽기 쓰기 분리 및 1 마스터 멀티 슬레이어 솔루션을 지원하며, 사용자의 데이터베이스 읽기 로드 성능을 대폭 업그레이드합니다. 상세내역은 [읽기 전용 인스턴스](https://intl.cloud.tencent.com/document/product/236/7270)를 참조하십시오.

### 연결 점검
[연결 점검] 웹페이지에서 클라우드 데이터베이스에 존재 가능한 연결 액세스 문제를 점검하고 제공한 솔루션에 따라 액세스 문제를 프로세싱하여 클라우드 데이터베이스를 정상적으로 액세스할 수 있습니다. 상세내역은 [원클릭 연결 점검 툴](https://cloud.tencent.com/document/product/236/33206)을 참조하십시오.

## 인스턴스 리스트 웹페이지
TencentDB for MySQL 콘솔 좌측 네비게이션 바의 [인스턴스 리스트] 웹페이지에서 인스턴스 관련 메시지를 조회하고 인스턴스를 관리할 수 있습니다. 
![](https://main.qcloudimg.com/raw/ad7eb840269b428dd044ddd45b08545e.png)

### 설정 조율
[인스턴스 리스트] 웹페이지에서 데이터베이스 인스턴스의 설정을 변경(확장/축소)할 수 있습니다. 인스턴스 레벨업과 레벨다운을 지원하며, 상세내역은 [데이터베이스 인스턴스 스펙 변경](https://cloud.tencent.com/document/product/236/19707)을 참조하십시오.

### 롤백
[인스턴스 리스트] 웹페이지에서 롤백하려는 인스턴스를 체크하고 [상세 조작]>[롤백]을 선택하면 콜드 백업과 binlog를 통해 데이터베이스를 지정 시간에 롤백합니다. 상세내역은 [데이터 롤백](https://intl.cloud.tencent.com/document/product/236/7276).을 참조하십시오.

### 재기동
[인스턴스 리스트] 웹페이지에서 재시작하려는 데이터베이스 인스턴스를 체크 및 [재시작]을 클릭하면 인스턴스를 재시작할 수 있습니다. 일괄 재시작(멀티 인스턴스를 선택)을 지원합니다.
> - 재기동 기간에 인스턴스를 정상 액세스할 수 없습니다. 또한 기존 연결이 끊기므로 차질없이 준비해주시기 바랍니다.
> - 재기동 기간에 서비스에 쓰기 량이 많을 경우, 더티 페이지가 많아 재기동에 실패합니다. 재기동 실패 시, 인스턴스는 재기동 전의 상태가 되며, 인스턴스를 액세스할 수 있습니다.
> - 재기동 성공률을 확보하고 서비스에 대한 영향을 줄이고자 서비스의 낮은 피크타임에 재기동해주시기 바랍니다. 
