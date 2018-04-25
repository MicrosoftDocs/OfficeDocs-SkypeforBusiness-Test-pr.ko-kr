---
title: Set-CsKerberosAccountPassword
TOCTitle: Set-CsKerberosAccountPassword
ms:assetid: 837292b9-3c08-4c3c-a49d-3f9492518ddd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398659(v=OCS.15)
ms:contentKeyID: 49304232
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsKerberosAccountPassword

 

_**마지막으로 수정된 항목:** 2015-03-09_

Kerberos 계정이 할당된 사이트에서 웹 서비스를 실행하는 각 웹 서버를 찾은 다음 이러한 각 서버에서 IIS(인터넷 정보 서비스) 구성 설정을 업데이트합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsKerberosAccountPassword -UserAccount <String> <COMMON PARAMETERS>

    Set-CsKerberosAccountPassword -FromComputer <Fqdn> -ToComputer <Fqdn> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Kerberos 계정 litwareinc\\kerberostest에 대해 암호를 설정합니다.

    Set-CsKerberosAccountPassword -UserAccount "litwareinc\kerberostest"

## 예제 2

예제 2에서는 atl-cs-001.litwareinc.com 컴퓨터에서 dublin-cs-001.litwareinc.com 컴퓨터로 Kerberos 계정 암호를 복사합니다.

    Set-CsKerberosAccountPassword -FromComputer "atl-cs-001.litwareinc.com" -ToComputer "dublin-cs-001.litwareinc.com"

## 자세한 정보

Microsoft Office Communications Server 2007 및 Microsoft Office Communications Server 2007 R2에서는 IIS가 표준 사용자 계정으로 실행되었습니다. 이로 인해 문제가 발생할 수 있었습니다. 즉, 이 암호가 만료되어 웹 서비스의 연결이 끊어진 경우 진단하기 어려운 문제가 발생합니다. 암호 만료 문제를 피하는 데 도움이 되도록 Lync Server에서는 IIS를 실행하는 사이트의 모든 컴퓨터에 대한 인증 주체 역할을 할 수 있는 컴퓨터 계정(실제로는 존재하지 않는 컴퓨터에 대해)을 만들 수 있습니다. 이러한 계정은 Kerberos 인증 프로토콜을 사용하므로 Kerberos 계정이라고 하며, 새로운 인증 프로세스를 Kerberos 웹 인증이라고 합니다. 이를 통해 단일 계정으로 모든 IIS 서버를 관리할 수 있습니다.

이 새 인증 주체로 서버를 실행하려면 먼저 **New-CsKerberosAccount** cmdlet을 사용하여 컴퓨터 계정을 만들어야 합니다. 그러면 이 계정이 하나 이상의 사이트에 할당됩니다. 계정이 할당된 후에는 **Enable-CsTopology** cmdlet을 실행하여 계정과 Lync Server 사이트 간의 연결을 활성화합니다. 이렇게 하면 필요한 SPN(서비스 사용자 이름)이 Active Directory 도메인 서비스에 만들어집니다. 클라이언트 응용 프로그램은 SPN을 통해 특정 서비스를 찾을 수 있습니다.

새 연결이 설정되고 나면 **Set-CsKerberosAccountPassword** cmdlet은 계정에 할당된 암호를 수정하고, 더 중요한 점은 Kerberos 웹 인증에 지정된 Kerberos 테스트 계정을 사용하는 모든 컴퓨터에서 암호를 업데이트할 수 있는 방법을 제공합니다.

또한 이 cmdlet은 ToComputer 및 FromComputer 매개 변수를 사용하여 이 구성 정보를 한 컴퓨터에서 다른 컴퓨터로 복사할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsKerberosAccountPassword** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsKerberosAccountPassword"}

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
<td><p><em>FromComputer</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>다른 컴퓨터에 복사할 Kerberos 계정의 암호를 포함하는 컴퓨터의 FQDN(정규화된 도메인 이름)입니다. UserAccount 매개 변수를 사용하는 경우 이 매개 변수를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ToComputer</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Kerberos 계정 암호를 복사할 컴퓨터의 FQDN입니다. UserAccount 매개 변수를 사용하는 경우 이 매개 변수를 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserAccount</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>암호를 변경해야 하는 계정의 계정 이름입니다.changed. 이 계정 이름은 도메인_이름\사용자_이름형식을 사용해야 합니다(예: -UserAccount &quot;litwareinc\kerberostest&quot;).</p>
<p>이름은 UserAccount지만 계정은 실제로 사용자 계정이 아니라 컴퓨터 계정입니다.</p></td>
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
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다. -Report &quot;C:\Logs\SetKerberosPassword.html&quot;.</p></td>
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

없음.

## 반환 형식

**Set-CsKerberosAccountPassword** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccount 개체의 기존 인스턴스를 수정합니다.

