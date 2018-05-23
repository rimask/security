---



copyright:

  years: 2014, 2018

lastupdated: "2018-04-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# {{site.data.keyword.Bluemix_notm}} 安全
{: #security}

{{site.data.keyword.Bluemix}} 平台以安全工程作法進行設計，具有跨網路及基礎架構的分層安全控制。{{site.data.keyword.Bluemix_notm}} 提供一組安全服務，可讓應用程式開發人員用來保護其行動及 Web 應用程式。這些元素結合在一起，讓 {{site.data.keyword.Bluemix_notm}} 成為具有清楚的安全應用程式開發選擇的平台。
{:shortdesc}

{{site.data.keyword.Bluemix_notm}} 堅守由 IBM 在系統、網路及安全工程方面的最佳作法所驅動的安全原則，進而確保安全無虞。這些原則包括原始碼掃描、動態掃描、威脅建模以及滲透測試等作法。{{site.data.keyword.Bluemix_notm}} 遵循 IBM Product Security Incident Response Team (PSIRT) 處理程序，來進行資安突發事件管理。如需詳細資料，請參閱 [IBM Security Vulnerability Management (PSIRT) ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www-03.ibm.com/security/secure-engineering/process.html){: new_window} 網站。

{{site.data.keyword.Bluemix_notm}} Public 及 Bluemix Dedicated 使用「{{site.data.keyword.BluSoftlayer}} 基礎架構即服務 (IaaS)」雲端服務，並充分運用其安全架構。{{site.data.keyword.BluSoftlayer}} IaaS 為您的應用程式及資料提供層層重疊的多個保護層級。若為 {{site.data.keyword.Bluemix_notm}} Local，您藉由在公司防火牆後、自己的資料中心內管理 {{site.data.keyword.Bluemix_notm}} Local，而掌控實體安全並提供基礎架構。此外，{{site.data.keyword.Bluemix_notm}} 也在「平台即服務」層新增不同種類（平台、資料及應用程式）的安全功能。

## {{site.data.keyword.Bluemix_notm}} 平台的安全
{: #platform-security}

{{site.data.keyword.Bluemix_notm}} 為核心平台提供了功能安全、基礎架構安全、作業安全及實體安全（透過 {{site.data.keyword.BluSoftlayer}}）。 不過，{{site.data.keyword.Bluemix_notm}} Local 獨特之處在於，客戶會提供基礎架構及資料中心，並掌控實體安全。

{{site.data.keyword.BluSoftlayer}} 的 {{site.data.keyword.Bluemix_notm}} 環境符合最嚴格的 IBM 資訊技術 (IT) 安全標準，這些標準已達到或超越業界標準。這些標準包括下列項目：網路、資料加密及存取控制
 * 應用程式 ACL、許可權及滲透測試
 * 識別、鑑別及授權
 * 資訊及資料保護
 * 服務完整性和可用性
 * 漏洞及修正程式管理
 * 拒絕服務及系統攻擊偵測
 * 資安突發事件回應

![Bluemix 平台安全概觀](images/platform_sec.svg)

圖 1. {{site.data.keyword.Bluemix_notm}} 平台安全概觀

運用 {{site.data.keyword.Bluemix_notm}} Local，您可以管理受公司防火牆保護以及在資料中心內的 {{site.data.keyword.Bluemix_notm}}。因此，您要負責特定的安全層面。下圖詳述客戶掌控哪些部分的安全，而哪些部分的安全則由 IBM 所管理及維護。

![Bluemix Local 平台安全概觀](images/security_local_platform.svg) {: #localplatformsecurity}

圖 2. {{site.data.keyword.Bluemix_notm}} Local 平台安全概觀

IBM 透過「轉遞」來安裝、遠端監視及管理資料中心中的 {{site.data.keyword.Bluemix_notm}} Local，而「轉遞」是 {{site.data.keyword.Bluemix_notm}} Local 內含的一種交付功能。「轉遞」會使用每一個 {{site.data.keyword.Bluemix_notm}} Local 實例特有的憑證安全地進行連接。如需 {{site.data.keyword.Bluemix_notm}} Local 及「轉遞」的相關資訊，請參閱 [Bluemix Local](/docs/local/index.html)。

### 功能安全

{{site.data.keyword.Bluemix_notm}} 提供各種功能安全方面的功能，包括使用者鑑別、存取授權、重要作業審核，以及資料保護。

<dl>
<dt>鑑別</dt>
<dd>應用程式開發人員利用 IBM Web 身分向 {{site.data.keyword.Bluemix_notm}} 進行鑑別。

若為 {{site.data.keyword.Bluemix_notm}} Dedicated 及 Bluemix Local，依預設會支援透過 LDAP 進行鑑別。在要求時，可以改為針對 {{site.data.keyword.Bluemix_notm}} 設定透過 IBM Web 身分進行鑑別。
</dd>

<dt>授權</dt>
<dd>{{site.data.keyword.Bluemix_notm}} 使用 Cloud Foundry 機制來確保每一個應用程式開發人員都只能存取其所建立的應用程式及服務實例。對 {{site.data.keyword.Bluemix_notm}} 服務的授權是根據 OAuth。外部使用者在存取所有「{{site.data.keyword.Bluemix_notm}} 平台」內部端點時會受到限制。</dd>

<dt>審核</dt>
<dd>對應用程式開發人員的所有鑑別嘗試，不論成功或失敗，都會建立審核日誌。對於管理 {{site.data.keyword.Bluemix_notm}} 應用程式執行所在容器的 Linux 系統，其特許存取也會建立審核日誌。</dd>

<dt>資料保護</dt>
<dd> 所有 {{site.data.keyword.Bluemix_notm}} 資料流量都會通過 IBM WebSphere® DataPower® SOA Appliance，它們提供反向 Proxy、SSL 終止及負載平衡功能。以下是允許使用的 HTTP 方法：
<ul>
<li>DELETE</li>
<li>GET</li>
<li>HEAD</li>
<li>OPTIONS</li>
<li>POST</li>
<li>PUT</li>
<li>TRACE</li>
</ul>
HTTP 閒置逾時為 2 分鐘。</dd>
<dd>下列標頭由 DataPower 移入：<dl>
<dt>$wsis</dt>
<dd>如果用戶端連線為安全的連線 (HTTPS)，請設為 true；否則請設為 false。</dd>
<dt>$wssc</dt>
<dd>設為下列其中一個用戶端連線方法：https、http、ws 或 wss。</dd>
<dt>$wssn</dt>
<dd>設為用戶端傳送的主機名稱。</dd>
<dt>$wssp</dt>
<dd>設為用戶端連接的伺服器埠。</dd>
<dt>x-client-ip</dt>
<dd>設為用戶端 IP 位址。</dd>
<dt>x-forwarded-proto</dt>
<dd>設為下列其中一個用戶端連線方法：https、http、ws 或 wss。</dd>
</dl>
</dd>

<dt>安全開發作法</dt>
<dd> 若為 {{site.data.keyword.Bluemix_notm}} Public 及 Bluemix Dedicated，會利用 IBM Security AppScan® Dynamic Analyzer，在各種 {{site.data.keyword.Bluemix_notm}} 元件上定期執行安全漏洞掃描。會執行威脅建模及滲透測試，以偵測並解決所有類型之 {{site.data.keyword.Bluemix_notm}} 部署的任何潛在漏洞。此外，應用程式開發人員可以使用 AppScan Dynamic Analyzer 服務來保護在 {{site.data.keyword.Bluemix_notm}} 上部署的 Web 應用程式。</dd>
</dl>

### 基礎架構安全

{{site.data.keyword.Bluemix_notm}} 以 Cloud Foundry 為建置基礎，為執行應用程式提供了強固的基礎。在架構內，提供了多個元件用於安全保護及隔離。此外，也實作了變更管理與備份及回復程序，以確保完整性及可用性。

<dl>
<dt>環境隔離</dt>
<dd> 對於 {{site.data.keyword.Bluemix_notm}} Public，開發及正式作業環境會彼此隔離，以提高應用程式的穩定性及安全。</dd>

<dt>防火牆</dt>
<dd> 實施了防火牆，以限制對 {{site.data.keyword.Bluemix_notm}} 網路的存取。對於 {{site.data.keyword.Bluemix_notm}} Local，貴公司的防火牆會隔離您的 {{site.data.keyword.Bluemix_notm}} 實例與您網路的其餘部分。</dd>

<dt>侵入防禦</dt>
<dd>{{site.data.keyword.Bluemix_notm}} Public 及 Bluemix Dedicated 能促成侵入防禦，以便發現威脅，進而解決這些威脅。防火牆上已啟用侵入防禦原則。</dd>

<dt>安全應用程式容器管理</dt>
<dd>每一個 {{site.data.keyword.Bluemix_notm}} 應用程式都會在自己的容器中隔離和執行，而容器對於處理器、記憶體及磁碟具有特定的資源限制。</dd>

<dt>強化作業系統安全</dt>
<dd>IBM 管理者會利用 IBM Endpoint Manager 等工具，定期執行網路及作業系統的強化作業。</dd>
</dl>

### 作業安全

{{site.data.keyword.Bluemix_notm}} 提供了強固的作業安全環境，以及下列控制措施。

<dl>
<dt>漏洞掃描</dt>
<dd>{{site.data.keyword.Bluemix_notm}} 會使用 Tenable Network Security 漏洞掃描工具 Nessus，來偵測網路及主機配置中發生的任何問題，以便能解決這些問題。</dd>

<dt>自動化修正程式管理</dt>
<dd>{{site.data.keyword.Bluemix_notm}} 管理者確保依適當的頻率套用作業系統的修正程式。利用 IBM Endpoint Manager 即可啟用自動化修正程式。</dd>

<dt>審核日誌合併及分析</dt>
<dd>{{site.data.keyword.Bluemix_notm}} 使用 IBMSecurity QRadar® 工具來合併 Linux 日誌，以監視 Linux 系統上的特許存取。{{site.data.keyword.Bluemix_notm}} 也會使用 IBM QRadar 安全資訊及事件管理 (SIEM)，來監視應用程式開發人員的成功和不成功的登入嘗試。</dd>

<dt>使用者存取管理</dt>
<dd>在 {{site.data.keyword.Bluemix_notm}} 內，會遵循「權責區分」準則，指派精細的存取權給使用者，並確保根據最低專用權原則，使用者僅具備執行其工作所需的存取權。

在 {{site.data.keyword.Bluemix_notm}} Dedicated 及 Bluemix Local 環境內，已指派的管理者可以利用「管理主控台」來管理 {{site.data.keyword.Bluemix_notm}} 使用者在其組織中的角色及許可權。如需詳細資料，請參閱[管理 {{site.data.keyword.Bluemix_local_notm}} 及 {{site.data.keyword.Bluemix_dedicated_notm}}](/docs/hybrid/index.html#mng)。
</dd>
</dl>

### 實體安全

{{site.data.keyword.Bluemix_notm}} Public 及 Bluemix Dedicated 依賴 {{site.data.keyword.BluSoftlayer}} 的「網中網」(network-within-a-network) 拓蹼來確保實體網路安全。這個網中網架構可確保系統只能由獲得授權的人員進行完全存取。若為 {{site.data.keyword.Bluemix_notm}} Local，您掌控了本端實例的實體安全。您的資料中心受到貴公司防火牆的安全保護。

在 {{site.data.keyword.BluSoftlayer}} 網中網內，公用網路層會處理受管理網站或線上資源的公用資料流量。私密網路層容許透過不同的獨立式第三方營運商，經由 SSL、PPTP 或 IPSec VPN 閘道進行真正的頻外管理。資料中心到資料中心的網路層，在位於不同 {{site.data.keyword.BluSoftlayer}} 設施的伺服器之間，提供了免費的安全連線功能。

每個 {{site.data.keyword.BluSoftlayer}} 資料中心都受到符合 SSAE 16 及業界公認要求的控制措施的全面保護，無一例外。

## 資料安全
{: #data-security}

使用 {{site.data.keyword.Bluemix_notm}}，{{site.data.keyword.Bluemix_notm}} 會與您共同努力來保護您的資料不受未獲授權的存取。

與執行中應用程式相關聯的資料，可能處於下列三種狀態之一：data-in-transit、data-at-rest 及 data-in-use。

<dl>
<dt>Data-in-transit</dt>
<dd>在網路上的節點之間傳送的資料。</dd>

<dt>Data-at-rest</dt>
<dd>儲存的資料。</dd>

<dt>Data-in-use</dt>
<dd>目前未儲存，且在某一端點上接受操作的資料。</dd>
</dl>

當您在規劃資料安全時，需要考量每一種類型的資料。

{{site.data.keyword.Bluemix_notm}} 平台會透過網路，利用 SSL 來保護使用者的應用程式存取安全，藉以保護傳輸中資料的安全，直到資料在 {{site.data.keyword.Bluemix_notm}} 內部網路的界限達到 IBM DataPower Gateway 為止。IBM DataPower Gateway 作為反向 Proxy，並提供 SSL 終止。從這裡到應用程式，IPSEC 是用來保護從 IBM DataPower Gateway 前進到應用程式的資料安全。

當您在開發應用程式時，必須負責保護 data-in-use 與 data-at-rest 的安全。您可以充分運用 {{site.data.keyword.Bluemix_notm}}「型錄」中可用的數個資料相關服務，來協助這些重要事項。

## {{site.data.keyword.Bluemix_notm}} 應用程式的安全
{: #application-security}

身為應用程式開發人員，您必須為 {{site.data.keyword.Bluemix_notm}} 上執行的應用程式啟用安全配置，包括應用程式資料保護。

您可以使用數個 {{site.data.keyword.Bluemix_notm}} 服務所提供的安全功能來保護應用程式。IBM 生產的所有 {{site.data.keyword.Bluemix_notm}} 服務都遵循 IBM 安全工程開發作法。

**附註：**這裡所述的一些服務可能不適用於 {{site.data.keyword.Bluemix_notm}} Dedicated 或 Bluemix Local 實例。

### SSO 服務

IBM Single Sign On for {{site.data.keyword.Bluemix_notm}} 是以原則為基礎的鑑別服務，為 Node.js 或 Liberty for Java™ 應用程式提供了易於內嵌的單一登入功能。若要讓應用程式開發人員將單一登入功能內嵌至應用程式，管理者需建立服務實例並新增身分來源。

Single Sign On 服務支援數個儲存使用者認證的身分來源：

<dl>
<dt>SAML 企業</dt>
<dd>透過交換 SAML 記號而完成鑑別的使用者登錄。</dd>

<dt>雲端目錄</dt>
<dd>IBM Cloud 中所管理的使用者登錄。</dd>

<dt>社交身分來源</dt>
<dd> 由 Google、Facebook 及 LinkedIn 所維護的使用者登錄。</dd>
</dl>

如需相關資訊，請參閱[開始使用 Single Sign On](/docs/services/SingleSignOn/index.html)。

### Application Security on Cloud

此服務提供行動及 Web 應用程式的安全分析，並可讓您掃描原始碼是否有安全漏洞。如需相關資訊，請參閱[開始使用 Application Security on Cloud](/docs/services/ApplicationSecurityonCloud/index.html)。

### 用於應用程式安全測試的 IBM UrbanCode 外掛程式

IBM Application Security Testing for {{site.data.keyword.Bluemix_notm}} 外掛程式可讓您針對 {{site.data.keyword.Bluemix_notm}} 上管理的 Web 或 Android 應用程式執行安全掃描。此外掛程式由 IBM UrbanCode™ Deploy Community 所開發及支援。

如需相關資訊，請前往 [IBM Application Security Testing for Bluemix ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/urbancode/plugindoc/ibmucd/ibm-application-security-testing-bluemix/1-0/){: new_window}。

### Db2 on Cloud

{{site.data.keyword.Db2_on_Cloud_long}} 是雲端中為您所佈建的 SQL 資料庫。{{site.data.keyword.Db2_on_Cloud_short}} 的使用方式就像使用任何資料庫軟體一樣，但沒有硬體設定或軟體安裝及維護的額外負擔及費用。  

您也可以使用[免費 Db2 Developer Edition 下載 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions) 來安裝本端 Db2 資料庫。它會在 Docker 容器內使用工具快速安裝 Db2 的備妥開發人員版本（不需要 Docker；它將會自動安裝任何必要元件）。

如需相關資訊，請參閱[開始使用 Db2 on Cloud](/docs/services/Db2onCloud/index.html#getting_started_db2oncloud)。

### Secure Gateway

Secure Gateway 服務可讓您將 {{site.data.keyword.Bluemix_notm}} 應用程式安全地連接至遠端位置（內部部署或雲端）。它提供安全連線功能，並在您的 {{site.data.keyword.Bluemix_notm}} 組織與您要連接的遠端位置之間建立通道。您可以利用 {{site.data.keyword.Bluemix_notm}} 使用者介面或 API 套件，來配置及建立安全閘道。

如需相關資訊，請參閱[開始使用 Secure Gateway](/docs/services/SecureGateway/secure_gateway.html)。

### 安全資訊及事件管理

您可以使用安全資訊及事件管理 (SIEM) 工具來分析應用程式日誌中的安全警示。其中一種這類工具是 IBM Security QRadar&reg; SIEM，其提供雲端環境中的安全智慧。如需相關資訊，請參閱 [IBM QRadar Security Intelligence Platform ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www-01.ibm.com/support/knowledgecenter/SS42VS/welcome?lang=en){: new_window}。
