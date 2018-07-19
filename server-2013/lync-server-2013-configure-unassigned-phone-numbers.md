---
title: 할당되지 않은 전화 번호 구성
TOCTitle: 할당되지 않은 전화 번호 구성
ms:assetid: a0650659-dce7-455f-8977-02454bbfa400
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182559(v=OCS.15)
ms:contentKeyID: 49304562
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 할당되지 않은 전화 번호 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server에서는 조직에 대해 유효하지만 할당된 사용자나 전화가 없는 전화 번호로 걸려오는 전화를 처리하는 방법을 구성할 수 있습니다. 이러한 전화에 대한 처리를 구성하려면 할당되지 않은 번호 테이블을 설정합니다. 이 테이블을 사용하여 해당 전화를 알림 응용 프로그램 또는 Exchange UM 서버로 라우팅할 수 있습니다.

할당되지 않은 번호 테이블을 구성하는 방법은 테이블 사용 방법에 따라 다릅니다. 조직에 대해 유효한 모든 내선 번호로 또는 할당되지 않은 내선 번호만으로 또는 두 번호 유형의 결합으로 테이블을 구성할 수 있습니다. 할당되지 않은 번호 테이블은 할당된 번호와 할당되지 않은 번호를 모두 포함할 수 있지만 발신자가 현재 할당되지 않은 번호로 전화를 걸 때만 호출됩니다. 할당되지 않은 번호 테이블에 유효한 내선 번호를 모두 포함하면 테이블을 재구성하지 않고도 다른 사용자가 조직을 떠날 때마다 발생하는 동작을 지정할 수 있습니다. 테이블에 할당되지 않은 내선 번호를 포함하면 특정 번호에 대해 발생하는 동작을 조정할 수 있습니다. 예를 들어 고객 서비스 센터의 내선 번호를 변경하려면 테이블에 기존의 고객 서비스 센터 번호를 포함하고 새 번호를 제공하는 알림에 이 번호를 할당하면 됩니다.


> [!IMPORTANT]
> 할당되지 않은 번호 테이블을 구성하려면 하나 이상의 알림을 정의하거나 Exchange UM 자동 전화 교환을 설정해야 합니다. 알림을 만드는 방법에 대한 자세한 내용은 <A href="lync-server-2013-create-an-announcement.md">Lync Server 2013에서 알림 만들기</A>를 참조하십시오. Exchange UM 설정이 구성되었는지 확인하려면 <STRONG>Get-CsExUmContact</STRONG> cmdlet을 실행합니다. 자세한 내용은 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExUmContact">Get-CsExUmContact</A>를 참조하십시오.



## 이 단원의 내용

  - [Lync Server 2013에서 할당되지 않은 번호 범위 만들기 또는 수정](lync-server-2013-create-or-modify-an-unassigned-number-range.md)

  - [할당되지 않은 번호 범위 삭제](lync-server-2013-delete-an-unassigned-number-range.md)

