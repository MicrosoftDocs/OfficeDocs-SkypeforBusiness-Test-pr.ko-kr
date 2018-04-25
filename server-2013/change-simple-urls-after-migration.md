---
title: 마이그레이션 후 단순 URL 변경
TOCTitle: 마이그레이션 후 단순 URL 변경
ms:assetid: addb0dc8-8324-42b1-9a00-f4bd14fdf5c0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721844(v=OCS.15)
ms:contentKeyID: 49885923
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 마이그레이션 후 단순 URL 변경

 

_**마지막으로 수정된 항목:** 2012-09-22_

Lync Server에서는 세 가지 단순 URL을 지원합니다.

  - **모임** 은 사이트 또는 조직의 모든 전화 회의에 대한 기본 URL로 사용됩니다. 모임 단순 URL을 사용하면 모임에 참가할 링크를 쉽게 이해하고 전달하고 배포할 수 있습니다.

  - **전화 접속** 은 전화 접속 회의 설정 웹 페이지에 액세스할 수 있게 합니다. 전화 접속 단순 URL은 모든 모임 초대에 포함되므로 모임에 전화 접속하려는 사용자가 필요한 전화 번호 및 PIN 정보에 액세스할 수 있습니다.

  - **관리** 는 Lync Server 제어판에 빠르게 액세스할 수 있게 해줍니다. 관리 단순 URL은 조직의 내부 URL입니다.

Lync Server 2013으로 마이그레이션한 후에는 단순 URL의 DNS 레코드 및 인증서가 이러한 변경에 따라 받을 수 있는 영향을 알아야 합니다. 레거시 Lync Server 2010 디렉터를 토폴로지에서 계속 사용하는 경우 단순 URL을 변경할 필요가 없습니다. 마이그레이션 후에 Lync Server 2010 디렉터를 토폴로지에서 제거하는 경우 Lync Server 2013 풀 중 하나를 가리키도록 단순 URL DNS 레코드를 업데이트해야 합니다. 그러나 단순 URL 이름을 변경할 때마다 각 디렉터 및 프런트 엔드 서버에서 Enable-CsComputer를 실행하여 변경 내용을 등록해야 합니다.

## 마이그레이션 후 단순 URL 변경

**모임 단순 URL을 업데이트하려면**

1.  토폴로지 작성기에서 최상위 노드인 **Lync Server**를 마우스 오른쪽 단추로 클릭하고 **속성 편집** 을 클릭합니다.

2.  왼쪽 창에서 **단순 URL** 을 선택한 후 **모임 URL:** 아래에서 해당 모임 URL을 선택하고 **URL 편집** 을 클릭합니다.

3.  URL을 원하는 값으로 업데이트하고 **확인** 을 클릭하여 편집한 URL을 저장합니다.

**관리 단순 URL을 업데이트하려면**

1.  토폴로지 작성기에서 최상위 노드인 **Lync Server**를 마우스 오른쪽 단추로 클릭하고 **속성 편집** 을 클릭합니다.

2.  왼쪽 창에서 **단순 URL** 을 선택한 후 **관리 액세스 URL** 상자에 Lync Server 2013 제어판에 대한 관리 액세스에 사용할 단순 URL을 입력하고 **확인** 을 클릭합니다.
    

    > [!TIP]
    > 관리 URL에는 최대한 간단한 URL을 사용하는 것이 좋습니다. 가장 간단한 옵션은 <STRONG>https://admin.</STRONG> <EM>&lt;도메인&gt;</EM> 입니다.



## 참고 항목

#### 개념

[Lync Server 2013의 단순 URL 계획](lync-server-2013-planning-for-simple-urls.md)

