---
title: Update-CsTenantMeetingUrl
TOCTitle: Update-CsTenantMeetingUrl
ms:assetid: 9aed3ede-bbd3-405a-997f-f7553e66aecd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn424754(v=OCS.15)
ms:contentKeyID: 59602777
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Update-CsTenantMeetingUrl

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 비즈니스용 Skype Online 테넌트에 대한 모임 URL을 업데이트합니다. 업데이트된 URL은 클라이언트가 쉽게 모임을 찾고 연결할 수 있도록 더욱 간단하고 표준화된 형식을 사용합니다.

이 cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Update-CsTenantMeetingUrl [-Tenant] <guid> [-Force] [-WhatIf] [-Confirm]

## 예제

## 예제 1

예제 1에 나와 있는 명령은 테넌트의 모임 URL을 테넌트 ID 38aad667-af54-4397-aaa7-e94c79ec2308로 업데이트합니다. 이 명령을 완료하려면 테넌트 ID를 제공해야 합니다. Enter 키를 눌러 명령을 실행하면 모임 URL을 업데이트할지 묻는 메시지가 나타납니다. 이 메시지에 "예"라고 응답해야 Update-CsTenantMeetingUrl이 실제로 비즈니스용 Skype Online 구성 설정을 변경합니다.

    Update-CsTenantMeetingUrl -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"

## 예제 2

예제 2도 테넌트의 모임 URL을 테넌트 ID 38aad667-af54-4397-aaa7-e94c79ec2308로 업데이트합니다. 그러나 이 경우에는 Force 매개 변수가 포함됩니다. 이 매개 변수는 Update-CsTenantMeetingUrl을 업데이트할 때 일반적으로 나타나는 확인 메시지를 무시합니다. 이 경우 Enter 키를 누르자마자 명령이 실행되고 비즈니스용 Skype Online 구성 설정이 수정됩니다.

    Update-CsTenantMeetingUrl -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308" -Force

## 자세한 정보

Update-CsTenantMeetingUrl은 비즈니스용 Skype Online 모임 URL을 더욱 간단하고 표준화된 형식으로 업데이트합니다. 이렇게 하면 원래의 모임 URL에서 자주 발생하던 문제를 없애는 데 도움이 됩니다. 예를 들어 조직에서 Office 365 도메인을 contoso.onmicrosoft.com이라는 이름으로 설정한 경우 모임 URL은 다음과 같습니다.

https://meet.lync.com/onmicrosoft/contoso/user1/45GZFH99

이번에는 조직에 몇 가지 변화가 생겨 onmicrosoft.com URL 대신 litwareinc.com이라는 "베니티" URL을 사용하기로 결정했다고 가정해 보겠습니다. 이에 따라 조직이 사용자 전자 메일 주소를 litwareinc.com 도메인을 사용하도록 수정해도 모임 URL은 여전히 다음과 같이 이전 도메인 이름을 사용합니다.

https://meet.lync.com/contoso/user1/45GZFH99

이 문제를 해결하려면 관리자가 Update-CsTenantMeetingUrl cmdlet을 실행해야 합니다. 그러면 이전 모임 URL이 베니티 URL을 사용하는 URL로 바뀝니다.

https://meet.lync.com/litwareinc.com/user1/37JYLP71

이 URL 변경을 수행하는 유일한 방법은 Update-CsTenantMeetingUrl cmdlet을 실행하는 것입니다.

Update-CsTenantMeetingUrl을 실행하면 잠깐 동안 동기화된 후에 비즈니스용 Skype Online 테넌트가 새 URL로 즉시 전환됩니다. 그렇다고 해서 사용자가 예약하는 새 모임에 문제가 생기는 것은 아닙니다. 새 모임은 새 URL을 사용해 자동으로 예약되기 때문입니다. 그러나 이전에 예약한 모임은 문제가 될 수 있습니다. 사용되지 않는 이전 URL을 사용하여 예약했기 때문입니다. 이 문제를 해결하는 유일한 방법은 사용자가 해당 모임을 다시 예약하는 것입니다.

일부 조직, 특히 이미 많은 모임이 예약되어 있는 조직의 경우 이는 잠재적으로 문제가 될 수 있기 때문에 Update-CsTenantMeetingUrl은 모임 URL을 실제로 업데이트하기 전에 기본적으로 다음과 같은 메시지를 표시합니다.

경고: 이 테넌트의 사용자 입장에서 크게 변경됩니다. 모임 URL 구성이 업데이트됩니다\! 이전 모임 URL을 더 이상 사용할 수 없습니다. 이전 모임 URL이 더 이상 작동하지 않습니다. 이 변경은 되돌릴 수 없습니다.  
계속하시겠습니까?  
\[Y\] 예 \[A\] 모두 예 \[N\] No \[L\] 모두 아니요 \[S\] 일시 중단 \[?\] 도움말(기본값 "Y"):

"예" 또는 "모두 예"라고 답해야 명령이 실제로 실행됩니다. "아니요"로 답하면 명령이 취소되고 모임 URL이 업데이트되지 않습니다. 모임 URL이 변경되면 원래 URL로 되돌릴 수 있는 방법이 없습니다. 명령이 실행되면 URL이 변경되고 이전에 예약한 모든 모임을 다시 예약해야 합니다. 또한 테넌트 하나당 이 명령을 한 번만 실행하면 됩니다. 즉, 명령을 주기적으로 실행하고 모임 URL을 다시 업데이트할 필요가 없습니다.

확인 메시지를 거치지 않고 명령을 실행하려는 경우 Force 매개 변수를 포함하면 됩니다. 이 경우 Update-CsTenantMeetingUrl이 다음과 같은 확인 메시지를 표시하지 않고 실행됩니다.

경고: 이 테넌트의 사용자 입장에서 크게 변경됩니다. 모임 URL 구성이 업데이트됩니다\!

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Tenant</strong></p></td>
<td><p>필수</p></td>
<td><p>System.Guid</p></td>
<td><p>페더레이션 설정이 반환되는 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Tenant 매개 변수를 포함하지 않으면 계속하기 전에 Update-CsMeetingUrl이 해당 매개 변수를 입력하라는 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p>
<p>Update-CsMeetingUrl의 기본 동작은 업데이트하기 전에 확인 메시지를 표시하는 것입니다. 다시 말해 확인 메시지를 표시하려는 경우 Confirm 매개 변수를 포함할 필요가 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Update-CsMeetingUrl이 업데이트를 진행하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. Update-CsMeetingUrl은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음

## 참고 항목

#### 기타 리소스

[Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)

