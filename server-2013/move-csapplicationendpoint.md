---
title: Move-CsApplicationEndpoint
TOCTitle: Move-CsApplicationEndpoint
ms:assetid: 0f5a5b7a-aca5-4672-b712-d47683e28caf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398188(v=OCS.15)
ms:contentKeyID: 49302821
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsApplicationEndpoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

끝점을 다른 등록자 풀로 이동합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsApplicationEndpoint -Identity <UserIdParameter> -TargetApplicationPool <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 SIP 주소가 endpoint1@litwareinc.com인 응용 프로그램 끝점 연락처 개체를 신뢰할 수 있는 등록자 풀인 TrustPoolA.litwareinc.com으로 이동합니다. 이 명령을 사용하여 UCMA 2.0 응용 프로그램을 공존 후 Lync Server 응용 프로그램으로 업그레이드할 수 있습니다.

    Move-CsApplicationEndpoint -Identity sip:endpoint1@litwareinc.com -TargetApplicationPool TrustPoolA.litwareinc.com

## 예제 2

이 예제에서는 SIP 주소가 endpoint2@litwareinc.com인 응용 프로그램 끝점 연락처 개체를 신뢰할 수 있는 등록자 풀인 TrustPoolA.litwareinc.com으로 이동합니다. 이 예제는 예제 1과 달리 Force 매개 변수가 명령에 포함되어 있습니다. 이 명령은 UCMA 2.0 응용 프로그램을 바로 마이그레이션하거나 순수 Lync Server 배포에 대해 UCMA 2.0 응용 프로그램을 직접 배포하는 데 사용됩니다. 또한 이 명령은 Lync Server 등록자를 통해 경로 지정이 발생하도록 필요한 특성을 사용하여 Active Directory의 기존 개체를 업데이트합니다.

    Move-CsApplicationEndpoint -Identity sip:endpoint2@litwareinc.com -TargetApplicationPool TrustPoolA.litwareinc.com -Force

## 자세한 정보

이 cmdlet은 Active Directory 도메인 서비스의 기존 끝점 연락처 개체를 Microsoft Office Communications Server 2007 R2 응용 프로그램 풀에서 Lync Server 응용 프로그램 풀로 이동하거나 특정 Lync Server 응용 프로그램 풀에서 다른 응용 프로그램 풀로 이동합니다. 지정된 끝점과 연결된 응용 프로그램이 대상 풀에 있어야 합니다. 끝점과 연결된 응용 프로그램을 확인하려면 **Get-CsTrustedApplicationEndpoint** cmdlet 또는 **Get-CsDialInConferencingAccessNumber** cmdlet을 실행합니다.

이 cmdlet은 Office Communications Server 2007 R2에 대해 배포된 응용 프로그램의 대상이 Lync Server로 변경된 경우 Active Directory 연락처 개체 속성을 업그레이드하는 데도 사용됩니다. 이 경우 원본 및 대상 응용 프로그램 풀이 같아야 합니다. 또한 원래 Office Communications Server 2007 R2에서 작동하도록 설계된 응용 프로그램이 Lync Server에 직접 배포된 경우 이 cmdlet을 Force 플래그와 함께 사용하여 Active Directory 연락처 개체 속성을 업그레이드해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Move-CsApplicationEndpoint** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsApplicationEndpoint"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>이동할 끝점 연락처의 SIP 주소 또는 DN(고유 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetApplicationPool</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>끝점이 이동할 대상 풀의 FQDN(정규화된 도메인 이름)입니다. 대상 풀은 등록자 서비스 종속성이 있어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인 컨트롤러를 지정하는 데 사용됩니다. 도메인 컨트롤러가 지정되지 않은 경우 사용 가능한 첫 번째 도메인 컨트롤러가 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 플래그는 Microsoft Unified Communications Managed API(UCMA) 2.0 연락처 개체를 Lync Server 배포의 같은 풀로 이동하는 경우에 필요합니다. 이 플래그를 사용하면 Lync Server 등록자를 통해 경로 지정이 발생합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 백 엔드 데이터베이스에서 발생했을 수 있는 모든 오류를 무시하고 오류가 발생했더라도 응용 프로그램 끝점 이동을 시도하도록 컴퓨터에 명령합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 개체가 이동된 후 응용 프로그램 끝점 개체가 반환됩니다.</p></td>
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

문자열. 응용 프로그램 끝점의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

PassThru 매개 변수와 함께 사용된 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsApplicationEndpoint](get-csapplicationendpoint.md)

