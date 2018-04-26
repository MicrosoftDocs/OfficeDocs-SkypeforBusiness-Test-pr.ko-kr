---
title: Enable-CsComputer
TOCTitle: Enable-CsComputer
ms:assetid: ac014030-4cd0-4503-b70e-12ab5b0ec34b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412815(v=OCS.15)
ms:contentKeyID: 49304695
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enable-CsComputer

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 실행 중인 컴퓨터에서 새 서비스나 서버 역할 또는 새로 업데이트된 서비스나 서버 역할을 사용하도록 설정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Enable-CsComputer [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터에 설치된 모든 새 Lync Server 서비스 또는 서버 역할을 활성화합니다.

    Enable-CsComputer

## 예제 2

예제 2에서도 로컬 컴퓨터에 설치된 모든 새 Lync Server 서비스 또는 서버 역할을 활성화합니다. 그러나 이 경우에는 Verbose 매개 변수를 추가하여 **Enable-CsComputer** cmdlet으로 수행되는 작업의 단계별 계정이 화면에 보고되도록 합니다.

    Enable-CsComputer -Verbose

## 자세한 정보

필요한 소프트웨어를 설치한다고 해서 컴퓨터가 새 서비스 역할을 자동으로 채택하는 것은 아닙니다. 대신 컴퓨터를 사용하도록 설정해야 실제로 새 역할에서 작동을 시작합니다. **Enable-CsComputer** cmdlet을 사용하면 관리자가 새로 업데이트된 서비스 또는 서버 역할을 로컬 컴퓨터에 사용하도록 설정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: **Enable-CsComputer** cmdlet을 로컬로 실행하려면 로컬 관리자 및 도메인 구성원이어야 합니다.

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
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인의 계정을 가진 컴퓨터에서 <strong>Enable-CsComputer</strong> cmdlet을 실행하는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory의 시스템 컨테이너에 저장되는 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다 (예: -Report &quot;C:\Logs\EnableComputer.html&quot;).</p></td>
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

없음. **Enable-CsComputer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Enable-CsComputer** cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.Machine 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsComputer](disable-cscomputer.md)  
[Get-CsComputer](get-cscomputer.md)  
[Test-CsComputer](test-cscomputer.md)

