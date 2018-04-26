---
title: Disable-CsAdForest
TOCTitle: Disable-CsAdForest
ms:assetid: 06a6117c-27da-400f-8db9-eb28fe353aae
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398122(v=OCS.15)
ms:contentKeyID: 49302694
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsAdForest

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Enable-CsAdForest** cmdlet이 수행한 포리스트 준비 작업을 실행 취소합니다. 이 cmdlet은 일반적으로 Lync Server를 제거하는 경우에만 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Disable-CsAdForest [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-GroupDomain <Fqdn>] [-GroupDomainController <Fqdn>] [-Report <String>] [-RootDomainController <Fqdn>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 **Enable-CsAdForest** cmdlet이 수행한 포리스트 준비 작업을 롤백합니다. Force 매개 변수가 포함되어 있지 않으므로 **Disable-CsAdForest** cmdlet에서 포리스트의 도메인 중 하나 이상이 Lync Server에 대해 준비되어 있음을 감지한 경우 명령이 실패합니다. 이 경우 **Disable-CsAdDomain** cmdlet을 실행하여 도메인 준비를 롤백해야 합니다.

    Disable-CsAdForest

## 예제 2

예제 2에서는 **Disable-CsAdForest** cmdlet에서 포리스트의 도메인 중 하나 이상이 Lync Server에 대해 준비되어 있음을 감지한 경우에도 포리스트 준비가 롤백됩니다. Force 매개 변수를 포함하여 강제로 롤백합니다.

    Disable-CsAdForest -Force

## 자세한 정보

Lync Server를 설치할 때 Active Directory 도메인 서비스에 대해 몇 가지 포리스트 수준의 변경 작업을 수행해야 합니다. **Enable-CsAdForest** cmdlet을 사용하여 수행할 수 있는 이러한 변경 내용에는 Lync Server에 특정한 개체 및 표시 지정자 만들기, Lync Server를 관리하는 데 필요한 유니버설 보안 그룹 만들기, 전역 설정 개체에 이러한 그룹에 대한 액세스 관리 권한 및 사용 권한 부여 등이 포함됩니다. 나중에 Lync Server를 제거하기로 결정하거나 설치 프로세스 중에 문제가 발생한 경우 이러한 포리스트 수준 변경 내용을 롤백해야 할 수도 있습니다. **Disable-CsAdForest** cmdlet을 사용하면 **Enable-CsAdForest** cmdlet으로 수행한 모든 포리스트 수준의 수정 사항을 실행 취소할 수 있습니다.

**Disable-CsAdForest** cmdlet에서 수행하는 작업은 다음 Microsoft Office Communications Server 2007 R2 명령이 수행하는 작업과 비슷합니다.

Lcscmd.exe /forest /action:ForestUnprep

이 cmdlet을 실행할 수 있는 사용자: **Disable-CsAdForest** cmdlet을 로컬로 실행하려면 엔터프라이즈 관리자여야 합니다.

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
<td><p>이 매개 변수가 있으면 포리스트의 도메인 중 하나 이상이 Lync Server에 대해 준비되어 있음을 <strong>Disable-CsAdForest</strong> cmdlet에서 감지한 경우에도 포리스트 준비 단계가 강제로 롤백됩니다. 이 매개 변수가 없으면 포리스트의 도메인 중 하나 이상이 Lync Server에 대해 준비되어 있음을 <strong>Disable-CsAdForest</strong> cmdlet에서 감지한 경우 명령이 실패합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 도메인의 계정이 있는 컴퓨터에서 <strong>Disable-CsComputer</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory 도메인 서비스의 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GroupDomain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Lync Server 유니버설 그룹이 만들어진 도메인의 FQDN(정규화된 도메인 이름)입니다(예: -GroupDomain asia.litwareinc.com). 이 매개 변수를 포함하지 않으면 <strong>Disable-CsAdForest</strong> cmdlet에서 로컬 도메인의 유니버설 그룹을 찾습니다.</p></td>
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
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\DisableForest.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>RootDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>외부 도메인의 리소스에 액세스해야 하는 클라이언트를 위해 신뢰 경로를 만드는 데 사용되는 루트 도메인 컨트롤러의 FQDN입니다.</p></td>
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

없음.

## 반환 형식

없음.

