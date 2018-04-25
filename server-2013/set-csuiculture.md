---
title: Set-CsUICulture
TOCTitle: Set-CsUICulture
ms:assetid: 53fbc126-1df9-4ea0-8055-4e9530ab89d6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398354(v=OCS.15)
ms:contentKeyID: 49303660
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUICulture

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 관리 셸에서 사용되는 문화권(언어 및 국가별 설정)을 수정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUICulture -Culture <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 관리 셸의 문화권을 영어(미국)로 설정합니다. 이를 위해 언어 코드 en-US를 사용합니다.

    Set-CsUICulture -Culture "en-US"

## 예제 2

예제 2에서는 Lync Server 관리 셸의 문화권을 기본 문화권 값으로 설정합니다. 기본값은 원래 Lync Server를 설치할 때 사용된 문화권입니다.

    Set-CsUICulture -Culture "default"

## 자세한 정보

Lync Server를 여러 언어로 사용할 수 있지만 이 소프트웨어는 실제로 MUI(다국어 사용자 인터페이스) 응용 프로그램이 아닙니다. 특히 이는 운영 체제 언어를 변경할 때 Lync Server 관리 셸의 사용자 인터페이스 언어가 변경되지 않음을 의미합니다. 예를 들어 영어(미국) 버전의 Lync Server를 설치하고 영어(미국) 버전의 Windows 운영 체제를 실행 중인 경우, 운영 체제 문화권(즉, 언어 및 지역 설정)을 한국어로 변경하면 Lync Server 관리 셸이 그에 맞게 자동으로 변경되지 않고 대신 오류 메시지 및 도움말 텍스트를 포함하여 Lync Server 관리 셸 사용자 인터페이스가 영어(미국)로 유지됩니다. Lync Server 관리 셸의 문화권을 변경하려면 **Set-CsUICulture** cmdlet을 실행해야 합니다.

**Set-CsUICulture** cmdlet을 사용할 때 두 가지 사항에 유의해야 합니다. 첫째, 로컬 컴퓨터의 Lync Server 관리 셸 설정을 수정하는 데만 cmdlet을 사용할 수 있습니다. **Set-CsUICulture** cmdlet으로 Lync Server 관리 셸의 원격 인스턴스를 변경할 수는 없습니다. 이는 컴퓨터의 모든 사용자가 Lync Server 관리 셸의 동일한 인스턴스를 공유하기 때문입니다. 즉, 원격 사용자가 문화권을 변경하도록 허용하면 로컬 사용자를 비롯한 Lync Server 관리 셸의 다른 모든 사용자에 대한 문화권이 즉시 변경됩니다.

둘째, 언어를 미국 영어("en-US") 또는 Lync Server을 처음 설치할 때 사용된 언어("기본값")로만 설정할 수 있습니다. 예를 들어, 원래 Lync Server의 이탈리아어 버전을 설치한 경우 UI 문화권을 영어 또는 이탈리아어로 구성하는 두 가지 옵션이 제공됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Set-CsUICulture** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p><em>Culture</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관리 셸에 사용되는 문화권을 지정하는 데 사용됩니다. 문화권을 미국 영어의 &quot;en-US&quot;로 설정하거나, 원래 Lync Server를 설치할 때 사용된 언어를 사용하려면 문화권을 &quot;기본값&quot;으로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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

없음. **Set-CsUICulture** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Set-CsUICulture** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 System.Globalization.CultureInfo 클래스의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUICulture](get-csuiculture.md)

