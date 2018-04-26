---
title: Get-CsTopology
TOCTitle: Get-CsTopology
ms:assetid: ad52f545-b8dd-411e-8584-b6e29fe8ef18
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412824(v=OCS.15)
ms:contentKeyID: 49304705
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTopology

 

_**마지막으로 수정된 항목:** 2015-03-09_

내부 도메인, 사이트, 클러스터, 컴퓨터, 서비스 및 SQL Server의 백 엔드 인스턴스 등 Lync Server 인프라에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsTopology [-AsXml <SwitchParameter>] [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 Lync Server 토폴로지에 대한 전체 세부 정보를 반환합니다. 이 작업을 수행하기 위해 추가 매개 변수 없이 **Get-CsTopology** cmdlet을 호출합니다.

    Get-CsTopology

## 예제 2

예제 2에서는 Lync Server 토폴로지에 있는 컴퓨터에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsTopology** cmdlet을 호출하여 전체 Lync Server 토폴로지를 반환합니다. 이 정보는 ExpandProperty 매개 변수를 사용하여 해당 토폴로지에 포함된 모든 컴퓨터에 대한 자세한 정보를 추출하고 표시하는 **Select-Object** cmdlet에 파이프됩니다.

    Get-CsTopology | Select-Object -ExpandProperty Machines

## 예제 3

예제 3에 표시된 명령은 Lync Server 토폴로지에 대한 정보를 반환한 다음 해당 정보를 XML 파일에 저장합니다. 이 작업을 수행하기 위해 명령은 먼저 데이터를 서식이 지정된 XML로 반환하는 AsXml 매개 변수와 함께 **Get-CsTopology** cmdlet을 호출합니다. 서식이 지정된 이 데이터는 C:\\Logs\\Topology.xml 파일에 정보를 저장하는 **Out-File** cmdlet에 파이프됩니다.

    Get-CsTopology -AsXML | Out-File C:\Logs\Topology.xml

## 자세한 정보

**Get-CsTopology** cmdlet은 Lync Server가 설정 및 구성된 방식에 대한 정보를 반환합니다. 이 cmdlet을 추가 매개 변수 없이 호출하면 Lync Server 인프라에 대한 개요가 제공됩니다. 여기에서는 이 cmdlet을 통해 도메인, 사이트, Lync Server 서비스 및 서버 역할을 실행하는 컴퓨터 등을 개괄적으로 확인할 수 있습니다. 또는 **Select-Object** cmdlet에 **Get-CsTopology** cmdlet의 출력을 전달할 수 있습니다. 이렇게 하면 토폴로지의 한 부분에 대한 자세한 정보에 액세스할 수 있습니다. 예를 들어 다음 명령은 Lync Server에서 사용하는 SQL Server 인스턴스와 관련된 자세한 정보를 제공합니다.

Get-CsTopology | Select-Object -ExpandProperty SqlInstances

또한 AsXml 매개 변수를 사용하여 XML 형식의 전체 토폴로지에 대한 자세한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsTopology** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p><em>AsXml</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>XML 형식의 토폴로지 정보를 반환합니다. <strong>Get-CsTopology</strong> cmdlet, AsXml 매개 변수 및 <strong>Out-File</strong> cmdlet을 결합하여 토폴로지를 XML 파일로 내보낼 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 토폴로지 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsTopology** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsTopology** cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.DefaultTopology 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Enable-CsTopology](enable-cstopology.md)  
[Publish-CsTopology](publish-cstopology.md)  
[Test-CsTopology](test-cstopology.md)

