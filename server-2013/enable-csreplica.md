---
title: Enable-CsReplica
TOCTitle: Enable-CsReplica
ms:assetid: 4a745da5-5b09-4b5a-8ab6-8b8b03d7afc6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425965(v=OCS.15)
ms:contentKeyID: 49303547
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enable-CsReplica

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 복제 경로에 로컬 컴퓨터를 추가합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Enable-CsReplica [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 복제 경로에 로컬 컴퓨터를 추가합니다.

    Enable-CsReplica

## 자세한 정보

서비스 또는 서버 역할이 컴퓨터에 설치되어 있으면 복제 경로에 해당 컴퓨터를 추가해야 합니다. 이렇게 하면 컴퓨터가 중앙 관리 저장소에서 토폴로지 및 구성 파일을 받을 수 있습니다. **Enable-CsReplica** cmdlet을 사용하면 복제 경로에 컴퓨터를 수동으로 추가할 수 있습니다. 일반적으로 컴퓨터를 수동으로 복제 경로에 추가할 필요는 없습니다. 이 작업은 Lync Server를 컴퓨터에 설치할 때 자동으로 수행됩니다.

이 cmdlet을 실행할 수 있는 사용자: **Enable-CsReplica** cmdlet을 로컬로 실행하려면 로컬 관리자 및 도메인 구성원이어야 합니다.

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
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인의 계정으로 컴퓨터에서 <strong>Enable-CsReplica</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
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
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\EnableReplica.html&quot;).</p></td>
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

없음. **Enable-CsReplica** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. **Enable-CsReplica** cmdlet은 값이나 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)

