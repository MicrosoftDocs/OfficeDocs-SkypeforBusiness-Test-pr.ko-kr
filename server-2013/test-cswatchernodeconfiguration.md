---
title: Test-CsWatcherNodeConfiguration
TOCTitle: Test-CsWatcherNodeConfiguration
ms:assetid: 085507a1-17e8-4dfa-aa6a-062620584335
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204652(v=OCS.15)
ms:contentKeyID: 49302721
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsWatcherNodeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용되는 감시자 노드 구성 설정을 확인합니다. 감시자 노드는 주기적으로 Microsoft System Center Operations Manager 2007 R2 및 Lync Server 2013 가상 트랜잭션을 사용하여 Lync Server 구성 요소가 예상대로 작동하고 있는지를 확인하는 컴퓨터입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsWatcherNodeConfiguration [-FileName <String>] [-ReadCredentialsFromCurrentUserStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용되는 각 감시자 노드에 대한 구성 설정을 확인합니다.

    Test-CsWatcherNodeConfiguration

## 자세한 정보

Microsoft System Center Operations Manager를 사용하여 Lync Server 2013을 모니터링하는 경우에는 "감시자 노드", 즉 주기적으로 가상 트랜잭션을 자동 실행하여 Lync Server가 예상대로 작동하고 있는지를 확인하는 컴퓨터를 설정할 수 있습니다. 감시자 노드는 풀에 할당되며 **CsWatcherNodeConfiguration** cmdlet을 사용하여 관리됩니다. System Center Operations Manager를 사용 중이라면 감시자 노드를 설치할 필요가 없습니다. 감시자 노드를 사용하지 않고도 시스템을 모니터링할 수 있으며, 감시자 노드 사용 시와의 차이는 실행하려는 가상 트랜잭션이 Operations Manager를 통해 자동으로 호출되지 않으므로 해당 트랜잭션을 수동으로 호출해야 한다는 것뿐입니다.

**Test-CsWatcherNodeConfiguration** cmdlet을 사용하면 감시자 노드가 올바르게 구성되었으며 유효한 Lync Server 2013 풀에 할당되었는지를 확인할 수 있습니다. **Test-CsWatcherNodeConfiguration** cmdlet은 감시자 노드 자체에 대해 실행해야 하며 원격 컴퓨터에 대해서는 실행할 수 없습니다.

**Lync Server 제어판:** **Test-CsWatcherNodeConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>FileName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다.</p>
<p>-Report &quot;C:\Logs\WatcherNode.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>ReadCredentialsFromCurrentUserStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 사용자의 자격 증명 저장소에서 사용자 자격 증명을 검색하도록 <strong>Test-CsWatcherNodeConfiguration</strong> cmdlet에 명령합니다. 기본적으로 <strong>Test-CsWatcherNodeConfiguration</strong> cmdlet은 네트워크 서비스 계정의 자격 증명 저장소에서 자격 증명을 찾습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsWatcherNodeConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsWatcherNodeConfiguration** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)  
[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)  
[Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)

