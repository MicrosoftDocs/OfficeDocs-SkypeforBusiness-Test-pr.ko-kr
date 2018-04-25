---
title: 'Lync Server 2013: 단순 URL 편집 또는 구성'
TOCTitle: 단순 URL 편집 또는 구성
ms:assetid: 0008aeea-4ae9-4e36-83cd-ef7ff7b6e128
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398063(v=OCS.15)
ms:contentKeyID: 49302600
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 단순 URL 편집 또는 구성

 

_**마지막으로 수정된 항목:** 2014-02-04_

이 절차는 로컬 관리자 구성원 자격 또는 권한이 있는 도메인 그룹 구성원 자격이 없어도 수행할 수 있습니다. 즉, 컴퓨터에 표준 사용자로 로그온하면 됩니다.

Lync Server 2013에서는 단순 URL을 사용하여 프런트 엔드 서버 또는 디렉터(배포된 경우)에서 내부 및 외부 통화를 서비스로 전달합니다. 단순 URL에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 단순 URL 계획](lync-server-2013-planning-for-simple-urls.md)를 참고하세요. 단순 URL의 형식을 여러 옵션 중에서 선택할 수 있습니다. 이러한 옵션에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 단순 URL에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-simple-urls.md)를 참고하세요.

기본적으로 단순 URL은 https://dialin.\<SIP 도메인\>(전화 접속 단순 URL의 경우) 형식으로 구성됩니다.

## 단순 URL을 구성하려면

1.  토폴로지 작성기에서 **Lync Server** 노드를 마우스 오른쪽 단추로 클릭하고 **속성 편집**을 클릭합니다.

2.  **단순 URL** 창에서 편집할 **전화 액세스 URL:** (전화 접속) 또는 **모임 URL:** (모임)을 선택한 다음 **URL 편집** 을 클릭합니다.

3.  URL을 원하는 값으로 업데이트하고 **확인** 을 클릭하여 편집한 URL을 저장합니다. 여기에 나와 있는 예제에서는 전화 접속 URL을 https://pool01.contoso.net/dialin으로 수정했습니다.

4.  필요한 경우 같은 단계를 수행하여 모임 URL을 편집합니다.

## 관리 단순 URL(선택 사항)을 정의하려면

1.  토폴로지 작성기에서 **Lync Server** 노드를 마우스 오른쪽 단추로 클릭하고 **속성 편집**을 클릭합니다.

2.  **관리 액세스 URL** 상자에 Lync Server 2013 제어판에 대한 관리 권한을 부여할 단순 URL을 입력하고 **확인** 을 클릭합니다.
    

    > [!TIP]
    > 관리 URL에는 최대한 간단한 URL을 사용하는 것이 좋습니다. 가장 간단한 옵션은 <STRONG>https://admin.</STRONG> <EM>&lt;도메인&gt;</EM> 입니다.

    

    > [!IMPORTANT]
    > 초기 배포 후에 단순 URL을 변경하는 경우에는 변경 내용이 단순 URL의 DNS(Domain Name System) 레코드 및 인증서에 주는 영향을 파악해야 합니다. 변경 내용이 단순 URL의 기준에 영향을 주는 경우에는 DNS 레코드 및 인증서도 변경해야 합니다. 예를 들어 https://lync.contoso.com/Meet에서 https://meet.contoso.com으로 변경하는 경우 기준 URL이 lync.contoso.com에서 meet.contoso.com으로 변경되므로, DNS 레코드와 인증서가 meet.contoso.com을 참조하도록 변경해야 합니다. 단순 URL을 https://lync.contoso.com/Meet에서 https://lync.contoso.com/Meetings로 변경하는 경우에는 기준 URL인 lync.contoso.com이 동일하게 유지되므로 DNS 또는 인증서를 변경하지 않아도 됩니다. 그러나 단순 URL 이름을 변경할 때마다 각 디렉터 및 프런트 엔드 서버에서 <STRONG>Enable-CsComputer</STRONG> cmdlet을 실행하여 변경 내용을 등록해야 합니다.



## 참고 항목

#### 개념

[Lync Server 2013의 단순 URL 계획](lync-server-2013-planning-for-simple-urls.md)

