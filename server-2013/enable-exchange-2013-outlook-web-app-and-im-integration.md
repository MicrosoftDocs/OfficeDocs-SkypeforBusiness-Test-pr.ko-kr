---
title: Exchange 2013 Outlook Web App 및 메신저 통합 사용
TOCTitle: Exchange 2013 Outlook Web App 및 메신저 통합 사용
ms:assetid: 44d08cf0-b17d-46e1-a4f0-fcc2fe96a958
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204857(v=OCS.15)
ms:contentKeyID: 49303481
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exchange 2013 Outlook Web App 및 메신저 통합 사용

 

_**마지막으로 수정된 항목:** 2012-10-19_

Lync Server 2013에 대한 Exchange 2013 OWA(Outlook Web Access) 및 IM(인스턴트 메시징) 통합을 설정하려면 Exchange 2013 CAS(Client Access Server) 서버를 Lync Server 2013에 신뢰할 수 있는 응용 프로그램 서버로 추가해야 합니다.

## 트러스트된 응용 프로그램 풀을 만들려면

1.  Lync Server 2013 관리 셸를 시작합니다.

2.  다음 cmdlet을 실행합니다.
    
        Get-CsSite
    
    그러면 풀을 만들려는 siteName의 siteID가 반환됩니다. 자세한 내용은 Lync Server 2013 관리 셸 설명서에서 [Get-CsSite](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsSite)를 참조하십시오.

3.  다음 cmdlet을 실행합니다.
    
        New-CsTrustedApplicationPool -Identity <E14 CAS FQDN> -ThrottleAsServer $true -TreatAsAuthenticated $true -ComputerFQDN <E14 CAS FQDN> -Site <Site> -Registrar <Pool FQDN in the site> -RequiresReplication $false
    
    자세한 내용은 Lync Server 2013 관리 셸 설명서에서 [New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)를 참조하십시오.
    
    Exchange Server FQDN은 Exchange OWA 인증서 SN(주체 이름) 또는 SAN(주체 대체 이름)으로 구성되어야 합니다.
    
    Exchange OWA에서 풀의 FQDN도 신뢰할 수 있는지 확인합니다.
    

    > [!IMPORTANT]
    > CAS 서버가 Exchange 2013 UM(통합 메시징)을 실행하는 서버와 동일한 서버에 함께 배치되지 <EM>않은</EM> 경우 이 절차의 남은 단계를 건너뛰고 이 항목의 뒷 부분에 있는 " Exchange 2013 CAS 서버에 대한 신뢰할 수 있는 응용 프로그램 만들기" 절차를 수행합니다. CAS 서버가 Exchange 2013 UM(통합 메시징)을 실행하는 서버와 동일한 서버에 함께 배치된 경우 이 절차의 단계를 완료하고 이 항목의 뒷 부분에 있는 " Exchange 2013 CAS 서버에 대한 신뢰할 수 있는 응용 프로그램 만들기" 절차를 수행하지 않습니다.



4.  **Enable-CsTopology** 를 실행합니다.

5.  토폴로지 작성기를 열고 기존 토폴로지를 다운로드합니다.

6.  왼쪽 창에서 **트러스트된 응용 프로그램 서버** 가 표시될 때까지 트리를 확장합니다.

7.  **신뢰할 수 있는 응용 프로그램 서버** 노드를 확장합니다.

8.  이제 Exchange 2013 CAS 서버가 신뢰할 수 있는 응용 프로그램 서버로 나열됩니다.

## Exchange 2013 CAS 서버에 대한 신뢰할 수 있는 응용 프로그램을 만들려면

1.  Lync Server 2013 관리 셸를 시작합니다.

2.  CAS 서버가 Exchange 2013 UM(통합 메시징)을 실행하는 서버와 동일한 서버에 함께 배치되지 *않은* 경우 다음 cmdlet을 실행합니다.
    
        New-CsTrustedApplication -ApplicationId <AppID String> -TrustedApplicationPoolFqdn <E14 CAS FQDN> -Port <available port number>
    
    자세한 내용은 Lync Server 2013 관리 셸 설명서의 [New-CsTrustedApplication](new-cstrustedapplication.md) 항목을 참조하십시오.

3.  **Enable-CsTopology** 를 실행합니다.

4.  토폴로지 작성기의 왼쪽 창에서 **신뢰할 수 있는 응용 프로그램 서버** 가 표시될 때까지 트리를 확장합니다.

5.  **신뢰할 수 있는 응용 프로그램 서버** 노드를 확장합니다.

6.  이제 Exchange 2013 CAS 서버가 신뢰할 수 있는 응용 프로그램 서버로 나열됩니다.

