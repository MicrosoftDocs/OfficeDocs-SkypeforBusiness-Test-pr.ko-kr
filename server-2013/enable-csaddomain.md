---
title: Enable-CsAdDomain
TOCTitle: Enable-CsAdDomain
ms:assetid: a39768de-51ae-45e8-b6b7-441b5da0b3b2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412764(v=OCS.15)
ms:contentKeyID: 49304593
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enable-CsAdDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

포리스트 준비 중에 만들어진 유니버설 그룹에 대한 보안 설정을 수정합니다. 이러한 수정을 통해 도메인 내에서 Lync Server를 사용하도록 설정된 사용자를 호스트 및 관리하는 데 필요한 권한을 제공할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Enable-CsAdDomain [-Confirm [<SwitchParameter>]] [-CrossForest <SwitchParameter>] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-SkipPrepareCheck <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 설치를 위한 로컬 도메인을 준비합니다.

    Enable-CsAdDomain

## 예제 2

예제 2에서는 Lync Server 설치를 위한 asia.litwareinc.com 도메인을 준비합니다.

    Enable-CsAdDomain -Domain asia.litwareinc.com

## 자세한 정보

도메인에 Lync Server를 설치하려면 먼저 해당 도메인이 제대로 준비되어 있어야 합니다. 여기에는 Lync Server 관련 특성의 추가를 허용하도록 Active Directory 스키마를 확장하고, Lync Server 관리 및 운영에 필요한 유니버설 그룹에 필수 액세스 제어 항목을 할당하는 과정이 포함됩니다. 도메인 준비는 일반적으로 Lync Server 설치 마법사를 통해 수행됩니다. 그러나 관리자가 **Enable-CsAdDomain** cmdlet을 실행하여 도메인 준비를 수행할 수도 있습니다.

**Enable-CsAdDomain** cmdlet의 실행이 완료되면 **Get-CsAdDomain** cmdlet을 사용하여 해당 도메인이 설치 프로세스의 다음 단계를 수행할 준비가 되었는지 확인할 수 있습니다.


> [!NOTE]
> "여러 도메인이 포함된 단일 포리스트 환경의 하위 도메인을 준비하기 위한 작업을 실행하는 동안 Active Directory에서 'CrossRef' 개체를 찾을 수 없습니다."라는 오류가 표시되면 상위 도메인으로부터 RTCComponentUniversalServices 그룹을 하위 도메인의 Windows 인증 액세스 그룹에 추가합니다.



이 cmdlet은 다음 Microsoft Office Communications Server 2007 R2 명령과 유사한 작업을 수행합니다.

Lcscmd.exe /domain /action:DomainPrep

이 cmdlet을 실행할 수 있는 사용자: **Enable-CsAdDomain** cmdlet을 로컬로 실행하려면 도메인 관리자여야 합니다.

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
<td><p><em>CrossForest</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 해당 도메인 준비가 다른 포리스트의 도메인에서 수행됨을 나타냅니다. 사용하도록 설정할 도메인이 명령을 실행하는 컴퓨터와 동일한 포리스트에 있는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Domain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인 준비를 수행할 도메인의 FQDN(정규화된 도메인 이름)입니다(예: -Domain asia.litwareinc.com). 이 매개 변수가 포함되지 않은 경우 로컬 도메인에서 도메인 준비가 수행됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리자가 <strong>Enable-CsAdDomain</strong> cmdlet을 실행할 때 사용할 도메인 컨트롤러의 FQDN을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용하게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 도메인의 계정이 있는 컴퓨터에서 <strong>Enable-CsAdDomain</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory 도메인 서비스의 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장되는 경우에는 모든 도메인 컨트롤러를 사용할 수 있으며 이 매개 변수를 생략할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다 (예: -Report &quot;C:\Logs\DomainPrep.html&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>SkipPrepareCheck</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 <strong>Enable-CsAdDomain</strong> cmdlet이 초기 준비 검사를 건너뜁니다.</p></td>
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

없음. **Enable-CsAdDomain** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Disable-CsAdDomain](disable-csaddomain.md)  
[Get-CsAdDomain](get-csaddomain.md)

