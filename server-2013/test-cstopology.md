---
title: Test-CsTopology
TOCTitle: Test-CsTopology
ms:assetid: 06ffa245-f1c7-46b7-9be6-5b291deda5c1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398127(v=OCS.15)
ms:contentKeyID: 49302703
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsTopology

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 설치에 대한 서비스 활성화 및 그룹 권한을 확인합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsTopology [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-Service <String>]

## 예제

## 예제 1

예제 1에서는 전체 Lync Server 토폴로지의 유효성을 검사합니다.

    Test-CsTopology

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 그러나 이 경우에는 Report 매개 변수를 포함하여 출력 파일이 기록되는 위치(C:\\Logs\\Topology.xml)를 지정합니다.

    Test-CsTopology -Report "C:\Logs\Topology.xml"

## 예제 3

예제 3에서는 **Test-CsTopology** cmdlet을 사용하여 Registrar:atl-cs-001.litwareinc.com이라는 단일 서비스의 유효성을 검사합니다.

    Test-CsTopology -Service "Registrar:atl-cs-001.litwareinc.com"

## 자세한 정보

**Test-CsTopology** cmdlet을 사용하면 Lync Server가 전역 수준에서 올바르게 작동하는지 확인할 수 있습니다. 기본적으로 이 cmdlet은 전체 Lync Server 인프라를 검사하여 필요한 서비스가 실행되고 있는지, 그리고 이러한 서비스 및 Lync Server를 설치할 때 만들어진 유니버설 보안 그룹에 대해 적절한 사용 권한이 설정되었는지 확인합니다.

Lync Server 전체의 유효성 확인 외에도 **Test-CsTopology** cmdlet을 통해 특정 서비스의 유효성을 검사할 수 있습니다. 예를 들어 다음 명령은 atl-cs-001.litwareinc.com 풀의 A/V 회의 서버 상태를 검사합니다.

Test-CsTopology –Service "ConferencingServer:atl-cs-001.litwareinc.com"

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsTopology"}

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
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인 계정을 가진 컴퓨터에서 <strong>Test-CsTopology</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
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
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\Topology.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Service</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수가 있으면 <strong>Test-CsTopology</strong> cmdlet에서 유효성 검사를 지정된 서비스로 제한합니다. Service 매개 변수를 사용하는 경우 한 번에 하나의 서비스만 지정할 수 있습니다. 적절한 서비스 ID를 사용하여 서비스를 지정해야 합니다. 예를 들어 -Service &quot;Registrar:atl-cs-001.litwareinc.com&quot; 구문은 atl-cs-001.litwareinc.com 풀의 등록자 서비스를 나타냅니다.</p>
<p>이 매개 변수를 포함하지 않으면 전체 토폴로지의 유효성이 검사됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsTopology** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsTopology** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Enable-CsTopology](enable-cstopology.md)  
[Get-CsTopology](get-cstopology.md)  
[Publish-CsTopology](publish-cstopology.md)

