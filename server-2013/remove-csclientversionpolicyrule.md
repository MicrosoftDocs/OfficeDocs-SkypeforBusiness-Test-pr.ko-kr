---
title: Remove-CsClientVersionPolicyRule
TOCTitle: Remove-CsClientVersionPolicyRule
ms:assetid: 71a107c9-5499-460f-b4b8-08b368be9321
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398541(v=OCS.15)
ms:contentKeyID: 49303994
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsClientVersionPolicyRule

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 하나 이상의 클라이언트 버전 정책 규칙을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsClientVersionPolicyRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 site:Redmond/74ba9211-8610-42f9-91ba-846cdee98820인 클라이언트 버전 정책 규칙을 삭제합니다. ID는 고유해야 하므로 이 명령은 단일 규칙만 삭제합니다.

    Remove-CsClientVersionPolicyRule -Identity site:Redmond/74ba9211-8610-42f9-91ba-846cdee98820

## 예제 2

예제 2에서는 Redmond 사이트에 대해 구성된 모든 클라이언트 버전 정책 규칙을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClientVersionPolicyRule** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "site:Redmond/\*"는 반환된 데이터를 문자열 값 "site:Redmond/"로 시작하는 ID를 가진 정책 규칙으로 제한합니다. 이 필터링된 컬렉션은 해당 컬렉션의 각 항목을 삭제하는 **Remove-CsClientVersionPolicyRule** cmdlet에 파이프됩니다.

    Get-CsClientVersionPolicyRule -Filter "site:Redmond/*" | Remove-CsClientVersionPolicyRule

## 예제 3

예제 3에서는 현재 비활성화된 모든 클라이언트 버전 정책 규칙을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClientVersionPolicyRule** cmdlet을 매개 변수 없이 호출하여 조직에서 현재 사용되고 있는 모든 정책 규칙의 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 False와 같은 모든 규칙을 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 필터링된 컬렉션은 해당 컬렉션의 각 항목을 삭제하는 **Remove-CsClientVersionPolicyRule** cmdlet에 파이프됩니다.

    Get-CsClientVersionPolicyRule | Where-Object {$_.Enabled -eq $False} | Remove-CsClientVersionPolicyRule

## 자세한 정보

클라이언트 버전 규칙은 Lync Server에 로그온할 수 있는 클라이언트 응용 프로그램을 결정하는 데 사용됩니다. 사용자가 Lync Server에 로그온하려고 하면 클라이언트 응용 프로그램이 서버에 SIP 헤더를 전송합니다. 이 헤더에는 소프트웨어의 주 버전, 부 버전, 빌드 번호 등 응용 프로그램 자체에 대한 자세한 정보가 포함되어 있습니다. 그런 다음 클라이언트 버전 규칙 컬렉션과 버전 정보를 비교하여 특정 응용 프로그램에 적용되는 규칙이 있는지 확인합니다. 예를 들어 사용자가 Microsoft Office Communicator 2007 R2를 사용하여 로그온하려는 경우를 가정해 보겠습니다. 사용자가 로그인하기 전에 시스템에서 Office Communicator 2007 R2에 적용되는 클라이언트 버전 규칙이 있는지 확인합니다. 이러한 규칙이 있으면 Lync Server에서 해당 규칙에 의해 지정된 작업을 수행합니다. 작업은 다음 중 하나여야 합니다.

Allow. 사용자에게 로그온이 허용됩니다.

AllowAndUpgrade. 사용자에게 로그온이 허용되고, 이 사용자의 Communicator 2007 R2가 최신 버전의 Lync로 자동으로 업그레이드됩니다. 업그레이드는 시스템 구성 방법에 따라 Microsoft Update 또는 Windows Server Update Services를 사용하여 수행됩니다.

AllowWithUrl. 사용자에게 로그온이 허용되고, 최신 버전의 Lync를 다운로드하여 설치할 수 있는 URL로 이동되는 메시지가 표시됩니다. 이 URL은 Lync Server를 설치할 때 자동으로 만들어진 사이트가 아니라 사용자가 만든 웹 사이트를 가리켜야 합니다.

Block. 사용자에게 로그온이 허용되지 않습니다.

BlockAndUpgrade. 사용자에게 로그온이 허용되지는 않지만, 이 사용자의 Communicator 2007 R2가 최신 버전의 Lync로 자동으로 업그레이드됩니다. 그러면 사용자가 새 클라이언트 응용 프로그램을 사용하여 로그온할 수 있습니다. 업그레이드는 시스템 구성 방법에 따라 Microsoft Update 또는 Windows Server Update Services를 사용하여 수행됩니다.

BlockWithUrl. 사용자에게 로그온이 허용되지는 않지만, 최신 버전의 Lync를 다운로드하여 설치할 수 있는 URL로 이동되는 메시지가 표시됩니다. 이 URL은 Lync Server를 설치할 때 자동으로 만들어진 사이트가 아니라 사용자가 만든 웹 사이트를 가리켜야 합니다.

클라이언트 버전 규칙은 전역 범위, 사이트 범위, 서비스 범위(등록자 서비스) 또는 사용자별 범위에서 구성할 수 있는 클라이언트 버전 정책에서 수집됩니다. **Remove-CsClientVersionPolicyRule** cmdlet을 사용하면 조직에서 사용하도록 구성된 클라이언트 정책 규칙 중 하나 이상을 삭제할 수 있습니다. 전역 정책을 포함하여 클라이언트 버전 정책에서 이러한 규칙을 삭제할 수 있습니다.

클라이언트 버전 정책은 페더레이션 사용자에게 적용되지 않습니다. 대신 페더레이션 사용자에게는 조직에서 사용되는 클라이언트 버전 정책이 적용됩니다. 예를 들어 페더레이션 사용자가 클라이언트 A를 사용하고, 이 클라이언트가 페더레이션 조직에서 허용된다고 가정해 보겠습니다. 페더레이션 조직에서 클라이언트 A 사용을 허용하는 한 이 사용자는 해당 클라이언트를 사용하여 조직과 통신할 수 있습니다. 이는 클라이언트 버전 정책이 클라이언트 A 사용을 차단하는 경우에도 마찬가지입니다. 조직에서 시행되는 클라이언트 버전 정책은 페더레이션 조직에서 사용되는 클라이언트 버전 정책을 무시하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsClientVersionPolicyRule** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsClientVersionPolicyRule"}

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
<td><p>제거할 클라이언트 버전 정책 규칙의 고유한 식별자입니다. 클라이언트 버전 규칙의 ID는 규칙이 구성된 범위와 GUID(Globally Unique Identifier)로 구성됩니다. 즉, 규칙의 ID는 site:Redmond/1987d3c2-4544-489d-bbe3-59f79f530a83과 유사한 형태가 됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.Rule 개체입니다. **Remove-CsClientVersionPolicyRule** cmdlet은 클라이언트 버전 규칙 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsClientVersionPolicyRule** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.Rule 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClientVersionPolicyRule](get-csclientversionpolicyrule.md)  
[New-CsClientVersionPolicyRule](new-csclientversionpolicyrule.md)  
[Set-CsClientVersionPolicyRule](set-csclientversionpolicyrule.md)

