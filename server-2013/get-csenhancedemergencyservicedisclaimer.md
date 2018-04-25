---
title: Get-CsEnhancedEmergencyServiceDisclaimer
TOCTitle: Get-CsEnhancedEmergencyServiceDisclaimer
ms:assetid: b5e3a01e-4056-47a0-9c3c-efdf55a08f69
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412877(v=OCS.15)
ms:contentKeyID: 49304795
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsEnhancedEmergencyServiceDisclaimer

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 9-1-1) 구현을 위한 위치 정보를 묻는 메시지를 표시하는 데 전역적으로 사용되는 고지 사항 텍스트를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsEnhancedEmergencyServiceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsEnhancedEmergencyServiceDisclaimer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 명령은 고급 응급 서비스 고지 사항 텍스트를 검색합니다.

    Get-CsEnhancedEmergencyServiceDisclaimer

## 자세한 정보

Enterprise Voice 구현에서 E9-1-1 서비스를 제공하려면 발신자의 위치를 식별할 수 있도록 포트, 서브넷, 스위치 및 무선 액세스 지점에 위치를 매핑해야 합니다. 발신자가 이러한 매핑된 지점 중 하나의 외부에서 연결한 경우 응급 서비스를 받으려면 자신의 위치를 수동으로 입력해야 합니다. 이 cmdlet은 위치 정보를 입력하지 않기로 결정한 사용자에게 표시할 텍스트 문자열을 검색합니다. 이 메시지는 사용자 위치 정책의 LocationRequired 속성이 Disclaimer로 설정된 경우에만 표시됩니다. 위치 정책 설정은 **Get-CsLocationPolicy** cmdlet을 호출하여 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsEnhancedEmergencyServiceDisclaimer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsEnhancedEmergencyServiceDisclaimer"}

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
<td><p>이 매개 변수를 사용하면 ID에 대한 와일드카드 검색을 수행할 수 있습니다. 그러나 Identity에 사용할 수 있는 유일한 값이 Global이므로 이 매개 변수는 이 cmdlet에 유용하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>이 값은 항상 Global입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 고지 사항 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsEnhancedEmergencyServiceDisclaimer](remove-csenhancedemergencyservicedisclaimer.md)  
[Set-CsEnhancedEmergencyServiceDisclaimer](set-csenhancedemergencyservicedisclaimer.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)

