---
title: Export-CsLisConfiguration
TOCTitle: Export-CsLisConfiguration
ms:assetid: 714bd67e-4cd6-4066-a065-59f7e079b6ad
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398539(v=OCS.15)
ms:contentKeyID: 49304003
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Export-CsLisConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Enterprise Voice E9-1-1(Enhanced 9-1-1) 구성을 백업을 위해 압축 형식의 파일로 내보냅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Export-CsLisConfiguration -FileName <String> <COMMON PARAMETERS>

    Export-CsLisConfiguration [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

이 예제에서는 LIS(위치 정보 서버)의 전체 E9-1-1 구성을 E911Config.back이라는 백업 파일로 내보냅니다.

    Export-CsLisConfiguration -FileName C:\E911Config.bak

## 예제 2

이 예제에서 LIS 구성은 변수 $lisconfig에 바이트 배열로 저장됩니다.

    $lisconfig = Export-CsLisConfiguration -AsBytes

## 예제 3

예제 3은 예제 2의 보다 완전한 버전입니다. 첫째 줄은 동일합니다. AsBytes 매개 변수와 함께 **Export-CsLisConfiguration** cmdlet을 호출하여 LIS 구성을 변수 $lisconfig에 바이트 배열로 저장합니다. 이 예제의 나머지 부분에서는 이 구성을 파일로 저장한 다음 위치 구성 데이터베이스로 다시 가져오는 방법을 보여 줍니다.

둘째 줄은 LIS 구성을 나타내는 바이트 배열인 $lisconfig의 내용을 Windows PowerShell **Set-Content** cmdlet에 파이프합니다. **Set-Content** cmdlet의 두 매개 변수 Path와 Encoding에 값을 할당합니다. 구성을 저장할 파일의 전체 경로와 파일 이름을 Path 매개 변수에 할당합니다. Encoding 매개 변수에는 byte 값을 사용하여 구성이 바이트 배열로 저장되도록 합니다.

마지막으로 셋째 줄에서 위치 구성 데이터베이스로 구성을 다시 가져옵니다. 먼저 **Get-Content** cmdlet을 호출하여 파일의 내용을 검색합니다. ReadCount 속성에 0 값을 전달하여 **Get-Content** cmdlet에 파일의 내용을 한 번에 한 줄씩이 아니라 한꺼번에 모두 읽도록 지시합니다. 다시 Encoding 매개 변수에 byte 값을 사용하여 파일에서 읽는 데이터의 형식을 지정합니다. 마지막으로 파일 이름을 Path 매개 변수에 전달합니다. **Get-Content** cmdlet을 사용하여 읽은 파일의 내용은 저장된 구성을 위치 데이터베이스로 가져오는 **Import-CsLisConfiguration** cmdlet에 파이프됩니다.

    $lisconfig = Export-CsLisConfiguration -AsBytes
    $lisconfig | Set-Content -Path C:\E911Config.bak -Encoding byte
    Get-Content -ReadCount 0 -Encoding byte -Path C:\E911Config.bak  | Import-CsLisConfiguration

## 자세한 정보

조직에서 E9-1-1을 구현하려면 조직의 규모에 따라 수천 개의 서브넷, 포트, 스위치 및 WAP(무선 액세스 지점)를 위치에 매핑하는 작업이 필요합니다. 또한 E9-1-1 구성에는 E9-1-1 네트워크 경로 지정 공급자에서 제공하는 웹 서비스에 대한 정보, 위치 및 구/군/시 주소에 대한 정보, 그리고 이러한 항목들의 유효성이 검사되었는지 여부에 대한 정보도 포함됩니다. E9-1-1을 구현하는 데 필요한 정보 및 설정의 규모를 감안할 때 전체 구성을 정기적으로 백업하는 것이 좋습니다. 이 cmdlet을 사용하여 E9-1-1 구성을 파일로 백업할 수 있습니다. 이 파일은 전체 구성을 압축 형식으로 저장합니다. 구성을 복구하려면 **Import-CsLisConfiguration** cmdlet을 호출합니다.

이 cmdlet은 새 백업 파일을 만들며 기존 파일은 덮어쓰지 않습니다. 즉, 이 cmdlet에 대한 호출에 지정된 파일 이름은 기존 파일 이름일 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Export-CsLisConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsLisConfiguration"}

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
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>구성을 저장할 파일의 경로 및 파일 이름입니다. 기존 파일 이름일 수 없습니다.</p>
<p>AsBytes 매개 변수에 값을 지정할 경우 FileName 매개 변수에는 값을 지정할 수 없습니다. 이 cmdlet에 원격으로 액세스하는 경우 FileName이 아닌 AsBytes를 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AsBytes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>구성을 바이트 배열로 반환합니다. 명령의 출력은 이후 가져오기 작업을 위해 변수에 할당해야 합니다. 출력을 변수에 할당하지 않으면 구성을 나타내는 바이트 배열이 Lync Server 관리 셸 창 아래로 스크롤됩니다.) AsBytes 매개 변수와 FileName 매개 변수를 함께 지정할 수는 없습니다. 이 cmdlet에 대한 각 호출에서 둘 중 하나만 사용할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

AsBytes 매개 변수가 사용되는 경우 바이트 배열(Byte\[\])을 반환합니다.

## 참고 항목

#### 기타 리소스

[Import-CsLisConfiguration](import-cslisconfiguration.md)  
[Debug-CsLisConfiguration](debug-cslisconfiguration.md)  
[Publish-CsLisConfiguration](publish-cslisconfiguration.md)  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

