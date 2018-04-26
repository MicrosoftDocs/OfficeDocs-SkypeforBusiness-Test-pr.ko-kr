---
title: Remove-CsTestUserCredential
TOCTitle: Remove-CsTestUserCredential
ms:assetid: 49290251-276d-41d5-bcfd-077018d74f59
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204870(v=OCS.15)
ms:contentKeyID: 49303538
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsTestUserCredential

 

_**마지막으로 수정된 항목:** 2015-03-09_

감시자 노드 테스트 사용자로 구성된 사용자 집합에서 지정한 사용자를 제거합니다. 감시자 노드는 주기적으로 Microsoft System Center Operations Manager 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsTestUserCredential -SipAddress <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 SIP 주소가 sip:kenmyer@litwareinc.com인 사용자를 감시자 노드 테스트 사용자로 구성된 사용자의 컬렉션에서 제거합니다.

    Remove-CsTestUserCredential "sip:kenmyer@litwareinc.com"

## 예제 2

예제 2에 표시된 명령은 감시자 노드 테스트 사용자로 구성된 모든 사용자를 제거합니다. 이렇게 해도 사용자 계정이 삭제되지는 않으며 단순히 감시자 노드 테스트 사용자 상태만 삭제됩니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 Windows PowerShell $ErrorActionPreference 변수 값을 "SilentlyContinue"로 설정합니다. 그러면 **Remove-CsTestUserCredential** cmdlet에서 감시자 노드 테스트 사용자로 구성되지 않은 사용자로부터 테스트 자격 증명을 제거하려 할 때마다 표시되는 오류 메시지가 표시되지 않습니다.

오류 메시지가 표시되지 않도록 설정되면 예제의 두 번째 명령은 **Get-CsUser** cmdlet을 사용하여 Lync Server 2013을 사용할 수 있도록 설정된 모든 사용자의 컬렉션을 반환합니다. 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. **ForEach-Object** cmdlet은 컬렉션의 각 사용자 계정을 순환하며 각 계정에 대해 **Remove-CsTestUserCredential** cmdlet을 실행하여 감시자 노드 테스트 사용자를 제거합니다.

예제의 마지막 명령은 $ErrorActionPreference의 값을 "Continue"로 다시 설정합니다.

    $ErrorActionPreference = "SilentlyContinue"
    
    Get-CsUser | ForEach-Object {Remove-CsTestUserCredential -SipAddress $_.SipAddress}
    
    $ErrorActionPreference = "Continue"

## 자세한 정보

System Center Operations Manager를 Lync Server 2013과 함께 사용 중인 경우에는 "감시자 노드" 컴퓨터를 구성할 수 있습니다. 감시자 노드는 가상 트랜잭션을 주기적으로 자동 실행하는 컴퓨터입니다. 가상 트랜잭션이란 다양한 Lync Server 기능을 테스트하는 cmdlet입니다. 사용자가 Lync Server에 등록할 수 있는지, Lync Server를 사용하여 메신저 대화 및 현재 상태 정보를 교환할 수 있는지, 데이터 공동 작업 및 응용 프로그램 공유 회의를 진행할 수 있는지, 그리고 공중 전화망을 통한 전화 통화를 할 수 있는지를 확인하는 가상 트랜잭션을 예로 들 수 있습니다. 앞에서도 언급한 것처럼 이러한 가상 트랜잭션은 주기적으로 실행되며 실패하는 경우 시스템에 문제가 있을 수 있음을 관리자에게 알리는 경고를 발급합니다.

대부분의 가상 트랜잭션에서는 테스트 사용자가 필요합니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 있는지를 테스트하려면 사용자 계정 한 쌍이 있어야 하며 해당 계정을 사용하여 메신저 대화 교환을 시도해야 합니다. 감시자 노드를 구성할 때는 해당 노드에 두 명 이상의 테스트 사용자를 할당해야 합니다. 이러한 테스트 사용자는 Lync Server 2013을 사용할 수 있도록 설정되었으며 테스트 계정으로 등록된 모든 유효한 Active Directory 사용자 계정일 수 있습니다. [Set-CsTestUserCredential](set-cstestusercredential.md) cmdlet을 사용하여 계정을 테스트 계정으로 등록합니다. 나중에 특정 계정을 테스트 계정으로 사용하지 않으려는 경우에는 **Remove-CsTestUserCredential** cmdlet을 사용하여 계정 등록을 취소하면 됩니다. 이 cmdlet은 단순히 계정을 감시자 노드 테스트 계정으로 사용할 수 없도록 지정할 뿐 계정을 삭제 또는 수정하거나 사용하지 않도록 설정하지는 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsTestUserCredential"}

**Lync Server 제어판:** **Remove-CsTestUserCredential** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>SipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>해당 테스트 사용자 자격 증명을 제거할 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-SipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p></td>
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

없음. **Remove-CsTestUserCredential** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Remove-CsTestUserCredential** cmdlet은 System.Management.Automation.PSCredential 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTestUserCredential](get-cstestusercredential.md)  
[Set-CsTestUserCredential](set-cstestusercredential.md)

