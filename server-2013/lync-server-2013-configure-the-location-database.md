---
title: Lync Server 2013에서 위치 데이터베이스 구성
TOCTitle: Lync Server 2013에서 위치 데이터베이스 구성
ms:assetid: 8544be31-6958-47ef-b926-fdc80d56191c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398679(v=OCS.15)
ms:contentKeyID: 49304262
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 위치 데이터베이스 구성

 

_**마지막으로 수정된 항목:** 2012-09-17_

클라이언트가 네트워크 내에서 자신의 위치를 자동으로 감지하도록 하려면 먼저 위치 데이터베이스를 구성해야 합니다. 위치 데이터베이스를 구성하지 않은 상태에서 위치 정책의 **위치 필요**가 **예** 또는 **고지 사항**으로 설정되어 있으면 수동으로 위치를 입력하라는 메시지가 표시됩니다.

위치 데이터베이스를 구성하려면 다음 작업을 수행합니다.

1.  데이터베이스를 위치에 대한 네트워크 요소 매핑으로 채웁니다. ELIN(Emergency Location Identification Number) 게이트웨이를 사용할 경우 \<회사 이름\> 필드에 ELIN을 포함해야 합니다.

2.  E9-1-1 서비스 공급자가 유지 관리하는 MSAG(마스터 주소 가이드)에 대해 주소를 확인합니다.

3.  업데이트된 데이터베이스를 게시합니다.


> [!NOTE]
> 또는 위치 데이터베이스 대신 사용할 수 있는 보조 위치 원본 데이터베이스를 정의할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-configure-a-secondary-location-information-service.md">Lync Server 2013에서 보조 위치 정보 서비스 구성</A>을 참조하십시오.



## 이 단원의 내용

  - [위치 데이터베이스 채우기](lync-server-2013-populate-the-location-database.md)

  - [주소 유효성 검사](lync-server-2013-validate-addresses.md)

  - [Lync Server 2013에서 위치 데이터베이스 게시](lync-server-2013-publish-the-location-database.md)

