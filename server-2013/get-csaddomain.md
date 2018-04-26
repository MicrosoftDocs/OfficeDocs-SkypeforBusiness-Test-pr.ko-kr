---
title: Get-CsAdDomain
TOCTitle: Get-CsAdDomain
ms:assetid: 64554035-3ba5-4aa7-b5d3-91277f107275
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398453(v=OCS.15)
ms:contentKeyID: 49303844
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAdDomain

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory 도메인 서비스가 Lync Server를 설치할 수 있도록 올바르게 구성되었는지 여부를 나타내는 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAdDomain [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>]

## 예제

## 예제 1

예제 1에서는 로컬 Active Directory 도메인의 현재 상태에 대한 정보를 반환합니다. 도메인 설정이 최신인 경우 도메인이 Lync Server를 호스트할 준비가 된 것이며 LC\_DOMAIN\_SETTINGS\_STATE\_READY가 반환됩니다.

    Get-CsAdDomain

## 예제 2

예제 2에 표시된 명령은 Litwareinc.com이라는 특정 도메인의 현재 상태를 반환합니다. 다중 도메인 환경에서는 Domain 매개 변수를 포함하여 지정한 도메인에 대한 정보를 반환할 수 있습니다.

    Get-CsAdDomain -Domain "fabrikam.com" 

## 예제 3

예제 3에서는 Active Directory 도메인의 현재 상태를 검색하고 확인된 상태에 대한 정보를 C:\\Logs\\DomainReport.html이라는 파일에 기록합니다. 이 파일에는 도메인의 준비 상태를 확인하기 위해 **Get-CsAdDomain** cmdlet에서 수행하는 단계에 대한 자세한 내용이 포함됩니다. 이러한 단계에는 Active Directory 그룹이 존재하는지 확인하고, 다양한 Active Directory 컨테이너에서 권한 설정을 확인하는 등의 작업이 포함됩니다.

    Get-CsAdDomain -Report "C:\Logs\DomainReport.html"

## 자세한 정보

Lync Server를 설치하려면 먼저 해당 도메인이 제대로 준비되어 있어야 합니다. 여기에는 Lync Server 관련 특성의 추가를 허용하도록 Active Directory 스키마를 확장하고, Lync Server 관리 및 운영에 사용되는 유니버설 그룹에 필수 액세스 제어 항목을 할당하는 과정이 포함됩니다. **Get-CsAdDomain** cmdlet은 도메인에 Lync Server를 설치할 수 있는지 여부를 나타내는 단일 값을 반환합니다. **Get-CsAdDomain** cmdlet이 LC\_DOMAINSETTINGS\_STATE\_READY 값을 반환하는 경우 해당 도메인에 Lync Server를 설치할 수 있습니다. cmdlet이 LC\_DOMAINSETTINGS\_STATE\_NOT\_READY를 반환하는 경우 Lync Server를 설치하려고 시도하기 전에 도메인을 올바르게 준비해야 합니다.

**Get-CsAdDomain** cmdlet은 설치 마법사의 일부로 실행됩니다. 마법사가 도메인이 올바르게 준비되지 않았다고 판단하면 오류 메시지가 표시되고 설치가 중지됩니다. 그러나 Lync Server 설치를 시도하기 전에 설치 마법사와는 별도로 **Get-CsAdDomain** cmdlet을 실행하여 도메인 상태를 확인할 수 있습니다.

**Get-CsAdDomain**cmdlet은 다음 Microsoft Office Communications Server 2007 R2 명령과 동일한 기능을 수행합니다.

Lcscmd.exe /domain /action:CheckDomainPrepState

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 Active Directory에 대한 읽기 권한을 가진 사용자는 누구나 **Get-CsAdDomain** cmdlet을 실행할 수 있습니다. 일반적으로 모든 도메인 구성원은 이 권한이 있습니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAdDomain"}

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
<td><p><em>Domain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>확인할 도메인의 FQDN(정규화된 도메인 이름)입니다(예: -Domain &quot;litwareinc.com&quot;). 이 매개 변수가 지정되지 않은 경우 로컬 도메인이 확인됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>관리자가 <strong>Get-CsAdDomain</strong> cmdlet을 실행할 때 사용할 도메인 컨트롤러의 FQDN을 지정하는 데 사용됩니다. 이 매개 변수를 지정하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용하게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 도메인의 계정이 있는 컴퓨터에서 <strong>Get-CsAdDomain</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory의 시스템 컨테이너에 저장되는 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다 (예: -Report &quot;C:\Logs\DomainPrep.html&quot;).</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsAdDomain** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsAdDomain** cmdlet은 Microsoft.Rtc.Management.Deployment.LcDomainSettingsState 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsAdDomain](disable-csaddomain.md)  
[Enable-CsAdDomain](enable-csaddomain.md)

