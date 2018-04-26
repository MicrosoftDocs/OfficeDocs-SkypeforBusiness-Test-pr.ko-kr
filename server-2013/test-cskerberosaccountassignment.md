---
title: Test-CsKerberosAccountAssignment
TOCTitle: Test-CsKerberosAccountAssignment
ms:assetid: 442bbb32-7ad1-40c4-bf17-42ecde0a7286
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425938(v=OCS.15)
ms:contentKeyID: 49303471
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsKerberosAccountAssignment

 

_**마지막으로 수정된 항목:** 2015-03-09_

사이트에 할당된 Kerberos 계정의 구성을 확인합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsKerberosAccountAssignment -Identity <XdsIdentity> [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 할당된 Kerberos 계정이 제대로 구성되고 예상대로 작동하고 있는지 확인합니다.

    Test-CsKerberosAccountAssignment -Identity site:Redmond

## 자세한 정보

Microsoft Office Communications Server 2007 및 Microsoft Office Communications Server 2007 R2에서는 IIS가 표준 사용자 계정으로 실행되었습니다. 이로 인해 문제가 발생할 수 있었습니다. 즉, 이 암호가 만료되어 웹 서비스의 연결이 끊어진 경우 진단하기 어려운 문제가 발생합니다. 암호 만료 문제를 피하는 데 도움이 되도록 Lync Server에서는 IIS를 실행하는 사이트의 모든 컴퓨터에 대한 인증 주체 역할을 할 수 있는 컴퓨터 계정(실제로는 존재하지 않는 컴퓨터에 대해)을 만들 수 있습니다. 이러한 계정은 Kerberos 인증 프로토콜을 사용하므로 Kerberos 계정이라고 하며, 새로운 인증 프로세스를 Kerberos 웹 인증이라고 합니다. 이를 통해 단일 계정으로 모든 IIS 서버를 관리할 수 있습니다.

**Test-CsKerberosAccountAssignment** cmdlet은 Kerberos 계정이 지정된 사이트와 연결되었는지, 이 계정이 제대로 구성되었는지, 계정이 예상대로 작동하는지를 확인하기 위한 방법을 제공합니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsKerberosAccountAssignment"}

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
<td><p>Kerberos 계정이 할당된 사이트의 이름입니다(예: -Identity &quot;site:Redmond&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다.(예: -Report &quot;C:\Logs\TestKerberos.html&quot;).</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsKerberosAccountAssignment** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsKerberosAccountAssignment** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)  
[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)  
[Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)  
[Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

