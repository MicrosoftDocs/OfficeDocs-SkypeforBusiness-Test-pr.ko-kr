---
title: Get-CsTrunkConfiguration
TOCTitle: Get-CsTrunkConfiguration
ms:assetid: 15951113-5f96-4f44-8cad-9ff97fb5dfd6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398224(v=OCS.15)
ms:contentKeyID: 49302906
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTrunkConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

PSTN(공중 전화망) 게이트웨이, IP-PBX(Public Branch Exchange) 또는 SBC(세션 경계 컨트롤러)와 같은 서비스 공급자 쪽 트렁크 피어 엔터티에 대한 설정을 설명하는 하나 이상의 트렁크 구성을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsTrunkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsTrunkConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 Lync Server 배포에 대한 모든 트렁크 구성을 검색합니다.

    Get-CsTrunkConfiguration

## 예제 2

이 예제에서는 ID가 site:Redmond인 트렁크 구성을 검색합니다. ID는 고유하므로 이 명령은 개체를 하나 이하로 반환합니다.

    Get-CsTrunkConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 사이트 수준에 정의된 모든 트렁크 구성을 검색합니다. **Get-CsTrunkConfiguration** cmdlet은 Filter 매개 변수를 사용하여 ID가 site:로 시작하는 모든 트렁크 구성을 검색하며, 이에 따라 사이트 수준에 정의된 모든 트렁크 구성이 검색됩니다.

    Get-CsTrunkConfiguration -Filter site:*

## 자세한 정보

이 cmdlet을 사용하여 PSTN 게이트웨이 엔터티에 적용 가능한 트렁크 구성을 하나 이상 검색할 수 있습니다. 각 구성은 PSTN 게이트웨이, IP-PBX 또는 SBC와 같은 서비스 공급자 쪽 트렁크 피어 엔터티에 대한 특정 설정을 포함합니다. 이러한 설정은 이 트렁크에서 미디어 우회를 사용하도록 설정할지 여부, 특정 상황에서 RTCP(Real-time Transmission Control Protocol) 패킷을 보낼지 여부, SRTP(Secure Real-Time Protocol) 암호화를 요구할지 여부 등을 구성합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsTrunkConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsTrunkConfiguration"}

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
<td><p>이 매개 변수에는 와일드카드 문자열이 허용되며 해당 문자열과 일치하는 ID를 가진 모든 트렁크 구성이 반환됩니다. 예를 들어 Filter 값 site:*는 사이트 수준에서 정의된 모든 트렁크 구성을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 트렁크 구성의 고유한 식별자입니다. 트렁크 구성은 전역 범위, 사이트 범위 또는 PSTN 게이트웨이 서비스에 대한 서비스 범위에 정의할 수 있습니다. site:Redmond(사이트의 경우) 또는 PstnGateway:Redmond.litwareinc.com(서비스의 경우)을 예로 들 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 트렁크 구성을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrunkConfiguration](new-cstrunkconfiguration.md)  
[Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)  
[Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)  
[Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)

