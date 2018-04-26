---
title: 자동 검색용 인증서 구성
TOCTitle: 자동 검색용 인증서 구성
ms:assetid: 1842191d-df9a-41e0-9286-08c25f9b5dca
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945617(v=OCS.15)
ms:contentKeyID: 52056794
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 자동 검색용 인증서 구성

 

_**마지막으로 수정된 항목:** 2012-12-12_

디렉터 풀, 프런트 엔드 풀 및 역방향 프록시에 대한 인증서에는 Lync 클라이언트와의 보안 연결을 지원하기 위한 추가 주체 대체 이름 항목이 필요합니다.


> [!NOTE]
> <STRONG>Get-CsCertificate</STRONG> cmdlet을 사용하여 현재 지정된 인증서에 대한 정보를 볼 수 있습니다. 하지만 기본 보기에서는 인증서의 속성이 잘려서 표시되므로 SubjectAlternativeNames 속성의 모든 값이 표시되지 않습니다. <STRONG>Get-CsCertificate</STRONG> , <STRONG>Request-</STRONG>CsCertificate 및 <STRONG>Set-CsCertificate</STRONG> cmdlet을 사용하면 일부 정보를 보고 인증서를 요청 및 지정할 수 있습니다. 하지만 현재 인증서에 있는 SAN(주체 대체 이름)의 속성이 확실하지 않을 때는 최선의 방법이 아닙니다. 인증서 및 모든 속성 멤버를 보려면 <EM>MMC(Microsoft Management Console)</EM>에서 인증서 스냅인을 사용하거나 Lync Server 배포 마법사를 사용하는 것이 좋습니다. Lync Server 배포 마법사에서는 인증서 마법사를 사용하여 인증서 속성을 볼 수 있습니다. Lync Server 관리 셸 및 <EM>MMC(Microsoft Management Console)</EM>를 사용하여 인증서를 보고, 요청 및 지정하는 방법은 다음 절차에서 자세히 설명합니다. 선택적인 디렉터 또는 디렉터 풀을 배포한 경우 Lync Server 배포 마법사를 사용하려면 <A href="lync-server-2013-configure-certificates-for-the-director.md">Lync Server 2013에서 디렉터에 대한 인증서 구성</A>을 참조하십시오. 프런트 엔드 서버 또는 프런트 엔드 풀의 경우 <A href="lync-server-2013-configure-certificates-for-servers.md">Lync Server 2013에서 서버에 대한 인증서 구성</A>을 참조하십시오.<BR>이 절차의 시작 단계는 현재 인증서가 수행하는 역할을 확인하는 준비 단계입니다. 이전에 Mobility Services를 설치하지 않았거나 인증서를 미리 준비하지 않은 한 기본적으로 인증서에는 lyncdiscover.&lt;sipdomain&gt; 또는 lyncdiscoverinternal.&lt;내부 도메인 이름&gt; 항목이 포함되지 않습니다. 이 절차에서는 예제 SIP 도메인 이름 'contoso.com' 및 예제 내부 도메인 이름 'contoso.net'을 사용합니다.<BR>Lync Server 2013 및 Lync Server 2010의 기본 인증서 구성은 기본값(웹 서비스를 제외한 모든 용도), WebServicesExternal 및 WebServicesInternal 용도로 단일 인증서('Default')를 사용하는 것입니다. 선택적인 구성은 각 용도에 대해 별도의 인증서를 사용하는 것입니다. 인증서는 Lync Server 관리 셸 및 Windows PowerShell cmdlet을 사용하거나 Lync Server 배포 마법사에서 인증서 마법사를 사용하여 관리할 수 있습니다.



## Lync Server 관리 셸을 사용하여 새 주체 대체 이름으로 인증서를 업데이트하려면

1.  로컬 관리자 권한이 있는 계정을 사용하여 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  서버에 지정된 인증서 및 인증서를 사용할 유형을 확인합니다. 다음 단계에서 업데이트된 인증서를 지정하려면 이 정보가 필요합니다. 정보를 확인하려면 명령줄에 다음을 입력합니다.
    
        Get-CsCertificate

4.  이전 단계의 출력에서 단일 인증서가 여러 용도로 지정되어 있는지 또는 각 용도에 따라 서로 다른 인증서가 지정되어 있는지를 확인합니다. 또한 Use 매개 변수에서 인증서 사용 방법을 확인하고, 표시된 인증서의 Thumbprint 매개 변수를 비교해 같은 인증서가 여러 용도로 사용되는지 확인합니다.

5.  인증서를 업데이트합니다. 명령줄에 다음을 입력합니다.
    
        Set-CsCertificate -Type <type of certificate as displayed in the Use parameter> -Thumbprint <unique identifier>
    
    예를 들어 **Get-CsCertificate** cmdlet을 실행한 결과 용도가 각각 Default, WebServicesInternal, WebServicesExternal인 인증서가 표시되었는데 이들 인증서의 Thumbprint 값은 모두 같은 경우에는 명령줄에 다음을 입력합니다.
    
        Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
    
    **중요:**
    
    각 용도에 따라 별도의 인증서가 지정된 경우, 즉 각 인증서의 Thumbprint 값이 다른 경우에는 여러 유형으로 **Set-CsCertificate** cmdlet을 실행해서는 안 됩니다. 이 경우에는 각 용도에 대해 별도로 **Set-CsCertificate** cmdlet을 실행해야 합니다. 예를 들면 다음과 같습니다.
    
        Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>

6.  인증서를 보려면 **시작**, **실행…**을 차례로 클릭하고 MMC를 입력해서 Microsoft Management Console을 엽니다.

7.  MMC 메뉴에서 **파일**, **프로그램 스냅인 추가/제거…**, 인증서를 차례로 선택합니다. 그런 후에 **추가**를 클릭합니다. 메시지가 표시되면 **컴퓨터 계정**을 선택한 후 **다음**을 클릭합니다.

8.  이 컴퓨터에 인증서가 있으면 **로컬 컴퓨터**를 선택합니다. 인증서가 다른 컴퓨터에 있으면 **다른 컴퓨터**를 선택하고 컴퓨터의 정규화된 도메인 이름을 입력하거나 **선택할 개체 이름을 입력하십시오.**에서 **찾아보기**를 클릭하고 컴퓨터 이름을 입력합니다. 그런 다음 **이름 확인**을 클릭합니다. 컴퓨터 이름이 확인되면 밑줄로 표시됩니다. **확인**을 클릭한 후 **마침**을 클릭합니다. **확인**을 클릭하여 선택을 커밋하고 **스냅인 추가 또는 제거** 대화 상자를 닫습니다.
    

    > [!IMPORTANT]
    > 콘솔에 인증서가 표시되지 않으면 사용자 또는 서비스를 선택하지 않았는지 확인하십시오. 여기서는 컴퓨터를 선택해야 하며, 그렇지 않으면 적절한 인증서를 찾을 수 없습니다.



9.  인증서의 속성을 보려면 **인증서**, **개인**을 차례로 확장하고 **인증서**를 선택합니다. 보려는 인증서를 선택하고 마우스 오른쪽 단추로 클릭한 후 **열기**를 선택합니다.

10. **인증서** 보기에서 **자세히**를 선택합니다. 여기서는 **주체**를 선택하여 인증서 주체 이름을 선택할 수 있으며, 그러면 지정된 주체 이름 및 연결된 속성이 표시됩니다.

11. 지정된 주체 대체 이름을 보려면 **주체 대체 이름**을 선택합니다. 그러면 지정된 모든 주체 대체 이름이 표시됩니다. 속성에서 발견되는 주체 대체 이름은 기본적으로 **DNS 이름** 유형입니다. 다음과 같은 멤버가 표시됩니다(모든 멤버가 DNS 호스트(A 또는 IPv6인 경우 AAAA) 레코드에 표시된 대로 정규화된 도메인 이름으로 표시됨).
    
      - 이 풀의 풀 이름 또는 단일 서버 이름(풀이 아닌 경우)
    
      - 인증서가 지정된 서버 이름
    
      - 단순 URL 레코드(일반적으로 meet 및 dialin)
    
      - 토폴로지 작성기에서 선택한 항목 및 재정의된 웹 서비스 선택 항목에 따른 웹 서비스 내부 및 웹 서비스 외부 이름(예: webpool01.contoso.net, webpool01.contoso.com)
    
      - 이미 지정된 경우 lyncdiscover.\<SIP 도메인\> 및 lyncdiscoverinternal.\<SIP 도메인\> 레코드
    
    lyncdiscover 및 lyncdiscoverinternal SAN 항목이 있는 경우 마지막 항목이 가장 중요한 항목입니다.
    
    이러한 정보를 준비했으면 인증서 보기 및 MMC를 닫을 수 있습니다.

12. 자동 검색 서비스(외부 인증서인지 내부 인증서인지에 따라 lyncdiscover.\>도메인 이름\> 및 lyncdiscoverinternal.\<도메인 이름\>) 주체 대체 이름이 누락되었고 Default, WebServicesInternal 및 WebServiceExternal 형식에 대해 단일 기본 인증서를 사용하는 경우 다음을 수행합니다.
    
      - Lync Server 관리 셸 명령줄 프롬프트에 다음을 입력합니다.
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        SIP 도메인이 여러 개인 경우 새 AllSipDomain 매개 변수는 사용할 수 없습니다. 대신 DomainName 매개 변수를 사용해야 합니다. DomainName 매개 변수를 사용할 때는 lyncdiscoverinternal 및 lyncdiscover 레코드에 대해 FQDN을 정의해야 합니다. 예를 들면 다음과 같습니다.
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - 인증서를 지정하려면 다음을 입력합니다.
        
            Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        여기서 "Thumbprint"는 새로 발급된 인증서에 표시되는 지문입니다.

13. Default, WebServicesInternal 및 WebServicesExternal에 대해 개별 인증서를 사용할 때 내부 자동 검색 주체 대체 이름이 누락된 경우 다음을 수행합니다.
    
      - Lync Server 관리 셸 명령줄 프롬프트에 다음을 입력합니다.
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -AllSipDomain -verbose
        
        SIP 도메인이 여러 개인 경우 새 AllSipDomain 매개 변수는 사용할 수 없습니다. 대신 DomainName 매개 변수를 사용해야 합니다. DomainName 매개 변수를 사용할 때는 SIP 도메인 FQDN에 대해 적절한 접두사를 사용해야 합니다. 예를 들면 다음과 같습니다.
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - 누락된 외부 자동 검색 주체 대체 이름에 대해 명령줄에 다음을 입력합니다.
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        SIP 도메인이 여러 개인 경우 새 AllSipDomain 매개 변수는 사용할 수 없습니다. 대신 DomainName 매개 변수를 사용해야 합니다. DomainName 매개 변수를 사용할 때는 SIP 도메인 FQDN에 대해 적절한 접두사를 사용해야 합니다. 예를 들면 다음과 같습니다.
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -DomainName "Lyncdiscover.contoso.com, Lyncdiscover.contoso.net" -verbose
    
      - 개별 인증서 유형을 지정하려면 다음을 입력합니다.
        
            Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        여기서 "Thumbprint"는 새로 발급된 인증서에 표시되는 지문입니다.

