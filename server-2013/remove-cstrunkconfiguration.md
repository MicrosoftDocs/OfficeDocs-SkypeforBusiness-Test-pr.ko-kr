---
title: Remove-CsTrunkConfiguration
TOCTitle: Remove-CsTrunkConfiguration
ms:assetid: 45546534-1a18-4db2-be61-850bacf55a52
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425943(v=OCS.15)
ms:contentKeyID: 49303487
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsTrunkConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

PSTN(공중 전화망) 게이트웨이, IP-PBX(Public Branch Exchange) 또는 SBC(세션 경계 컨트롤러)와 같은 서비스 공급자 쪽 트렁크 피어 엔터티에 대한 설정을 설명하는 기존 트렁크 구성을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsTrunkConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 site:Redmond인 트렁크 구성을 제거합니다.

    Remove-CsTrunkConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 수준에 정의된 모든 트렁크 구성을 제거합니다. 명령의 첫 번째 부분은 Filter 매개 변수를 사용하는 **Get-CsTrunkConfiguration** cmdlet을 호출하여 ID가 site:로 시작하는 모든 트렁크 구성을 검색합니다. 즉, 사이트 수준에 정의된 모든 트렁크 구성을 검색합니다. 그런 다음 구성의 컬렉션은 컬렉션의 각 개체를 제거하는 **Remove-CsTrunkConfiguration** cmdlet에 파이프됩니다.

    Get-CsTrunkConfiguration -Filter site:* | Remove-CsTrunkConfiguration

## 자세한 정보

이 cmdlet을 사용하여 PSTN 게이트웨이 엔터티에 적용 가능한 트렁크 구성을 제거할 수 있습니다. 각 구성은 PSTN 게이트웨이, IP-PBX 또는 SBC와 같은 서비스 공급자 쪽 트렁크 피어 엔터티에 대한 특정 설정을 포함합니다. 이러한 설정은 이 트렁크에서 미디어 우회를 사용하도록 설정할지 여부, 특정 상황에서 RTCP(Real-time Transmission Control Protocol) 패킷을 보낼지 여부, SRTP(Secure Real-Time Protocol) 암호화를 요구할지 여부 등을 구성합니다.

전역 구성에 대해 **Remove-CsTrunkConfiguration** cmdlet을 호출하더라도 해당 트렁크 구성이 제거되지는 않습니다. 대신 구성이 "다시 설정"되고 모든 사용자 지정 설정이 기본값으로 대체됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsTrunkConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsTrunkConfiguration"}

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
<td><p>제거할 트렁크 구성의 고유한 식별자입니다.</p></td>
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
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration 개체입니다. 트렁크 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrunkConfiguration](new-cstrunkconfiguration.md)  
[Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)  
[Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)

