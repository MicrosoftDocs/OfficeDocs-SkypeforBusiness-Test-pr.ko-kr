---
title: New-CsClientPolicyEntry
TOCTitle: New-CsClientPolicyEntry
ms:assetid: e975d048-4911-4ae6-9446-2a6363726a4a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399046(v=OCS.15)
ms:contentKeyID: 49305397
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClientPolicyEntry

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 클라이언트 정책에 새 옵션을 추가합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsClientPolicyEntry -Name <String> -Value <String>

## 예제

## 예제 1

예제 1에 표시된 명령은 새 정책 항목을 전역 클라이언트 정책에 추가하는 방법을 보여 줍니다. 이 예제는 새 사용자 의견 옵션을 Lync에 추가합니다. 이 예제는 참고용으로 제공됩니다. 이러한 명령을 실행하여 Lync에 유사한 사용자 의견 옵션을 추가할 수 있을 것으로 기대해서는 안 됩니다.

새 정책 항목을 추가하기 위해 이 예제의 첫 번째 명령은 **New-CsClientPolicyEntry** cmdlet을 사용하여 이름이 OnlineFeedbackURL이고 값이 http://www.litwareinc.com/feedback인 항목을 만듭니다. 결과 정책 항목 개체는 $x라는 변수에 저장됩니다.

두 번째 명령에서는 **Get-CsClientPolicy** cmdlet을 사용하여 전역 클라이언트 정책에 대한 개체 참조($y)를 만듭니다. 개체 참조를 만든 후에는 Add 메서드를 사용하여 PolicyEntry 속성에 새 정책 항목을 추가합니다. PolicyEntry에 하나 이상의 항목이 이미 있는 경우에는 해당 컬렉션의 끝에 새 값이 추가됩니다.

끝으로, 이 예제의 마지막 명령은 **Set-CsClientPolicy** cmdlet을 사용하여 실제 전역 정책에 변경 내용을 기록합니다. **Set-CsClientPolicy** cmdlet을 호출하지 않으면 변경 사항이 메모리에만 남아 있게 되고 Windows PowerShell 세션을 종료하거나 $x 변수를 삭제하자마자 사라집니다.

    $x = New-CsClientPolicyEntry -Name "OnlineFeedbackURL" -Value "http://www.litwareinc.com/feedback"
    
    $y = Get-CsClientPolicy -Identity global
    $y.PolicyEntry.Add($x)
    
    Set-CsClientPolicy -Instance $y

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 그러나 이 예제에서는 새 정책 항목이 현재 전역 정책의 PolicyEntry 속성에 있는 모든 항목을 대체합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 $x라는 변수에 저장되는 새 정책 항목을 만듭니다. 그런 다음 두 번째 명령에서 **Set-CsClientPolicy** cmdlet을 사용하여 PolicyEntry 속성 값을 $x로 설정합니다. 명령이 완료되면 PolicyEntry 속성에는 새 항목만 있게 됩니다 **Set-CsClientPolicy** cmdlet을 호출하기 전에 이 속성에 포함된 모든 항목은 새 항목으로 대체됩니다.

    $x = New-CsClientPolicyEntry -Name "OnlineFeedbackURL" -Value "http://www.litwareinc.com/feedback"
    Set-CsClientPolicy -Identity global -PolicyEntry $x

## 예제 3

예제 3은 전역 정책에서 클라이언트 정책 항목을 제거하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 전역 클라이언트 정책을 검색하고 해당 정보를 $y라는 변수에 저장합니다.

전역 정책이 검색되면 예제의 두 번째 명령이 RemoveAt() 메서드를 사용하여 해당 정책의 첫 번째 정책 항목을 삭제합니다. 제거할 정책 항목은 인덱스 번호로 표시됩니다. 첫 번째 항목에는 인덱스 번호 0이 있고, 두 번째 정책 항목에는 인덱스 번호 1이 있는 식입니다. RemoveAt(0) 구문은 첫 번째 정책 항목이 제거된다는 의미입니다.

정책 항목이 전역 정책의 메모리에만 나타나는 인스턴스에서 제거되자 마자 **Set-CsClientPolicy** cmdlet을 호출하여 전역 클라이언트 정책의 실제 인스턴스에 이러한 변경 내용을 기록합니다.

    $y = Get-CsClientPolicy -Identity global
    $y.PolicyEntry.RemoveAt(0)
    
    Set-CsClientPolicy -Instance $y 

## 예제 4

예제 4에 표시된 명령은 전역 정책에 대해 구성된 모든 클라이언트 정책 항목을 제거합니다. 이 작업을 수행하기 위해 PolicyEntry 매개 변수를 사용하여 매개 변수 값을 null($Null)로 설정합니다.

    Set-CsClientPolicy -Identity global -PolicyEntry $Null

## 자세한 정보

클라이언트 정책은 Lync Server에서 Lync와 같은 클라이언트 소프트웨어를 관리하는 데 사용하는 기본 메커니즘입니다. 클라이언트 정책을 만들거나 구성할 때 여러 가지 옵션을 사용할 수 있습니다. 예를 들어 Lync에서 사진을 사용할지 여부, 메신저 대화에 이모티콘을 허용할지 여부, Lync에서 메신저 대화 세션의 대화 내용을 자동으로 저장할지 여부 등을 지정할 수 있습니다. 이러한 옵션에는 관리자가 관리해야 하는 클라이언트 관련 설정의 많은 부분이 포함되어 있습니다.

그러나 이 옵션에 포함되지 않은 관리자가 관리해야 클라이언트 설정이 있을 수 있습니다. 관리의 유연성과 확장성을 높이기 위해 클라이언트 정책에는 PolicyEntry라는 속성이 포함되어 있습니다. 이 다중값 속성을 통해 관리자는 클라이언트 정책에 명시적으로 나타나지 않은 새 관리 옵션을 추가할 수 있습니다. 예를 들어 Lync Server를 릴리스하기 전에 베타 테스터에게 Lync에 사용자 의견 옵션을 추가할 수 있는 기능이 제공되었습니다. 이 옵션은 **New-CsClientPolicyEntry** cmdlet을 사용하여 만들었으며 새 정책 항목으로 추가되었습니다.

새 정책 항목을 임의로 만들고 이러한 항목이 Lync 또는 다른 클라이언트 응용 프로그램을 관리할 것으로 기대해서는 안 됩니다. 대신 새 클라이언트 정책 항목을 작성하는 데 사용할 수 있는 이름 및 값과 관련한 Microsoft의 통지를 기다려야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsClientPolicyEntry** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientPolicyEntry"}

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
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 정책 항목의 이름입니다(예: -Name &quot;OnlineFeedbackURL&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Value</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 정책 항목에 할당할 값입니다(예: -Value http://www.litwareinc.com/feedback).</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. New-CsClientPolicyEntry cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsClientPolicyEntry** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Client.PolicyEntryType 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsClientPolicy](new-csclientpolicy.md)  
[Set-CsClientPolicy](set-csclientpolicy.md)

