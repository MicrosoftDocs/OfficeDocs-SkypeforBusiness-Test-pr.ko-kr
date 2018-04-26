---
title: Test-CsTrunkConfiguration
TOCTitle: Test-CsTrunkConfiguration
ms:assetid: 07f2ef04-49aa-4857-b213-fa98506c0427
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398137(v=OCS.15)
ms:contentKeyID: 49302715
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsTrunkConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 번호에 대한 트렁크 구성의 유효성을 검사합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsTrunkConfiguration -TrunkConfiguration <TrunkConfiguration> [-CallingNumber <PhoneNumber>] [-DialedNumber <PhoneNumber>]

## 예제

## 예제 1

이 예제에서는 Redmond 사이트에 대해 정의된 트렁크 구성을 테스트합니다. 이 예제의 첫째 줄에서는 **Get-CsTrunkConfiguration** cmdlet을 호출하여 Redmond 사이트에 대한 구성(ID가 site:Redmond인 구성)을 검색합니다. 검색된 트렁크 구성 개체는 $tc 변수에 할당됩니다.

둘째 줄에서는 테스트할 전화 번호를 DialedNumber 매개 변수에 전달하고 첫째 줄에서 검색한 트렁크 구성($tc에 저장됨)을 TrunkConfiguration 매개 변수에 전달하여 **Test-CsTrunkConfiguration** cmdlet을 호출합니다.

    $tc = Get-CsTrunkConfiguration -Identity Site:Redmond
    Test-CsTrunkConfiguration -DialedNumber 4255551212 -TrunkConfiguration $tc

## 자세한 정보

이 cmdlet을 사용하여 트렁크 구성이 전화 건 번호에 대해 예상대로 작동하는지 확인할 수 있습니다. 각 구성은 중재 서버와 서비스 공급자 쪽 PSTN(공중 전화망) 게이트웨이, IP-PBX(Public Branch Exchange) 또는 SBC(세션 경계 컨트롤러) 간의 관계 및 기능을 정의하는 특정 설정을 포함합니다. 이러한 설정은 이 트렁크에서 미디어 우회를 사용하도록 설정할지 여부, 특정 상황에서 RTCP(Real-time Transmission Control Protocol) 패킷을 보낼지 여부, SRTP(Secure Real-Time Protocol) 암호화를 요구할지 여부 등을 구성합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsTrunkConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsTrunkConfiguration"}

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
<td><p><em>TrunkConfiguration</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration</p></td>
<td><p>테스트를 실행할 트렁크 구성 개체에 대한 참조입니다. <strong>Get-CsTrunkConfiguration</strong> cmdlet을 호출하여 트렁크 구성 개체를 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CallingNumber</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
<td><p>지정하는 경우 지정된 전화 번호에 일치하는 아웃바운드 변환 규칙을 반환합니다. 예를 들면 다음과 같습니다.</p>
<p>-CallingNumber &quot;tel:+14255551219&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>DialedNumber</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
<td><p>구성을 테스트할 전화 번호입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration 개체입니다. 트렁크 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.Voice.TrunkConfigurationTestResult 유형의 값을 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrunkConfiguration](new-cstrunkconfiguration.md)  
[Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)  
[Set-CsTrunkConfiguration](set-cstrunkconfiguration.md)  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)

