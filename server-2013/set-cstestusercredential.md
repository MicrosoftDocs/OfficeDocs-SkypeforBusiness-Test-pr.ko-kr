---
title: Set-CsTestUserCredential
TOCTitle: Set-CsTestUserCredential
ms:assetid: e613fad9-e91b-4bce-a67d-b1c9860ab34d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205341(v=OCS.15)
ms:contentKeyID: 49305357
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTestUserCredential

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 감시자 노드 테스트 사용자를 만듭니다. 감시자 노드는 주기적으로 Microsoft System Center Operations Manager 2007 R2 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsTestUserCredential -Credential <PSCredential> <COMMON PARAMETERS>

    Set-CsTestUserCredential -Password <String> -UserName <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -SipAddress <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 SIP 주소가 sip:kenmyer@litwareinc.com인 사용자를 감시자 노드 테스트 사용자로 구성합니다. 계정을 감시자 노드 테스트 사용자로 구성할 때는 사용자 이름(도메인 이름\\사용자 이름 형식) 및 사용자 암호도 제공해야 합니다.

    Set-CsTestUserCredential -SipAddress "sip:kenmyer@litwareinc.com" -UserName "litwareinc\kenmyer" -Password "07Apples"

## 예제 2

위의 예제에 표시된 명령도 SIP 주소가 sip:kenmyer@litwareinc.com인 사용자를 감시자 노드 테스트 사용자로 구성합니다. 그러나 이 예제에서는 UserName 및 Password 매개 변수 대신 Credential 매개 변수를 사용합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 litwareinc\\kenmyer 계정에 대해 Windows PowerShell 명령줄 인터페이스 자격 증명 개체를 만듭니다. 해당 자격 증명 개체는 $x 변수에 저장됩니다. 자격 증명 개체를 만들 때 litwareinc\\kenmyer 계정의 암호를 제공해야 합니다. 예제의 두 번째 명령은 Credential 매개 변수 및 매개 변수 값 $x를 사용하여 테스트 자격 증명을 구성합니다.

    $x = Get-Credential "litwareinc\kenmyer"
    
    Set-CsTestUserCredential -SipAddress "sip:kenmyer@litwareinc.com" -Credential $x

## 자세한 정보

System Center Operations Manager를 Lync Server 2013과 함께 사용 중인 경우에는 "감시자 노드" 컴퓨터를 구성할 수 있습니다. 감시자 노드는 가상 트랜잭션을 주기적으로 자동 실행하는 컴퓨터입니다. 가상 트랜잭션이란 다양한 Lync Server 기능을 테스트하는 cmdlet입니다. 사용자가 Lync Server에 등록할 수 있는지, Lync Server를 사용하여 메신저 대화 및 현재 상태 정보를 교환할 수 있는지, 데이터 공동 작업 및 응용 프로그램 공유 회의를 진행할 수 있는지, 그리고 공중 전화망을 통한 전화 통화를 할 수 있는지를 확인하는 가상 트랜잭션을 예로 들 수 있습니다. 앞에서도 언급한 것처럼 이러한 가상 트랜잭션은 주기적으로 실행되며 실패하는 경우 시스템에 문제가 있을 수 있음을 관리자에게 알리는 경고를 발급합니다.

대부분의 가상 트랜잭션에서는 테스트 사용자가 필요합니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 있는지를 테스트하려면 사용자 계정 한 쌍이 있어야 하며 해당 계정을 사용하여 메신저 대화 교환을 시도해야 합니다. 감시자 노드를 구성할 때는 해당 노드에 두 명 이상의 테스트 사용자를 할당해야 합니다. 이러한 테스트 사용자는 Lync Server 2013에서 사용할 수 있도록 설정되었으며 테스트 계정으로 등록된 모든 유효한 Active Directory 사용자 계정일 수 있습니다. **Set-CsTestUserCredential** cmdlet을 사용하여 계정을 테스트 계정으로 등록합니다. 나중에 특정 계정을 테스트 계정으로 사용하지 않으려는 경우에는 [Remove-CsTestUserCredential](remove-cstestusercredential.md) cmdlet을 사용하여 계정 등록을 취소하면 됩니다. 이 cmdlet은 단순히 계정을 감시자 노드 테스트 계정으로 사용할 수 없도록 지정할 뿐 계정을 삭제 또는 수정하거나 사용하지 않도록 설정하지는 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsTestUserCredential"}

**Lync Server 제어판:** **Set-CsTestUserCredential** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Credential</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>Password 및 UserName 매개 변수가 아닌 Windows PowerShell 자격 증명 개체를 사용하여 테스트 자격 증명을 구성할 수 있습니다. 이 경우 사용자 암호를 화면에 입력할 때 암호가 마스킹된다는 장점이 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만든 다음 해당 개체를 변수에 저장해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 변수는 Credential 매개 변수의 매개 변수 값으로 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Password</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>해당 테스트 사용자 자격 증명을 설정할 계정의 암호입니다. 이 암호는 화면에 일반 텍스트로 표시됩니다. 예를 들면 다음과 같습니다.</p>
<p>-Password &quot;p@ssw0rd&quot;</p>
<p>Credential 매개 변수를 사용하는 경우에는 Password 또는 UserName 매개 변수를 사용할 필요가 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>해당 테스트 사용자 자격 증명을 설정할 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-SipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>UserName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>테스트 자격 증명을 구성할 계정의 사용자 이름입니다. 사용자 이름은 SamAccountName 또는 Active Directory DisplayName일 수 있습니다. 예를 들면 다음과 같습니다.</p>
<p>-UserName &quot;Ken Myer&quot;</p>
<p>도메인 이름\사용자 이름 형식을 사용하여 UserName을 지정할 수도 있습니다. 예를 들면 다음과 같습니다.</p>
<p>-UserName &quot;litwareinc\kenmyer&quot;</p></td>
</tr>
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
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Set-CsTestUserCredential** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Set-CsTestUserCredential** cmdlet은 System.Management.Automation.PSCredential 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTestUserCredential](get-cstestusercredential.md)  
[Remove-CsTestUserCredential](remove-cstestusercredential.md)

