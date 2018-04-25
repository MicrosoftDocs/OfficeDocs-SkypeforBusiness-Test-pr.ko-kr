---
title: Install-CsAdServerSchema
TOCTitle: Install-CsAdServerSchema
ms:assetid: 86e13601-7e80-4276-b176-77d9c6e7d55a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398681(v=OCS.15)
ms:contentKeyID: 49304272
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Install-CsAdServerSchema

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 설치를 허용하도록 Active Directory 스키마를 확장합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Install-CsAdServerSchema [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Ldf <String>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 레지스트리에서 정보를 읽어 .LDF 파일의 위치를 확인한 다음 이 파일을 사용하여 Active Directory 스키마를 업데이트합니다.

    Install-CsAdServerSchema

## 예제 2

예제 2에서는 C:\\Schemas 폴더에 있는 스키마 업데이트 파일에서 가져온 정보로 Active Directory 스키마를 업데이트합니다. 이 폴더 위치는 Ldf 매개 변수를 사용하여 지정합니다.

    Install-CsAdServerSchema -Ldf "C:\Schemas"

## 자세한 정보

Lync Server에서는 자체 데이터베이스에 대부분의 구성 정보를 저장하지만 Active Directory 도메인 서비스를 저장 위치로 사용하기도 합니다. 예를 들어 사용자 관련 정보는 해당 사용자 Active Directory 계정의 일부로 저장됩니다. 이렇게 하려면 Lync Server에서 일반 Active Directory 사용자 계정의 일부가 아닌 특성으로 이러한 값을 저장합니다. 이는 Active Directory 스키마를 "확장"해야 함을 의미합니다. Lync Server에 필요한 사용자 지정 특성 및 기타 항목을 추가하기 위해 스키마를 수정해야 합니다.

Active Directory 스키마를 확장하는 가장 쉬운 방법은 **Install-CsAdServerSchema** cmdlet을 사용하는 것입니다. **Install-CsAdServerSchema** cmdlet은 일반적으로 Lync Server 설치 프로세스의 일부로 실행되지만 필요한 경우 관리자는 언제든 cmdlet을 실행할 수 있습니다. cmdlet 실행이 완료되면 **Get-CsAdServerSchema** cmdlet을 사용하여 스키마가 업데이트되었는지, Active Directory가 설치 프로세스의 다음 단계로 진행할 준비가 되었는지 확인할 수 있습니다.

**Install-CsAdServerSchema** cmdlet을 실행할 때는 cmdlet이 Active Directory 개체 및 특성 정의를 관리하는 작업 마스터 역할인 스키마 마스터에 액세스할 수 있어야 합니다. 스키마 마스터가 아닌 컴퓨터에서 **Install-CsAdServerSchema** cmdlet을 실행하는 경우에는 스키마 마스터를 호스트하는 컴퓨터에서 레지스트리에 대한 원격 액세스를 허용해야 합니다. 그렇지 않으면 스키마 마스터 자체에서 **Install-CsAdServerSchema** cmdlet을 실행해야 합니다.

**Install-CsAdServerSchema** cmdlet이 수행하는 기능은 다음 Microsoft Office Communications Server 2007 R2 명령이 수행하는 기능과 비슷합니다.

Lcscmd.exe /forest /action:SchemaPrep /SchemaType:Server

이 cmdlet을 실행할 수 있는 사용자: **Install-CsAdServerSchema** cmdlet을 로컬로 실행하려면 루트 도메인의 Active Directory 스키마 관리자인 동시에 스키마 마스터 컴퓨터의 로컬 관리자여야 합니다.

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
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인의 계정을 가진 컴퓨터에서 <strong>Install-CsAdServerSchema</strong> cmdlet을 실행하는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 도메인 컨트롤러의 FQDN입니다. 도메인의 계정이 있는 컴퓨터에서 <strong>Install-CsAdServerSchema</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Ldf</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>가져올 .LDF 파일이 있는 폴더에 대한 경로입니다. .LDF(LDAP 데이터 교환 형식) 파일에는 Active Directory 스키마에 필요한 업데이트가 포함되어 있습니다. 이 매개 변수를 포함하지 않으면 <strong>Install-CsAdServerSchema</strong> cmdlet이 레지스트리에 기록된 Lync Server 설치 경로에서 파일을 찾습니다. 일반적으로 설치 경로는 C:\Program Files\ Microsoft Lync Server 2010\Deployment\Setup입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다(예: -Report &quot;C:\Logs\ServerSchema.html&quot;).</p></td>
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

없음. **Install-CsAdServerSchema** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Install-CsAdServerSchema** cmdlet은 값이나 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsAdServerSchema](get-csadserverschema.md)

