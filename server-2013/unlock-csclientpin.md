---
title: Unlock-CsClientPin
TOCTitle: Unlock-CsClientPin
ms:assetid: eef7877c-0302-4ce7-84f5-06968d0623b9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412982(v=OCS.15)
ms:contentKeyID: 49305454
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Unlock-CsClientPin

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 사용자에 대한 개인식별번호(PIN) 잠금을 해제하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Unlock-CsClientPin -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Unlock-CsClientPin** cmdlet을 사용하여 사용자 litwareinc\\kenmyer에게 속한 PIN의 잠금을 해제합니다.

    Unlock-CsClientPin -Identity "litwareinc\kenmyer"

## 예제 2

예제 2에서는 **Unlock-CsClientPin** cmdlet을 사용하여 현재 잠겨 있는 모든 PIN의 잠금을 해제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUser** cmdlet을 사용하여 Lync Server를 사용하도록 설정된 모든 사용자 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet과 함께 IsLockedOut 속성이 True($True)와 같은(-eq) 사용자만 선택하는 **Get-CsClientPinInfo** cmdlet에 파이프됩니다.

그런 다음 필터링된 결과 컬렉션은 이전에 PIN이 잠긴 각 사용자에 대해 PIN의 잠금을 해제하는 **Unlock-CsClientPin** cmdlet에 파이프됩니다.

    Get-CsUser | Get-CsClientPinInfo | Where-Object {$_.IsLockedOut -eq $True} | Unlock-CsClientPin 

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 시스템에 연결하거나 PSTN(공중 전화망) 전화 회의에 참가할 수 있습니다. 일반적으로 사용자가 시스템에 로그온하거나 전화 회의에 참가하려면 사용자 이름 또는 암호를 입력해야 합니다. 그러나 영숫자 키패드가 없는 전화기를 사용하는 경우 사용자 이름 및 암호를 입력하기 어려울 수 있습니다. 따라서 Lync Server는 사용자에게 숫자로만 구성된 PIN을 제공할 수 있도록 지원합니다. PIN을 묻는 메시지가 표시되면 사용자 이름 및 암호 대신 PIN을 입력하여 시스템에 로그온하거나 전화 회의에 참가할 수 있습니다.

그러나 이는 사용자의 PIN 잠금이 해제된 경우에만 가능합니다. PIN이 잠긴 경우(사용자가 로그온에 반복적으로 실패하거나 관리자가 명시적으로 PIN을 잠근 경우) 사용자는 PIN 인증을 사용하여 시스템에 액세스하거나 전화 회의에 참가할 수 없게 됩니다. 하지만 사용자 이름 및 암호를 제공하여 Lync와 같은 응용 프로그램을 통해 시스템에 로그온할 수는 있습니다. PIN이 잠긴 경우 PIN 인증을 사용하여 시스템에 액세스할 수 있는 권한을 복원하려면 관리자가 잠긴 PIN의 잠금을 해제하는 방법밖에 없습니다. 이 작업은 **Unlock-CsClientPin** cmdlet을 사용하여 수행할 수 있습니다.

Lync Server Standard Edition을 설치한 경우에는 기본적으로 SQL Server Express에 대한 방화벽 예외가 활성화되지 않습니다. 따라서 Windows PowerShell의 원격 인스턴스에서는 **Unlock-CsClientPin** cmdlet을 실행할 수 없습니다. 명령이 방화벽을 통과하여 SQL Server Express 데이터베이스에 액세스할 수 없기 때문입니다. 그러나 cmdlet을 Standard Edition 서버 자체에서 로컬로 실행할 수는 있습니다. Standard Edition 서버에 대해 원격으로 **Unlock-CsClientPin** cmdlet을 실행하려면 SQL Server Express의 방화벽 예외를 수동으로 활성화해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Unlock-CsClientPin** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Unlock-CsClientPin"}

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
<td><p>PIN 잠금을 해제해야 하는 사용자 계정의 ID. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>또한 표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Unlock-CsClientPin** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Unlock-CsClientPin** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.UserPinService.PinInfoDetails 개체의 인스턴스를 하나 이상 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientPinInfo](get-csclientpininfo.md)  
[Lock-CsClientPin](lock-csclientpin.md)  
[Set-CsClientPin](set-csclientpin.md)

