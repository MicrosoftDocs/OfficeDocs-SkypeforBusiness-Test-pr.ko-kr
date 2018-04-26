---
title: 'Lync Server 2013: 모바일 기능용으로 인증서 수정'
TOCTitle: 모바일 기능용으로 인증서 수정
ms:assetid: 4e9107af-20f4-4c2a-8c98-ca35b39a4e2d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690015(v=OCS.15)
ms:contentKeyID: 49303587
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 모바일 기능용으로 인증서 수정

 

_**마지막으로 수정된 항목:** 2014-06-20_

Lync 환경과 모바일 클라이언트 간에 보안 연결을 지원하려면 디렉터 풀, 프런트 엔드 풀, 역방향 프록시에 대한 SSL(Secure Socket Layer) 인증서가 몇 가지 추가 SAN(주체 대체 이름) 항목과 함께 업데이트되어야 합니다. 모바일 관련 인증서 요구 사항에 대한 자세한 내용을 확인하려면 [Lync Server 2013의 모바일 기능에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-mobility.md)의 인증서 요구 사항 섹션을 참고해도 되지만, 기본적으로 인증 기관에서 추가 SAN 항목이 포함된 새 인증서를 받은 다음 이 문서의 단계를 따라 해당 인증서를 추가해야 합니다.

물론 시작하기 전에 인증서에 이미 있는 주체 대체 이름이 무엇인지 알아 두는 것이 좋습니다. 무엇이 구성되었는지 확실하지 않은 경우 여러 가지 방법으로 찾을 수 있습니다. **Get-CsCertificate** 및 기타 PowerShell 명령을 실행하여 이러한 정보를 보는 옵션이 있지만(아래에 방법이 설명되어 있음), 기본적으로 데이터가 잘리기 때문에 필요한 모든 속성을 보지 못할 수도 있습니다. 인증서 및 모든 속성을 제대로 살펴보려면 MMC(Microsoft Management Console)로 이동하여 인증서 스냅인을 로드하거나(아래에 방법이 설명되어 있음) Lync Server 배포 마법사를 확인하면 됩니다.

위에서 설명한 것과 같이 다음 단계에서는 Lync Server 관리 셸 및 MMC를 사용하여 인증서를 업데이트하는 방법을 설명합니다. 이렇게 하는 대신 Lync Server 배포 마법사에서 인증서 마법사를 사용하고 싶다면, 구성한(구성하지 않았을 수도 있음) 디렉터 또는 디렉터 풀에서 [Lync Server 2013에서 디렉터에 대한 인증서 구성](lync-server-2013-configure-certificates-for-the-director.md)을 확인해 보세요. 프런트 엔드 서버 또는 프런트 엔드 풀의 경우 [Lync Server 2013에서 서버에 대한 인증서 구성](lync-server-2013-configure-certificates-for-servers.md)을 확인해 보세요.

한가지 더 유의해야 할 점은 Lync Server 2013 환경에 단일 기본 인증서가 있거나 Default(웹 서비스를 제외한 모든 항목), WebServicesExternal, WebServicesInternal에 대한 별도의 인증서가 있을 수 있다는 것입니다. 어떻게 구성되었든, 다음 단계가 도움이 될 것입니다.

## Lync Server 관리 셸을 사용하여 새 주체 대체 이름으로 인증서를 업데이트하려면

1.  로컬 관리자 권한이 있는 계정을 사용하여 Lync Server 2013 서버에 로그온해야 합니다. 또한, 12단계 및 다음 단계에서 PowerShell **Request-CsCertificate**을 실행하는 경우 이 계정에 특정 CA(인증 기관)에 대한 권한이 있어야 합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  업데이트된 인증서를 할당하기 전에 서버에 어떤 인증서가 할당되었는지, 사용 유형은 무엇인지 알아야 합니다. 명령줄에 다음을 입력합니다.
    
        Get-CsCertificate

4.  이전 단계의 결과를 검토하여 여러 사용자에게 단일 인증서가 할당되었는지 또는 용도별로 다른 인증서가 할당되었는지 확인합니다. Use 매개 변수를 통해 인증서가 어떻게 사용되는지 확인합니다. 표시된 인증서의 Thumbprint 매개 변수를 비교하여 동일한 인증서에 여러 용도가 있는지 확인합니다. 항상 Thumbprint 매개 변수를 유의해야 합니다.

5.  인증서를 업데이트합니다. 명령줄에 다음을 입력합니다.
    
        Set-CsCertificate -Type <type of certificate as displayed in the Use parameter> -Thumbprint <unique identifier>
    
    예를 들어 **Get-CsCertificate** cmdlet을 실행한 결과 용도가 각각 Default, WebServicesInternal, WebServicesExternal인 인증서가 표시되었으며 이들 인증서의 Thumbprint 값이 모두 같은 경우에는 명령줄에 다음을 입력합니다.
    
        Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
    
    **중요:**
    
    용도별로 개별 인증서가 할당되어 있는 경우(위에서 확인한 Thumbprint 값은 인증서마다 다름), 위 예제에서처럼 여러 유형에 **Set-CsCertificate** cmdlet을 실행하지 **않는** 것이 중요합니다. 이 경우 다음과 같이 용도별로 **Set-CsCertificate** cmdlet을 별도로 실행합니다.
    
        Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>

6.  인증서를 보려면 **시작**을 클릭하고 **실행…**을 클릭합니다. MMC를 입력하여 Microsoft Management Console을 엽니다.

7.  MMC 메뉴에서 **파일** , **프로그램 스냅인 추가/제거…** , 인증서를 차례로 선택합니다. 그런 후에 **추가** 를 클릭합니다. 메시지가 표시되면 **컴퓨터 계정** 을 선택한 후 **다음** 을 클릭합니다.

8.  이 서버가 인증서가 위치한 서버인 경우 **로컬 컴퓨터**를 선택합니다. 인증서가 다른 컴퓨터에 있으면 **다른 컴퓨터**를 선택한 다음 컴퓨터의 정규화된 도메인 이름을 입력하거나 **선택할 개체 이름 입력**에서 **찾아보기**를 클릭하고 컴퓨터 이름을 입력합니다. **이름 확인**을 클릭합니다. 컴퓨터 이름이 확인되면 밑줄로 표시됩니다. **확인**을 클릭한 후 **마침**을 클릭합니다. **확인**을 클릭하여 선택을 확정하고 **스냅인 추가/제거** 대화 상자를 닫습니다.

9.  인증서의 속성을 보려면 **인증서** , **개인** 을 차례로 확장하고 **인증서** 를 선택합니다. 보려는 인증서를 선택하고 마우스 오른쪽 단추로 클릭한 후 **열기** 를 선택합니다.

10. **인증서** 보기에서 **자세히** 를 선택합니다. 여기서는 **주체** 를 선택하여 인증서 주체 이름을 선택할 수 있으며, 그러면 지정된 주체 이름 및 연결된 속성이 표시됩니다.

11. 지정된 주체 대체 이름을 보려면 **주체 대체 이름**을 선택합니다. 그러면 지정된 모든 주체 대체 이름이 여기에 표시됩니다. 여기에서 발견되는 주체 대체 이름은 기본적으로 **DNS 이름** 유형입니다. 다음과 같은 구성원이 표시됩니다(모든 구성원이 DNS 호스트(A 또는 IPv6인 경우 AAAA) 레코드에 표시된 대로 정규화된 도메인 이름으로 표시됨).
    
      - 이 풀의 풀 이름 또는 단일 서버 이름(풀이 아닌 경우)
    
      - 인증서가 지정된 서버 이름
    
      - 단순 URL 레코드(일반적으로 meet 및 dialin)
    
      - 토폴로지 작성기에서 선택한 항목 및 재정의된 웹 서비스 선택 항목에 따른 웹 서비스 내부 및 웹 서비스 외부 이름(예: webpool01.contoso.net, webpool01.contoso.com)
    
      - 이미 지정된 경우 lyncdiscover.\<SIP 도메인\> 및 lyncdiscoverinternal.\<SIP 도메인\> 레코드
    
    lyncdiscover 및 lyncdiscoverinternal SAN 항목이 있는 경우 마지막 항목이 가장 중요한 항목입니다.
    
    확인할 인증서가 여러 개인 경우 이 단계를 반복합니다. 정보가 준비되면 인증서 보기 및 MMC를 닫을 수 있습니다.

12. 자동 검색 서비스 주체 대체 이름이 누락되었고 기본, WebServicesInternal 및 WebServiceExternal 형식에 대해 단일 기본 인증서를 사용하는 경우 다음을 수행합니다.
    
      - Lync Server 관리 셸 명령줄 프롬프트에 다음을 입력합니다.
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        SIP 도메인이 여러 개인 경우 새 AllSipDomain 매개 변수는 사용할 수 없습니다. 대신 DomainName 매개 변수를 사용해야 합니다. DomainName 매개 변수를 사용할 때는 lyncdiscoverinternal 및 lyncdiscover 레코드에 대해 FQDN을 정의해야 합니다. 예를 들면 다음과 같습니다.
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - 인증서를 지정하려면 다음을 입력합니다.
        
            Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        여기서 "Thumbprint"는 새로 발급된 인증서에 표시되는 지문입니다.

13. Default, WebServicesInternal, WebServicesExternal에 대해 개별 인증서를 사용할 때 내부 자동 검색 SAN이 누락된 경우 다음을 수행합니다.
    
      - Lync Server 관리 셸 명령줄 프롬프트에 다음을 입력합니다.
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -AllSipDomain -verbose
        
        SIP 도메인이 여러 개인 경우 새 AllSipDomain 매개 변수는 사용할 수 없습니다. 대신 DomainName 매개 변수를 사용해야 합니다. DomainName 매개 변수를 사용할 때는 SIP 도메인 FQDN에 적절한 접두사를 사용해야 합니다. 예를 들면 다음과 같습니다.
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - 누락된 외부 자동 검색 주체 대체 이름에 대해 명령줄에 다음을 입력합니다.
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        SIP 도메인이 여러 개인 경우 새 AllSipDomain 매개 변수는 사용할 수 없습니다. 대신 DomainName 매개 변수를 사용해야 합니다. DomainName 매개 변수를 사용할 때는 SIP 도메인 FQDN에 적절한 접두사를 사용해야 합니다. 예를 들면 다음과 같습니다.
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -DomainName "Lyncdiscover.contoso.com, Lyncdiscover.contoso.net" -verbose
    
      - 개별 인증서 유형을 지정하려면 다음을 입력합니다.
        
            Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        여기서 "Thumbprint"는 새로 발급된 인증서에 표시되는 지문입니다.
    

    > [!NOTE]
    > 12 및 13단계는 해당 단계를 실행하는 계정이 적절한 권한으로 인증 기관에 액세스할 수 있는 경우에만 수행해야 합니다. 이러한 권한이 있는 계정으로 로그인할 수 없거나 인증서에 공용 또는 원격 인증 기관을 사용 중인 경우, 문서 위에서 설명한 Lync Server 배포 마법사를 통해 요청해야 합니다.


