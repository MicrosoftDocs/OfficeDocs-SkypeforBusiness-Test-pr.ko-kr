---
title: Import-CsLisConfiguration
TOCTitle: Import-CsLisConfiguration
ms:assetid: 579c0c38-311b-4961-b924-11731403d9f2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398380(v=OCS.15)
ms:contentKeyID: 49303692
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsLisConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

백업 파일에서 Enterprise Voice E9-1-1(Enhanced 9-1-1) 구성을 가져옵니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Import-CsLisConfiguration -FileName <String> <COMMON PARAMETERS>

    Import-CsLisConfiguration -ByteInput <Byte[]> <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

이 예제에서는 E911Config.back이라는 백업 파일에서 위치 구성 데이터베이스로 E9-1-1 구성을 가져옵니다.

    Import-CsLisConfiguration -FileName C:\E911Config.bak

## 예제 2

예제 2에서는 **Import-CsLisConfiguration** cmdlet의 ByteInput 매개 변수를 사용하는 방법을 보여 줍니다. 첫 번째 줄은 AsBytes 매개 변수와 함께 **Export-CsLisConfiguration** cmdlet을 호출합니다. 명령은 LIS 구성을 포함하는 바이트 배열을 출력합니다. 이 배열은 변수 $lisconfig에 할당됩니다. 두 번째 줄은 **Import-CsLisConfiguration** cmdlet을 호출합니다. ByteInput 매개 변수는 내보낸 바이트 배열을 포함하는 변수인 $lisconfig의 값을 받습니다. 그러면 이 바이트 배열을 위치 구성 데이터베이스로 다시 가져옵니다.

    $lisconfig = Export-CsLisConfiguration -AsBytes 
    Import-CsLisConfiguration -ByteInput $lisconfig

## 예제 3

예제 3은 예제 2의 보다 완전한 버전입니다. 첫째 줄은 동일합니다. AsBytes 매개 변수와 함께 **Export-CsLisConfiguration** cmdlet을 호출하여 LIS 구성을 변수 $lisconfig에 바이트 배열로 저장합니다. 이 예제의 나머지 부분에서는 이 구성을 파일로 저장한 다음 위치 구성 데이터베이스로 다시 가져오는 방법을 보여 줍니다.

둘째 줄은 LIS 구성을 나타내는 바이트 배열인 $lisconfig의 내용을 Windows PowerShell **Set-Content** cmdlet에 파이프합니다. **Set-Content** cmdlet의 두 매개 변수 Path와 Encoding에 값을 할당합니다. 구성을 저장할 파일의 전체 경로와 파일 이름을 Path 매개 변수에 할당합니다. Encoding 매개 변수에는 byte 값을 사용하여 구성이 바이트 배열로 저장되도록 합니다.

마지막으로 셋째 줄에서 위치 구성 데이터베이스로 구성을 다시 가져옵니다. 먼저 **Get-Content** cmdlet을 호출하여 파일의 내용을 검색합니다. ReadCount 속성에 0 값을 전달하여 **Get-Content** cmdlet에 파일의 내용을 한 번에 한 줄씩이 아니라 한꺼번에 모두 읽도록 지시합니다. 이번에도 다시 Encoding 매개 변수에 byte 값을 사용하여 파일에서 읽을 데이터의 형식을 지정합니다. 마지막으로 파일 이름을 Path 매개 변수에 전달합니다. **Get-Content** cmdlet을 사용하여 읽은 파일의 내용은 저장된 구성을 위치 구성 데이터베이스로 가져오는 **Import-CsLisConfiguration** cmdlet에 파이프됩니다.

    $lisconfig = Export-CsLisConfiguration -AsBytes
    $listconfig | Set-Content -Path C:\E911Config.bak -Encoding byte
    Get-Content -ReadCount 0 -Encoding byte -Path C:\E911Config.bak | Import-CsLisConfiguration

## 자세한 정보

조직에서 E9-1-1을 구현하려면 조직의 규모에 따라 수천 개의 서브넷, 포트, 스위치 및 무선 액세스 지점을 위치에 매핑하는 작업이 필요합니다. 또한 E9-1-1 구성에는 E9-1-1 네트워크 경로 지정 공급자에서 제공하는 LIS(위치 정보 서버)에 대한 정보, 위치 및 도시 주소에 대한 정보, 그리고 이러한 항목들의 유효성이 검사되었는지 여부에 대한 정보도 포함됩니다. E9-1-1을 구현하는 데 필요한 정보와 설정의 규모를 감안할 때 전체 구성을 정기적으로 백업하는 것이 좋습니다. **Export-CsLisConfiguration** cmdlet을 호출하여 전체 E9-1-1 구성을 파일에 백업할 수 있습니다. **Import-CsLisConfiguration** cmdlet을 호출하면 해당 파일에서 구성을 복원합니다.

이 cmdlet을 호출하여 구성을 복원하더라도 기존 구성을 덮어쓰지는 않습니다. 제거된 정보는 삽입하지만 백업이 만들어진 이후에 추가된 기존 레코드를 제거하지는 않습니다.

중요: 백업에서 가져오기는 기존 레코드를 바꾸지 않고 변경된 레코드가 복원되므로 고립된 위치에 놓일 수 있습니다. 예를 들어 Location 값이 Building30/Room10인 WAP(무선 액세스 지점)를 정의했다고 가정해 보겠습니다. **Export-CsLisConfiguration** cmdlet을 호출하여 이 구성을 백업할 수 있습니다. 나중에 무선 액세스 지점의 Location 속성을 Building30/Rooms20-40으로 수정한 경우 **Import-CsLisConfiguration** cmdlet을 호출하여 백업된 구성을 복원합니다. 그러면 해당 WAP의 위치는 Building30/Room10(백업 전의 위치)이 되지만 Building30/Rooms20-40의 위치는 위치 구성 데이터베이스에 그대로 유지됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Import-CsLisConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsLisConfiguration"}

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
<td><p><em>ByteInput</em></p></td>
<td><p>필수</p></td>
<td><p>System.Byte[]</p></td>
<td><p>이 매개 변수에 전달되는 값은 <strong>Export-CsLisConfiguration</strong> cmdlet과 AsBytes 매개 변수를 사용하여 만든 LIS 구성의 바이트 배열을 포함하는 변수입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>구성을 가져올 백업 파일의 이름입니다. FileName과 ByteInput을 함께 지정할 수는 없습니다. 이 cmdlet을 호출할 때는 이러한 두 매개 변수 중 하나만 사용할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

바이트\[\]. 내보낸 LIS 구성의 바이트 배열을 허용합니다. 바이트 배열은 단일 레코드로 파이프되어야 합니다. 예제 3을 참조하십시오.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Export-CsLisConfiguration](export-cslisconfiguration.md)  
[Publish-CsLisConfiguration](publish-cslisconfiguration.md)  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)  
[Debug-CsLisConfiguration](debug-cslisconfiguration.md)  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

