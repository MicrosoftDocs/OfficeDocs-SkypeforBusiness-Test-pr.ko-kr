---
title: Get-CsClientPolicy
TOCTitle: Get-CsClientPolicy
ms:assetid: c8e1cb96-2bf7-447c-b41c-d896fe85e349
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398830(v=OCS.15)
ms:contentKeyID: 49305011
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClientPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 클라이언트 정책에 대한 정보를 반환합니다. 특히 클라이언트 정책은 사용자가 사용할 수 있는 Lync 기능을 결정하는 데 도움이 됩니다. 예를 들어 일부 사용자에게는 파일 전송 권한을 부여하고 다른 사용자에 대해서는 이 권한을 거부할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsClientPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClientPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 추가 매개 변수 없이 **Get-CsClientPolicy** cmdlet을 호출합니다. 그러면 조직에서 사용하도록 구성된 모든 클라이언트 정책 컬렉션이 반환됩니다.

    Get-CsClientPolicy

## 예제 2

예제 2에서는 **Get-CsClientPolicy** cmdlet을 사용하여 ID가 SalesPolicy인 사용자별 클라이언트 정책을 반환합니다. ID는 고유하므로 이 명령은 두 개 이상의 항목을 반환하지 않습니다.

    Get-CsClientPolicy -Identity SalesPolicy

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 사용자별 범위에서 구성된 모든 클라이언트 정책을 반환합니다. 필터 값 "tag:\*"는 ID가 문자열 값 "tag:"으로 시작하는 정책만 반환하도록 **Get-CsClientPolicy** cmdlet에 지시합니다.

    Get-CsClientPolicy -Filter "tag:*"

## 예제 4

예제 4에서는 DisableSavingIM 속성이 True인 모든 클라이언트 정책 컬렉션을 반환합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsClientPolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 클라이언트 정책 컬렉션을 반환합니다. 이 컬렉션은 DisableSavingIM 속성이 True와 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsClientPolicy | Where-Object {$_.DisableSavingIM -eq $True}

## 예제 5

예제 5에서는 DisableSavingIM 속성이 True이고 EnableIMAutoArchiving 속성이 False여야 한다는 두 가지 조건을 충족하는 클라이언트 정책만 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClientPolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 클라이언트 정책 컬렉션을 반환합니다. 이 컬렉션은 DisableSavingIM이 True와 같고 EnableIMAutoArchiving이 False와 같아야 한다는 두 조건을 모두 충족하는 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. -and 연산자는 지정된 조건을 모두 충족하는 개체만 선택하도록 **Where-Object** cmdlet에 지시합니다.

    Get-CsClientPolicy | Where-Object {$_.DisableSavingIM -eq $True -and $_.EnableIMAutoArchiving -eq $False}

## 예제 6

예제 6은 예제 5에 표시된 명령의 변형입니다. 그러나 이 예제에서는 DisableSavingIM 속성이 True인 조건과 EnableIMAutoArchiving 속성이 False인 조건 중 하나 또는 둘 다를 충족하는 정책을 선택합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClientPolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 클라이언트 정책 컬렉션을 반환합니다. 이 컬렉션은 DisableSavingIM이 True와 같다는 조건과 EnableIMAutoArchiving이 False와 같다는 조건 중 하나 또는 둘 다를 충족하는 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. -or 연산자는 지정된 조건 중 하나 이상을 충족하는 개체를 선택하도록 **Where-Object** cmdlet에 지시합니다.

## 자세한 정보

Lync Server에서는 이전 버전의 제품에서 사용된 그룹 정책 설정 대신 클라이언트 정책을 사용합니다. Microsoft Office Communicator 2007 및 Microsoft Office Communicator 2007 R2에서는 Communicator 및 기타 클라이언트로 사용자가 수행할 수 있는 작업을 결정할 때 그룹 정책을 사용했습니다. 예를 들어 사용자가 메신저 대화 세션의 대화 내용을 저장할 수 있는지 여부, Microsoft Outlook의 정보를 상태 정보로 통합할지 여부, 사용자가 메신저 대화에 이모티콘이나 서식 있는 텍스트를 포함할 수 있는지 여부 등을 결정하는 그룹 정책 설정이 있었습니다.

그룹 정책은 유용하지만 Lync Server에 적용할 때 몇 가지 기술적인 제한이 있습니다. 우선, 그룹 정책은 도메인별 또는 OU(조직 구성 단위)별로 적용하도록 설계되었기 때문에 보다 선별적인 사용자 그룹(예: 특정 부서에서 근무하는 모든 사용자나 특정 직책의 모든 사용자)에 적용하기 어렵습니다. 둘째, 그룹 정책은 도메인에 로그온하는 사용자 및 컴퓨터를 사용하여 로그온하는 사용자에게만 적용됩니다. 인터넷을 통해 시스템에 액세스하거나 휴대폰을 사용하여 시스템에 액세스하는 사용자에게는 그룹 정책이 적용되지 않습니다. 따라서 로그온하는 데 사용한 장치 및 로그온한 위치에 따라 동일한 사용자에게 다른 환경이 제공될 수 있습니다.

이러한 불일치를 해결하기 위해 Lync Server에서는 그룹 정책 대신 클라이언트 관리 정책을 사용합니다. 클라이언트 정책은 로그온한 위치 및 로그온하는 데 사용한 장치 유형에 관계없이 사용자가 시스템에 액세스할 때마다 적용됩니다. 또한 다른 Lync Server 정책과 마찬가지로 클라이언트 정책을 언제든지 선택한 사용자 그룹으로 지정할 수 있을 뿐만 아니라 단일 사용자에게 할당되는 사용자 지정 정책을 만들 수도 있습니다.

클라이언트 정책은 전역, 사이트 및 사용자별 범위에서 구성할 수 있습니다. **Get-CsClientPolicy** cmdlet을 사용하면 조직에서 사용하도록 구성된 모든 클라이언트 정책에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsClientPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClientPolicy"}

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
<td><p>반환할 정책을 지정할 때 와일드카드 문자를 활용하는 데 사용됩니다. 예를 들어 사이트 범위에서 구성된 모든 정책을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용하고, 모든 사용자별 정책 컬렉션을 반환하려면 -Filter &quot;tag:*&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 클라이언트 정책의 고유 식별자입니다. 전역 정책을 참조하려면 -Identity global 구문을 사용하고, 사이트 정책을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 사용자별 정책을 참조하려면 -Identity SalesDepartmentPolicy와 같은 구문을 사용합니다.</p>
<p>이 매개 변수가 없으면 조직에서 사용하도록 구성된 모든 클라이언트 정책이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 클라이언트 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsClientPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsClientPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Client.ClientPolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsClientPolicy](grant-csclientpolicy.md)  
[New-CsClientPolicy](new-csclientpolicy.md)  
[Remove-CsClientPolicy](remove-csclientpolicy.md)  
[Set-CsClientPolicy](set-csclientpolicy.md)

