---
title: Grant-CsSetupPermission
TOCTitle: Grant-CsSetupPermission
ms:assetid: 753bccc1-edb4-48c9-bd0a-2db5d86f8c5e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398569(v=OCS.15)
ms:contentKeyID: 49304052
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Grant-CsSetupPermission

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory OU(조직 구성 단위)에 Lync Server 설정 권한을 부여합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Grant-CsSetupPermission -ComputerOU <String> [-Confirm [<SwitchParameter>]] [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 litwareinc.com 도메인의 CsServers OU에 대한 설치 권한을 부여합니다.

    Grant-CsSetupPermission -ComputerOU "ou=CsServers,dc=litwareinc,dc=com"

## 자세한 정보

Lync Server를 설치할 때 수행되는 도메인 준비에서는 RTCUniversalServerAdmins 그룹의 구성원이 **Enable-CsTopology** cmdlet을 실행할 수 있는 권한을 자동으로 추가하지 않습니다. 이는 기본적으로 토폴로지를 사용하려면 도메인 관리자여야 함을 의미합니다. RTCUniversalServerAdmins 그룹의 구성원에게 토폴로지를 사용할 수 있는 권한을 부여하려면 **Grant-CsSetupPermissions** cmdlet을 실행해야 합니다. 또한 Lync Server를 실행하는 컴퓨터가 속해 있는 각 Active Directory 컨테이너에 대해 이 cmdlet을 실행해야 합니다.

이 cmdlet은 RTCUniversalServerAdmins 그룹에만 사용 권한을 부여하며, 다른 보안 그룹 또는 개별 사용자에게 사용 권한을 부여하는 데는 사용할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: **Grant-CsSetupPermission** cmdlet을 로컬로 실행하려면 도메인 관리자여야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsSetupPermission"}

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
<td><p><em>ComputerOU</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server가 설치되어 있거나 설치될 컴퓨터에 대한 계정이 있는 OU의 고유 이름입니다(예: &quot;ou=CsServers,dc=litwareinc,dc=com&quot;).</p>
<p>원할 경우 OU를 지정할 때 고유 이름에서 도메인 부분은 비워둘 수 있습니다.(예:</p>
<p>-ComputerOU &quot;ou=CsServers&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Domain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>OU가 있는 도메인의 이름입니다. 이 매개 변수를 포함하지 않으면 <strong>Grant-CsSetupPermission</strong> cmdlet은 현재 도메인에서 OU를 찾습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>정책을 할당할 때 연결할 도메인 컨트롤러의 정규화된 이름입니다(예: -DomainController atl-dc-001.litwareinc.com).</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Grant-CsSetupPermission</strong> cmdlet은 정책을 할당할 때 사용 가능한 가장 가까운 도메인 컨트롤러에 연결합니다.</p></td>
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
<td><p>정책을 할당할 때 연결할 전역 카탈로그 서버의 정규화된 이름입니다(예: -GlobalCatalog atl-dc-001.litwareinc.com).</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Grant-CsSetupPermission</strong> cmdlet은 정책을 할당할 때 사용 가능한 가장 가까운 전역 카탈로그 서버에 연결합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\SetupPermissions.html&quot;).</p></td>
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

없음. **Grant-CsSetupPermission** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. **Grant-CsSetupPermission** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Revoke-CsSetupPermission](revoke-cssetuppermission.md)  
[Test-CsSetupPermission](test-cssetuppermission.md)

