---
title: Remove-CsConferencingPolicy
TOCTitle: Remove-CsConferencingPolicy
ms:assetid: 8fe81ace-d167-414b-9455-8be7ddc0cab5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398728(v=OCS.15)
ms:contentKeyID: 49304364
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsConferencingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 전화 회의 정책을 제거합니다. 전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정합니다. 여기에는 전화 회의에 IP 오디오 및 비디오를 포함할 수 있는지 여부부터 모임에 참가할 수 있는 최대 사용자 수에 이르기까지 모든 기능이 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsConferencingPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsConferencingPolicy** cmdlet을 사용하여 ID가 SalesConferencingPolicy인 전화 회의 정책을 삭제합니다.

    Remove-CsConferencingPolicy -Identity SalesConferencingPolicy

## 예제 2

예제 2에서는 사이트 범위에서 구성된 모든 전화 회의 정책을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsConferencingPolicy** cmdlet 및 Filter 매개 변수를 사용하여 모든 사이트 수준 정책의 컬렉션을 반환합니다. 필터 값 "site:\*"는 ID가 문자열 값 "site:"으로 시작하는 정책만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsConferencingPolicy** cmdlet에 파이프됩니다.

    Get-CsConferencingPolicy -Filter "site:*" | Remove-CsConferencingPolicy

## 예제 3

예제 3에서는 100명이 넘는 최대 모임 크기(MaxMeetingSize)를 허용하는 모든 정책이 삭제됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsConferencingPolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 전화 회의 정책의 컬렉션을 검색합니다. 이 컬렉션은 반환된 데이터를 MaxMeetingSize 값이 100보다 큰 정책으로 제한하는 필터를 적용하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 필터링된 컬렉션의 모든 정책을 삭제하는 **Remove-CsConferencingPolicy** cmdlet에 전달됩니다.

    Get-CsConferencingPolicy | Where-Object {$_.MaxMeetingSize -gt 100} | Remove-CsConferencingPolicy 

## 자세한 정보

전화 회의는 Lync Server의 중요한 부분입니다. 전화 회의 기능을 사용하면 사용자 그룹이 온라인으로 모여 슬라이드 및 비디오 보기, 응용 프로그램 공유, 파일 교환, 기타 통신 및 공동 작업 등을 수행할 수 있기 때문입니다.

관리자가 전화 회의 및 전화 회의 설정에 대한 제어를 유지 관리하는 기능도 중요합니다. 경우에 따라 보안 문제가 발생할 수 있습니다. 기본적으로 인증되지 않은 사용자를 비롯한 모든 사용자가 모임에 참가하고 모임 중에 배포된 슬라이드나 유인물을 저장할 수 있습니다. 대역폭 문제가 발생하는 경우도 있습니다. 예를 들어 동시 모임 수가 많은 경우, 각 모임에 수백 명의 참가자가 있는 경우 및 각 모임에서 화상 공급 및 파일 공유를 사용하는 경우에 네트워크에 문제가 발생할 수 있습니다. 그리고, 드물긴 하지만 법률 문제가 발생할 수도 있습니다. 예를 들어 모임 참가자는 기본적으로 공유 콘텐츠에 주석을 추가할 수 있지만 이러한 주석은 모임을 보관할 때 저장되지 않습니다. 조직에서 모든 전자 통신의 기록을 보관해야 하는 경우 주석을 사용하지 않도록 설정할 수 있습니다.

물론 전화 회의 설정을 관리해야 하는 것도 중요한 사항입니다. 실제로 이러한 설정을 관리하는 것은 또 다른 문제입니다. Lync Server에서는 전화 회의 정책을 사용하여 전화 회의를 관리합니다. 이전 버전의 소프트웨어에서는 이러한 정책을 모임 정책이라고 했습니다. 앞서 언급한 것처럼 전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정하며, 여기에는 전화 회의에 IP 오디오 및 비디오를 포함할 수 있는지 여부부터 모임에 참가할 수 있는 최대 사용자 수에 이르기까지 모든 기능이 포함됩니다. 전화 회의 정책은 전역 범위, 사이트 범위 또는 사용자별 범위에서 구성할 수 있습니다. 따라서 각 사용자가 사용할 수 있는 기능을 관리자가 유동적으로 결정할 수 있습니다.

조직에서 사용하도록 구성된 전화 회의 정책을 삭제하려면 **Remove-CsConferencingPolicy** cmdlet을 사용하면 됩니다. 한 가지 예외가 있는데, 전역 정책은 삭제할 수 없습니다. 전역 정책에 대해 **Remove-CsConferencingPolicy** cmdlet을 실행할 수도 있습니다. 이 경우 정책이 제거되지 않고 대신 모든 전역 정책 속성이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsConferencingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsConferencingPolicy"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 전화 회의 정책의 고유한 식별자입니다. 전화 회의 정책은 전역, 사이트 또는 사용자별 범위에서 구성할 수 있습니다. 전역 정책을 제거하려면 -Identity global 구문을 사용합니다. 전역 정책은 실제로 제거할 수 없습니다. 대신 모든 정책 속성이 기본값으로 다시 설정됩니다. 사이트 정책을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 사용자별 정책을 제거하려면 -Identity SalesConferencingPolicy와 유사한 구문을 사용합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 정책이 현재 하나 이상의 사용자에게 할당된 경우에도 <strong>Remove-CsConferencingPolicy</strong> cmdlet을 통해 사용자별 정책을 삭제할 수 있습니다. 이 매개 변수가 없으면 정책을 제거하기 전에 삭제 요청을 확인하는 메시지가 나타납니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MeetingPolicy 개체입니다. **Remove-CsConferencingPolicy** cmdlet은 모임 정책 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsConferencingPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Meeting.MeetingPolicy 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsConferencingPolicy](get-csconferencingpolicy.md)  
[Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)  
[New-CsConferencingPolicy](new-csconferencingpolicy.md)  
[Set-CsConferencingPolicy](set-csconferencingpolicy.md)

