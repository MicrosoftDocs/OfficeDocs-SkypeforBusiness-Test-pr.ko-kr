---
title: Get-CsTestUserCredential
TOCTitle: Get-CsTestUserCredential
ms:assetid: 2af8d526-005c-40fb-957c-5b2ee5bce432
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204759(v=OCS.15)
ms:contentKeyID: 49303141
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTestUserCredential

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 감시자 노드 테스트 사용자로 구성되었는지 여부를 알려 주는 정보를 반환합니다. 감시자 노드는 주기적으로 Microsoft System Center Operations Manager 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsTestUserCredential -SipAddress <String>

## 예제

## 예제 1

예제 1에 표시된 명령은 sip:kenmyer@litwareinc.com 사용자가 감시자 노드 테스트 사용자로 구성된 경우 해당 사용자에 대한 정보를 반환합니다. 사용자가 테스트 사용자로 구성되지 않은 경우 **Get-CsTestUserCredential** cmdlet은 오류를 반환합니다.

    Get-CsTestUserCredential -SipAddress "sip:kenmyer@litewareinc.com"

## 예제 2

예제 2에 표시된 명령은 감시자 노드 테스트 사용자로 구성된 모든 사용자의 목록을 반환합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 Windows PowerShell 명령줄 인터페이스 $ErrorActionPreference 변수 값을 "SilentlyContinue"로 설정합니다. 그러면 **Get-CsTestUserCredential** cmdlet에서 감시자 노드 테스트 사용자로 구성되지 않은 사용자에 대한 테스트 사용자 정보를 반환하려 할 때 표시되는 오류 메시지가 표시되지 않습니다.

오류 메시지가 표시되지 않는 상태에서 예제의 두 번째 명령은 **Get-CsUser** cmdlet을 사용하여 Lync Server 2013에 대해 설정된 모든 사용자의 컬렉션을 반환합니다. 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. **ForEach-Object** cmdlet은 컬렉션의 각 사용자 계정을 순환하면서 각 계정에 대해 **Get-CsTestUserCredential** cmdlet을 실행하여 사용자가 테스트 사용자로 구성되었는지를 확인합니다. 사용자가 테스트 사용자로 구성된 경우에는 해당 사용자에 대한 정보가 화면에 표시되고 그렇지 않은 경우에는 화면에 아무 정보도 표시되지 않습니다.

예제의 마지막 명령은 $ErrorActionPreference의 값을 "Continue"로 다시 설정합니다.

    $ErrorActionPreference = "SilentlyContinue"
    Get-CsUser | ForEach-Object {Get-CsTestUserCredential -SipAddress $_.SipAddress}
    $ErrorActionPreference = "Continue"

## 자세한 정보

System Center Operations Manager를 Lync Server 2013과 함께 사용 중인 경우에는 "감시자 노드" 컴퓨터를 구성할 수 있습니다. 감시자 노드는 가상 트랜잭션을 주기적으로 자동 실행하는 컴퓨터입니다. 가상 트랜잭션이란 다양한 Lync Server 기능을 테스트하는 cmdlet입니다. 사용자가 Lync Server에 등록할 수 있는지, Lync Server를 사용하여 메신저 대화 및 현재 상태 정보를 교환할 수 있는지, 데이터 공동 작업 및 응용 프로그램 공유 회의를 진행할 수 있는지, 그리고 공중 전화망을 통한 전화 통화를 할 수 있는지를 확인하는 가상 트랜잭션을 예로 들 수 있습니다. 앞에서도 언급한 것처럼 이러한 가상 트랜잭션은 주기적으로 실행되며 실패하는 경우 시스템에 문제가 있을 수 있음을 관리자에게 알리는 경고를 발급합니다.

대부분의 가상 트랜잭션에서는 테스트 사용자가 필요합니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 있는지를 테스트하려면 사용자 계정 한 쌍이 있어야 하며 해당 계정을 사용하여 메신저 대화 교환을 시도해야 합니다. 감시자 노드를 구성할 때는 해당 노드에 두 명 이상의 테스트 사용자를 할당해야 합니다. 이러한 테스트 사용자는 Lync Server 2013에서 사용할 수 있도록 설정되었으며 테스트 계정으로 등록된 모든 유효한 Active Directory 사용자 계정일 수 있습니다. [Set-CsTestUserCredential](set-cstestusercredential.md) cmdlet을 사용하여 계정을 테스트 계정으로 등록합니다. 나중에 특정 계정을 테스트 계정으로 사용하지 않으려는 경우에는 [Remove-CsTestUserCredential](remove-cstestusercredential.md) cmdlet을 사용하여 계정 등록을 취소하면 됩니다. 이 cmdlet은 단순히 계정을 감시자 노드 테스트 계정으로 사용할 수 없도록 지정할 뿐 계정을 삭제 또는 수정하거나 사용하지 않도록 설정하지는 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsTestUserCredential"}

**Lync Server 제어판:** **Get-CsTestUserCredential** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>테스트 사용자 자격 증명을 확인할 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-SipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p><strong>Get-CsTestUserCredential</strong> cmdlet을 호출할 때는 SipAddress 매개 변수를 포함해야 합니다. 그렇지 않으면 해당 주소를 입력하라는 메시지가 표시됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsTestUserCredential** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsTestUserCredential** cmdlet은 System.Management.Automation.PSCredential 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsTestUserCredential](remove-cstestusercredential.md)  
[Set-CsTestUserCredential](set-cstestusercredential.md)

