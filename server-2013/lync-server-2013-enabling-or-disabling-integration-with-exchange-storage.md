---
title: Exchange Storage와 통합 사용 또는 사용 안 함
TOCTitle: Exchange Storage와 통합 사용 또는 사용 안 함
ms:assetid: c08b9ba5-04f6-452a-b44c-c130f1564a34
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205228(v=OCS.15)
ms:contentKeyID: 49304920
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exchange Storage와 통합 사용 또는 사용 안 함

 

_**마지막으로 수정된 항목:** 2012-10-09_

Lync Server 2013 제어판에서는 보관 구성을 사용하여 Exchange 저장소와의 통합을 사용하거나 사용하지 않도록 설정합니다. 여기에는 다음과 같은 보관 구성이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 전역 구성

  - 특정 사이트 또는 풀에 대해 보관이 구현되는 방식을 지정하도록 만들어서 사용하는 선택적인 사이트 수준 및 풀 수준 구성

지정할 수 있는 옵션과 보관 구성의 계층 구조를 비롯하여 보관 구성이 구현되는 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.

## Microsoft Exchange 저장소와의 통합을 사용하거나 사용하지 않도록 설정하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 구성**을 클릭합니다.

4.  보관 구성 목록에서 적합한 전역, 사이트 또는 풀 구성 이름을 클릭하고 **편집**, **자세한 정보 표시**를 차례로 클릭한 후 다음을 수행합니다.
    
      - Exchange 2013 저장소와 통합을 사용하도록 설정하려면 **Microsoft Exchange 통합** 확인란을 선택합니다.
    
      - Exchange 2013 저장소와 통합을 사용하지 않도록 설정하려면 **Microsoft Exchange 통합** 확인란의 선택을 취소합니다.

5.  **커밋**을 클릭합니다.

## 참고 항목

#### 개념

[Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)  

#### 기타 리소스

[Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

