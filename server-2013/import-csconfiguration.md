---
title: Import-CsConfiguration
TOCTitle: Import-CsConfiguration
ms:assetid: 9a9c27f2-313c-4327-aeed-c47852a831ec
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398800(v=OCS.15)
ms:contentKeyID: 49304497
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 토폴로지, 정책 및 구성 설정을 중앙 관리 저장소 또는 로컬 컴퓨터로 가져옵니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Import-CsConfiguration -ByteInput <Byte[]> <COMMON PARAMETERS>

    Import-CsConfiguration -FileName <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 C:\\Config.zip 파일에서 현재 토폴로지, 구성 설정 및 정책을 중앙 관리 저장소로 가져옵니다.

    Import-CsConfiguration -FileName "C:\Config.zip"

## 예제 2

예제 2에서는 경계 네트워크에 있는 컴퓨터로 데이터를 초기에 복제하는 방법을 보여 줍니다. 이 예제에서는 구성 데이터를 Config.zip 파일로 내보낸 다음 이 파일을 경계 네트워크에 있는 컴퓨터의 C:\\ 폴더에 복사합니다. 그런 다음 Import-CsConfiguration과 LocalStore 매개 변수를 사용하여 데이터를 가져옵니다. 이 매개 변수는 데이터를 중앙 관리 저장소 대신 로컬 컴퓨터로 가져오게 합니다.

    Import-CsConfiguration -FileName "C:\Config.zip" -LocalStore

## 예제 3

예제 3에 표시된 두 명령은 현재 토폴로지, 구성 설정 및 정책을 내보낸 다음 .ZIP 파일을 사용하지 않고 해당 데이터를 모두 로컬 컴퓨터로 가져옵니다. 이 작업을 수행하기 위해 첫 번째 명령은 **Export-CsConfiguration** cmdlet 및 AsBytes 매개 변수를 사용하여 현재 토폴로지, 구성 설정 및 정책을 바이트 배열로 내보냅니다. 이 바이트 배열은 $x라는 변수에 저장됩니다. 두 번째 명령은 **Import-CsConfiguration** cmdlet 및 ByteInput 매개 변수를 사용하여 $x에 저장된 정보를 가져옵니다. LocalStore 매개 변수는 데이터를 중앙 관리 저장소 대신 로컬 컴퓨터로 가져오게 합니다. 결과적으로 이 데이터는 중앙 관리 저장소에서 로컬 컴퓨터로 복사됩니다.

    $x = Export-CsConfiguration -AsBytes
    Import-CsConfiguration -ByteInput $x -LocalStore

## 자세한 정보

Lync Server 서비스 또는 서버 역할을 실행하는 컴퓨터는 현재 토폴로지, 현재 구성 설정 및 현재 정책의 복사본이 있어야 지정된 역할을 제대로 수행할 수 있습니다. Lync Server는 이러한 정보가 해당 컴퓨터에 제대로 전달되도록 합니다.

Import-CsConfiguration 및 Export-CsConfiguration cmdlet은 중앙 관리 저장소를 업그레이드하는 동안 Lync Server 토폴로지, 구성 설정 및 정책을 백업 및 복원하는 데 사용됩니다. **Export-CsConfiguration** cmdlet을 사용하여 데이터를 .ZIP 파일로 내보낸 다음 **Import-CsConfiguration** cmdlet을 사용하여 해당 .ZIP 파일을 읽고 토폴로지, 설정 및 정책을 중앙 관리 저장소로 복원할 수 있습니다. 그런 다음 Lync Server의 복제 서비스는 복원된 정보를 서비스를 실행하는 컴퓨터에 복제합니다.

구성 데이터 내보내기/가져오기 기능은 경계 네트워크(예: 에지 서버)에 있는 컴퓨터를 처음 구성할 때도 사용됩니다. 경계 네트워크에 있는 컴퓨터를 구성할 때는 먼저 CsConfiguration cmdlet을 사용하여 수동 복제를 수행해야 합니다. 이를 수행하려면 **Export-CsConfiguration** cmdlet을 사용하여 구성 데이터를 내보낸 다음 경계 네트워크의 컴퓨터에 .ZIP 파일을 복사해야 합니다. 이렇게 하면 나중에 **Import-CsConfiguration** cmdlet 및 LocalStore 매개 변수를 사용하여 데이터를 가져올 수 있습니다. 이 작업을 한 번만 수행하면 자동으로 복제됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Import-CsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 또한 이 cmdlet을 실행하려면 RTCUniversalServerAdmins 그룹의 구성원인 동시에 로컬 관리자이거나 로컬 구성 복제자 권한을 가지고 있어야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsConfiguration"}

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
<td><p>변수에 저장된 바이트 배열에서 토폴로지 정보를 읽습니다. <strong>Export-CsConfiguration</strong> cmdlet을 호출할 때 ByteInput 매개 변수를 사용하면 이 바이트 배열이 생성됩니다.</p>
<p>같은 명령에서 ByteInput 매개 변수와 FileName 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Export-CsConfiguration에 의해 생성되는 .ZIP 파일의 경로입니다(예: -FileName &quot;C:\Config.zip&quot;). <strong>Import-CsConfiguration</strong> cmdlet을 호출할 때 FileName 또는 ByteInput 매개 변수 중 하나를 포함해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 심각하지 않은 오류 메시지가 발생하는 경우 표시될 수 있는 확인 메시지를 생략합니다. Force 매개 변수를 True로 설정하려면 다음 구문을 사용합니다.</p>
<p>-Force:$True</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소가 아니라 로컬 컴퓨터에 구성 데이터를 복사합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Import-CsConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Import-CsConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Export-CsConfiguration](export-csconfiguration.md)

