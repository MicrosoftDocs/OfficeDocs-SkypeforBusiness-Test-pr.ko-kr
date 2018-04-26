---
title: New-CsKerberosAccount
TOCTitle: New-CsKerberosAccount
ms:assetid: 67ffa1b1-0ca5-410b-81f7-2375b9dbef3c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398485(v=OCS.15)
ms:contentKeyID: 49303899
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsKerberosAccount

 

_**마지막으로 수정된 항목:** 2015-03-09_

IIS(인터넷 정보 서비스) 인증에 사용되는 새 Kerberos 계정을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsKerberosAccount -UserAccount <String> [-Confirm [<SwitchParameter>]] [-ContainerDN <String>] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 두 명령은 새 Kerberos 계정(litwareinc\\kerberostest)을 만든 다음 이 계정을 Redmond 사이트에 할당합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 계정 이름이 "litwareinc\\kerberostest"인 계정을 만듭니다. 이 계정은 Litwareinc.com domain의 Computers 컨테이너에 만들어집니다. 계정이 생성된 후 두 번째 명령은 **New-CsKerberosAccountAssignment** cmdlet을 사용하여 해당 Kerberos 계정을 Redmond 사이트에 할당합니다.

새 계정을 할당한 후 마지막 명령은 **Enable-CsTopology** cmdlet을 호출하여 변경 내용을 활성화합니다.

    New-CsKerberosAccount -UserAccount "litwareinc\kerberostest" -ContainerDN "cn=Computers,dc=litwareinc,dc=com"
    
    New-CsKerberosAccountAssignment -UserAccount "litwareinc\kerberostest" -Identity "site:Redmond"
    Enable-CsTopology

## 자세한 정보

Microsoft Office Communications Server 2007 및 Microsoft Office Communications Server 2007 R2에서는 IIS가 표준 사용자 계정으로 실행되었습니다. 이로 인해 문제가 발생할 수 있었습니다. 즉, 이 암호가 만료되어 웹 서비스의 연결이 끊어진 경우 진단하기 어려운 문제가 발생합니다. 암호 만료 문제를 피하는 데 도움이 되도록 Lync Server에서는 IIS를 실행하는 사이트의 모든 컴퓨터에 대한 인증 주체 역할을 할 수 있는 컴퓨터 계정(실제로는 존재하지 않는 컴퓨터에 대해)을 만들 수 있습니다. 이러한 계정은 Kerberos 인증 프로토콜을 사용하므로 Kerberos 계정이라고 하며, 새로운 인증 프로세스를 Kerberos 웹 인증이라고 합니다. 이를 통해 단일 계정으로 모든 IIS 서버를 관리할 수 있습니다.

이 인증 주체로 서버를 실행하려면 먼저 **New-CsKerberosAccount** cmdlet을 사용하여 컴퓨터 계정을 만들어야 합니다. 그러면 이 계정이 하나 이상의 사이트에 할당됩니다. 계정이 할당된 후에는 **Enable-CsTopology** cmdlet을 실행하여 계정과 Lync Server 사이트 간의 연결을 활성화합니다. 이렇게 하면 필요한 SPN(서비스 사용자 이름)이 Active Directory 도메인 서비스에 만들어집니다. 클라이언트 응용 프로그램은 SPN을 통해 특정 서비스를 찾을 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: **New-CsKerberosAccount** cmdlet을 로컬로 실행하려면 도메인 관리자여야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsKerberosAccount\\b"}

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
<td><p><em>UserAccount</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>format 도메인_이름\사용자_이름 형식을 사용하는 새 계정의 계정 이름입니다((예: -UserAccount &quot;litwareinc\kerberostest&quot;). 지정한 계정이 이미 있는 경우 명령이 실패합니다.</p>
<p>이름은 UserAccount지만 <strong>New-CsKerberosAccount</strong> cmdlet을 실행하여 만든 계정은 실제로 사용자 계정이 아니라 컴퓨터 계정입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ContainerDN</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 계정이 생성되는 Active Directory 컨테이너의 고유 이름입니다(예: -ContainerDN &quot;ou=Finance,dc=litwareinc,dc=com&quot;). 이 매개 변수를 지정하지 않으면 <strong>New-CsKerberosAccount</strong> cmdlet이 Active Directory의 Computers 컨테이너에 새 계정을 만듭니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다(예: -Report &quot;C:\Logs\KerberosAccount.html&quot;).</p></td>
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

없음. **New-CsKerberosAccount** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsKerberosAccount** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccount 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)

