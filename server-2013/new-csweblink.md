---
title: New-CsWebLink
TOCTitle: New-CsWebLink
ms:assetid: f5c19896-4ce0-42cd-a934-30b1cdc64e3a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690053(v=OCS.15)
ms:contentKeyID: 49305540
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsWebLink

 

_**마지막으로 수정된 항목:** 2015-03-09_

자동 검색 서비스를 가리키는 새 웹 링크를 만들 수 있습니다. 자동 검색 서비스를 사용하면 Lync Web App 또는 Lync Mobile 등의 클라이언트 응용 프로그램에서 사용자의 홈 풀 또는 전화 접속 회의 참가용 URL 같은 주요 리소스를 찾을 수 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    New-CsWebLink -Href <String> -Token <String>

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 할당된 자동 검색 구성 설정에 새 자동 검색 URL(http://LyncDiscover.fabrikam.com)을 추가합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsWebLink** cmdlet을 사용하여 새 자동 검색 URL을 만들며, 이 URL은 $Link1이라는 변수에 저장됩니다. 그런 후에 **Set-CsAutoDiscoverConfiguration** cmdlet을 사용하여 이러한 설정에 이미 할당된 모든 URL에 새 URL을 추가합니다. 이 작업을 수행하기 위해 WebLinks 매개 변수와 매개 변수 값 @{Add=$Link1}을 사용합니다.

    $Link1 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscover.fabrikam.com"
    
    Set-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Add=$Link1}

## 예제 2

예제 2의 명령은 Redmond 사이트에 할당된 자동 검색 구성 설정에 한 쌍의 자동 검색 URL(http://LyncDiscover.fabrikam.com 및 http://LyncDiscoverInternal.fabrikam.com)을 할당합니다. 이 작업을 수행하기 위해 처음 두 명령은 **New-CsWebLink** cmdlet을 사용하여 두 자동 검색 URL을 만듭니다. 그러면 새로 만들어진 URL은 각각 $Link1 및 $Link2라는 변수에 저장됩니다. 두 URL이 만들어지면 세 번째 명령은 **Set-CsAutoDiscoverConfiguration** cmdlet을 사용하여 두 URL을 Redmond 사이트에 할당합니다. 이를 위해 WebLinks 매개 변수와 함께 매개 변수 값 @{Add=$Link1,$Link2}를 포함합니다. 이 구문은 변수 $Link1 및 $Link2에 저장된 값이 설정의 WebLinks 속성에 추가되도록 합니다.

    $Link1 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscover.fabrikam.com"
    $Link2 = New-CsWebLink -Token "Fabrikam" -Href "http://LyncDiscoverInternal.fabrikam.com"
    
    Set-CsAutoDiscoverConfiguration -Identity "site:Redmond" -WebLinks @{Add=$Link1,$Link2}

## 자세한 정보

클라이언트 응용 프로그램에서 Lync Server를 최대한 효과적으로 사용하도록 하려면 이러한 응용 프로그램에서 주요 Lync Server 구성 요소의 위치를 인식하고 있어야 합니다. 예를 들어 인증된 사용자가 해당 홈 풀을 찾을 수 있어야 합니다. 즉, 이러한 사용자는 해당 홈 풀을 통해서만 인증될 수 있습니다. 마찬가지로, 인증되지 않은 사용자가 전화 회의에 참가하는 데 사용되는 URL을 찾는 등의 작업을 수행할 수 있어야 합니다.

모든 사용자가 조직의 방화벽 뒤에서 로그온한 경우에는 이러한 위치를 검색하기가 비교적 쉽습니다. 하지만 사용자가 Lync Mobile 또는 Lync Web App을 사용하여 외부 위치에서 시스템에 액세스하게 되면 이처럼 비교적 단순한 작업도 점점 더 복잡해집니다.

이는 분할 도메인 시나리오에서 특히 심하게 나타나는데, 이러한 시나리오의 경우 조직의 일부 사용자는 온-프레미스 버전의 Lync Server에 계정을 가지고 있지만 다른 사용자는 Microsoft Office 365에 계정을 가지고 있습니다. 이 경우 사용자 계정이 각기 다른 Active Directory 포리스트에 있을 수 있는데, 이렇게 되면 특정한 문제가 발생할 수 있습니다. 예를 들어 미국의 사용자가 유럽에서 로그온하는 경우 시스템에서는 이 사용자의 포리스트를 인식한 다음 로그온 요청을 적절한 풀에 조회할 수 있어야 합니다.

자동 검색 서비스는 바로 이러한 문제를 해결하기 위해 Lync Server의 2011년 11월 릴리스에 도입되었습니다. 클라이언트 응용 프로그램이 Lync Server에 액세스를 시도하면 자동 검색 서비스에서는 클라이언트 SIP 주소를 구문 분석한 다음 해당 요청을 적절한 풀로 리디렉션합니다. 클라이언트 응용 프로그램은 HTTP 요청을 자동 검색 URL로 보내는 방식으로 자동 검색 서비스에 연결되는데, 자동 검색 서비스가 올바르게 작동하려면 관리자가 이러한 URL을 구성해야 합니다. 참고적으로, URL을 구성하는 것 외에도 관리자는 이러한 URL에 해당하는 DNS 레코드를 만들어야 합니다.

자동 검색 URL은 자동 검색 구성 설정에 할당되며, 이를 통해 이러한 설정을 전역 범위나 사이트 범위에 적용할 수 있습니다. Lync Server를 설치하면 설정의 전역 컬렉션이 자동으로 만들어집니다. 그러나 이 컬렉션에 자동 검색 URL이 할당되지는 않습니다. 자동 검색 설정 컬렉션 하나로 요구 사항이 충족되지 않는 경우에는 **New-CsAutoDiscoverConfiguration** cmdlet을 사용하여 사이트 범위에서 추가 구성 설정을 만들 수 있습니다.

일반적으로 자동 검색 구성 설정을 관리하려면 자동 검색 URL을 추가해야 합니다. 이러한 URL은 **New-CsWebLink** cmdlet을 사용하여 만들어야 하며, 결과로 생성된 URL은 변수에 저장된 다음 자동 검색 구성 설정 컬렉션에 추가됩니다. 자동 검색 URL은 조직에서 사용되는 SIP 도메인을 기반으로 합니다. 대개 관리자는 조직 방화벽 외부의 사용자를 위한 URL 하나(예: http://LyncDiscover.litwareinc.com)와 방화벽 내부의 사용자를 위한 또 다른 URL(예: http://LyncDiscoverInternal.litwareinc.com)을 만듭니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsWebLink** cmdlet을 로컬로 실행할 수 있습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Href</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>자동 검색 서비스 URL로, 예를 들면 다음과 같습니다.</p>
<p>–Href &quot;http://LyncDiscover.fabrikam.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Token</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>URL에 지정할 고유한 이름으로, 예를 들면 다음과 같습니다.</p>
<p>-Token &quot;Fabrikam&quot;</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsWebLink** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WriteableConfig.Settings.WebLink.WebLink 개체의 새 인스턴스를 만듭니다.

