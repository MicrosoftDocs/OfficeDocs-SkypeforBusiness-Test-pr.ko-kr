---
title: Remove-CsKerberosAccountAssignment
TOCTitle: Remove-CsKerberosAccountAssignment
ms:assetid: f878fed1-ee6d-4275-8f76-2bc134e465c2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413052(v=OCS.15)
ms:contentKeyID: 49305581
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsKerberosAccountAssignment

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 Kerberos 계정 할당을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsKerberosAccountAssignment -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에서 Kerberos 계정 할당을 제거한 다음 **Enable-CsTopology** cmdlet을 호출하여 Kerberos 웹 인증 비활성화를 완료합니다.

    Remove-CsKerberosAccountAssignment -Identity "site:Redmond"
    Enable-CsTopology

## 예제 2

예제 2에서는 현재 사용 중인 모든 Kerberos 계정 할당을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsKerberosAccountAssignment** cmdlet을 추가 매개 변수 없이 호출하여 모든 Kerberos 계정 할당의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 할당을 삭제하는 **Remove-CsKerberosAccountAssignment** cmdlet에 파이프됩니다. 이 과정이 완료되면 예제의 두 번째 명령이 **Enable-CsTopology** cmdlet을 호출하여 Kerberos 웹 인증 비활성화를 완료합니다.

    Get-CsKerberosAccountAssignment | Remove-CsKerberosAccountAssignment
    Enable-CsTopology

## 자세한 정보

Microsoft Office Communications Server 2007 및 Microsoft Office Communications Server 2007 R2에서는 IIS가 표준 사용자 계정으로 실행되었습니다. 이로 인해 문제가 발생할 수 있었습니다. 즉, 이 암호가 만료되어 웹 서비스의 연결이 끊어진 경우 진단하기 어려운 문제가 발생합니다. 암호 만료 문제를 피하는 데 도움이 되도록 Lync Server에서는 IIS를 실행하는 사이트의 모든 컴퓨터에 대한 인증 주체 역할을 할 수 있는 컴퓨터 계정(실제로는 존재하지 않는 컴퓨터에 대해)을 만들 수 있습니다. 이러한 계정은 Kerberos 인증 프로토콜을 사용하므로 Kerberos 계정이라고 하며, 새로운 인증 프로세스를 Kerberos 웹 인증이라고 합니다. 이를 통해 단일 계정으로 모든 IIS 서버를 관리할 수 있습니다.

이 새 인증 사용자로 서버를 실행하려면 먼저 **New-CsKerberosAccount** cmdlet을 사용하여 컴퓨터 계정(이 역시 실제 컴퓨터와 연결되지 않음)을 만들어야 합니다. 이후에 이 계정은 하나 이상의 사이트에 할당됩니다. 할당이 수행된 후에는 **Enable-CsTopology** cmdlet을 실행하여 연결을 설정하며, 특히 이 과정에서 Active Directory 도메인 서비스 내에 필요한 SPN(서비스 사용자 이름)이 만들어집니다. SPN은 클라이언트 응용 프로그램에 특정 서비스를 찾을 수 있는 방법을 제공합니다.

각 Lync Server 사이트는 한 개 이하의 Kerberos 계정과 연결할 수 있습니다. 반면 각 계정은 여러 사이트와 연결할 수 있습니다. **Remove-CsKerberosAccountAssignment** cmdlet을 사용하면 언제든지 사이트와 계정 간의 연결을 제거할 수 있습니다. 이 cmdlet은 해당 계정을 삭제하지는 않으며 단순히 계정과 사이트 간의 연결을 끊어서 해당 사이트에서 Kerberos 웹 인증을 비활성화합니다.

**Remove-CsKerberosAccountAssignment** cmdlet을 실행한 후에는 **Enable-CsTopology** cmdlet을 실행해야 합니다. 그러면 Active Directory에서 계정의 서비스 사용자 이름이 제거되고 Kerberos 웹 인증 비활성화가 완료됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsKerberosAccountAssignment** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsKerberosAccountAssignment"}

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
<td><p>Kerberos 계정 할당을 제거할 사이트의 고유 식별자입니다. 이것은 Kerberos 계정 ID가 아니라 사이트 ID입니다(예: -Identity &quot;site:Redmond&quot;).</p></td>
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
<td><p>이 매개 변수가 있으면 심각한 오류를 제외한 모든 오류 메시지가 표시되지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment 개체입니다. **Remove-CsKerberosAccountAssignment** cmdlet은 Kerberos 계정 할당 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. **Remove-CsKerberosAccountAssignment** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)  
[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)  
[Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

