---
title: New-CsAutodiscoverConfiguration
TOCTitle: New-CsAutodiscoverConfiguration
ms:assetid: 6b878b0e-f0c0-46a2-99b8-fd2105250600
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690022(v=OCS.15)
ms:contentKeyID: 49303953
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsAutodiscoverConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사이트 범위에서 자동 검색 구성 설정의 새 컬렉션을 만듭니다. 자동 검색 서비스를 사용하면 Lync Web App 또는 Microsoft Lync Mobile 등의 클라이언트 응용 프로그램에서 사용자의 홈 풀 또는 전화 접속 회의 참가용 URL 같은 주요 리소스를 찾을 수 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    New-CsAutodiscoverConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-ExternalSipClientAccessFqdn <String>] [-ExternalSipClientAccessPort <UInt32>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WebLinks <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령에서는 Redmond 사이트에 대한 자동 검색 구성 설정의 새 컬렉션을 만듭니다. WebLinks 매개 변수를 포함하지 않았기 때문에 이러한 설정에는 자동 검색 URL이 포함되지 않습니다.

    New-CsAutoDiscoverConfiguration -Identity "site:Redmond"

## 예제 2

예제 2에 표시된 명령에서는 Redmond 사이트에 대한 자동 검색 구성 설정의 새 컬렉션을 만들고 이러한 새 설정에 한 쌍의 자동 검색 URL(http://LyncDiscover.fabrikam.com 및 http://LyncDiscoverInternal.fabrikam.com)을 할당합니다. 이 작업을 수행하기 위해 처음 두 명령은 **New-CsWebLink** cmdlet을 사용하여 두 개의 자동 검색URL을 만듭니다. 그러면 새로 만들어진 URL은 각각 $Link1 및 $Link2라는 변수에 저장됩니다. 두 URL이 만들어지면 세 번째 명령은 **New-CsAutoDiscoverConfiguration** cmdlet을 사용하여 새 자동 검색 구성 설정을 만듭니다. 두 개의 URL을 이러한 설정에 할당하기 위해 WebLinks 매개 변수와 함께 매개 변수 값 @{Add=$Link1,$Link2}를 포함합니다. 이 구문은 변수 $Link1 및 $Link2에 저장된 값이 WebLinks 속성에 추가되도록 합니다.

    $Link1 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscover.fabrikam.com"
    $Link2 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscoverInternal.fabrikam.com"
    
    New-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Add=$Link1,$Link2}

## 자세한 정보

클라이언트 응용 프로그램에서 Lync Server를 최대한 효과적으로 사용하도록 하려면 이러한 응용 프로그램에서 주요 Lync Server 구성 요소의 위치를 인식하고 있어야 합니다. 예를 들어 인증된 사용자가 해당 홈 풀을 찾을 수 있어야 합니다. 즉, 이러한 사용자는 해당 홈 풀을 통해서만 인증될 수 있습니다. 마찬가지로, 인증되지 않은 사용자가 전화 회의에 참가하는 데 사용되는 URL을 찾는 등의 작업을 수행할 수 있어야 합니다.

모든 사용자가 조직의 방화벽 뒤에서 로그온한 경우에는 이러한 위치를 검색하기가 비교적 쉽습니다. 하지만 사용자가 Microsoft Lync Mobile 또는 Lync Web App을 사용하여 외부 위치에서 시스템에 액세스하게 되면 이처럼 비교적 단순한 작업도 점점 더 복잡해집니다.

이는 분할 도메인 시나리오에서 특히 심하게 나타나는데, 이러한 시나리오의 경우 조직의 일부 사용자는 온-프레미스 버전의 Lync Server에 계정을 가지고 있지만 다른 사용자는 비즈니스용 Skype Online에 계정을 가지고 있습니다. 이 경우 사용자 계정이 각기 다른 Active Directory 포리스트에 있을 수 있는데, 이렇게 되면 특정한 문제가 발생할 수 있습니다. 예를 들어 미국의 사용자가 유럽에서 로그온하는 경우 시스템에서는 이 사용자의 포리스트를 인식한 다음 로그온 요청을 적절한 풀에 조회할 수 있어야 합니다.

자동 검색 서비스는 바로 이러한 문제를 해결하기 위해 Lync Server 2011년 11월 누적 업데이트에 도입되었습니다. 클라이언트 응용 프로그램이 Lync Server에 액세스를 시도하면 자동 검색 서비스에서는 클라이언트 SIP 주소를 구문 분석한 다음 해당 요청을 적절한 풀로 리디렉션합니다. 클라이언트 응용 프로그램은 HTTP 요청을 자동 검색 URL로 보내는 방식으로 자동 검색 서비스에 연결되는데, 자동 검색 서비스가 올바르게 작동하려면 관리자가 이러한 URL을 구성해야 합니다. 참고적으로, URL을 구성하는 것 외에도 관리자는 이러한 URL에 해당하는 DNS 레코드를 만들어야 합니다.

자동 검색 URL은 자동 검색 구성 설정에 할당되며, 이를 통해 이러한 설정을 전역 범위나 사이트 범위에 할당할 수 있습니다. Lync Server를 설치하면 설정의 전역 컬렉션이 자동으로 만들어집니다. 그러나 이 컬렉션에 자동 검색 URL이 할당되지는 않습니다. 자동 검색 설정 컬렉션 하나로 요구 사항이 해결되지 않는 경우에는 **New-CsAutoDiscoverConfiguration** cmdlet을 사용하여 사이트 범위에서 추가 구성 설정을 만들 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsAutoDiscoverConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 자동 검색 구성 설정 컬렉션의 고유 식별자입니다. 사이트 범위에서 구성된 컬렉션을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExternalSipClientAccessFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>외부 클라이언트 액세스에 사용되는 서버의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalSipClientAccessPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>외부 클라이언트 액세스에 사용되는 포트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 내용으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 명령의 출력을 변수에 할당하면 개체 참조의 속성을 변경한 후 <strong>Set-CsAutoDiscoverConfiguration</strong> cmdlet을 호출하여 이러한 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WebLinks</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>자동 검색 URL 컬렉션입니다. 이러한 URL은 <strong>New-CsWebLink</strong> cmdlet을 사용하여 만들어야 합니다.</p></td>
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

**New-CsAutoDiscoverConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WriteableConfig.Settings.AutoDiscoverConfiguration.AutoDiscoverConfiguration 개체의 새 인스턴스를 만듭니다.

