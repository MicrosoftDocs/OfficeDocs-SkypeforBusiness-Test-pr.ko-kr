---
title: Get-CsRegistrarConfiguration
TOCTitle: Get-CsRegistrarConfiguration
ms:assetid: 67f2caf6-84a8-46d8-b034-7161e9841ab8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398483(v=OCS.15)
ms:contentKeyID: 49303893
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsRegistrarConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용되고 있는 등록자 구성 설정에 대한 정보를 반환합니다. 등록자는 로그온 요청을 인증하고 사용자 상태에 대한 정보를 유지 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsRegistrarConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsRegistrarConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용되고 있는 모든 등록자 구성 설정의 컬렉션을 반환합니다.

    Get-CsRegistrarConfiguration

## 예제 2

예제 2에서는 등록자 구성 설정, 즉 Redmond 사이트(-Identity site:Redmond)에 대해 구성된 설정의 단일 컬렉션을 반환합니다.

    Get-CsRegistrarConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 서비스 범위에 할당된 모든 등록자 구성 설정에 대한 정보를 반환합니다. 이를 위해 명령은 Filter 매개 변수와 필터 값 "service:\*"를 사용합니다. 해당 필터 값은 문자열 값 "service:"으로 시작하는 ID를 가진 설정만 반환되도록 합니다.

    Get-CsRegistrarConfiguration -Filter "service:*"

## 예제 4

예제 4에서는 클라이언트를 등록하기 위해 DHCP 서버 사용을 활성화하는 등록자 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsRegistrarConfiguration** cmdlet을 매개 변수 없이 호출하여 현재 사용되고 있는 모든 등록자 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 EnableDHCPServer 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsRegistrarConfiguration | Where-Object {$_.EnableDHCPServer -eq $True}

## 예제 5

예제 5에서는 사용자당 9개 이상의 끝점을 허용하는 모든 등록자 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsRegistrarConfiguration** cmdlet을 사용하여 조직에서 사용되는 모든 등록자 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 MaxEndpointsPerUser 속성이 8보다 큰 설정을 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsRegistrarConfiguration | Where-Object {$_.MaxEndpointsPerUser -gt 8}

## 자세한 정보

등록자는 Lync Server의 가장 중요한 구성 요소라고 할 수 있습니다. 등록자 없이는 사용자가 시스템에 로그온할 수 없으며 Lync Server에서 사용자와 사용자의 현재 상태를 추적할 수 없기 때문입니다. 사용자가 Lync Server에 로그온하면 로그온한 끝점에서 등록자에 REGISTER 요청을 보냅니다. 그러면 서버에서 클라이언트 장치의 인증 자격 증명을 요구하여 응답합니다. 클라이언트가 이 요구를 충족하면, 즉 클라이언트에서 유효한 자격 증명 집합을 제공하면 사용자가 인증되고 IP 주소, 포트 및 사용자 이름과 같은 정보가 등록 데이터베이스에 로깅됩니다. 이 정보는 사용자가 로그오프하면 데이터베이스에서 제거됩니다. 로그온한 시점부터 로그오프할 때까지 등록자는 상태 정보를 최신 상태로 유지하면서 사용자가 주고받는 메시지의 경로 지정을 지원합니다.

등록자 구성 설정은 끝점과 끝점 구독을 관리하는 데 사용됩니다. 이러한 설정은 전역, 사이트 또는 서비스 범위에서 적용할 수 있습니다. 서비스 범위 설정은 등록자 서비스에만 사용할 수 있습니다. 조직에서 현재 사용되고 있는 모든 등록자 구성 컬렉션에 대한 정보를 반환하려면 **Get-CsRegistrarConfiguration** cmdlet을 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsRegistrarConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsRegistrarConfiguration"}

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
<td><p>와일드카드를 사용하여 등록자 구성 설정의 컬렉션을 하나 이상 반환하는 데 사용됩니다. 예를 들어 사이트 범위에서 구성된 모든 설정을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용합니다. 서비스 범위에서 구성된 모든 설정을 반환하려면 -Filter &quot;service:*&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 등록자 구성 설정의 고유 식별자입니다. 전역 설정을 반환하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 설정을 반환하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 반환하려면 -Identity service:Registrar:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다.</p>
<p>이 매개 변수를 생략하면 <strong>Get-CsRegistrarConfiguration</strong> cmdlet은 조직에서 현재 사용되고 있는 모든 등록자 구성 설정을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 등록자 구성 설정 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsRegistrarConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsRegistrarConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Registrar.RegistrarSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsRegistrarConfiguration](new-csregistrarconfiguration.md)  
[Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)  
[Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)

