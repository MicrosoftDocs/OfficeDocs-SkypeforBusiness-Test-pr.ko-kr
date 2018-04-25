---
title: Get-CsKerberosAccountAssignment
TOCTitle: Get-CsKerberosAccountAssignment
ms:assetid: 6eaba274-1693-42a7-841d-513bc1153647
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398526(v=OCS.15)
ms:contentKeyID: 49303975
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsKerberosAccountAssignment

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 Kerberos 계정 할당에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsKerberosAccountAssignment [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsKerberosAccountAssignment [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 Kerberos 계정 할당에 대한 정보를 반환합니다.

    Get-CsKerberosAccountAssignment

## 예제 2

예제 2에서는 Redmond 사이트의 계정 할당인 단일 Kerberos 계정 할당에 대한 정보를 반환합니다.

    Get-CsKerberosAccountAssignment -Identity "site:Redmond"

## 예제 3

예제 3에서는 사이트 ID에 문자열 값 "Redmond"가 포함된 사이트에 할당된 모든 Kerberos 계정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 필터 값 "\*Redmond"와 함께 Filter 매개 변수를 포함합니다.

    Get-CsKerberosAccountAssignment -Filter "*Redmond*"

## 예제 4

예제 4에서는 할당된 계정의 ID에 문자열 값 "litwareinc"가 포함된 모든 Kerberos 계정 할당에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsKerberosAccountAssignment** cmdlet을 호출합니다. 그러면 현재 사용 중인 모든 Kerberos 계정 할당 컬렉션이 반환됩니다. 이 컬렉션은 계정의 ID에 문자열 값 "litwareinc"가 포함된 계정 할당만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 매개 변수 이름은 UserAccount지만, 이 계정은 실제로 컴퓨터 계정입니다.

    Get-CsKerberosAccountAssignment | Where-Object {$_.UserAccount -match "litwareinc"}

## 자세한 정보

Microsoft Office Communications Server 2007 및 Microsoft Office Communications Server 2007 R2에서는 IIS가 표준 사용자 계정으로 실행되었습니다. 이로 인해 문제가 발생할 수 있었습니다. 즉, 이 암호가 만료되어 웹 서비스의 연결이 끊어진 경우 진단하기 어려운 문제가 발생합니다. 암호 만료 문제를 피하는 데 도움이 되도록 Lync Server에서는 IIS를 실행하는 사이트의 모든 컴퓨터에 대한 인증 주체 역할을 할 수 있는 컴퓨터 계정(실제로는 존재하지 않는 컴퓨터에 대해)을 만들 수 있습니다. 이러한 계정은 Kerberos 인증 프로토콜을 사용하므로 Kerberos 계정이라고 하며, 새로운 인증 프로세스를 Kerberos 웹 인증이라고 합니다. 이를 통해 단일 계정으로 모든 IIS 서버를 관리할 수 있습니다.

이 새 인증 주체로 서버를 실행하려면 먼저 **New-CsKerberosAccount** cmdlet을 사용하여 컴퓨터 계정을 만들어야 합니다. 그러면 이 계정이 하나 이상의 사이트에 할당됩니다. 계정이 할당된 후에는 **Enable-CsTopology** cmdlet을 실행하여 계정과 Lync Server 사이트 간의 연결을 활성화합니다. 이렇게 하면 필요한 SPN(서비스 사용자 이름)이 Active Directory 도메인 서비스에 만들어집니다. 클라이언트 응용 프로그램은 SPN을 통해 특정 서비스를 찾을 수 있습니다.

**Get-CsKerberosAccountAssignment** cmdlet을 사용하면 조직에서 현재 사용 중인 Kerberos 계정 할당에 대한 정보를 가져올 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsKerberosAccountAssignment** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsKerberosAccountAssignment"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 Kerberos 계정 할당을 지정할 때 와일드카드 문자를 사용하는 데 사용됩니다. 예를 들어 -Filter &quot;*Europe*&quot; 구문은 문자열 값 &quot;Europe&quot;이 포함된 모든 계정 할당을 반환합니다.</p>
<p>Identity 매개 변수와 Filter 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Kerberos 계정이 할당된 사이트의 고유 식별자입니다(예: -Identity &quot;site:Redmond&quot;). 이것은 컴퓨터 계정 ID가 아니라 사이트 ID입니다. 사이트 ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용하려면 Filter 매개 변수를 대신 사용합니다.</p>
<p>Identity 및 Filter 매개 변수를 둘 다 포함하지 않은 경우 <strong>Get-CsKerberosAccountAssignment</strong> cmdlet은 조직에서 사용하도록 구성된 모든 Kerberos 계정 할당을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 Kerberos 할당 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsKerberosAccountAssignment** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsKerberosAccountAssignment** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.KerberosAccount.KerberosAccountAssignment 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)  
[Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)  
[Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

