---
title: Get-CsStaticRoutingConfiguration
TOCTitle: Get-CsStaticRoutingConfiguration
ms:assetid: 94f126b4-b714-42ba-b9b6-81269634875f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398754(v=OCS.15)
ms:contentKeyID: 49304417
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsStaticRoutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용되는 고정 경로 구성 설정에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsStaticRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsStaticRoutingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 조직에서 사용 중인 모든 고정 경로 구성 컬렉션에 대한 정보를 반환합니다.

    Get-CsStaticRoutingConfiguration

## 예제 2

예제 2에서는 하나의 고정 경로 구성 컬렉션에 대한 정보가 반환됩니다. 이 컬렉션은 Identity가 service:Registrar:atl-cs-001.litwareinc.com입니다.

    Get-CsStaticRoutingConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com"

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 서비스 범위에 할당된 고정 경로 구성 컬렉션에 대한 정보를 반환합니다. 필터 값 "service:\*"는 ID가 문자열 값 "service:"로 시작하는 컬렉션에 대한 데이터만 반환하도록 제한합니다.

    Get-CsStaticRoutingConfiguration -Filter "service:*"

## 예제 4

예제 4에서는 조직에서 사용 중인 모든 고정 경로 구성 컬렉션에 대한 세부적인 경로 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsStaticRoutingConfiguration** cmdlet을 매개 변수 없이 호출하여 각 고정 경로 컬렉션에 대한 전체 정보를 반환합니다. 그런 다음 이 정보가 ExpandProperty 매개 변수를 사용하여 Route 속성 값을 "확장"하는 **Select-Object** cmdlet에 파이프됩니다. 속성을 확장하면 해당 속성 내에 포함된 모든 개체와 값이 읽기 쉬운 형태로 화면에 표시됩니다.

    Get-CsStaticRoutingConfiguration | Select-Object -ExpandProperty Route

## 예제 5

예제 5에 표시된 명령은 전화 URI(Uniform Resource Identifier)만 대조하도록 구성된 모든 고정 경로에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsStaticRoutingConfiguration** cmdlet을 매개 변수 없이 호출합니다. 이렇게 하면 고정 경로 구성 컬렉션과 여기에 연결된 경로가 모두 반환됩니다. 이 컬렉션은 **Select-Object** cmdlet에 파이프되며, 해당 cmdlet은 ExpandProperty 매개 변수를 사용하여 Route 속성에 저장된 모든 개체를 확장합니다. 이러한 경로 개체는 MatchOnlyPhoneUri 속성이 True와 같은 경로만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsStaticRoutingConfiguration | Select-Object -ExpandProperty Route | Where-Object {$_.MatchOnlyPhoneUri -eq $True}

## 자세한 정보

SIP 메시지를 누군가에게 보내는 경우 이 메시지는 배달되기 전에 여러 서브넷과 네트워크를 통과해야 할 수 있습니다. 메시지가 거치는 이러한 길을 일반적으로 경로라고 합니다. 네트워킹에는 동적 경로와 고정 경로의 두 가지 유형의 경로가 있습니다. 동적 경로의 경우 서버에서 알고리즘을 사용하여 메시지가 전달되어야 하는 다음 위치(다음 홉)를 확인합니다. 고정 경로의 경우 메시지 경로는 시스템 관리자에 의해 미리 결정됩니다. 메시지가 서버에 수신되면 서버는 메시지 주소를 확인한 다음 관리자가 미리 구성한 다음 홉 서버로 메시지를 전달합니다. 고정 경로를 제대로 구성한 경우에는 제시간에 정확하게 메시지를 전달하고 서버에 대한 오버헤드를 최소화할 수 있습니다. 고정 경로의 단점은 네트워크 실패 시 메시지가 동적으로 다시 경로 지정되지 않는다는 것입니다.

Lync Server를 설치하면 전역 고정 경로 컬렉션이 자동으로 만들어집니다. 컬렉션이 만들어지지만 이 컬렉션에 경로는 할당되지 않습니다. 또한 이 소프트웨어를 통해 서비스 범위에 적용되는 추가 컬렉션을 만들 수 있습니다. 이러한 새 컬렉션은 등록자 서비스에만 할당할 수 있습니다. **Get-CsStaticRoutingConfiguration** cmdlet은 조직에서 사용 중인 모든 고정 경로 구성 컬렉션에 대한 정보를 반환할 수 있는 수단을 제공합니다. 여기에는 컬렉션에 할당된 각 경로에 대한 세부 정보를 반환하는 기능도 포함됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsStaticRoutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsStaticRoutingConfiguration"}

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
<td><p>반환할 고정 경로 구성 컬렉션을 지정할 때 와일드카드를 사용할 수 있도록 합니다. 예를 들어 -Filter &quot;service:*&quot; 구문은 서비스 범위에 구성된 모든 고정 경로 컬렉션을 반환합니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>고정 경로 구성 컬렉션에 대한 고유 식별자입니다. 전역 컬렉션에 대한 정보를 반환하려면 -Identity global 구문을 사용합니다. 서비스 범위에 구성된 컬렉션에 대한 정보를 검색하려면 -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;과 같은 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 Filter 매개 변수를 대신 사용하십시오.</p>
<p>Identity 또는 Filter 매개 변수 중 하나를 포함하지 않으면 <strong>Get-CsStaticRoutingConfiguration</strong> cmdlet은 모든 고정 경로 구성 컬렉션에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 고정 경로 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsStaticRoutingConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsStaticRoutingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)  
[Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)  
[Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

