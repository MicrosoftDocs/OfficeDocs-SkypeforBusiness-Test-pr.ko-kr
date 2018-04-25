---
title: Set-CsTrustedApplication
TOCTitle: Set-CsTrustedApplication
ms:assetid: 35b2812b-43da-4a0a-88dc-960f3cab0dfc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425840(v=OCS.15)
ms:contentKeyID: 49303282
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTrustedApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램의 설정을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsTrustedApplication [-Identity <ExternalApplicationIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Port <Int32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Identity가 TrustPool.litwareinc.com/tapp2인 신뢰할 수 있는 응용 프로그램의 포트를 포트 6200으로 수정합니다. 이 작업을 수행하기 위해 **Set-CsTrustedApplication** cmdlet에 TrustPool.litwareinc.com/tapp2라는 Identity를 전달합니다. 이 Identity는 응용 프로그램이 상주하는 풀의 이름 뒤에 응용 프로그램 이름(또는 ID)을 포함하여 구성됩니다. 그런 다음 Port 매개 변수를 포함하고 값 6200을 제공하여 해당 값을 수정합니다.

    Set-CsTrustedApplication -Identity TrustPool.litwareinc.com/tapp2 -Port 6200

## 자세한 정보

신뢰할 수 있는 응용 프로그램은 Lync Server의 일부로 포함되어 기본 제공되지는 않지만 이 제품의 일부로 실행하도록 신뢰할 수 있는 상태가 지정된 타사에서 개발한 응용 프로그램입니다. 이 cmdlet을 사용하면 응용 프로그램을 실행하는 외부 서비스에서 사용 중인 포트 번호를 수정할 수 있습니다.

이 cmdlet을 사용하여 신뢰할 수 있는 응용 프로그램을 수정하는 경우 Identity 매개 변수에 값을 제공해야 합니다. ID는 응용 프로그램이 이동되는 풀의 FQDN(정규화된 도메인 이름) 뒤에 슬래시(/)와 응용 프로그램 ID를 포함합니다. 예를 들어 TrustPool.litwareinc.com/tapp2에서 TrustPool.litwareinc.com은 풀 FQDN이고 tapp2는 응용 프로그램 ID입니다. **Get-CsTrustedApplication** cmdlet을 호출하여 기존 응용 프로그램을 보는 경우 TrustPool.litwareinc.com/urn:application:tapp2와 같은 ID가 표시됩니다. urn:application: 접두사가 응용 프로그램 이름(tapp2) 앞에 붙습니다. 이 접두사는 ID의 일부이지만 Identity 매개 변수에 값을 지정할 때는 필요하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsTrustedApplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –matches "Set-CsTrustedApplication\\b"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.ExternalApplicationIdentity</p></td>
<td><p>수정할 신뢰할 수 있는 응용 프로그램의 고유 식별자입니다. Identity 값은 &lt;풀 FQDN&gt;/&lt;응용 프로그램 ID&gt; 형식으로 입력해야 합니다. 여기서 풀 FQDN은 응용 프로그램이 있는 풀의 FQDN이고, 응용 프로그램 ID는 응용 프로그램의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Port</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>응용 프로그램이 실행될 포트 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.Xds.DisplayTrustedApplication 개체입니다. 신뢰할 수 있는 응용 프로그램 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.Xds.DisplayTrustedApplication 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplication](new-cstrustedapplication.md)  
[Remove-CsTrustedApplication](remove-cstrustedapplication.md)  
[Get-CsTrustedApplication](get-cstrustedapplication.md)

