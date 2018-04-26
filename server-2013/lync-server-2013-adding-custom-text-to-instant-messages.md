---
title: 'Lync Server 2013: 메신저 대화에 사용자 지정 텍스트 추가'
TOCTitle: 메신저 대화에 사용자 지정 텍스트 추가
ms:assetid: cabcc3ec-9d35-42ac-a403-e21b7d538c2c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398847(v=OCS.15)
ms:contentKeyID: 52056942
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 메신저 대화에 사용자 지정 텍스트 추가

 

_**마지막으로 수정된 항목:** 2013-02-20_

**New-CSClientPolicy** 또는 **Set-CSClientPolicy**Lync Server 관리 셸 cmdlet과 IMWarning 매개 변수를 사용하여 모든 Lync 2013 메신저 대화의 시작 부분에 알림 또는 경고를 추가합니다.

다음 예의 명령은 새 메신저 대화가 시작될 때마다 대화 창 상단에 보안 알림을 추가합니다.

    New-CsClientPolicy -Identity IMSecurityNotice -IMWarning 
    "Remember, security is everyone's responsibility. Keep it confidential."

**Grant-CSClientPolicy**를 사용하여 새로운 이 정책을 사용자에게 지정합니다. 자세한 내용은 Lync Server 관리 셸 설명서에서 **New-CSClientPolicy** 및 **Grant-CSClientPolicy**를 참조하세요.

