---
title: 'Lync Server 2013: 통합 메시징 기능'
TOCTitle: 통합 메시징 및 Lync Server의 기능
ms:assetid: 094f549d-fccc-43ab-9f39-6ddd18130915
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398144(v=OCS.15)
ms:contentKeyID: 49302737
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 통합 메시징 및 Lync Server 2013의 기능

 

_**마지막으로 수정된 항목:** 2012-10-01_

Lync Server 2013, Enterprise Voice는 Exchange 통합 메시징(UM) 인프라를 사용하여 전화 응답, 전화 알림, 음성 액세스(음성 메일 포함) 및 자동 전화 응답 서비스를 제공합니다.

## 전화 응답

전화 응답은 전화를 받지 않거나 통화 중인 사용자를 대신하여 음성 메시지를 받는 것입니다. 또한 개인 인사말을 재생하고, 메시지를 녹음하며, 사용자의 사서함에 배달되어 Exchange 사서함 서버에 저장될 때까지 대기하도록 해당 메시지를 전송합니다.

발신자가 남긴 메시지는 사용자의 받은 편지함으로 라우팅됩니다. 발신자가 메시지를 남기지 않으면 부재 중 전화 알림이 사용자의 사서함에 저장됩니다. 그러면 사용자는 Microsoft Outlook 메시징 및 공동 작업 클라이언트, Outlook Web Access, Exchange ActiveSync 기술 또는 Outlook Voice Access를 사용하여 받은 편지함에 액세스할 수 있습니다. 통화의 제목과 우선 순위는 전자 메일과 유사한 방식으로 표시할 수 있습니다.

## Outlook Voice Access

Outlook Voice Access를 사용하면 Enterprise Voice 사용자가 음성 메일에 액세스할 수 있을 뿐 아니라 전화 통신 인터페이스의 전자 메일, 일정 및 연락처를 포함하는 Exchange 받은 편지함에도 액세스할 수 있습니다. Exchange UM 관리자가 구독자 액세스 번호를 지정합니다.

## 자동 전화 교환

자동 전화 교환은 외부 사용자가 회사 담당자와 연결하기 위해 걸 수 있는 전화 번호를 구성하는 데 사용할 수 있는 Exchange UM 기능입니다. 특히 이 기능은 외부 발신자가 메뉴 시스템을 탐색하는 데 도움이 되는 일련의 음성 안내 메시지를 제공합니다. 사용 가능한 옵션 목록은 Exchange UM 관리자가 Exchange UM 서버에 구성합니다.

## 팩스 서비스

Exchange UM에는 Exchange 사서함에서 팩스를 받아 볼 수 있는 팩스 기능이 포함됩니다. 자세한 내용은 Microsoft Exchange Server 설명서에서 "통합 메시징"( [http://go.microsoft.com/fwlink/?linkid=135652\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=135652%26clcid=0x412))을 참조하십시오.


> [!NOTE]
> Microsoft Exchange Server 2010, Exchange 2010(최신 서비스 팩 포함) 또는 Exchange 2013과 통합되는 Lync Server 배포에서는 Exchange UM 서버에서 제공하는 팩스 서비스를 사용할 수 없습니다.


