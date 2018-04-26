---
title: Publish-CsTopology
TOCTitle: Publish-CsTopology
ms:assetid: d8f5dfd9-0ab6-4703-9d50-2fa50b3fd58b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398953(v=OCS.15)
ms:contentKeyID: 49305202
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Publish-CsTopology

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Get-CsTopology** cmdlet을 사용하여 검색한 Lync Server 토폴로지를 게시합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Publish-CsTopology -FileName <String> <COMMON PARAMETERS>

    Publish-CsTopology -Document <XElement> <COMMON PARAMETERS>

    Publish-CsTopology -FinalizeUninstall <SwitchParameter> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BackupFileName <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 현재 토폴로지를 검색한 다음 다시 게시합니다. 이러한 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-CsTopology** cmdlet 및 AsXml 매개 변수를 사용하여 현재 토폴로지를 검색합니다. 그런 다음 Windows PowerShell 리디렉션 기호 \>을 사용하여 검색된 데이터를 C:\\Topologies\\Topology.xml 파일에 저장합니다. 또한 ToString 메서드를 사용하여 검색된 토폴로지를 문자열 값으로 변환합니다. 예제의 두 번째 명령은 **Publish-CsTopology** cmdlet을 사용하여 새로 검색된 토폴로지를 다시 게시합니다.

    (Get-CsTopology -AsXml).ToString() > C:\Topologies\Topology.xml 
    Publish-CsTopology -FileName "C:\Topologies\Topology.xml"

## 자세한 정보

Lync Server를 설치한 후에는 Lync Server 인프라를 변경해야 합니다. 예를 들어 새 사이트를 추가하거나 기존 등록자 풀을 삭제하거나 보관 서버를 추가해야 할 수 있습니다. 이러한 인프라 변경은 토폴로지 작성기를 사용하여 수행해야 합니다. 토폴로지 작성기에서 변경 내용을 적용한 후에는 이 도구를 사용하여 변경 내용을 게시하고 활성화할 수 있습니다. 변경 내용을 게시하고 활성화하는 두 단계는 매우 중요합니다. 토폴로지 작성기를 사용하여 원하는 만큼 수정할 수 있지만 이러한 수정 사항을 게시하고 새 토폴로지를 활성화할 때까지는 실제로 수정 사항이 적용되지 않고 Lync Server 인프라가 변경되지 않기 때문입니다.

변경 내용을 게시하면 새 정보(예: 새 사이트 또는 새 서버 역할)가 중앙 관리 저장소에 기록됩니다. 그러나 이러한 새 개체 또는 새로 수정한 개체가 토폴로지에 즉시 조인되는 것은 아닙니다. 이는 업데이트된 토폴로지가 활성화된 경우에만 실행됩니다. 토폴로지 작성기에서 게시 옵션을 선택하면 변경 내용이 게시( 중앙 관리 저장소에 기록)된 다음 새 토폴로지가 활성화되는 두 가지 단계가 수행됩니다.

**Publish-CsTopology** cmdlet은 더 이상 토폴로지 작성기를 사용하여 만든 토폴로지를 게시할 때 권장되는 방법이 아닙니다. 대신 이전 단락에서 개략적으로 설명한 단계를 사용하여 토폴로지 작성기 내에서 게시를 수행하는 것이 좋습니다. 토폴로지 작성기는 이제 **Publish-CsTopology** cmdlet을 사용하여 게시할 수 없는 토폴로지 작성기 XML 파일 형식(.tbxml)을 사용하기 때문입니다. **Publish-CsTopology** cmdlet을 사용하여 수행할 수 있는 작업은 **Get-CsTopology** cmdlet을 사용하여 검색한 토폴로지를 다시 게시하는 작업밖에 없습니다. 이러한 방법으로 토폴로지를 구성한 후에는 단순 URL을 다시 구성해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Publish-CsTopology** cmdlet을 실행할 수 있습니다. 그러나 설정 권한을 위임 받지 않은 경우에는 도메인 관리자여야 **Publish-CsTopology** cmdlet을 실행할 수 있습니다. 실제로 **Publish-CsTopology** cmdlet을 사용할 수 있는 RTCUniversalServerAdmins 권한을 부여하려면 Lync Server 서비스를 실행하는 컴퓨터가 포함된 모든 Active Directory 컨테이너에 대해 **Grant-CsSetupPermission** cmdlet을 실행해야 합니다. 이 제한 사항은 토폴로지 작성기를 통해 토폴로지를 활성화하는 경우에도 적용됩니다. **Set-CsSetupPermission** cmdlet을 통해 권한을 위임 받지 않은 경우에는 도메인 관리자만 토폴로지 작성기를 통해 토폴로지를 게시할 수 있습니다.

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
<td><p><em>Document</em></p></td>
<td><p>필수</p></td>
<td><p>System.Xml.Linq.XElement</p></td>
<td><p>XML 파일 대신 XML 요소를 게시하는 데 사용됩니다. 이 XML 요소는 System.XML.Linq.XElement 개체로 구성해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 토폴로지 정보가 포함된 XML 파일의 전체 경로입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>FinalizeUninstall</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Lync Server를 제거할 때만 사용합니다. 중앙 관리 서버가 제거된 후에는 Publish-CsTopology 및 FinalizeUninstall 매개 변수를 사용하여 빈 토폴로지를 게시합니다. 무엇보다도 이렇게 하면 중앙 관리 서버에 대한 모든 Active Directory 항목이 제거됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BackupFileName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p><strong>Publish-CsTopology</strong> cmdlet을 실행할 때 자동으로 만들어지는 백업 파일의 전체 경로입니다. 이 매개 변수를 지정하지 않으면 <strong>Publish-CsTopology</strong> cmdlet이 Publish-CsTopology-Backup-[2010_10_01][08_30_00]과 유사한 임시 폴더(%temp%)에 백업 파일을 만듭니다. 여기서 파일 이름 2010_10_01은 게시가 수행된 날짜, 즉 년(2010), 월(10), 일(01)을 나타내고, 08_30_00은 게시가 수행된 시간, 즉 시(08), 분(30), 초(00)를 나타냅니다.</p></td>
</tr>
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
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인의 계정을 가진 컴퓨터에서 <strong>Publish-CsTopology</strong> cmdlet을 실행하는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
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
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\Publish_Topology.html&quot;).</p></td>
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

없음. **Publish-CsTopology** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Publish-CsTopology** cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.DefaultTopology 개체의 인스턴스를 게시합니다.

## 참고 항목

#### 기타 리소스

[Enable-CsTopology](enable-cstopology.md)  
[Get-CsTopology](get-cstopology.md)  
[New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)  
[Test-CsTopology](test-cstopology.md)

