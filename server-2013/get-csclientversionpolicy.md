---
title: Get-CsClientVersionPolicy
TOCTitle: Get-CsClientVersionPolicy
ms:assetid: d99bfa89-01a7-4dd4-8f6e-96e0a84ab1ce
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398957(v=OCS.15)
ms:contentKeyID: 49305205
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClientVersionPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자의 Lync Server 환경에서 지원되는 클라이언트(예: Microsoft Office Communicator 2007 R2)에 대한 정보를 반환합니다. 클라이언트 버전 정책을 사용하면 Lync Server 시스템에 로그온할 수 있는 클라이언트(예: Office Communicator 2007 R2)를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsClientVersionPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClientVersionPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

첫 번째 예제에서는 추가 매개 변수를 지정하지 않고 **Get-CsClientVersionPolicy** cmdlet을 호출합니다. 그러면 **Get-CsClientVersionPolicy** cmdlet이 조직에서 사용하도록 구성된 모든 클라이언트 버전 정책 컬렉션을 반환합니다.

    Get-CsClientVersionPolicy

## 예제 2

예제 2에서 **Get-CsClientVersionPolicy** cmdlet은 ID가 site:Redmond인 모든 클라이언트 버전 정책을 반환합니다. ID는 고유해야 하므로 이 명령은 두 개 이상의 항목을 반환하지 않습니다.

    Get-CsClientVersionPolicy -Identity site:Redmond

## 예제 3

예제 3에서는 사이트 범위에서 구성된 모든 클라이언트 버전 정책을 반환합니다. 이 작업을 수행하려면 Filter 매개 변수와 필터 값 "site:\*"를 포함하면 됩니다. 이 필터 값은 ID가 문자열 값 "site:"으로 시작하는 정책만 반환하도록 **Get-CsClientVersionPolicy** cmdlet에 지시합니다.

    Get-CsClientVersionPolicy -Filter site:*

## 예제 4

예제 4에 사용된 명령은 각 클라이언트 버전 정책에 대해 구성된 개별 규칙에 대한 자세한 정보를 표시합니다. 이 작업을 수행하기 위해 먼저 **Get-CsClientVersionPolicy** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 클라이언트 버전 정책 컬렉션을 검색합니다. 이 컬렉션은 ExpandProperty 필터를 사용하여 Rules 속성의 속성 값을 확장하는 **Select-Object** cmdlet에 파이프됩니다. 이 속성을 확장하면 각 규칙에 대한 자세한 정보(예: 빌드 번호, 주 번호 및 부 번호와 같은 속성 값)가 화면에 표시됩니다.

    Get-CsClientVersionPolicy | Select-Object -ExpandProperty Rules

## 자세한 정보

클라이언트 버전 정책은 클라이언트 버전 규칙 컬렉션을 나타내고, 클라이언트 버전 규칙은 Lync Server에 로그온할 수 있는 클라이언트 응용 프로그램을 지정하는 데 사용됩니다. 사용자가 Lync Server에 로그온하려고 하면 클라이언트 응용 프로그램이 서버에 SIP 헤더를 전송합니다. 이 헤더에는 소프트웨어의 주 버전, 부 버전, 빌드 번호 등 응용 프로그램 자체에 대한 자세한 정보가 포함되어 있습니다. 그런 다음 SIP 헤더에 포함된 버전 정보에서 클라이언트 버전 규칙 컬렉션을 검사하여 특정 응용 프로그램에 적용되는 규칙이 있는지 확인합니다. 이러한 규칙이 있으면 Lync Server에서 해당 규칙에 의해 지정된 작업을 수행합니다. 예를 들어 로그온을 허용 또는 차단하거나 로그온을 허용하되 클라이언트 응용 프로그램을 최신 버전으로 자동 업그레이드(예: Communicator 2007 R2dptj Lync으로 업그레이드)하도록 Lync Server에 지시하는 규칙이 있을 수 있습니다.

전역 범위, 사이트 범위, 서비스 범위(등록자 서비스) 또는 사용자별 범위에서 적용할 수 있는 클라이언트 버전 정책을 통해 시스템에 액세스하는 데 사용할 수 있는 클라이언트 응용 프로그램을 유동적으로 결정할 수 있습니다. 예를 들어 Lync Server가 Lync 2013과 동일한 요소 및 기능을 지원하지 않기 때문에 사용자가 Communicator 2007 R2를 사용하여 이러한 이전 버전의 클라이언트 응용 프로그램에 로그온하지 못하게 하려는 경우가 있습니다. 그러나 하드웨어 또는 소프트웨어 충돌로 인해 Lync로 업그레이드할 수 없는 사용자 그룹이 있을 수도 있습니다. 이 경우 해당 사용자가 Communicator 2007 R2 내에서 로그온하도록 하는 별도의 규칙과 별도의 클라이언트 버전 정책을 만들 수 있습니다.

**Get-CsClientVersionPolicy** cmdlet을 사용하면 조직에서 현재 사용 중인 모든 클라이언트 버전 정책을 검색하고 각 정책을 구성하는 개별 규칙을 볼 수 있습니다.

클라이언트 버전 정책은 페더레이션 사용자에게 적용되지 않습니다. 대신 페더레이션 사용자에게는 조직에서 사용되는 클라이언트 버전 정책이 적용됩니다. 예를 들어 페더레이션 사용자가 클라이언트 A를 사용하고, 이 클라이언트가 페더레이션 조직에서 허용된다고 가정해 보겠습니다. 페더레이션 조직에서 클라이언트 A 사용을 허용하는 한 이 사용자는 해당 클라이언트를 사용하여 조직과 통신할 수 있습니다. 이는 클라이언트 버전 정책이 클라이언트 A 사용을 차단하는 경우에도 마찬가지입니다. 조직에서 시행되는 클라이언트 버전 정책은 페더레이션 조직에서 사용되는 클라이언트 버전 정책을 무시하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsClientVersionPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClientVersionPolicy\\b"}

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
<td><p>검색할 정책을 지정할 때 와일드카드 문자를 사용하는 데 사용됩니다. 예를 들어 -Filter &quot;site:*&quot; 구문은 사이트 범위에서 구성된 모든 정책을 반환하고, -Filter &quot;tag:*&quot; 구문은 사용자별 범위에서 구성된 모든 정책을 반환합니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 정책의 고유 식별자입니다. 전역 정책을 반환하려면 -Identity global 구문을 사용하고, 사이트 범위에 구성된 정책을 반환하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용하고, 서비스 범위에서 구성된 정책을 반환하려면 -Identity &quot;Registrar:atl-cs-001.litwareinc.com&quot;과 같은 구문을 사용하십시오. 등록자 서비스는 클라이언트 버전 정책을 호스트할 수 있는 유일한 서비스입니다.</p>
<p>사용자별 범위에서 정책이 구성될 수도 있습니다. 이러한 정책 중 하나를 반환하려면 -Identity &quot;SalesDepartmentPolicy&quot;와 유사한 구문을 사용합니다.</p>
<p>이 매개 변수를 포함하지 않으면 조직에서 사용하도록 구성된 모든 클라이언트 버전 정책이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 클라이언트 버전 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsClientVersionPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsClientVersionPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersion 정책 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsClientVersionPolicy](grant-csclientversionpolicy.md)  
[New-CsClientVersionPolicy](new-csclientversionpolicy.md)  
[Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md)  
[Set-CsClientVersionPolicy](set-csclientversionpolicy.md)

