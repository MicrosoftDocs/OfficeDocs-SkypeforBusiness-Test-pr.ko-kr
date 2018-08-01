---
title: 보관된 Microsoft Lync Server 2013 데이터를 검색하도록 Microsoft SharePoint Server 2013 구성
TOCTitle: 보관된 Microsoft Lync Server 2013 데이터를 검색하도록 Microsoft SharePoint Server 2013 구성
ms:assetid: 17f49365-8778-4962-a41b-f96faf6902f1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687978(v=OCS.15)
ms:contentKeyID: 49885662
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관된 Microsoft Lync Server 2013 데이터를 검색하도록 Microsoft SharePoint Server 2013 구성

 

_**마지막으로 수정된 항목:** 2014-02-04_

인스턴트 메시징 및 웹 회의 대화 내용을 Microsoft Lync Server 2013이 아닌 Microsoft Exchange Server 2013에 저장하는 경우의 가장 큰 이점 중 하나는, 데이터를 같은 위치에 저장할 수 있으므로 관리자가 단일 도구를 사용해 보관된 Exchange 데이터 및/또는 보관된 Lync Server 데이터를 검색할 수 잇다는 것입니다. 모든 데이터가 같은 위치(Exchange)에 저장되므로, 보관된 Exchange 데이터를 검색할 수 있는 모든 도구를 통해 보관된 Lync Server 데이터도 검색할 수 있습니다.

보관된 데이터를 쉽게 검색하는 데 사용할 수 있는 도구 중 하나는 Microsoft SharePoint Server 2013입니다. SharePoint를 사용하여 Lync Server 데이터를 검색하려면 먼저 Lync Server에서 Exchange 보관 구성과 관련된 모든 단계를 완료해야 합니다. Exchange 2013 및 Lync Server 2013을 정상적으로 통합한 후에는 SharePoint 서버에 Exchange 웹 서비스 관리 API 버전 2.0을 설치해야 합니다. 해당 API의 설치 프로그램은 Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?linkid=258305\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=258305%26clcid=0x412))에서 다운로드할 수 있습니다. 다운로드한 파일(EWSManagedAPI.msi)은 SharePoint 서버의 원하는 폴더에 저장하면 됩니다.

파일을 다운로드한 후 SharePoint 서버에서 다음 절차를 완료합니다.

1.  **시작**, **모든 프로그램**, **보조 프로그램**을 차례로 클릭하고 **명령 프롬프트**를 마우스 오른쪽 단추로 클릭한 후 **관리자로 실행**을 클릭하여 명령 창을 엽니다.

2.  명령 창에서 **cd** 명령을 사용하여 현재 디렉터리를 EWSManagedAPI.msi 파일이 저장된 폴더로 변경합니다. 예를 들어 파일을 C:\\Download에 저장한 경우 명령 창에 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        cd C:\Downloads

3.  API를 설치하려면 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        msiexec /I EwsManagedApi.msi addlocal="ExchangeWebServicesApi_Feature,ExchangeWebServicesApi_Gac"

4.  API가 설치되고 나면 다음 명령을 입력하고 Enter 키를 눌러 IIS를 다시 설정합니다.
    
        iisreset

Exchange 웹 서비스를 설치한 후에는 SharePoint Server 2013과 Exchange 2013 간에 서버 간 인증을 구성해야 합니다. 이렇게 하려면 먼저 SharePoint 2013 관리 셸을 열고 다음 명령 집합을 실행합니다.

    New-SPTrustedSecurityTokenIssuer -Name "Exchange" -MetadataEndPoint "https://autodiscover.litwareinc.com/autodiscover/metadata/json/1"
    $service = Get-SPSecurityTokenServiceConfig
    $service.HybridStsSelectionEnabled = $True
    $service.AllowMetadataOverHttp = $False
    $service.AllowOAuthOverHttp = $False
    $service.Update()


> [!NOTE]
> 이때 자동 검색 서비스의 URI를 사용해야 합니다. 예제 URI https://autodiscover.litwareinc.com/autodiscover/metadata/json/1을 사용하지 마십시오.



토큰 발급자를 만들고 토큰 서비스를 구성한 후에는 예제 URL http://atl-sharepoint-001을 실제 SharePoint 사이트의 URL로 바꿔 다음 명령을 실행합니다.

    $exchange = Get-SPTrustedSecurityTokenIssuer "Exchange"
    $app = Get-SPAppPrincipal -Site "https://atl-sharepoint-001" -NameIdentifier $exchange.NameID
    $site = Get-SPSite  "https://atl-sharepoint-001"
    Set-SPAppPrincipalPermission -AppPrincipal $app -Site $site.RootWeb -Scope "SiteSubscription" -Right "FullControl" -EnableAppOnlyPolicy

Exchange 2013에 대해 서버 간 인증을 구성하려면 Exchange 관리 셸을 열고 다음과 같은 명령을 실행합니다(Exchange가 C 드라이브에 설치되었으며 기본 폴더 경로를 사용한다고 가정함).

    "C:\Program Files\Microsoft\Exchange Server\V15\Scripts\Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl 'https://atl-sharepoint-001/_layouts/15/metadata/json/1' -ApplicationType SharePoint"

파트너 응용 프로그램을 구성한 후에는 모든 Exchange 사서함 및 클라이언트 액세스 서버에서 IIS(인터넷 정보 서비스)를 중지했다가 다시 시작하는 것이 좋습니다. 다음과 같은 명령을 사용하여 IIS를 다시 시작할 수 있으며, 이 명령은 atl-exchange-001 컴퓨터에서 서비스를 다시 시작합니다.

    iisreset atl-exchange-001

이 명령은 Exchange 관리 셸 내에서 실행할 수도 있고 다른 명령 창에서 실행할 수도 있습니다.

다음으로 아래와 같은 명령을 실행하면 지정한 사용자(이 예제에서는 kenmyer)에게 Exchange에서 검색을 수행하는 권한이 제공됩니다.

    Add-RoleGroupMember "Discovery Management" -Member "kenmyer"

Exchange 및 SharePoint 간에 서버 간 인증을 설정한 후에는 SharePoint에서 eDiscovery 사이트를 만듭니다. 이 작업을 수행하려면 SharePoint 관리 셸에서 다음과 같은 명령을 실행합니다.

    $template = Get-SPWebTemplate | Where-Object {$_.Title -eq "eDiscovery Center"}
    New-SPSite -Url "https://atl-sharepoint-001/sites/discovery" -OwnerAlias "kenmyer" -Template $Template -Name "Discovery Center"


> [!NOTE]
> "eDiscovery"는 "electronic discovery(전자 검색)"의 줄임말로, 보통 법정에서 "적절하게 계산하여 채택될 수 있는 증거가 될 수 있는" 항목을 전자 보관 파일에서 찾는 프로세스를 지칭합니다.



새 사이트가 준비되면 다음 단계로는 SharePoint의 결과 원본으로 작동하도록 Exchange 2013을 구성합니다. 이렇게 하려면 SharePoint 2013 중앙 관리 페이지에서 다음 절차를 완료합니다.

1.  중앙 관리 페이지에서 **서비스 응용 프로그램 관리**를 클릭한 다음 **Search Service 응용 프로그램**을 클릭합니다.

2.  Search Service 응용 프로그램: 검색 관리 페이지에서 **결과 원본**을 클릭하고 **새 결과 원본**을 클릭합니다.

3.  **새 결과 원본** 창의 **이름** 상자에 새 결과 원본의 이름을 **Microsoft Exchange**와 같이 입력합니다. 결과 원본 **프로토콜**로는 **Exchange**를 선택하고 Exchange 서버의 웹 서비스 원본 URL을 **Exchange 원본 URL** 상자에 입력합니다. 원본 URL은 다음과 같습니다.
    
    https://atl-exchange-001.litwareinc.com/ews/exchange.asmx

4.  **자동 검색 사용**이 선택되어 있지 않은지 확인하고 **확인**을 클릭합니다.

마지막으로 SharePoint 검색 사이트(예: https://atl-sharepoint-001/sites/discovery)에서 다음 절차를 완료하여 새 eDiscovery 사례와 새 eDiscovery 설정을 만듭니다.

1.  사이트 콘텐츠 페이지에서 **새 사례 만들기**를 클릭합니다.

2.  사이트 콘텐츠: 새 SharePoint 사이트 페이지에서 사용자의 전자 메일 별칭(예: **kenmyer**)을 **제목**상자에 입력하고 동일한 URL을 **웹 사이트 주소** 상자에 추가합니다. 그러면 다음과 같은 URL이 작성됩니다.
    
    https://atl-sharepoint-001/sites/eDiscovery/kenmyer

3.  **만들기**를 클릭합니다.

4.  eDiscovery 설정 페이지가 나타나면 **식별 및 보존: 검색 설정**에서 **새 항목**을 클릭합니다.

5.  새로 만들기: 검색 설정 페이지의 **검색 설정 이름** 상자에 사용자의 전자 메일 별칭을 입력합니다. **필터** 상자에 **eDiscovery Lync\*** 를 입력하고 **원본 추가 및 관리**를 클릭합니다.

6.  원본 추가 및 관리 페이지에서 **사서함** 아래 첫 번째 텍스트 상자에 사용자 전자 메일 별칭을 입력합니다. 해당 텍스트 상자 옆의 사서함 확인 아이콘을 클릭하여 SharePoint에서 지정된 사서함에 연결할 수 있는지 확인합니다.

7.  **확인**을 클릭합니다.

8.  eDiscovery 설정 페이지에서 **저장**을 클릭하여 새 eDiscovery 집합을 저장합니다.

이제 다른 SharePoint 콘텐츠 또는 결과 원본과 같은 방식으로 지정된 사서함(kenmyer)을 검색하거나 원본 위치 유지를 사용하도록 설정할 수 있습니다.

