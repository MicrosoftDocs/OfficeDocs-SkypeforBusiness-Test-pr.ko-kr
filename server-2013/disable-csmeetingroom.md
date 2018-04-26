---
title: Disable-CsMeetingRoom
TOCTitle: Disable-CsMeetingRoom
ms:assetid: 1bce6b58-484f-4e59-a259-aa315d37d9b0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204723(v=OCS.15)
ms:contentKeyID: 49302974
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsMeetingRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 회의실을 사용하지 않도록 설정합니다. 회의실은 소규모 회의 공간의 비디오 회의 및 공동 작업 시나리오를 진행할 수 있도록 설계된 회의 장치입니다. 회의실 개체를 사용하지 않도록 설정하면 회의실을 나타내는 사용자 계정에 할당된 모든 Lync Server 관련 Active Directory 특성이 제거됩니다. 그러나 Active Directory 사용자 계정 자체는 삭제되지 않습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Disable-CsMeetingRoom -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 회의실 sip:RedmondMeetingRoom@litwareinc.com을 사용하지 않도록 설정합니다.

    Disable-CsMeetingRoom -Identity "sip:RedmondMeetingRoom@litwareinc.com"

## 예제 2

예제 2에서는 조직에서 현재 사용 중인 모든 회의실을 사용하지 않도록 설정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsMeetingRoom** cmdlet을 사용하여 모든 회의실의 컬렉션을 검색합니다. 해당 컬렉션은 **Disable-CsMeetingRoom** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 회의실을 사용하지 않도록 설정합니다.

    Get-CsMeetingRoom | Disable-CsMeetingRoom

## 자세한 정보

Lync Server에서 회의실은 회의 공간에 설치되며 다음과 같은 고급 모임 기능을 제공하는 자체 포함 컴퓨터 장비입니다.

  - 원터치 방식 모임 참가 환경

  - 다중 뷰 비디오 갤러리

  - 회의실 화면 전면의 터치 가능 화이트보드

  - 예약된 모임 액세스 제공을 위한 일정 통합

  - 콘텐츠 공유 및 전환

이와 같은 새로운 끝점 장치를 관리하려면 먼저 장치에 대해 Microsoft Exchange Server 2013 리소스 사서함 계정을 만들고 사용하도록 설정한 다음 Lync Server 2013에 대해 해당 리소스 계정을 사용하도록 설정해야 합니다. Lync Server의 경우에는 회의실을 만들거나 제거하는 데 사용할 수 있는 cmdlet이 없습니다. 대신 [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet을 사용하여 회의실을 사용하도록 설정하고 **Disable-CsMeetingRoom** cmdlet을 사용하여 회의실을 사용하지 않도록 설정합니다. 리소스 계정이 있어야 회의실을 사용하도록 설정할 수 있으며, 회의실을 사용하지 않도록 설정하면 해당 회의실이 회의실 컬렉션에서만 제거되며 리소스 사서함 계정이 삭제되지는 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Disable-CsMeetingRoom"}

**Lync Server 제어판:** **Disable-CsMeetingRoom** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>회의실로 구성할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 보통 네 가지 형식 중 하나를 사용하여 지정되는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다.</p>
<p>또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>회의실을 사용하지 않도록 설정하기 위해 지정된 도메인 컨트롤러에 연결할 수 있도록 합니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-dc-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-dc-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>사용하지 않도록 설정되는 회의실을 나타내는 파이프라인을 통해 회의실 개체를 전달할 수 있도록 합니다. 기본적으로 <strong>Disable-CsMeetingRoom</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Disable-CsMeetingRoom** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Disable-CsMeetingRoom** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Enable-CsMeetingRoom](enable-csmeetingroom.md)  
[Get-CsMeetingRoom](get-csmeetingroom.md)  
[Move-CsMeetingRoom](move-csmeetingroom.md)  
[Set-CsMeetingRoom](set-csmeetingroom.md)

