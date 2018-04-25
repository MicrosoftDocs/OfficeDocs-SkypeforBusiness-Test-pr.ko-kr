---
title: (권장) 전화 회의 디렉터리 만들기
TOCTitle: (권장) 전화 회의 디렉터리 만들기
ms:assetid: 787f4c94-1c96-468a-a74d-e06b7bd4b8a3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn832056(v=OCS.15)
ms:contentKeyID: 63232641
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (권장) 전화 회의 디렉터리 만들기

 

_**마지막으로 수정된 항목:** 2014-10-03_

전화 회의 디렉터리는 참가자가 Lync 2013을 사용하여 전화 회의에 참가할 때 사용하는 영숫자 모임 ID와 전화 접속 회의 참가자가 전화 회의에 참가할 때 사용하는 숫자 전용 전화 회의 ID 간의 매핑을 유지합니다. 전화 접속 ID의 형식은 다음과 같습니다.

    <housekeeping digit (1 digit)><conference directory (usually 1-2 digits)><conference number (variable number of digits><check digit (1 digit)>

전화 회의 디렉터리를 여러 개 만들면 상당히 많은 수의 전화 회의가 만들어질 때까지 전화 회의 ID가 짧게 유지될 수 있습니다. 전화 회의 ID를 약 6자리로 유지하려면 사용자당 전화 회의 수가 보편적인 조직의 경우 풀의 사용자 999명당 하나의 전화 회의 디렉터리를 만드는 것이 좋습니다. 이 지침을 사용하면 대개 전화 회의 ID가 짧게 유지될 수 있습니다. 그러나 회의 디렉터리 수가 풀 전체에서 9개를 초과하면 추가 전화 회의를 지원하기 위해 회의 ID 길이가 길어집니다.

## 전화 회의 디렉터리 만들기

1.  Lync Server 관리 셸에서 다음 cmdlet을 입력합니다.
    
        New-CsConferenceDirectory -Identity <XdsGlobalRelativeIdentity> -HomePool <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
    
    예를 들어 다음 명령은 ID가 42이고 atl-cs-001.litwareinc.com 풀에서 호스팅되는 전화 회의 디렉터리를 만듭니다.
    
        New-CsConferenceDirectory -Identity 42 -HomePool "atl-cs-001.litwareinc.com"

## 참고 항목

#### 개념

[Lync Server 2013의 전화 접속 회의 요구 사항](lync-server-2013-dial-in-conferencing-requirements.md)  

#### 기타 리소스

[New-CsConferenceDirectory](new-csconferencedirectory.md)

