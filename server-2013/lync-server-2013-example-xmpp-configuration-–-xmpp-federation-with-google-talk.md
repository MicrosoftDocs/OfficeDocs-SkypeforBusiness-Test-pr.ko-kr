---
title: 'Lync Server 2013: 예제 XMPP 구성 - Google Talk와 XMPP 페더레이션'
TOCTitle: 예제 XMPP 구성 - Google Talk와 XMPP 페더레이션
ms:assetid: 360a2f7b-015b-4e93-ac67-0f609c21f1a2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204807(v=OCS.15)
ms:contentKeyID: 49303286
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 예제 XMPP 구성 - Google Talk와 XMPP 페더레이션

 

_**마지막으로 수정된 항목:** 2014-04-22_

XMPP 프록시 배포를 위한 구성의 예에서는 Google Talk와의 페더레이션을 정의합니다.

## 예제 XMPP 구성 - Google Talk와 XMPP 페더레이션

1.  프런트 엔드 서버에서 Lync Server 배포 마법사를 엽니다. **Lync** **Server 시스템 설치 또는 업데이트** 를 클릭한 다음 **Lync** **Server 구성 요소 설치 또는 제거** 를 클릭합니다. **다시 실행** 을 클릭합니다.

2.  **Lync Server 구성 요소 설치** 에서 **다음** 을 클릭합니다. 요약 화면에는 실행되는 작업이 표시됩니다. 배포가 완료되면 **로그 보기** 를 클릭하여 사용 가능한 로그 파일을 확인합니다. 그런 후에 **마침** 을 클릭하여 배포를 완료합니다.

3.  에지 서버에서 Lync Server 배포 마법사를 엽니다. **Lync Server 시스템 설치 또는업데이트**를 클릭한 다음 **Lync Server 구성 요소 설치 또는제거**를 클릭합니다. **다시 실행**을 클릭합니다.

4.  Google Talk를 XMPP 허용 파트너로 추가합니다. 현재 Google Talk는 서버 간 XMPP 페더레이션에 대해서는 암호화되지 않은 TCP 연결만 지원하며 ID 확인에 대해서는 서버 전화 접속 회의만 지원합니다. <http://xmpp.org/extensions/xep-0220.html>을 참조하십시오.
    
        New-CsXmppAllowedPartner gmail.com -TlsNegotiation NotSupported -SaslNegotiation NotSupported -EnableKeepAlive $false -SupportDialbackNegotiation $true

5.  에지 페더레이션을 사용하도록 설정하려면 다음을 입력합니다.
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $true

6.  **Lync Server 구성 요소 설치** 에서 **다음** 을 클릭합니다. 요약 화면에는 실행되는 작업이 표시됩니다. 배포가 완료되면 **로그 보기** 를 클릭하여 사용 가능한 로그 파일을 확인합니다. 그런 후에 **마침** 을 클릭하여 배포를 완료합니다.

7.  에지 서버의 Lync Server 배포 마법사에서 **3단계: 인증서 요청, 설치 또는 할당** 옆의 **다시 실행** 을 클릭합니다.
    

    > [!TIP]  
    > 처음으로 에지 서버를 배포하는 경우 "다시 실행" 대신 "실행"이 나타납니다.



8.  **사용할 수 있는 인증서 작업** 페이지에서 **새 인증서 요청 만들기** 를 클릭합니다.

9.  **인증서 요청** 페이지에서 **외부 에지 인증서** 를 클릭합니다.

10. **지연 또는 즉시 요청** 페이지에서 **지금 요청을 준비하고 나중에 보냅니다** 확인란을 선택합니다.

11. **인증서 요청 파일** 페이지에 요청을 저장할 파일의 전체 경로 및 파일 이름(예: c:\\cert\_exernal\_edge.cer)을 입력합니다.

12. **대체 인증서 템플릿 지정** 페이지에서 기본 WebServer 템플릿이 아닌 다른 템플릿을 사용하려면 **선택한 인증 기관에 대체 인증서 템플릿 사용** 확인란을 선택합니다.

13. **이름 및 보안 설정** 페이지에서 다음을 수행합니다.
    
    1.  **대화명** 에 인증서 표시 이름을 입력합니다.
    
    2.  **비트 길이** 에서 비트 길이(일반적으로 기본값은 **2048** )를 지정합니다.
    
    3.  **인증서의 개인 키를 내보낼 수 있는 것으로 표시** 확인란이 선택되어 있는지 확인합니다.

14. **조직 정보** 페이지에 조직 및 조직 구성 단위의 이름(예: 사업부 또는 부서)을 입력합니다.

15. **지역 정보** 페이지에서 위치 정보를 지정합니다.

16. **주체 이름/주체 대체 이름** 페이지에 마법사에서 자동으로 채울 정보가 표시됩니다. 추가 주체 대체 이름이 필요한 경우 다음 두 단계에서 지정합니다.

17. **주체 대체 이름(SAN)에 대한 SIP 도메인 설정** 페이지에서 주체 대체 이름 목록에 sip. *\<SIP 도메인\>* 항목을 추가하려면 도메인 확인란을 선택합니다.

18. **추가 주체 대체 이름 구성** 페이지에서 필요한 추가 주체 대체 이름을 지정합니다.
    

    > [!TIP]  
    > XMPP 프록시가 설치된 경우 기본적으로 도메인 이름(예: contoso.com)이 SAN 항목에 채워집니다. 더 많은 항목이 필요한 경우 이 단계에서 추가합니다.



19. **요청 요약** 페이지에서 요청을 생성하는 데 사용할 인증서 정보를 검토합니다.

20. 명령 실행이 완료되면 **로그 보기** 를 수행하거나 **다음** 을 클릭하여 계속할 수 있습니다.

21. **인증서 요청 파일** 페이지에서 **보기** 를 클릭하여 생성된 인증서 서명 요청(CSR) 파일을 확인하거나, **마침** 을 클릭하여 인증서 마법사를 종료합니다.

22. 요청 파일을 복사하여 공용 CA(인증 기관)에 제출합니다.

23. 공용 인증서를 받고 가져오고 할당한 후에는 에지 서버 서비스를 중지했다가 다시 시작해야 합니다. Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.. Lync Server 관리 셸에서 다음을 입력합니다.
    
```
        Stop-CsWindowsService
```
```    
        Start-CsWindowsService
```

24. XMPP 페더레이션용으로 DNS를 구성하려면 외부 DNS에 대해 SRV 레코드 \_xmpp-server.\_tcp. *\<도메인 이름\>* 을 추가합니다. SRV 레코드는 에지 서버의 액세스 에지 FQDN(포트 값 5269)으로 확인됩니다.

25. 프런트 엔드 서버에서 Lync Server 관리 셸을 열고 다음을 입력하여 모든 사용자를 활성화하는 새 외부 액세스 정책을 구성합니다.
    
        New-CsExternalAccessPolicy -Identity FedPic -EnableFederationAccess $true -EnablePublicCloudAccess $true
        Get-CsUser | Grant-CsExternalAccessPolicy -PolicyName FedPic

