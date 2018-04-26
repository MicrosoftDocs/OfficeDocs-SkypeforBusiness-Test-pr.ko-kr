---
title: Remove-CsWebServiceConfiguration
TOCTitle: Remove-CsWebServiceConfiguration
ms:assetid: 1df2f881-6594-4de7-9762-8d64b2243355
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398266(v=OCS.15)
ms:contentKeyID: 49302996
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsWebServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

웹 서비스 구성 설정 컬렉션을 하나 이상 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsWebServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대한 웹 서비스 구성 설정을 제거합니다.

    Remove-CsWebServiceConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 범위에서 구성된 모든 웹 서비스 설정이 제거됩니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsWebServiceConfiguration** cmdlet 및 Filter 매개 변수를 호출합니다. 필터 값 "site:\*"는 Identity가 site: 문자로 시작하는 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsWebServiceConfiguration** cmdlet에 파이프됩니다.

    Get-CsWebServiceConfiguration -Filter "site:*" | Remove-CsWebServiceConfiguration

## 예제 3

예제 3에 표시된 명령은 그룹 확장이 비활성화된 모든 웹 서비스 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsWebServiceConfiguration** cmdlet을 호출하여 조직에서 사용된 모든 웹 서비스 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 EnableGroupExpansion 속성이 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsWebServiceConfiguration** cmdlet에 파이프됩니다.

    Get-CsWebServiceConfiguration | Where-Object {$_.EnableGroupExpansion -eq $False} | Remove-CsWebServiceConfiguration

## 자세한 정보

많은 Lync Server 구성 요소가 웹에 기반을 두고 있습니다. 이러한 구성 요소는 웹 서비스 또는 웹 페이지를 사용하여 작업을 수행합니다. 예를 들어 사용자는 주소록에서 새 연락처를 검색하거나 그룹 확장을 사용하여 메일 그룹의 개별 구성원을 볼 때 웹 서비스를 사용합니다. 마찬가지로 전화 접속 회의부터 Lync Server 제어판에 이르는 구성 요소는 Lync Server와 사용자 간의 인터페이스로 웹 페이지를 사용합니다.

**CsWebServiceConfiguration** cmdlet을 사용하면 관리자가 조직 전체의 웹 서비스 구성 설정을 관리할 수 있습니다. 여기에는 그룹 확장, 인증서 설정 및 허용되는 인증 방법 관리가 포함됩니다. 전역, 사이트 및 서비스(웹 서버 서비스로 제한) 범위에 여러 설정을 구성할 수 있으므로 다양한 사용자 및 위치에 대해 웹 서비스 기능을 사용자 지정할 수 있습니다.

사이트 또는 서비스 범위에서 사용자 지정 웹 서비스 구성 설정을 만든 경우 나중에 **Remove-CsWebServiceConfiguration** cmdlet을 사용하여 이러한 설정을 제거할 수 있습니다. 전역 웹 서비스 설정 컬렉션에 대해 **Remove-CsWebServiceConfiguration** cmdlet을 실행할 수도 있습니다. 그러나 이 경우 Lync Server에서 전역 설정 제거를 허용하지 않으므로 전역 컬렉션이 제거되지 않습니다. 대신, 전역 컬렉션의 모든 속성이 기본값으로 돌아갑니다. 예를 들어 MaxGroupSizeToExpand 값을 500으로 변경했다고 가정해 보십시오. 이 속성의 기본값은 100이므로 전역 컬렉션을 "제거"하면 MaxGroupSizeToExpand 속성의 값이 100으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsWebServiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsWebServiceConfiguration"}

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
<td><p>제거할 웹 서비스 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 구성된 설정을 제거하려면 -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다.</p>
<p>전역 컬렉션에 대해 <strong>Remove-CsWebServiceConfiguration</strong> cmdlet을 실행할 수도 있습니다. 그러나 이 경우 전역 컬렉션이 제거되는 것이 아니라 해당 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다. 전역 컬렉션을 다시 설정하려면 -Identity global 구문을 사용합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings 개체입니다. **Remove-CsWebServiceConfiguration** cmdlet은 웹 서비스 설정 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsWebServiceConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)  
[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

