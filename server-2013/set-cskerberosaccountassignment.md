---
title: Set-CsKerberosAccountAssignment
TOCTitle: Set-CsKerberosAccountAssignment
ms:assetid: 16a964d2-2515-4a37-9686-3e377de58b14
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398232(v=OCS.15)
ms:contentKeyID: 49302926
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsKerberosAccountAssignment

 

_**마지막으로 수정된 항목:** 2015-03-09_

IIS(인터넷 정보 서비스) 인증에 사용되는 Kerberos 계정을 사이트와 연결합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsKerberosAccountAssignment [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsKerberosAccountAssignment [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-UserAccount <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 기존 Kerberos 계정(litwareinc\\keberostest)을 Redmond 사이트와 연결한 다음 **Enable-CsTopology** cmdlet을 사용하여 새 연결을 설정합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Set-CsKerberosAccountAssignment** cmdlet을 사용하여 litwareinc\\keberostest 계정을 Redmond 사이트와 연결합니다. 두 번째 명령은 Active Directory에 필요한 서비스 사용자 이름을 만들고, 이와 동시에 수정된 계정 할당을 설정하기 위해 **Enable-CsTopology** cmdlet을 호출합니다.

    Set-CsKerberosAccountAssignment -UserAccount "litwareinc\keberostest" -Identity "site:Redmond"
    Enable-CsTopology

## 자세한 정보

Microsoft Office Communications Server 2007 및 Microsoft Office Communications Server 2007 R2에서는 IIS가 표준 사용자 계정으로 실행되었습니다. 이로 인해 문제가 발생할 수 있었습니다. 즉, 이 암호가 만료되어 웹 서비스의 연결이 끊어진 경우 진단하기 어려운 문제가 발생합니다. 암호 만료 문제를 피하는 데 도움이 되도록 Lync Server에서는 IIS를 실행하는 사이트의 모든 컴퓨터에 대한 인증 주체 역할을 할 수 있는 컴퓨터 계정(실제로는 존재하지 않는 컴퓨터에 대해)을 만들 수 있습니다. 이러한 계정은 Kerberos 인증 프로토콜을 사용하므로 Kerberos 계정이라고 하며, 새로운 인증 프로세스를 Kerberos 웹 인증이라고 합니다. 이를 통해 단일 계정으로 모든 IIS 서버를 관리할 수 있습니다.

이 새 인증 주체로 서버를 실행하려면 먼저 **New-CsKerberosAccount** cmdlet을 사용하여 컴퓨터 계정을 만들어야 합니다. 그러면 이 계정이 하나 이상의 사이트에 할당됩니다. 계정이 할당된 후에는 **Enable-CsTopology** cmdlet을 실행하여 계정과 Lync Server 사이트 간의 연결을 활성화합니다. 이렇게 하면 필요한 SPN(서비스 사용자 이름)이 Active Directory 도메인 서비스에 만들어집니다. 클라이언트 응용 프로그램은 SPN을 통해 특정 서비스를 찾을 수 있습니다.

**Set-CsKerberosAccountAssignment** cmdlet을 사용하면 지정된 사이트에 할당된 Kerberos 계정을 변경할 수 있습니다. 이 cmdlet은 계정과 이미 연결되어 있는 사이트에 사용됩니다. 현재 Kerberos 계정과 연결되어 있지 않은 사이트에 계정을 할당하려면 **New-CsKerberosAccountAssignment** cmdlet을 대신 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsKerberosAccountAssignment** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsKerberosAccountAssignment"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Kerberos 계정이 할당된 사이트의 고유 식별자입니다. 이것은 컴퓨터 계정 ID가 아니라 사이트 ID입니다(예: -Identity &quot;site:Redmond&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>KerberosAccountAssignment 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserAccount</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>도메인_이름\사용자_이름 형식을 사용하여 할당할 계정의 계정 이름입니다(예: -UserAccount &quot;litwareinc\kerberostest&quot;). 계정의 사용자 이름 부분(kerberostest)은 NETBIOS 이름이며 최대 15자를 포함할 수 있습니다.</p>
<p>이름은 UserAccount지만 계정은 실제로 사용자 계정이 아니라 컴퓨터 계정입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment 개체입니다. **Set-CsKerberosAccountAssignment** cmdlet은 Kerberos 계정 할당 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsKerberosAccountAssignment** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)  
[New-CsKerberosAccount](new-cskerberosaccount.md)  
[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)  
[Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)

