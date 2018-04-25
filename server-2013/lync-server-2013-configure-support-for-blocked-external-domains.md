---
title: 'Lync Server 2013: 차단된 외부 도메인 지원 구성'
TOCTitle: 차단된 외부 도메인 지원 구성
ms:assetid: 49103138-e1ab-42bf-91aa-57cf23bbf260
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619176(v=OCS.15)
ms:contentKeyID: 49303526
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 차단된 외부 도메인 지원 구성

 

_**마지막으로 수정된 항목:** 2012-09-08_

페더레이션 파트너에 대한 지원을 구성한 경우 조직과 페더레이션할 수 없도록 차단되는 도메인을 관리할 수 있습니다. 차단된 도메인 목록은 차단 목록(허용되지 않는 항목에 대한 목록)으로 작동하며 이 옵션을 설정한 경우 페더레이션 도메인 검색에 적용됩니다. 자세한 내용은 [Lync Server 2013에서 페더레이션 파트너 검색을 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md)을 참조하십시오.

하나 이상의 외부 도메인에서 조직에 연결하는 것을 차단합니다. 이렇게 하려면 차단된 도메인 목록에 도메인을 추가합니다.

## 차단된 도메인 목록에 외부 도메인을 추가하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **외부 사용자 액세스** 를 클릭합니다.

4.  **페더레이션 도메인** 에서 **새로 만들기** 를 클릭한 다음 **차단된 도메인** 을 클릭합니다.

5.  **새 페더레이션 도메인** 에서 다음을 수행합니다.
    
      - **도메인 이름 또는 FQDN** 에 차단할 페더레이션 파트너 도메인의 이름을 입력합니다.
        

        > [!NOTE]
        > 이름은 256자까지 지정할 수 있습니다.<BR>페더레이션 파트너 도메인 이름 검색에서는 일치하는 접미사를 찾습니다. 예를 들어 <STRONG>contoso.com</STRONG> 을 입력하면 <STRONG>it.contoso.com</STRONG> 도메인도 검색 결과에 반환됩니다.<BR>페더레이션 파트너 도메인은 동시에 차단하고 허용할 수 없습니다. Lync Server 2013에서는 차단과 허용이 동시에 적용되는 것을 허용하지 않으므로 목록을 동기화할 필요가 없습니다.

    
      - (선택 사항) **설명** 에 다른 시스템 관리자와 이 구성에 대해 공유할 정보를 입력합니다.

6.  **커밋** 을 클릭합니다.

7.  차단할 각 페더레이션 파트너에 대해 4-6단계를 반복합니다.

페더레이션 사용자 액세스를 허용하려면 조직에서 페더레이션 사용자 액세스를 지원하도록 설정해야 합니다. 자세한 내용은 [Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-remote-user-access.md)을 참조하십시오.

또한 페더레이션 사용자와 공동 작업을 수행할 수 있도록 하려는 사용자에 대한 정책을 구성하고 적용해야 합니다. 자세한 내용은 [Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성](lync-server-2013-configure-policies-to-control-federated-user-access.md)을 참조하십시오.

