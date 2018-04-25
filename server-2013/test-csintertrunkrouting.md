---
title: Test-CsInterTrunkRouting
TOCTitle: Test-CsInterTrunkRouting
ms:assetid: 2248d29a-8a2a-42b1-ab6b-a6c1d74b0455
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204741(v=OCS.15)
ms:contentKeyID: 49303053
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsInterTrunkRouting

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 SIP 트렁크에서 건 전화를 라우팅할 때 사용되는 경로 및 PSTN 사용을 확인합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsInterTrunkRouting -TargetNumber <PhoneNumber> -TrunkConfiguration <TrunkConfiguration> [-Force <SwitchParameter>] [-RouteSettings <PstnRoutingSettings>]

## 예제

## 예제 1

예제 1에 표시된 명령은 사용자가 Redmond 사이트에 대한 트렁크 구성 설정을 사용하여 전화 번호 1-206-555-1219로 전화를 걸 수 있도록 하는 일치 경로 및 일치 전화 사용을 반환합니다.

    $trunk = Get-CsTrunkConfiguration -Identity "site:Redmond"
    
    Test-CsInterTrunkRouting -TargetNumber "tel:+12065551219" -TrunkConfiguration $trunk

## 자세한 정보

Test-CsInterTrunkRouting은 SIP 간에 통화를 라우팅할 수 있는지 확인합니다. 이 작업을 수행하기 위해 이 cmdlet에서 전화 번호와 트렁크 구성을 지정합니다. 그러면 Test-CsInterTrunkRouting이 지정된 번호와 일치하는 경로 및 PSTN 사용을 보고합니다. 트렁크의 번호 패턴이 지정된 전화 번호와 일치하며 트렁크가 하나 이상의 PSTN 사용을 공유하는 경우에만 트렁크 간에 통화를 라우팅할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsInterTrunkRouting"}

**Lync Server 제어판:** Test-CsInterTrunkRouting cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>TargetNumber</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
<td><p>테스트를 수행할 때 전화를 걸 PSTN 전화 번호입니다. 대상 전화 번호는 다음과 같이 E.164 형식을 사용하여 지정해야 합니다.</p>
<p>-TargetNumber &quot;tel:+12065551219&quot;</p>
<p>전화 번호는 &quot;tel:&quot; 접두사 뒤에 더하기 기호(+), 국가 번호(1), 지역 번호(206) 및 전화 번호(5551219)가 차례로 붙는 형식이어야 합니다. 전화 번호를 지정할 때 대시, 괄호 또는 기타 문자를 사용해서는 안 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TrunkConfiguration</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration</p></td>
<td><p>테스트할 트렁크 구성에 대한 개체 참조입니다. 이 개체 참조를 만들려면 다음과 같은 명령을 사용합니다.</p>
<p>$trunk = Get-CsTrunkConfiguration –Identity &quot;site:Redmond&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RouteSettings</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings</p></td>
<td><p>Test-CsInterTrunkRouting을 호출할 때 음성 라우팅 구성 설정 컬렉션을 지정할 수 있도록 하는 개체 참조입니다. 이 개체 참조를 만들려면 다음과 같은 명령을 사용합니다.</p>
<p>$route = Get-CsRoutingConfiguration –Identity &quot;global&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. Test-CsInterTrunkRouting은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Test-CsInterTrunkRouting은 Microsoft.Rtc.Management.Voice.InterTrunkRoutingTestResult 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTrunk](get-cstrunk.md)  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)

