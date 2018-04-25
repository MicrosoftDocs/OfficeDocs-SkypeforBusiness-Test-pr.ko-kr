---
title: 'Lync Server 2013: 전화 접속 회의 액세스 번호 구성'
TOCTitle: 전화 접속 회의 액세스 번호 구성
ms:assetid: d8a18030-f318-43dd-834d-70e5014b5e8a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398952(v=OCS.15)
ms:contentKeyID: 49305217
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 전화 접속 회의 액세스 번호 구성

 

_**마지막으로 수정된 항목:** 2011-07-17_

전화 접속 회의를 배포하려면 회의의 오디오 부분에 참가하기 위해 사용자가 PSTN(공중 전화망)을 통해 전화를 걸 수 있는 전화 번호를 설정해야 합니다. 이러한 전화 접속 액세스 번호는 모임 초대장 및 전화 접속 회의 설정 웹 페이지에 표시됩니다.

전화 접속 액세스 번호를 만들려면 먼저 전화 접속 회의 지역을 계획한 다음 해당 지역이 포함된 다이얼 플랜을 구성해야 합니다. 지역에 대한 자세한 내용은 계획 설명서의 [Lync Server 2013의 전화 접속 회의 요구 사항](lync-server-2013-dial-in-conferencing-requirements.md)을 참조하십시오. 전화 접속 회의에 대한 다이얼 플랜을 구성하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 전화 접속 회의에 대한 다이얼 플랜 구성](lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md)을 참조하십시오.


> [!NOTE]
> 해당 액세스 번호에 대해 AD&nbsp;DS(Active Directory 도메인 서비스) 복제가 완료되어야 새 전화 접속 액세스 번호를 사용할 수 있습니다. 복제 작업은 몇 시간이 소요될 수 있습니다.




> [!NOTE]
> 전화 접속 액세스 번호를 만든 후 사용자가 올바른 액세스 번호를 보다 쉽게 식별할 수 있도록 Active Directory 대화 상대 개체에 대한 표시 이름을 수정할 수 있습니다. 표시 이름은 <STRONG>Set-CsDialInConferencingAccessNumber</STRONG> cmdlet를 사용하여 수정할 수 있습니다. Active Directory 개체는 수동으로 수정할 수 없습니다. 액세스 번호를 수정하는 방법에 대한 자세한 내용은 <STRONG>Set-CsDialInConferencingAccessNumber</STRONG> cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.



## 이 단원의 내용

[Lync Server 2013에서 전화 접속 회의 액세스 번호 만들기 또는 수정](lync-server-2013-create-or-modify-a-dial-in-conferencing-access-number.md)

## 참고 항목

#### 개념

[Lync Server 2013의 전화 접속 회의 요구 사항](lync-server-2013-dial-in-conferencing-requirements.md)  

#### 기타 리소스

[Lync Server 2013에서 전화 접속 회의에 대한 다이얼 플랜 구성](lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md)

