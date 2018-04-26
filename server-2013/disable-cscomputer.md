---
title: Disable-CsComputer
TOCTitle: Disable-CsComputer
ms:assetid: e64128f1-2b53-4569-bf37-90cbbba01b36
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399023(v=OCS.15)
ms:contentKeyID: 49305351
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsComputer

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 실행하는 컴퓨터에서 제거된 서비스 또는 서버 역할을 사용하지 않도록 설정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Disable-CsComputer [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-Scorch <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 컴퓨터를 비활성화합니다.

    Disable-CsComputer 

## 예제 2

예제 2에 표시된 명령도 로컬 컴퓨터를 비활성화합니다. 그러나 이 명령은 그 외에도 해당 작업의 성공 또는 실패에 대한 정보를 C:\\Logs\\Disable.html 파일에 기록합니다. 이 로그 파일은 -Report 매개 변수 뒤에 정보를 기록할 로그 파일의 경로를 포함하면 생성됩니다.

    Disable-CsComputer -Report C:\Logs\Disable.html

## 자세한 정보

서비스 또는 서버 역할을 컴퓨터에서 제거한 경우 Lync Server 토폴로지가 자동으로 업데이트되지 않습니다. 변경 내용을 토폴로지에서 완전히 업데이트하려면 해당 서비스 또는 역할을 사용하지 않도록 설정해야 합니다. **Disable-CsComputer** cmdlet을 사용하면 관리자가 로컬 컴퓨터에서 제거된 서비스 또는 서버 역할을 사용하지 않도록 설정할 수 있습니다.

Scorch 매개 변수를 사용하지 않으면 **Disable-CsComputer** cmdlet이 Lync Server 소프트웨어를 제거하지 않습니다. 대신 컴퓨터가 이전에 할당된 역할을 수행하지 못하도록 합니다.

이 cmdlet을 실행할 수 있는 사용자: **Disable-CsComputer** cmdlet을 로컬로 실행하려면 로컬 관리자 및 도메인 구성원이어야 합니다.

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
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 도메인의 계정이 있는 컴퓨터에서 <strong>Disable-CsComputer</strong> cmdlet을 실행하는 경우 이 매개 변수는 필요 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory 도메인 서비스의 시스템 컨테이너에 저장되는 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\DisableComputer.html&quot;)</p></td>
</tr>
<tr class="even">
<td><p><em>Scorch</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>로컬 컴퓨터에 대한 모든 Lync Server 서비스 및 서버 역할을 제거합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Disable-CsComputer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신에 **Disable-CsComputer** cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.Machine 개체의 인스턴스를 사용하지 않도록 설정합니다.

## 참고 항목

#### 기타 리소스

[Enable-CsComputer](enable-cscomputer.md)  
[Get-CsComputer](get-cscomputer.md)  
[Test-CsComputer](test-cscomputer.md)

