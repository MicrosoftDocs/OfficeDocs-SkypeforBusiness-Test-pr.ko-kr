---
title: Set-CsClientPin
TOCTitle: Set-CsClientPin
ms:assetid: d587c69c-9cf7-4cd8-81d4-26869524654b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398929(v=OCS.15)
ms:contentKeyID: 49305162
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsClientPin

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 사용자에게 새 개인식별번호(PIN)를 할당합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다. 이 cmdlet의 Lync Server 2013 버전은 Lync Server 2013에 있는 사용자에게만 PIN 번호를 할당할 수 있습니다. Lync Server 2010에 있는 사용자에게 PIN 번호를 할당하려면 Lync Server 2010 버전의 Set-CsClientPin을 사용해야 합니다.

## 구문

    Set-CsClientPin -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Pin <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 사용자 litwareinc\\kenmyer에게 자동 생성된 새 PIN을 할당합니다. 자동 생성된 PIN을 할당하려면 **Set-CsClientPin** cmdlet을 호출할 때 Pin 매개 변수를 삭제합니다. 명령이 완료되면 Ken Myer에게 할당된 새 PIN이 화면에 표시됩니다. 그런 다음 이 정보가 사용자에게 릴레이될 수 있습니다.

    Set-CsClientPin -Identity "litwareinc\kenmyer"

## 예제 2

예제 2의 명령은 사용자 litwareinc\\kenmyer에게 PIN 18723834를 할당합니다. 특정 PIN을 할당하려면 Pin 매개 변수 뒤에 할당할 번호를 포함하면 됩니다.

    Set-CsClientPin -Identity "litwareinc\kenmyer" -Pin 18723834

## 예제 3

예제 3에서는 지정된 Active Directory OU(조직 구성 단위)의 모든 사용자에게 새 PIN을 자동으로 할당하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 OU 매개 변수와 함께 **Get-CsUser** cmdlet을 사용하여 Finance OU의 계정을 가진 모든 사용자 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 사용자에 대한 새 PIN을 생성하는 **Set-CsClientPin** cmdlet에 파이프됩니다.

    Get-CsUser -OU "OU=Finance,DC=litwareinc,DC=com" | Set-CsClientPin

## 예제 4

예제 4에 표시된 명령은 현재 할당된 PIN이 없는 모든 사용자에게 새 PIN을 할당합니다. 이 작업을 수행하기 위해 **Get-CsUser** cmdlet을 사용하여 Lync Server를 사용하도록 설정된 모든 사용자 컬렉션을 반환합니다. 이 컬렉션은 **Get-CsClientPin** cmdlet 및 **Where-Object** cmdlet에 파이프됩니다. 이 두 cmdlet은 함께 작동하여 IsPinSet 속성이 False와 같은 사용자만 선택합니다. 그런 다음 PIN이 없는 사용자만 포함된 결과 컬렉션은 컬렉션의 각 사용자에 대한 PIN을 자동 생성하는 **Set-CsClientPin** cmdlet에 파이프됩니다.

    Get-CsUser | Get-CsClientPinInfo | Where-Object {$_.IsPinSet -eq $False} | Set-CsClientPin

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 시스템에 연결하거나 PSTN(공중 전화망) 전화 회의에 참가할 수 있습니다. 일반적으로 사용자가 시스템에 로그온하거나 전화 회의에 참가하려면 사용자 이름 또는 암호를 입력해야 합니다. 그러나 영숫자 키패드가 없는 전화기를 사용하는 경우 사용자 이름 및 암호를 입력하기 어려울 수 있습니다. 따라서 Lync Server는 사용자에게 숫자로만 구성된 PIN을 제공할 수 있도록 지원합니다. PIN을 묻는 메시지가 표시되면 사용자 이름 및 암호 대신 PIN을 입력하여 시스템에 로그온하거나 전화 회의에 참가할 수 있습니다.

PIN은 Lync Server를 사용하도록 사용자를 설정하면 해당 사용자에게 할당되는 것이 아닙니다. 즉, 기본적으로 사용자는 PIN 인증을 사용하여 시스템에 액세스할 수 없습니다. PIN은 사용자가 전화 접속 회의 웹 페이지에서 가져오거나 관리자가 **Set-CsClientPin** cmdlet을 사용하여 각 사용자에게 할당할 수 있습니다. **Set-CsClientPin** cmdlet을 사용하면 사용자에게 특정 PIN을 할당하거나 Lync Server에서 PIN을 생성하도록 할 수 있습니다. PIN을 자동으로 생성하려면 **Set-CsClientPin** cmdlet을 호출할 때 PIN 매개 변수를 생략하면 됩니다. 이렇게 하면 새 PIN이 생성되고, 명령이 완료되면 사용자 ID와 새 PIN이 화면에 표시됩니다.

명시적으로 할당하는 PIN은 해당 사용자에게 적용되는 PIN 인증 정책에 지정된 조건을 충족해야 합니다. 예를 들어 PIN은 적어도 MinPasswordLength 속성에 지정된 자릿수의 숫자를 포함해야 합니다. 또한 PIN은 숫자만 포함할 수 있습니다. 문자나 기타 숫자가 아닌 문자는 허용되지 않습니다.

**Set-CsClientPin** cmdlet을 사용하여 클라이언트 PIN을 설정하면 PIN 기록 개수가 적용되지 않습니다. 예를 들어 사용자에게 PIN 번호 12345가 있고 클라이언트 PIN 정책이 동일한 PIN 번호를 즉시 다시 사용하지 못하게 하는 경우를 가정해 보겠습니다. 해당 사용자가 전화 접속 회의 웹 페이지를 사용하여 클라이언트 PIN을 갱신하려고 하는 경우 동일한 PIN 번호(12345)를 다시 사용하는 모든 시도가 거부됩니다. 그러나 **Set-CsClientPin** cmdlet을 통해 관리자는 사용자에게 PIN 12345를 발급할 수 있습니다. **Set-CsClientPin** cmdlet에는 PIN 정책 기록 개수가 적용되지 않기 때문입니다.

Lync Server Standard Edition을 설치한 경우에는 기본적으로 SQL Server Express에 대한 방화벽 예외가 활성화되지 않습니다. 따라서 Windows PowerShell의 원격 인스턴스에서는 **Set-CsClientPin** cmdlet을 실행할 수 없습니다. 명령이 방화벽을 통과하여 SQL Server Express 데이터베이스에 액세스할 수 없기 때문입니다. 그러나 cmdlet을 Standard Edition 서버 자체에서 로컬로 실행할 수는 있습니다. Standard Edition 서버에 대해 원격으로 **Set-CsClientPin** cmdlet을 실행하려면 SQL Server Express의 방화벽 예외를 수동으로 활성화해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsClientPin** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClientPin"}

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
<td><p>PIN 잠금을 설정해야 하는 사용자 계정의 ID. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
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
<td><p><em>Pin</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자에게 할당할 선택적 PIN입니다. PIN 매개 변수를 포함하지 않으면 Lync Server에서 무작위로 PIN을 생성하여 해당 사용자에게 할당합니다. PIN은 사용자에게 할당된 클라이언트 PIN 정책에 있는 최소 길이, PIN 및 공통 패턴 설정을 준수해야 합니다.</p></td>
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

문자열 값 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Set-CsClientPin** cmdlet은 사용자 계정의 ID를 나타내는 문자열 값의 파이프라인된 입력을 허용합니다. 또한 이 cmdlet은 사용자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsClientPin** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.UserPinService.PinInfoDetails 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientPinInfo](get-csclientpininfo.md)  
[Lock-CsClientPin](lock-csclientpin.md)  
[Unlock-CsClientPin](unlock-csclientpin.md)

