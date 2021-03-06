## 설정 시나리오

도메인 원본 서버의 기본 정보, 원본 요청 프로토콜, 호스트 헤더 등 정보를 원본 서버의 설정 모듈에서 수정할 수 있습니다.

## 설정 가이드

### 설정 조회
[CDN 콘솔](https://console.cloud.tencent.com/cdn)에 로그인하여 메뉴에서 [Domain Management]를 클릭하고 도메인 오른쪽 [Manage]를 클릭하면 도메인 설정 페이지로 이동할 수 있습니다. 그중 첫 번째 바의 기본 정보 아래쪽에 원본 서버 설정 모듈이 있습니다.
![](https://main.qcloudimg.com/raw/6d631efa6f16887aa0d1a60071aec395.png)
**원본 서버 유형**
+ 외부 원본 서버: 안정적으로 실행되는 비즈니스 서버(즉 원본 서버)를 보유하고 있다면, 해당하는 IP 주소 리스트 또는 도메인을 원본 서버 주소로 입력합니다.
+ [COS](https://cloud.tencent.com/product/cos): 리소스가 Tencent Cloud COS에 저장되어 있다면, 하나의 bucket을 원본 서버로 선택합니다.

**원본 서버 주소**
원본 서버 주소는 최대 511개 문자 이내로 입력할 수 있고, 다중 IP 또는 단일 도메인의 원본 요청을 지원합니다.
**원본 요청 프로토콜**
CDN 가속 노드가 사용자의 원본 서버로부터 가져올 때 사용하는 프로토콜로, HTTP 또는 HTTPS를 말합니다.
**호스트 헤더**
즉 원본 서버의 도메인으로 CDN 노드가 원본 서버로부터 가져올 때 액세스하는 원본 서버의 사이트 도메인이며, 자세한 설명은 아래의 [원본 서버 도메인 설정](#exp)을 조회할 수 있습니다.

### 설정 수정
#### 1. 호스트 원본 서버 설정 수정
오른쪽 상단의 [Edit]를 클릭하여 호스트 원본 서버의 설정을 수정할 수 있습니다.
![](https://main.qcloudimg.com/raw/6486a3c43fa291564f5d89819c0b0b7a.png)
**원본 서버 주소 수정**
외부 원본 서버 선택 시, 원본 서버 주소는 최대 511개 문자로 입력할 수 있으며 아래의 설정 모드를 지원합니다.
+ **다중 IP의 원본 서버 폴링**: 원본 서버를 여러 개의 IP로 입력하면 원본 요청 시 폴링을 실행합니다. CDN은 원본 서버를 점검하도록 기본 설정되어 있어, 어느 한 IP의 원본 가져오기 실패 횟수가 일정 수준의 임계 값을 초과하면 해당 IP 주소로부터 원본을 가져오지 않고 한동안 차단한 후에 자동으로 복구합니다.
+ **IPv6 원본 서버**: 사용자가 IPv6 베타 테스트 자격을 활성화하고 도메인의 요청 프로토콜을 IPv4 + IPv6으로 선택했다면, IPv6 주소 하나를 원본 서버로 입력할 수 있습니다.
+ **특수 포트 원본 요청**: IP: 포트 형식을 지원하고, HTTP 프로토콜은 1 - 65535까지 포트를 사용자 정로 설정할 수 있으며, HTTPS 프로토콜은 현재 443 포트만 지원합니다.
+ **가중 원본 요청**: IP: 포트: 가중 형식을 지원합니다. 가중치는 1 - 100이며, 포트는 디폴트할 수 있습니다.
+ **도메인 원본 요청**: 원본 서버는 하나의 독립된 도메인(IPv6 도메인 원본 요청은 지원하지 않음)만 입력할 수 있습니다.

**원본 요청 프로토콜 수정**
원본 서버 설정에서 도메인 원본 요청 프로토콜을 HTTP, HTTPS 또는 원본 요청 따르기 조정할 수 있습니다.
+ **HTTP 원본 요청**: 액세스 시 HTTP나 HTTPS에 상관없이 모두 HTTP를 통해 가져옵니다.
+ **HTTPS 원본 요청**: 액세스 시 HTTP나 HTTPS에 상관없이 모두 HTTPS를 통해 가져옵니다.
+ **프로토콜 따르기**: HTTP 요청은 HTTP 를 통해 가져오고, HTTPS 요청은 HTTPS를 통해 가져옵니다.

>
> + HTTPS 원본 요청이 있다면 원본 서버가 HTTPS에 액세스하도록 설정하세요. 그렇지 않으면 원본 요청에 실패할 수 있습니다.
> + 현재 인증서 관리 페이지를 통해 해당 설정을 조정할 수 있으며, 이후에는 마이그레이션을 통해 설정합니다.

**호스트 헤더 수정**
도메인 이름 액세스 시, 호스트 헤더가 가속 도메인으로 기본 설정됩니다. 와일드카드 서브도메인에 액세스하는 경우에는 와일드카드 서브도메인으로 기본 설정되고, 실제 호스트 헤더가 액세스 도메인이 됩니다. 필요에 따라 이곳에서 수정할 수 있습니다.

> COS가 원본 서버인 경우에는 호스트 헤더를 수정할 수 없습니다.

#### 2. 핫 스탠바이 원본 서버 설정
사용자의 호스트 원본 서버가 외부 원본 서버일 경우 핫 스탠바이 원본 서버를 추가할 수 있고, 모든 원본 요청이 호스트 원본 서버에 먼저 액세스합니다. 4XX 5XX 에러 코드를 리턴하거나 연결 타임아웃, 프로토콜 호환되지 않음 등의 상황이 발생하면 다시 핫 스탠바이 원본 서버로부터 리소스를 요청하여 가져오므로 리소스를 원활하게 사용할 수 있습니다.

핫 스탠바이 원본 서버에 원본 요청 프로토콜, 호스트 헤더 정보를 각각 설정할 수 있습니다.
![](https://main.qcloudimg.com/raw/1bc84493e7cb671f71c0a94e7e3eb721.png)

#### 3. 리전 특수 설정
사용자의 가속 도메인의 서비스 지역이 글로벌 범위일 경우, 국가 간의 트래픽 발생을 막기 위해 가속 도메인의 각 서비스 리전마다 다른 원본 서버를 설정하고자 한다면 하단의 [Add Special Configuration]를 클릭하여 설정할 수 있습니다.
![](https://main.qcloudimg.com/raw/35bd00125a450abc9133279a010254e7.png)
다른 원본 요청 정책이 필요한 리전을 선택하고 해당하는 원본 서버 정보를 입력하면 됩니다.
![](https://main.qcloudimg.com/raw/b0d616363d87d09e1c67d8b92fe069da.png)

>
> + 리전 특수 설정을 추가한 후에 현재로서는 직접 삭제할 수 없습니다.
> + 리전 특수 설정이 기본 설정과 완전히 일치하면 자동으로 병합하므로, 일치하도록 설정하여 리전 특수 설정을 삭제할 수 있습니다.

## 설정 예시
### 원본 요청 도메인 설정<a ID="exp"></a>
CDN 원본 서버 설정이 아래와 같을 때, 가속 도메인 `www.test.com`을 아래와 같이 가정하여 설정합니다.
![](https://main.qcloudimg.com/raw/e00fa5ef5b1f86722505d8cb49f939fd.png)
사용자 액세스 경로는 다음과 같습니다.
사용자가 `http://www.test.com/test.txt` 리소스에 액세스할 때 CDN 노드에 해당 리소스가 캐시되지 않으면 CDN 노드의 원본 요청은 `www.abc.com` 도메인에 대해 리졸브합니다. 이를 통해 획득한 원본 서버 주소가 `1.1.1.1`이라 한다면, `1.1.1.1` 서버에 액세스하며 그에 해당하는 Web 사이트인 `www.def.com` 경로에서 test.txt 파일을 찾아 사용자에게 리턴합니다.

### 리전 특수 설정
Tencent Cloud CDN 원본 서버 설정이 아래와 같을 때, 가속 도메인 `www.test.com`을 아래와 같이 가정하여 설정합니다.
![](https://main.qcloudimg.com/raw/927987d96b223c37a5252ebe2f1ee593.png)
실제 원본 요청 시나리오는 다음과 같습니다.
1. 중국 내 사용자가 `http://www.test.com/test.txt` 파일에 액세스하고, 중국 내 노드에 해당 리소스가 캐시되지 않으면 서버 `1.1.1.1`에 요청하여 Web 사이트 `1.test.com`의 test.txt 파일을 찾습니다. 만약 해당 리소스가 있으면 직접 사용자에게 리턴하고, 없으면 2단계를 진행합니다.
2. CDN의 중국 내 노드가 호스트 원본 서버로 돌아가기에 실패하여 리소스를 찾지 못하면 서버 `2.2.2.2`에 요청하여 Web 사이트 `1.test.com`의 test.txt 파일을 찾고, 사용자에게 리턴 및 캐시합니다.
3. 이때 중국 외 사용자 또한 `http://www.test.com/test/txt` 파일에 액세스하고, 중국 외 노드에 해당 리소스가 캐시되지 않으면 서버 `3.3.3.3`에 요청하여 Web 사이트 `3.test.com`의 test.txt 파일을 찾습니다. 만약 해당 리소스가 있으면 직접 사용자에게 리턴하고, 없으면 4단계를 진행합니다.
4. CDN의 중국 외 노드가 중국 외에 위치한 호스트 원본 서버로 돌아가기에 실패하여 리소스를 찾지 못하면 `4.4.4.4`에 요청하여 Web 사이트 `4.test.com`의 test.txt 파일을 찾고, 사용자에게 리턴 및 캐시합니다.
