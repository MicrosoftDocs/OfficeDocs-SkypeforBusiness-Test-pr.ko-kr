---
title: Test-CsReplica
TOCTitle: Test-CsReplica
ms:assetid: cef1fcda-3292-411a-b3dd-7a8ef7935b20
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205289(v=OCS.15)
ms:contentKeyID: 49305080
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsReplica

 

_**마지막으로 수정된 항목:** 2015-03-09_

로컬 컴퓨터에서 복제본 서비스의 상태를 확인합니다. 복제본 서비스는 토폴로지의 모든 Lync Server 2013 컴퓨터에서 정보를 복제하는 데 사용됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsReplica [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터에서 Lync Server 2013 복제본 서비스를 테스트합니다. 이 예제에서는 Verbose 매개 변수를 사용하여 테스트에 대한 정보(테스트 최종 성공/실패 및 테스트에서 생성된 보고서의 위치 포함)를 화면에 표시합니다.

    Test-CsReplica -Verbose

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 그러나 이 경우에는 Report 매개 변수를 포함하여 테스트에서 생성되는 보고서의 폴더 경로와 이름을 지정합니다. 보고서 경로를 지정하지 않으면 보고서에 다음과 같은 자동 생성 이름이 지정됩니다.

C:\\Users\\Administrator.Litwareinc\\AppData\\Local\\Temp\\1\\Test-Cs-Replica-3db40ee0-4b5d-4f58-8d3d-b1e61253129e.html

    Test-CsReplica -Verbose -Report C:\Logs\ReplicaTest.html

## 자세한 정보

**Test-CsReplica** cmdlet은 Lync Server 2013 복제본 서비스가 로컬 컴퓨터에서 실행되고 있는지 확인합니다. **Test-CsReplica** cmdlet은 복제기 에이전트 및 중앙 로깅 서비스 에이전트 서비스의 상태를 확인하고, 필요한 포트가 Windows 방화벽에서 열렸는지 여부를 확인하고, 필요한 Active Directory 및 로컬 컴퓨터 보안 그룹이 있는지를 확인하는 등의 작업을 수행합니다.

이 cmdlet은 로컬로, 즉 복제본 서비스가 실행되고 있는 것과 같은 컴퓨터에서 실행해야 합니다. 원격 서버에 대해 **Test-CsReplica** cmdlet을 실행하는 옵션은 없습니다.

**Lync Server 제어판:** **Test-CsReplica** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>도메인에 있는 전역 카탈로그 서버의 정규화된 도메인 이름입니다. 사용자 도메인의 계정으로 컴퓨터에서 <strong>Test-CsReplica</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 도메인 컨트롤러의 정규화된 도메인 이름입니다. 사용자 도메인의 계정으로 컴퓨터에서 <strong>Test-CsReplica</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다.</p>
<p>-Report &quot;C:\Logs\ReplicaTest.html&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsReplica** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsReplica** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

