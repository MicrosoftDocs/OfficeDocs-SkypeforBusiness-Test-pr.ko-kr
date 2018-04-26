---
title: Enable-CsAdForest
TOCTitle: Enable-CsAdForest
ms:assetid: 2381fca7-294b-486d-919d-e8626cef6fea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425713(v=OCS.15)
ms:contentKeyID: 49303061
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enable-CsAdForest

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 설치하는 데 필요한 Active Directory 수정 작업을 수행합니다. 이러한 작업에는 구성 또는 시스템 컨테이너에 대한 전역 변경, 유니버설 그룹 만들기, 그리고 Lync Server 관련 속성 집합 및 표시 지정자 만들기가 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Enable-CsAdForest [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-GroupDomain <Fqdn>] [-GroupDomainController <Fqdn>] [-Report <String>] [-RootDomainController <Fqdn>] [-SkipPrepareCheck <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 Lync Server의 설치를 위해 Active Directory 포리스트를 준비합니다. GroupDomain 매개 변수를 사용하지 않았으므로 **Enable-CsAdForest** cmdlet을 실행하면 생성되는 유니버설 보안 그룹은 로컬 도메인에 만들어집니다.

    Enable-CsAdForest

## 예제 2

이 명령은 Lync Server의 설치를 위해 Active Directory 포리스트를 준비합니다. 이번에는 GroupDomain 매개 변수를 사용하고 **Enable-CsAdForest** cmdlet을 실행하여 northamerica.litwareinc.com 도메인에 유니버설 보안 그룹을 만들도록 지정합니다.

    Enable-CsAdForest -GroupDomain northamerica.litwareinc.com

## 자세한 정보

Lync Server를 설치하려면 Active Directory 도메인 서비스에서 몇 가지 포리스트 수준을 변경해야 합니다. 여기에는 Lync Server 관련 표시 지정자 및 개체를 만들고, Lync Server를 관리하는 데 필요한 유니버설 보안 그룹을 만들고, 전역 설정 개체에 이러한 그룹에 대한 액세스 권한을 부여하는 과정이 포함됩니다. 포리스트 준비는 일반적으로 Lync Server 설치 마법사를 통해 수행됩니다. 그러나 엔터프라이즈 관리자도 언제든지 **Enable-CsAdForest** cmdlet을 실행하여 포리스트 준비를 수행할 수 있습니다.

**Enable-CsAdForest** cmdlet의 실행이 완료되면 **Get-CsAdForest** cmdlet을 사용하여 해당 포리스트가 설치 프로세스의 다음 단계를 수행할 준비가 되었는지 확인할 수 있습니다.

이 cmdlet은 다음 Microsoft Office Communications Server 2007 R2 명령과 유사한 작업을 수행합니다.

Lcscmd.exe /forest /action:ForestPrep

이 cmdlet을 실행할 수 있는 사용자: **Enable-CsAdForest** cmdlet을 로컬로 실행하려면 엔터프라이즈 관리자여야 합니다.

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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 도메인의 계정이 있는 컴퓨터에서 <strong>Enable-CsAdForest</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory의 시스템 컨테이너에 저장되는 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GroupDomain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>새 유니버설 보안 그룹을 만들 도메인의 FQDN(정규화된 도메인 이름)입니다. 이 매개 변수가 포함되지 않은 경우 로컬 도메인에 그룹이 만들어집니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GroupDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>유니버설 그룹 정보가 저장된 도메인 컨트롤러의 FQDN입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다 (예: -Report &quot;C:\Logs\ForestPrep.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>RootDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>외부 도메인의 리소스에 액세스해야 하는 클라이언트를 위해 신뢰 경로를 만드는 데 사용되는 루트 도메인 컨트롤러의 FQDN입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SkipPrepareCheck</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True($True)로 설정하면 Enable-CsAdForest가 초기 준비 검사를 수행하지 않고 실행됩니다.</p></td>
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

없음.

## 반환 형식

없음.

