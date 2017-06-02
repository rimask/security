
{:shortdesc: .shortdesc}

# {{site.data.keyword.Bluemix_notm}} 보안
{: #security}
*마지막 업데이트 날짜: 2015년 10월 15일*

보안 엔지니어링 방식으로 디자인된
{{site.data.keyword.Bluemix}} 플랫폼에는
네트워크 및 인프라에서 계층화된 보안 제어가 있습니다. 또한 {{site.data.keyword.Bluemix_notm}}에서는
자체 모바일 및 웹 앱을 보호하기 위해 애플리케이션 개발자가 사용할 수 있는 보안 서비스 스위트도 제공합니다. 이러한 요소가 결합되어 {{site.data.keyword.Bluemix_notm}}는
보안 애플리케이션 개발을 위한 명확한 선택사항을 보유한 플랫폼이 됩니다.
{:shortdesc}

{{site.data.keyword.Bluemix_notm}}는 시스템, 네트워킹 및 보안 엔지니어링과 관련한 IBM의 우수 사례에 의해 구동되는 보안 정책을 고수함으로써 보안 준비성을 보장합니다. 이러한 정책에는 소스 코드 스캔, 동적 스캔, 위협 모델링 및 침입 테스트 등의 실행이 포함됩니다. {{site.data.keyword.Bluemix_notm}}는 보안 침해사고 관리를 위해 IBM PSIRT(Product Security Incident Response Team) 프로세스를 따릅니다. 세부사항은 [IBM Security Vulnerability Management(PSIRT)](http://www-03.ibm.com/security/secure-engineering/process.html) 사이트를 참조하십시오.

{{site.data.keyword.Bluemix_notm}} Public 및 Dedicated는 IBM SoftLayer IaaS(Infrastructure-as-a-Service) 클라우드 서비스를 사용하고 해당 보안 아키텍처를 완전히 활용합니다. SoftLayer IaaS는 애플리케이션 및 데이터에 대한 다중의 중첩된 보안 계층을 제공합니다. {{site.data.keyword.Bluemix_notm}} Local의 경우
사용자는 회사 방화벽 뒤의 사용자 소유 데이터 센터에서 {{site.data.keyword.Bluemix_notm}} Local을
호스트하여 실제 보안을 소유하고 인프라를 제공합니다. 또한 {{site.data.keyword.Bluemix_notm}}는
다양한 카테고리(플랫폼, 데이터 및 애플리케이션)의 PaaS(Platform as a Service) 계층에서 보안 기능을 추가합니다.

## {{site.data.keyword.Bluemix_notm}} 플랫폼 보안
{: #platform-security}

{{site.data.keyword.Bluemix_notm}}는 코어 플랫폼에 대해 (IBM SoftLayer를 통한) 기능, 인프라, 운영 및 물리적 보안을 제공합니다. 그러나
{{site.data.keyword.Bluemix_notm}} Local은 고객이 제공하는 인프라와 데이터 센터에서
고유하며 실제 보안을 소유합니다.

{{site.data.keyword.Bluemix_notm}} 환경은 산업 표준을 충족하거나 그 이상을 충족하는 가장 제한적인 IBM 정보 기술(IT) 보안 표준을 준수합니다. 표준에는 네트워크, 데이터 암호화 및
액세스 제어가 포함되어 있습니다.
 * 애플리케이션 ACL, 권한 및 침투 테스트
 * 식별, 인증 및 권한 부여
 * 정보 및 데이터 보호
 * 서비스 무결성 및 가용성
 * 취약성 및 수정사항 관리
 * 서비스 거부(DoS) 및 조직적 공격 발견
 * 보안 침해사고 대응

![Bluemix 플랫폼 보안 개요](images/platform_sec.png)

*그림 1. {{site.data.keyword.Bluemix_notm}} 플랫폼 보안 개요*

회사 방화벽 및 데이터 센터 뒤에 Bluemix를 호스팅하여 특정 보안 부분을 소유하고 있기 때문에 {{site.data.keyword.Bluemix_notm}} Local 보안은 다릅니다. 다음 보안 파트 이미지 세부사항은 고객 소유이며 보안 파트는 IBM에서 관리하고 유지보수합니다.

![Bluemix Local 플랫폼 보안 개요](images/security_local_platform.png)

*그림 2. {{site.data.keyword.Bluemix_notm}} Local 플랫폼 보안 개요*

### 기능적 보안

{{site.data.keyword.Bluemix_notm}}는
사용자 인증, 액세스 권한 부여, 중요 오퍼레이션 감사, 데이터 보호 등
다양한 기능적 보안 기능을 제공합니다.

<dl>
<dt>인증</dt>
<dd>애플리케이션 개발자는 IBM 웹 ID를 사용하여 {{site.data.keyword.Bluemix_notm}}에 인증됩니다.

{{site.data.keyword.Bluemix_notm}} Dedicated
및 Local의 경우 LDAP을 통한 인증이 기본적으로 지원됩니다. 요청 시 {{site.data.keyword.Bluemix_notm}} 대신 IBM 웹 ID를 통한 인증을 설정할 수 있습니다.
</dd>

<dt>권한 부여</dt>
<dd>{{site.data.keyword.Bluemix_notm}}는
Cloud Foundry 메커니즘을 사용하여 각 애플리케이션 개발자가
자신이 작성한 애플리케이션 및 서비스 인스턴스에만 액세스하도록 합니다. {{site.data.keyword.Bluemix_notm}} 서비스에
대한 권한 부여는 OAuth를 기반으로 합니다. 모든 {{site.data.keyword.Bluemix_notm}} 플랫폼 내부 엔드포인트에 대한 액세스는
외부 사용자로 제한됩니다.</dd>

<dt>감사</dt>
<dd>애플리케이션 개발자의 모든 성공 및 실패 인증 시도에 대해
감사 로그가 작성됩니다. 감사 로그는 {{site.data.keyword.Bluemix_notm}} 애플리케이션이 실행되는 컨테이너를 호스팅하는 Linux 시스템에 대한 권한 부여된 액세스에 대해서도 작성됩니다.</dd>

<dt>데이터 보호</dt>
<dd> 모든 {{site.data.keyword.Bluemix_notm}} 트랙픽은 리버스 프록시, SSL 종료 및 로드 밸런싱 기능을 제공하는 IBM WebSphere® DataPower® SOA 어플라이언스를 통과합니다.
다음과 같은 HTTP 메소드를
사용할 수 있습니다.
 * DELETE
 * GET
 * HEAD
 * OPTIONS
 * POST
 * PUT
 * TRACE

HTTP 비활성 제한시간은 2분입니다.

다음 헤더는 DataPower로 채워집니다.
<dl>
<dt>$wsis</dt>
<dd>클라이언트 측 연결이 안전(HTTPS)하면 true로 설정합니다.
그렇지 않으면 false로 설정합니다.</dd>
<dt>$wssc</dt>
<dd>클라이언트 연결 스킴(https, http, ws, wss) 중 하나로
설정합니다.</dd>
<dt>$wssn</dt>
<dd>클라이언트가 보내는 호스트 이름으로 설정합니다.</dd>
<dt>$wssp</dt>
<dd>클라이언트가 연결할 서버 포트로 설정합니다.</dd>
<dt>x-client-ip</dt>
<dd>클라이언트 IP 주소로 설정합니다.</dd>
<dt>x-forwarded-proto</dt>
<dd>클라이언트 연결 스킴(https, http, ws, wss) 중 하나로
설정합니다.</dd>
</dl>
</dd>

<dt>보안 개발 방식 실행</dt>
<dd> {{site.data.keyword.Bluemix_notm}} Public 및 Dedicated의 경우 주기적 보안 취약성 스캔은 IBM Security AppScan® Dynamic Analyzer 및 정적 분석기 오퍼링을 사용하여 다양한 {{site.data.keyword.Bluemix_notm}} 컴포넌트에서 수행됩니다. 위협 모델링 및 침입 테스트는 모든 {{site.data.keyword.Bluemix_notm}} 배치 유형에 대해 잠재적 취약점을 발견하고 해결하기 위해 사용됩니다. 또한 애플리케이션 개발자는 AppScan Dynamic Analyzer 서비스를 사용하여 {{site.data.keyword.Bluemix_notm}}에 배치된 자체 웹 앱을 보호할 수 있습니다.</dd>
</dl>

### 인프라 보안

{{site.data.keyword.Bluemix_notm}}는
애플리케이션 실행을 위한 강력한 토대를 제공하기 위해
Cloud Foundry를 기반으로 빌드됩니다. 아키텍처 내에서 보안 및 격리를 위한 여러 컴포넌트가
제공됩니다. 또한 변경 관리 및 백업 및 복구 프로시저가 무결성 및 가용성을 보장하기 위해 구현됩니다.

<dl>
<dt>환경 격리</dt>
<dd> {{site.data.keyword.Bluemix_notm}} Public의 경우 개발 및 프로덕션 환경은 애플리케이션 안정성 및 보안성을 높이기 위해 서로 격리됩니다.</dd>

<dt>방화벽</dt>
<dd> 방화벽은 {{site.data.keyword.Bluemix_notm}} 네트워크에 대한 액세스를 제한하기 위해 적절히 갖춰져 있습니다. {{site.data.keyword.Bluemix_notm}}
Local의 경우 사용자의 회사 방화벽은 사용자의 나머지 네트워크를
{{site.data.keyword.Bluemix_notm}} 인스턴스에서 분리합니다.</dd>

<dt>침입 방지</dt>
<dd>{{site.data.keyword.Bluemix_notm}} Public 및 Dedicated에서는 위협을 발견하여 이를 처리할 수 있도록 침입 방지를 사용합니다. 침입 방지 정책은 방화벽에서 사용됩니다.</dd>

<dt>보안 애플리케이션 컨테이너 관리</dt>
<dd>각 {{site.data.keyword.Bluemix_notm}} 애플리케이션은
격리되어 있으며 프로세서, 메모리 및 디스크에 대한 특정 자원 한계가 있는 자체 컨테이너에서 실행됩니다.</dd>

<dt>운영 체제 보안 강화</dt>
<dd>IBM 관리자는 IBM Endpoint Manager 등의 도구를 사용하여 네트워크 및 운영 체제 강화를 주기적으로 수행합니다.</dd>
</dl>

### 운영 보안

{{site.data.keyword.Bluemix_notm}}에서는
다음과 같은 제어 권한이 있는 강력한 운영 보안 환경을 제공합니다.

<dl>
<dt>취약성 스캔</dt>
<dd>{{site.data.keyword.Bluemix_notm}}는
Tenable Network Security 취약성 스캔 도구 Nessus를 사용하여
네트워크 및 호스트 구성 문제를 발견하여 해결할 수 있도록 합니다.</dd>

<dt>자동화된 수정사항 관리</dt>
<dd>{{site.data.keyword.Bluemix_notm}} 관리자는
운영 체제의 수정사항이 적합한 빈도로 적용되도록 보장합니다. 자동화된 수정사항은 IBM Endpoint Manager를 사용하여 적용됩니다.</dd>

<dt>감사 로그 통합 및 분석</dt>
<dd>{{site.data.keyword.Bluemix_notm}}에서는 IBMSecurity QRadar® 도구를 사용하여 Linux 로그를 통합함으로써 Linux 시스템에서 권한 부여된 액세스를 모니터링합니다. 또한 {{site.data.keyword.Bluemix_notm}}는 IBM QRadar 보안 정보 및 이벤트 관리(SIEM)를 사용하여 애플리케이션 개발자의 성공 및 실패한 로그인 시도를 모니터링합니다.</dd>

<dt>사용자 액세스 관리</dt>
<dd>{{site.data.keyword.Bluemix_notm}} 내에서는 업무 분리 가이드라인에 따라 사용자에게 세부 단위의 액세스 권한을 지정하며 사용자가 최소 권한 원칙에 따라 자체 작업의 수행에 필요한 액세스 권한만 갖도록 보장합니다.

{{site.data.keyword.Bluemix_notm}} Dedicated 및 Local 환경 내에서는 지정된 관리자가 관리 콘솔을 사용하여 조직 내 {{site.data.keyword.Bluemix_notm}} 사용자의 역할 및 권한을 관리할 수 있습니다. 세부사항은 [{{site.data.keyword.Bluemix_notm}}](../admin/index.html#mng) 관리를 참조하십시오.
</dd>
</dl>

### 물리적 보안

{{site.data.keyword.Bluemix_notm}} Public 및 Dedicated에서는 실제 네트워크 보안을 위해 SoftLayer의 네트워크 내 네트워크(network-within-a-network) 토폴로지에 의존합니다. 이러한 네트워크 내 네트워크 아키텍처를 사용하여
권한 있는 사용자만 시스템에 완전히 액세스할 수 있도록
할 수 있습니다. {{site.data.keyword.Bluemix_notm}} Local에 대해 사용자는 로컬 인스턴스에 대한
실제 보안을 소유합니다. 데이터 센터는 회사 방화벽 뒤에서 보호됩니다.

SoftLayer 네트워크 내 네트워크(network-within-a-network)에서 공용 네트워크 계층은 호스팅된 웹 사이트 또는 온라인 자원에 대한 공용 트래픽을 처리합니다. 사설 네트워크 계층을 사용하면 SSL, PPTP 또는 IPSec VPN 게이트웨이에서 개별 독립형 써드파티 업체를 통해 진정한 대역 외 관리를 수행할 수 있습니다. 데이터 센터 간 네트워크 계층은 개별 SoftLayer 설비에 포함된 서버 간의 무료 보안 연결을 제공합니다.

모든 SoftLayer 데이터 센터는 예외 없이 SSAE 16 및 업계에서 인정하는 요구사항을 충족하는 제어에 따라 완벽하게 보호됩니다. 자세한 정보는 SoftLayer 보안 규제 준수 페이지를 참조하십시오.

## 데이터 보안
{: #data-security}

{{site.data.keyword.Bluemix_notm}}에서는
비인가 액세스에 대한 데이터 보안이
{{site.data.keyword.Bluemix_notm}}와 사용자 간의 공동 노력으로 이루어집니다.

실행 중인 애플리케이션과 연관된 데이터는 전송 중 데이터(data-in-transit),
저장 데이터(data-at-rest) 및 사용 중 데이터(data-in-use)의 세 가지 상태 중 하나일 수 있습니다.

<dl>
<dt>전송 중 데이터(data-in-transit)</dt>
<dd>네트워크의 노드 간에 전송 중인 데이터입니다.</dd>

<dt>저장 데이터(data-at-rest)</dt>
<dd>저장된 데이터입니다.</dd>

<dt>사용 중 데이터(data-in-use)</dt>
<dd>현재 저장 중이 아니며 엔드포인트에서 실행 중인 데이터입니다.</dd>
</dl>

각각의 데이터 유형은 데이터 보안을 계획할 때 고려되어야 합니다.

{{site.data.keyword.Bluemix_notm}} 플랫폼은 {{site.data.keyword.Bluemix_notm}} 내부 네트워크의 경계에서 데이터가 IBM DataPower Gateway에 도달할 때까지 네트워크를 통해 SSL을 사용하여 애플리케이션에 대한 일반 사용자 액세스를 보호함으로써 전송 중 데이터를 보호합니다. IBM DataPower Gateway는 리버스 프록시 역할을 하며 SSL 종료를 제공합니다.

사용 중 데이터 및 저장 데이터 둘 다에 대한 보안은 애플리케이션 개발 중에 사용자의 책임입니다. {{site.data.keyword.Bluemix_notm}} 카탈로그에서 사용 가능한 다수의 데이터 관련 서비스를 활용하면 이와 관련하여 도움을 받을 수 있습니다.

## {{site.data.keyword.Bluemix_notm}} 애플리케이션 보안
{: #application-security}

애플리케이션 개발자는
{{site.data.keyword.Bluemix_notm}}에서 실행되는
애플리케이션에 대해 애플리케이션 데이터 보호를 포함하여
보안 구성을 사용하도록 설정해야 합니다.

여러 {{site.data.keyword.Bluemix_notm}} 서비스에서 제공하는 보안 기능을 사용하여
애플리케이션을 보호할 수 있습니다. IBM에서 생성하는 모든 {{site.data.keyword.Bluemix_notm}} 서비스는 IBM 보안 엔지니어링 개발 방식을 따릅니다.

**참고:** 여기에 설명된 서비스 중 일부는 Bluemix Dedicated 또는 Local 인스턴스에 적용되지 않을 수 있습니다.

### SSO 서비스

{{site.data.keyword.Bluemix_notm}}용 IBM Single Sign-On은 Node.js 또는 Liberty for Java™ 애플리케이션의 임베드 용이한 싱글 사인온 기능을 제공하는 정책 기반 인증 서비스입니다. 애플리케이션 개발자가 애플리케이션으로 싱글 사인온 기능을 임베드할 수 있도록 하기 위해
관리자는 서비스 인스턴스를 작성하고 ID 소스를 추가합니다.

Single Sign On 서비스는 사용자의 신임 정보가 저장된 다수의 ID 소스를 지원합니다.

<dl>
<dt>SAML Enterprise</dt>
<dd>인증을 수행하며 SAML 토큰 교환을 사용하는 사용자 레지스트리입니다.</dd>

<dt>클라우드 디렉토리</dt>
<dd>IBM Cloud에서 호스팅되는 사용자 레지스트리입니다.</dd>

<dt>소셜 ID 소스</dt>
<dd> Google, Facebook 및 LinkedIn에서 유지보수하는 사용자 레지스트리입니다.</dd>
</dl>

자세한 정보는 [Single Sign-On 시작하기](../services/SingleSignOn/index.html)를 참조하십시오.

### AppScan Mobile Analyzer

이 서비스는 Android 모바일 애플리케이션의
보안 분석을 제공합니다. 이 서비스를 사용하려면
컴파일된 Android 앱을 APK 파일로 업로드해야 합니다. 보안 분석 스캔이 완료되면
보고서를 다운로드할 수 있습니다.

자세한 정보는 [AppScan Mobile Analyzer 시작하기](../services/AppScanMobileAnalyzer/index.html)를 참조하십시오.

### AppScan Dynamic Analyzer

이 서비스는 동적 분석 도구를 사용한
웹 애플리케이션의 보안 분석을 제공합니다. 이 도구는 앱 소스 코드가 아니라 배치된 웹 앱에서 작동하고
언어 또는 기술에 관계없이
임의의 {{site.data.keyword.Bluemix_notm}} 웹 앱을
스캔할 수 있습니다. 사용자가 속해 있는 조직의 애플리케이션만
스캔할 수 있습니다. 스캔을 작성하려면
웹 앱 URL과 로그인 신임 정보(있는 경우)를
구성해야 합니다. 스캔이 완료되면
보고서를 다운로드할 수 있습니다.

자세한 정보는 [AppScan Dynamic Analyzer 시작하기](../services/AppScanDynamicAnalyzer/index.html)를 참조하십시오.

### Mobile Analyzer for iOS(베타)

Mobile Analyzer for iOS 서비스는 iOS 모바일 애플리케이션에 대한 AppScan 동적 보안 분석을 제공합니다. 이는 iOS 모바일 앱의 보안 문제를 식별하는 데 도움이 됩니다.

자세한 정보는 [Mobile Analyzer for iOS 시작하기](../services/AppScanIOS/index.html)를 참조하십시오.

### Static Analyzer(베타)

Static Analyzer 서비스는 클라우드에서 정적 애플리케이션 보안 테스트를 사용합니다. 이는 소프트웨어 개발 라이프사이클의 초기에 소스 코드 취약점을 찾는 데 도움이 되므로, 배치 전에 해당 취약점을 수정할 수 있습니다.

Static Analyzer로 로컬 디스크에서 명령행 인터페이스(CLI)를 사용하여 Java 및 Java 웹 컨텐츠를 스캔할 수 있습니다. 또한 Static Analyzer 플러그인을 Eclipse 또는 Maven에 추가하는 소형 설치 프로그램을 실행할 수 있습니다. 클라이언트 유틸리티를 사용하면 아카이브 파일에 사용자 파일에 대한 정보를 스캔 및 수집할 수 있으며,
이 파일을 다시 스캔 결과를 위해 클라우드에 제출할 수 있습니다.

자세한 정보는 [IBM Analyzer for Bluemix 시작하기](../services/StaticAnalyzer/index.html)를 참조하십시오.

### 애플리케이션 보안 테스트를 위한 IBM UrbanCode 플러그인

IBM Application Security Testing for {{site.data.keyword.Bluemix_notm}} 플러그인을 사용하면 {{site.data.keyword.Bluemix_notm}}에서 호스팅되는 사용자 웹 또는 Android 앱에서 보안 스캔을 실행할 수 있습니다. 이 플러그인은 IBM Bluemix DevOps 서비스 플랫폼에서 IBM UrbanCode™ Deploy 커뮤니티에 의해 개발되고 지원됩니다.

자세한 정보는 [IBM Application Security Testing for Bluemix](https://developer.ibm.com/urbancode/plugindoc/ibmucd/ibm-application-security-testing-bluemix/1-0/)로 이동하십시오.

### SQL Database

SQL Database 서비스는 완전히 프로비저닝된 관계형 데이터베이스를 앱에 추가합니다. 이 서비스는 애플리케이션에서 액세스하는 데이터베이스를 보호하기 위해 인증용 IBM Directory Server LDAP 및 IBM InfoSphere® Guardium® Data Activity Monitor를 사용합니다. 애플리케이션 및 데이터베이스 사이의 연결은
DigiCert가 서명하는 SSL 인증서에 의해 보호됩니다.

이 서비스의 특정 플랜에서 {{site.data.keyword.Bluemix_notm}}x의 SQL 데이터베이스 콘솔을 사용하여 다음 정보가 포함된 보고서를 가져올 수 있습니다.

 * 애플리케이션이 액세스하는 데이터베이스에 있을 수 있는
민감한 데이터
 * 지정된 기간 내에 데이터베이스에 액세스한
애플리케이션 사용자
 * 데이터베이스에 있는 민감한 데이터에 액세스하는
애플리케이션 사용자

SQL을 사용하여 데이터를 마스킹하기 위해
애플리케이션은 데이터베이스와 함께 배치되는
마스킹 사용자 정의 기능(UDF)을 호출할 수 있습니다. 예를 들어, 테스트를 위해 다른 곳에 사용하려는
데이터를 마스킹할 수 있습니다. UDF는 IBM Infosphere Optim™에서 데이터 마스킹 알고리즘을 구현합니다.

이 서비스의 프리미엄 플랜에는 데이터 암호화도 포함됩니다. 이 서비스에 대한 자세한 정보는 [SQL Database 시작하기](../services/SQLDB/index.html)를 참조하십시오.

### dashDB

dashDB 서비스는 애플리케이션에서 액세스하는 데이터베이스를 보호하기 위해 사용자 인증용 IBM Directory Server LDAP와 IBM InfoSphere Guardium Data Activity Monitor를 사용합니다. 애플리케이션 및 데이터베이스 사이의 연결은
SSL 인증서에 의해 보호됩니다. 이 서비스는 배치된 데이터베이스와 데이터베이스 백업을 자동으로 암호화하기 위해 DB2® 원시 암호화 기능을 사용합니다. 마스터 키 회전은 자동이고 90일마다
수행됩니다.

자세한 정보는 [dashDB 시작하기](services/dashDB/index.html)를 참조하십시오.

### Cloud Integration

Cloud Integration 서비스를 사용하면 클라우드 및 사내 구축형 데이터를 통합할 수 있습니다. 백엔드 데이터베이스(예: DB2, Oracle 및 SAP)와 상호작용하기 위한 서비스를 추가할 수 있습니다. 그리고 데이터를 이동하거나 액세스하고 사용할
{{site.data.keyword.Bluemix_notm}}
애플리케이션의 REST API를 작성할 수 있습니다. 서비스는 사내 구축형 보안 커넥터와의 보안 통신이 가능하도록 하며,
애플리케이션이 사용하는 REST API로서 백엔드 SOR(System of Record)을 노출합니다.

자세한 정보는 [Cloud Integration 시작하기](../services/CloudIntegration/index.html)를 참조하십시오.

### Secure Gateway

Secure Gateway 서비스를 사용하면 사내 구축형 또는 클라우드에서 원격 위치에 {{site.data.keyword.Bluemix_notm}} 앱을 안전하게 연결할 수 있습니다. 이는 보안 연결을 제공하며 {{site.data.keyword.Bluemix_notm}} 조직 및
연결하고자 하는 원격 위치 간에 터널을 설정합니다. {{site.data.keyword.Bluemix_notm}} 사용자 인터페이스 또는
API 패키지를 사용하여 보안 게이트웨이를 구성하고 작성할 수 있습니다.

자세한 정보는 [Secure Gateway 시작하기](../services/SecureGateway/index.html)를 참조하십시오.

## {{site.data.keyword.Bluemix_notm}} 보안 배치
{: #security-deployment}

{{site.data.keyword.Bluemix_notm}} 보안 배치 아키텍처에는
보안 액세스를 보장할 수 있도록 앱 사용자 및 개발자용 다양한 정보 플로우가 포함되어 있습니다.

![Bluemix 보안 배치 아키텍처](images/sec_deployment.png)

*그림 3. Bluemix 보안 배치 아키텍처*

{{site.data.keyword.Bluemix_notm}} *앱 사용자*용 정보 플로우는 다음과 같습니다.
 1. 방화벽을 통해(침입 방지 및 네트워크 보안이 적절히 갖춰져 있음).
 2. IBM DataPower Gateway를 통해(리버스 프록시 및 SSL 종료 프록시 포함).
 3. 네트워크 라우터를 통해.
 4. DEA(Droplet Execution Agent)에서 애플리케이션 런타임에 도달합니다.

{{site.data.keyword.Bluemix_notm}} *개발자*는 두 개의 기본 플로우(로그인용과 개발 및 배치용)를 따릅니다.
 * 로그인용 개발자 플로우에는 다음이 포함됩니다.
    * {{site.data.keyword.Bluemix_notm}} Public에 로그인한 개발자의 경우
플로우는 다음과 같습니다.
      1. IBM Single Sign On 서비스를 통해.
      2. IBM 웹 ID를 통해.
    * {{site.data.keyword.Bluemix_notm}} Dedicated 또는 Local에 로그인한 개발자의 경우 플로우는 엔터프라이즈 LDAP를 통합니다.
 * 앱 개발 및 배치용 개발자 플로우는 다음과 같습니다.
    1. 방화벽을 통해(침입 방지 및 네트워크 보안이 적절히 갖춰져 있음). {{site.data.keyword.Bluemix_notm}} Dedicated에만 적용됩니다.
    2. IBM DataPower Gateway를 통해(리버스 프록시 및 SSL 종료 프록시 포함).
    3. 네트워크 라우터를 통해.
    4. Cloud Foundry 클라우드 제어기를 사용한 권한 부여를 통해(개발자가 작성한 앱 및 서비스 인스턴스에 대한 액세스만 보장할 수 있도록).

이 경로에서 기술된 사용자와 더불어 인가된 IBM 보안 운영 팀은 다음과 같은 다양한 운영 보안 태스크를 수행합니다.
 * 취약성 스캔. {{site.data.keyword.Bluemix_notm}} Local에 대해 사용자는 방화벽 내 실제 보안 및 스캔을 소유합니다.
 * 사용자 액세스 관리.
 * IBM Endpoint Manager로 수정사항을 주기적으로 적용하여 운영 체제 강화.
 * 침입 방지로 위험성 관리.
 * QRadar로 보안 모니터링.
 * 관리 콘솔을 통해 사용 가능한 보안 보고서

# rellinks
## 일반 
* [SoftLayer 보안 규제 준수](http://www.softlayer.com/security)
* [Single Sign On 시작하기](../services/SingleSignOn/index.html)
