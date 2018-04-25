---
title: Exchange 통합 메시징 연락처 개체 이동
TOCTitle: Exchange 통합 메시징 연락처 개체 이동
ms:assetid: 35c7e987-41b5-4798-b617-3303f20e52e3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688022(v=OCS.15)
ms:contentKeyID: 49885723
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exchange 통합 메시징 연락처 개체 이동

 

_**마지막으로 수정된 항목:** 2012-10-19_

AA(자동 전화 교환) 및 SA(구독자 액세스) 대화 상대 개체를 새 Lync Server 2013 배포로 마이그레이션하려면 먼저 **Get-CsExUmContact** 및 **Move-CsExUmContact** cmdlet을 사용하여 레거시 Office Communications Server 2007 R2 배포에서 새 Lync Server 2013 배포로 개체를 이동합니다. 그런 다음 Exchange Server에서 **ExchUCUtil**Windows PowerShell 스크립트를 실행하여 새로 배포된 Lync 풀에서 다음을 수행합니다.

  - Unified Messaging IP 게이트웨이에 개체 추가

  - Unified Messaging 헌트 그룹에 개체 추가


> [!NOTE]
> <STRONG>Get-CsExUmContact</STRONG> 및 <STRONG>Move-CsExUmContact</STRONG> cmdlet을 사용하려면 RTCUniversalUserAdmins 그룹의 구성원이어야 하며 대화 상대 개체가 저장된 OU에 대한 OU(조직 구성 단위) 권한이 있어야 합니다. OU 권한은 <STRONG>Grant-OUPermission</STRONG> cmdlet을 사용하여 부여할 수 있습니다.



## Lync Server 관리 셸을 사용하여 대화 상대 개체를 이동하려면

1.  Lync Server 관리 셸를 엽니다.

2.  Exchange UM에 등록된 각 풀에 대해(pool1.contoso.net은 Office Communications Server 2007 R2 배포의 풀이고 pool2.contoso.net은 Lync Server 2013 배포의 풀임) 명령줄에 다음을 입력합니다.
    
        Get-CsExUmContact -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsExUmContact -Target pool02.contoso.net
    
    대화 상대 개체가 이동되었는지 확인하려면 **Get-CsExumContact** cmdlet을 실행하고 **RegistrarPool** 이 이제 새 풀을 가리키는지 확인합니다.

## ExchUCUtil Windows PowerShell 스크립트를 실행하려면

1.  Exchange 조직 관리자 권한이 있는 사용자로 Exchange UM 서버에 로그온합니다.

2.  ExchUCUtil Windows PowerShell 스크립트로 이동합니다.
    
    Exchange 2007의 경우 ExchUCUtil.ps1은 **%Program Files%\\Microsoft\\Exchange Server\\Scripts\\ExchUCUtil.ps1** 에 있습니다.
    
    Exchange 2010의 경우 ExchUCUtil.ps1은 **%Program Files%\\Microsoft\\Exchange Server\\V14\\Scripts\\ExchUCUtil.ps1** 에 있습니다.

3.  Exchange가 단일 포리스트에 배포된 경우 다음을 입력합니다.
    
        exchucutil.ps1
    
    또는 Exchange가 여러 포리스트에 배포된 경우 다음을 입력합니다.
    
        exchucutil.ps1 -Forest:" <forest FQDN>"
    
    여기서 *forest FQDN*은 Lync Server 2013가 배포된 포리스트를 나타냅니다.
    

    > [!IMPORTANT]
    > exchucutil.ps1을 실행한 <EM>후</EM><STRONG>Lync Server 프런트 엔드</STRONG> 서비스(rtcsrv.exe)를 다시 시작해야 합니다. 그렇지 않으면 Lync Server 2013가 토폴로지에서 통합 메시징을 검색하지 않습니다.


