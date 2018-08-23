---
title: 'Lync Server 2013: XMPP 페더레이션 설정'
TOCTitle: XMPP 페더레이션 설정
ms:assetid: 5fda6cb7-8d4d-495d-90c7-601f1036e085
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204939(v=OCS.15)
ms:contentKeyID: 49303790
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 XMPP 페더레이션 설정

 

_**마지막으로 수정된 항목:** 2012-12-03_

에지 서버에 XMPP 프록시를 배포하려면 XMPP 페더레이션의 에지 서버를 구성해야 합니다. 이렇게 하려면 다음 단계를 수행합니다.

## XMPP 페더레이션 설정

1.  Lync Server Deployment Wizard가 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원으로 설치되어 있는 컴퓨터에 로그온합니다.

2.  프런트 엔드 서버에서 Lync Server 배포 마법사를 엽니다. Lync Server 시스템 설치 또는 업데이트를 클릭한 후 Lync Server 구성 요소 설치 또는 제거를 클릭합니다. 다시 실행을 클릭합니다.

3.  Lync Server 구성 요소 설치에서 다음을 클릭합니다. 요약 화면에는 실행되는 작업이 표시됩니다. 배포가 완료되면 로그 보기를 클릭하여 사용 가능한 로그 파일을 확인합니다. 그런 후에 마침을 클릭하여 배포를 완료합니다.

4.  에지 서버에서 Lync Server 배포 마법사를 엽니다. Lync Server 시스템 설치 또는 업데이트를 클릭하고, Lync Server 구성 요소 설치 또는 제거를 클릭합니다. 다시 실행을 클릭합니다.

5.  Lync Server 구성 요소 설치에서 다음을 클릭합니다. 요약 화면에는 실행되는 작업이 표시됩니다. 배포가 완료되면 로그 보기를 클릭하여 사용 가능한 로그 파일을 확인합니다. 그런 후에 마침을 클릭하여 배포를 완료합니다.

6.  에지 서버의 배포 마법사에서 3단계: 인증서 요청, 설치 또는 할당 옆에 있는 다시 실행을 클릭합니다.
    

    > [!TIP]  
    > 처음으로 에지 서버를 배포하는 경우 "다시 실행" 대신 "실행"이 나타납니다.



7.  사용할 수 있는 인증서 작업 페이지에서 새 인증서 요청 만들기를 클릭합니다.

8.  인증서 요청 페이지에서 외부 에지 인증서를 클릭합니다.

9.  지연 또는 즉시 요청 페이지에서 지금 요청을 준비하고 나중에 보냅니다 확인란을 선택합니다.

10. 인증서 요청 파일 페이지에 요청을 저장할 파일의 전체 경로 및 파일 이름(예: c:\\cert\_exernal\_edge.cer)을 입력합니다.

11. 대체 인증서 템플릿 지정 페이지에서 기본 WebServer 템플릿이 아닌 다른 템플릿을 사용하려면 선택한 인증 기관에 대체 인증서 템플릿 사용 확인란을 선택합니다.

12. 이름 및 보안 설정 페이지에서 다음을 수행합니다.
    
    1.  대화명에 인증서 표시 이름을 입력합니다.
    
    2.  비트 길이에서 비트 길이(일반적으로 기본값은 2048)를 지정합니다.
    
    3.  인증서의 개인 키를 내보낼 수 있는 것으로 표시 확인란이 선택되어 있는지 확인합니다.

13. 조직 정보 페이지에 조직 및 조직 구성 단위의 이름(예: 사업부 또는 부서)을 입력합니다.

14. 지역 정보 페이지에서 위치 정보를 지정합니다.

15. 주체 이름/주체 대체 이름 페이지에 마법사에서 자동으로 채울 정보가 표시됩니다. 추가 주체 대체 이름이 필요한 경우 다음 두 단계에서 지정합니다.

16. 주체 대체 이름(SAN)에 대한 SIP 도메인 설정 페이지에서 주체 대체 이름 목록에 sip.\<SIP 도메인\> 항목을 추가하려면 도메인 확인란을 선택합니다.

17. 추가 주체 대체 이름 구성 페이지에서 필요한 추가 주체 대체 이름을 지정합니다.
    

    > [!TIP]  
    > XMPP 프록시가 설치된 경우 기본적으로 도메인 이름(예: contoso.com)이 SAN 항목에 채워집니다. 더 많은 항목이 필요한 경우 이 단계에서 추가합니다.



18. 요청 요약 페이지에서 요청을 생성하는 데 사용할 인증서 정보를 검토합니다.

19. 명령 실행을 마치면 로그 보기를 확인하거나 "다음"을 클릭하여 계속 진행합니다.

20. 인증서 요청 파일 페이지에서 보기를 클릭하여 생성된 인증서 서명 요청(CSR) 파일을 확인하거나, 마침을 클릭하여 인증서 마법사를 종료합니다.

21. 요청 파일을 복사하여 공용 CA(인증 기관)에 제출합니다.

22. 공용 인증서를 받아 가져오고 할당한 후 에지 서버 서비스를 중지한 다음 다시 시작해야 합니다. 이는 Lync Server 관리 콘솔에서 다음을 입력해서 수행할 수도 있습니다.
    
```
Stop-CsWindowsService
```
```    
Start-CsWindowsService
```

23. XMPP 프레젠테이션에 대해 DNS를 구성하려면 다음 SRV 레코드를 외부 DNS:\_xmpp-server.\_tcp.\<도메인 이름\>에 추가합니다. SRV 레코드는 포트 5269를 사용해서 에지 서버의 액세스 에지 FQDN으로 확인됩니다. 또한 액세스 에지 서버의 IP 주소를 가리키는 'A' 호스트 레코드(예: xmpp.contoso.com)를 구성합니다.
    

    > [!IMPORTANT]  
    > 여러 사이트에 에지 풀이 있는 경우 XMPP 페더레이션에 대해 여러 SRV 레코드를 추가하는 것이 좋습니다. 조직 내 모든 에지 풀에 대해 SRV 레코드를 추가하고 이러한 각 SRV 레코드에 서로 다른 우선 순위를 지정합니다. 모든 에지 풀이 실행될 때 XMPP 요청은 우선 순위가 가장 높은 에지 풀에서 처리됩니다. 하지만 해당 에지 풀이 다운된 경우 XMPP 페더레이션 기능을 다시 확보하기 위해 새로운 SRV 레코드를 추가할 필요가 없습니다.



24. 프런트 엔드에서 Lync Server 관리 셸을 열고 다음을 입력하여 모든 사용자를 사용하도록 설정하기 위해 새로운 외부 액세스 정책을 구성합니다.
    
```
New-CsExternalAccessPolicy -Identity <name of policy to create.  If site scope, prepend with 'site:'> -EnableFederationAcces $true -EnablePublicCloudAccess $true
```
```    
New-CsExternalAccessPolicy -Identity FedPic -EnableFederationAcces $true -EnablePublicCloudAccess $true
```
```    
Get-CsUser | Grant-CsExternalAccessPolicy -PolicyName FedPic
```

다음을 입력하여 외부 사용자에 대해 XMPP 액세스를 사용하도록 설정합니다.
    
```
Set-CsExternalAccessPolicy -Identity <name of the policy being used> EnableXmppAccess $true
```
```    
Set-CsExternalAccessPolicy -Identity FedPic -EnableXmppAccess $true
```

25. XMPP 프록시가 배포된 에지 서버에서 명령 프롬프트 또는 Windows PowerShell™ 명령줄 인터페이스를 열고 다음을 입력합니다.
    
```
Netstat -ano | findstr 5269
```
```    
Netstat -ano | findstr 23456
```

**netstat -ano** 명령은 네트워크 통계 명령입니다. **-ano** 매개 변수는 netstat으로 모든 연결 및 수신 대기 포트를 표시하고, 주소 및 포트를 숫자 형식으로 표시하고, 소유 프로세스 ID가 각 연결과 연결되도록 요청합니다. **|** 문자는 다음 명령인 **findstr** 또는 find string에 대한 파이프를 정의합니다. findstr에 매개 변수로 전달된 숫자 5269 및 23456은 findstr이 netstat 출력에서 5269 및 23456 문자열을 찾도록 지시합니다. XMPP를 올바르게 구성한 경우 이 명령의 출력에 따라 외부 에지 서버의 외부(포트 5269) 및 내부(포트 23456) 모두에서 수신 대기 중이고 설정된 연결을 가져옵니다.
    
명령이 5269 및 23456에서 설정되었거나 수신 대기 중인 포트를 반환하지 않으면 다음을 확인합니다.

## XMPP 페더레이션 문제 해결

1.  XMPP 프록시가 실행 중인지 확인하려면 다음을 수행합니다.

2.  XMPP 프록시 서비스를 실행 중인 에지 서버에 로컬 관리자 그룹의 구성원으로 로그온합니다.

3.  **시작** 을 클릭하고 **모든 프로그램** , **관리 도구** 를 차례로 클릭한 다음 **서비스** 를 클릭합니다.

4.  서비스에서 Lync Server XMPP Translating Gateway Proxy를 찾습니다. 이 서비스는 **시작됨** 상태여야 합니다. 시작되지 않았으면 도구 모음에서 **시작** 아이콘을 클릭합니다. 아이콘은 녹색 오른쪽 화살표로 표시됩니다.

5.  서비스가 **시작됨** 으로 변경되었는지 확인합니다. 성공적으로 시작되었으면 **서비스** 를 닫고 계속합니다.
    
    서비스가 성공적으로 시작되지 않았으면 관리 도구에서 이벤트 뷰어를 열고 **응용 프로그램 및 서비스 로그** 아래의 **Lync Server** 부분에서 오류 및 경로를 확인합니다.

6.  **Lync Server XMPP Translating Gateway** 서비스가 실행되면 이전에 사용한 netstat 명령을 다시 확인합니다. 설정되었거나 수신 대기 중인 세션이 표시되지 않으면 **XMPP 페더레이션 경로** 가 토폴로지 작성기에 올바르게 구성되었는지 확인합니다.

7.  토폴로지 작성기가 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원으로 설치되어 있는 컴퓨터에 로그온합니다.

8.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.

9.  토폴로지 작성기에서 XMPP 페더레이션 경로에 대한 사이트를 선택하고 검토하여 **XMPP 페더레이션** 에 대한 **사이트 페더레이션 경로 지정** 에 에지 서버 또는 에지 풀이 선택한 XMPP 페더레이션 경로 지정으로 표시되는지 확인합니다.
    
    경로 지정이 잘못되었거나 설정되지 않았으면 사이트를 마우스 오른쪽 단추로 클릭하고 **속성 편집** 을 클릭합니다. XMPP 페더레이션 확인란을 선택한 후 올바른 에지 서버 또는 에지 풀을 선택합니다.

10. 토폴로지를 게시합니다. 자세한 내용은 [Lync Server 2013에서 토폴로지 게시](lync-server-2013-publish-your-topology.md)를 참조하십시오.
    

    > [!TIP]  
    > 필수는 아니고 일반적으로 필요하지 않지만 에지 서버를 다시 시작해야 할 수 있습니다.



11. 이전에 사용된 netstat 프로세스를 사용해서 에지 서버가 포트 5269 및 포트 23456에서 이제 수신 대기 중인지 또는 설정된 세션을 포함하는지 확인합니다.

12. 여전히 예상한 세션이 표시되지 않으면 이벤트 뷰어에서 통신 관련 문제가 있는지 확인합니다.

## 참고 항목

#### 작업

[Lync Server 2013의 예제 XMPP 구성 - Google Talk와 XMPP 페더레이션](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### 기타 리소스

[Lync Server 2013에서 XMPP 페더레이션 파트너 관리](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)

