---
title: Disable-CsAdDomain
TOCTitle: Disable-CsAdDomain
ms:assetid: 98a4982c-7d8d-460d-bff9-243373b20290
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398785(v=OCS.15)
ms:contentKeyID: 49304475
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsAdDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Enable-CsAdDomain** cmdlet으로 수행된 도메인 준비 작업의 실행을 취소합니다. 이 cmdlet은 일반적으로 도메인에서 Lync Server를 제거하는 경우에만 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Disable-CsAdDomain [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 도메인의 도메인 준비 프로세스를 롤백합니다. Force 매개 변수를 포함하지 않았으므로 **Disable-CsAdDomain** cmdlet을 통해 하나 이상의 프런트 엔드 서버, A/V 회의 서버 또는 웹 서비스 서버가 도메인에서 아직 활성 상태임이 확인될 경우 명령이 실패합니다.

    Disable-CsAdDomain

## 예제 2

예제 2에서는 asia.litwareinc.com 도메인에 대한 도메인 준비 프로세스를 롤백합니다.

    Disable-CsAdDomain -Domain asia.litwareinc.com

## 예제 3

예제 3의 명령은 Force 매개 변수를 사용하여 로컬 도메인에서 도메인 준비 프로세스의 롤백을 강제로 수행합니다. 이는 **Disable-CsAdDomain** cmdlet을 통해 하나 이상의 프런트 엔드 서버, A/V 회의 서버 또는 웹 서비스 서버가 도메인에서 아직 활성 상태임이 확인되더라도 롤백이 수행됨을 의미합니다.

    Disable-CsAdDomain -Force

## 자세한 정보

도메인에 Lync Server를 설치하려면 해당 도메인이 제대로 준비되어 있어야 합니다. 여기에는 Lync Server 관련 특성의 추가를 허용하도록 Active Directory 스키마를 확장하고, Lync Server 관리 및 운영에 필요한 유니버설 그룹에 필수 액세스 제어 항목을 할당하는 과정이 포함됩니다. 나중에 Lync Server를 제거하기로 결정하는 경우(또는 설치 프로세스 중에 문제가 발생한 경우) 이러한 도메인 수준 변경을 롤백해야 할 수 있습니다. **Disable-CsAdDomain** cmdlet을 사용하면 **Enable-CsAdDomain** cmdlet으로 수행한 모든 도메인 수준 수정의 실행을 취소할 수 있습니다.

**Disable-CsAdDomain** cmdlet에서 수행하는 작업은 다음 Microsoft Office Communications Server 2007 R2 명령이 수행하는 작업과 비슷합니다.

Lcscmd.exe /domain /action:DomainUnprep

이 cmdlet을 실행할 수 있는 사용자: **Disable-CsAdDomain** cmdlet을 로컬로 실행하려면 도메인 관리자여야 합니다.

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
<td><p><em>Domain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인 준비를 롤백해야 하는 도메인의 FQDN(정규화된 도메인 이름)입니다(예: -Domain asia.litwareinc.com). 이 매개 변수를 포함하지 않으면 로컬 도메인에서 롤백이 수행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리자가 <strong>Disable-CsAdDomain</strong>을 실행할 때 사용할 도메인 컨트롤러의 FQDN을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 cmdlet은 사용 가능한 첫 번째 도메인 컨트롤러를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 <strong>Disable-CsAdDomain</strong> cmdlet을 통해 하나 이상의 프런트 엔드, 전화 회의 또는 웹 서비스 서버가 도메인에서 아직 활성 상태임이 확인되더라도 롤백이 수행됩니다. 이 매개 변수가 없으면 프런트 엔드, 전화 회의 또는 웹 서비스 서버가 도메인에서 활성 상태인 경우 명령이 실패합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 도메인의 계정이 있는 컴퓨터에서 <strong>Disable-CsAdDomain</strong> cmdlet을 실행하는 경우 이 매개 변수는 필요 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory 도메인 서비스의 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다(예: -Report &quot;C:\Logs\DisableDomain.html&quot;).</p></td>
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

없음. **Disable-CsAdDomain** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Enable-CsAdDomain](enable-csaddomain.md)  
[Get-CsAdDomain](get-csaddomain.md)

