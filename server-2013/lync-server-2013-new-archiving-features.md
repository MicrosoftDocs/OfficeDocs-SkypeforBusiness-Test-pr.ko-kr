---
title: 'Lync Server 2013: 새로운 보관 기능'
TOCTitle: 새로운 보관 기능
ms:assetid: c002e367-41ad-498d-9d23-8b117ac435b2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205225(v=OCS.15)
ms:contentKeyID: 49304905
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 새로운 보관 기능

 

_**마지막으로 수정된 항목:** 2012-10-09_

Lync Server 2013의 보관은 다음과 같은 콘텐츠 유형을 아카이빙할 수 있습니다.

  - 피어 투 피어 메신저

  - 단체 인스턴트 메시지인 회의(모임)

  - 업로드된 콘텐츠(예: 참고 파일) 및 이벤트 관련 콘텐츠(예: 입장, 퇴장, 업로드 공유 및 표시 여부 변경)를 비롯한 회의 콘텐츠

또한 Lync Server 2013의 보관은 배포 및 운영 효율성을 개선하는 새로운 기능을 제공합니다. 이러한 새 기능은 다음과 같습니다.

  - **프런트 엔드 서버에 보관 배치.**    Lync Server 2013에는 별도의 보관 서버 역할이 없습니다. 보관은 Enterprise Edition 배포의 모든 프런트 엔드 서버와 풀 또는 사이트에 대해 구성하여 구현될 수 있는 Standard Edition Server에서 사용할 수 있는 선택적 기능입니다.

  - **Microsoft Exchange 통합.**   보관을 배포할 때 보관에 대한 데이터 저장소를 Exchange 2013에 속해 있고 사서함을 원본 위치 유지로 설정한 모든 사용자를 위한 기존 Exchange 2013 저장소와 통합할 수 있습니다. 따라서 Lync 데이터를 보관하기 위한 별도의 SQL Server 데이터베이스를 배포할 필요가 없습니다. Exchange 2013 배포가 없거나, 통합을 원하지 않거나, 사서함을 원본 위치 유지로 설정하고 Exchange 2013에 속해 있지 않은 Lync 2013 사용자가 있는 경우 SQL Server를 사용하여 별도의 보관 데이터베이스를 배포하고 Lync 통신의 보관된 데이터를 저장할 수 있습니다. 배포의 일부 사용자만을 위해 Microsoft Exchange 통합을 사용하려는 경우 Microsoft Exchange 통합과 Lync Server 2013 보관 데이터베이스를 둘 다 사용할 수 있습니다. 원본 위치 유지에 대한 자세한 내용은 “원본 위치 유지”( [http://go.microsoft.com/fwlink/?linkid=267500\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=267500%26clcid=0x412))를 참조하십시오.

  - **SQL 저장소 미러링.**   보관을 배포할 때 보관 데이터베이스에 SQL Server 데이터베이스 미러링을 사용하도록 설정할 수 있습니다.

  - **화이트보드 및 설문 조사 보관.**   이제 모임 중 공유되는 화이트보드 및 설문 조사가 보관되는 회의 콘텐츠에 포함됩니다.

보관되지 않는 콘텐츠 형식은 다음과 같습니다.

  - 피어 투 피어 파일 전송

  - 피어 투 피어 인스턴스 메시지 및 회의에 대한 오디오/비디오

  - 피어 투 피어 인스턴스 메시지 및 회의에 대한 응용 프로그램 공유

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 보관 계획](lync-server-2013-planning-for-archiving.md)

