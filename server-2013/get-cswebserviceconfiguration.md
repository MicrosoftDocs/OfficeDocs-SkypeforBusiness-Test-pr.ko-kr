---
title: Get-CsWebServiceConfiguration
TOCTitle: Get-CsWebServiceConfiguration
ms:assetid: 28582668-839c-4b04-8211-928c91634672
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425751(v=OCS.15)
ms:contentKeyID: 49303118
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsWebServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 모든 웹 서비스 구성 설정에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsWebServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsWebServiceConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 현재 사용 중인 모든 웹 서비스 구성 설정에 대한 정보를 반환합니다.

    Get-CsWebServiceConfiguration

## 예제 2

예제 2에 표시된 명령은 ID가 site:Redmond인 웹 서비스 구성 설정에 대한 정보를 반환합니다.

    Get-CsWebServiceConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 사이트 범위에 할당된 모든 웹 서비스 구성 설정을 반환합니다. 이 작업을 수행하기 위해 **Get-CsWebServiceConfiguration** cmdlet을 호출할 때 Filter 매개 변수를 포함합니다. 필터 값 "site:\*"는 ID가 "site:" 문자열 값으로 시작하는 설정만 반환되도록 합니다.

    Get-CsWebServiceConfiguration -Filter "site:*"

## 예제 4

예제 4에서는 개인식별번호(PIN) 인증을 허용하지 않는 모든 웹 서비스 구성 설정을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsWebServiceConfiguration** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 웹 서비스 구성 설정을 반환합니다. 이 컬렉션은 UsePinAuth 속성이 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsWebServiceConfiguration | Where-Object {$_.UsePinAuth -eq $False}

## 예제 5

예제 5에서는 최대 그룹 확장 크기가 100보다 큰 모든 웹 서비스 구성 설정을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsWebServiceConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 웹 서비스 구성 설정을 반환합니다. 그런 다음 이 정보는 MaxGroupSizeToExpand 속성이 100보다 큰 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsWebServiceConfiguration | Where-Object {$_.MaxGroupSizeToExpand -gt 100}

## 자세한 정보

많은 Lync Server 구성 요소가 웹에 기반을 두고 있습니다. 이러한 구성 요소는 웹 서비스 또는 웹 페이지를 사용하여 작업을 수행합니다. 예를 들어 사용자는 주소록에서 새 연락처를 검색하거나 그룹 확장을 사용하여 메일 그룹의 개별 구성원을 볼 때 웹 서비스를 사용합니다. 마찬가지로 전화 접속 회의부터 Lync Server 제어판에 이르는 구성 요소는 Lync Server와 사용자 간의 인터페이스로 웹 페이지를 사용합니다.

**CsWebServiceConfiguration** cmdlet을 통해 관리자는 조직 전체의 웹 서비스 구성 설정을 관리할 수 있습니다. 여기에는 그룹 확장, 인증서 설정 및 허용되는 인증 방법 관리가 포함됩니다. 전역, 사이트 및 서비스(웹 서비스에만 해당) 범위에 여러 설정을 구성할 수 있으므로 다양한 사용자 및 위치에 대해 웹 서비스 기능을 사용자 지정할 수 있습니다.

**Get-CsWebServiceConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 웹 서비스 구성 설정에 대한 자세한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsWebServiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsWebServiceConfiguration"}

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
<td><p>반환할 웹 서비스 구성 설정 컬렉션을 지정할 때 와일드카드를 활용하는 데 사용됩니다. 예를 들어 -Filter &quot;site:*&quot; 구문은 사이트 범위에서 구성된 모든 설정을 -Filter &quot;site:*&quot; 구문을 사용하고,</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 웹 서비스 구성 설정의 고유 식별자입니다. 전역 설정을 반환하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 설정을 반환하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위 설정은 -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용하여 반환할 수 있습니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다. 두 매개 변수를 모두 지정하지 않은 경우 <strong>Get-CsWebServiceConfiguration</strong> cmdlet은 조직에서 현재 사용 중인 모든 웹 서비스 설정 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 웹 서비스 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsWebServiceConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsWebServiceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Web.WebServiceSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)  
[Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

