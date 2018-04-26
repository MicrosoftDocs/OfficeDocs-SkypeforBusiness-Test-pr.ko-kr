---
title: Test-CsComputer
TOCTitle: Test-CsComputer
ms:assetid: 0b33d951-510d-445c-9b01-c6431fda6d47
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398162(v=OCS.15)
ms:contentKeyID: 49302765
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsComputer

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Test-CsComputer** cmdlet은 로컬 컴퓨터에서 실행 중인 Lync Server 서비스의 상태를 확인합니다. 또한 이 cmdlet은 적절한 Lync Server Active Directory 그룹이 컴퓨터의 해당 로컬 그룹에 추가되었는지, 필요한 컴퓨터 방화벽 포트가 열렸는지 확인합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsComputer [-Report <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터의 서비스 활성화 상태를 확인합니다. 작업 성공(또는 실패)이 화면에 자세히 보고되도록 Verbose 매개 변수가 명령에 포함됩니다.

    Test-CsComputer -Verbose

## 예제 2

예제 2에서는 로컬 컴퓨터의 서비스 활성화 상태도 확인합니다. 또한 이 명령은 활성화 상태에 대한 자세한 정보를 C:\\Logs\\Computer.html 파일에 씁니다. 이 로그는 Report 매개 변수 뒤에 정보가 기록될 로그 파일의 전체 경로를 포함하면 생성됩니다.

    Test-CsComputer -Verbose -Report C:\Logs\Computer.html

## 자세한 정보

**Test-CsComputer** cmdlet은 Lync Server "가상 트랜잭션"의 한 예입니다. 가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 수동으로 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

로컬 컴퓨터에서만 실행할 수 있는 **Test-CsComputer** cmdlet은 해당 컴퓨터에 있는 모든 Lync Server 서비스의 상태를 확인합니다. 또한 이 cmdlet은 컴퓨터에서 적절한 방화벽 포트가 열렸는지, Lync Server를 설치할 때 만들어진 Active Directory 그룹이 해당 로컬 그룹에 추가되었는지 확인합니다. 예를 들어 **Test-CsComputer** cmdlet은 Active Directory 그룹인 RTCUniversalUserAdmins가 로컬 관리자 그룹에 추가되었는지 확인합니다.

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
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\Computer.html&quot;). 이 파일이 이미 있는 경우 cmdlet을 실행하면 파일을 덮어씁니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsComputer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsComputer** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsComputer](disable-cscomputer.md)  
[Enable-CsComputer](enable-cscomputer.md)  
[Get-CsComputer](get-cscomputer.md)

