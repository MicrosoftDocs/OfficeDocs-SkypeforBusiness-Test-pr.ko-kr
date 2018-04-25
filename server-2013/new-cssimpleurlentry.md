---
title: New-CsSimpleUrlEntry
TOCTitle: New-CsSimpleUrlEntry
ms:assetid: 3d9dbebf-d23f-40da-9676-19e7906decda
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425902(v=OCS.15)
ms:contentKeyID: 49303392
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsSimpleUrlEntry

 

_**마지막으로 수정된 항목:** 2015-03-09_

단순 URL을 만들 때 필요한 요소인 새 단순 URL 항목을 만듭니다. 단순 URL을 사용하면 사용자가 모임 및 회의에 쉽게 참가하고, 관리자가 Lync Server 제어판에 쉽게 로그온할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsSimpleUrlEntry -Url <String>

## 예제

## 예제 1

예제 1에서는 단순 URL의 기존 컬렉션에 새 URL을 추가하는 방법을 보여 줍니다. 먼저 이 예제의 첫 번째 명령은 **New-CsSimpleUrlEntry** cmdlet을 사용하여 https://meet.fabrikam.com을 가리키는 URL 항목을 만듭니다. 이 URL 항목은 $urlEntry라는 변수에 저장됩니다.

두 번째 명령은 **New-CsSimpleUrl** cmdlet을 사용하여 메모리에만 나타나는 단순 URL의 인스턴스를 만듭니다. 이 예제에서 URL 구성 요소는 Meet로, 도메인은 fabrikam.com으로, ActiveUrl은 https://meet.fabrikam.com으로, SimpleUrl 속성은 $urlEntry로 설정되며 $urlEntry는 첫 번째 명령에서 만들어진 URL 항목입니다.

URL이 만들어지고 개체 참조 $simpleUrl에 저장되면 이 예제의 마지막 명령이 Redmond 사이트의 단순 URL 컬렉션에 새 URL을 추가합니다. 이 작업을 수행하기 위해 **Set-CsSimpleUrlConfiguration**과 함께 SimpleUrl 매개 변수 및 매개 변수 값 @{Add=$simpleUrl}을 사용합니다. 이 구문은 개체 참조 $simpleUrl에 저장된 URL을 SimpleUrl 속성에 추가하도록 지정합니다.

    $urlEntry = New-CsSimpleUrlEntry -Url "https://meet.fabrikam.com"
    $simpleUrl = New-CsSimpleUrl -Component "meet" -Domain "fabrikam.com" -SimpleUrlEntry $urlEntry -ActiveUrl "https://meet.fabrikam.com"
    
    Set-CsSimpleUrlConfiguration -Identity "site:Redmond" -SimpleUrl @{Add=$simpleUrl}

## 예제 2

예제 2에서는 한 쌍의 URL 항목을 기존 단순 URL 컬렉션에 추가합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsSimpleUrlEntry** cmdlet을 사용하여 https://meet.fabrikam.com을 가리키는 URL 항목을 만듭니다. 이 URL 항목은 $urlEntry라는 변수에 저장됩니다. 두 번째 명령은 두 번째 URL 항목을 만듭니다. 이 URL 항목은 변수 $urlEntry2에 저장되며 URL https:// dialin.fabrikam.com을 가리킵니다.

두 개의 URL 항목이 만들어진 후 **New-CsSimpleUrl** cmdlet을 사용하여 메모리에만 나타나는 단순 URL의 인스턴스를 만듭니다. 첫 번째 인스턴스에서는 URL Component를 Meet로, 도메인을 fabrikam.com으로, ActiveUrl을 https://meet.fabrikam.com으로 설정합니다. 두 번째 인스턴스에서는 구성 요소를 Dialin으로, 도메인을 별표(\*)로, ActiveURL 속성을 https://dialin.fabrikam.com으로 설정합니다.

URL이 만들어지고 개체 참조 $simpleUrl 및 simpleUrl2에 저장되면 이 예제의 마지막 명령이 Redmond 사이트의 단순 URL 컬렉션에 새 URL을 추가합니다. 이 작업을 수행하기 위해 **Set-CsSimpleUrlConfiguration**과 함께 SimpleUrl 매개 변수 및 매개 변수 값 @{Add=$simpleUrl, $simpleUrl2}를 사용합니다. 이 구문은 개체 참조 $simpleUrl 및 $simpleUrl2에 저장된 URL을 SimpleUrl 속성에 추가하도록 지정합니다.

    $urlEntry = New-CsSimpleUrlEntry -Url "https://meet.fabrikam.com"
    $urlEntry2 = New-CsSimpleUrlEntry -Url "https://dialin.fabrikam.com"
    
    $simpleUrl = New-CsSimpleUrl -Component "meet" -Domain "fabrikam.com" -SimpleUrlEntry $urlEntry -ActiveUrl "https://meet.fabrikam.com"
    $simpleUrl2 = New-CsSimpleUrl -Component "dialin" -Domain "*" -SimpleUrlEntry $urlEntry -ActiveUrl "https://dialin.fabrikam.com"
    
    Set-CsSimpleUrlConfiguration -Identity "site:Redmond" -SimpleUrl @{Add=$simpleUrl, $simpleUrl2}

## 자세한 정보

Microsoft Office Communications Server 2007 R2에서는 모임의 URL이 다음과 유사했습니다.

https://imdf.litwareinc.com/Join?uri=sip%3Akenmyer%40litwareinc.com%3Bgruu%3Bopaque%3Dapp%3Aconf%3Afocus%3Aid%3A125f95a0b0184dcea706f1a0191202a8\&key=EcznhLh5K5t

그러나 이러한 URL은 한 눈에 파악하기 힘들고 다른 사람에게 전달하기도 어렵습니다. Lync Server 2010에서 도입된 단순 URL은 다음과 같은 URL을 사용자에게 제공하여 이러한 문제를 해결합니다.

https://meet.litwareinc.com/kenmyer/071200

단순 URL은 Office Communications Server에서 사용되는 URL의 명백하게 향상된 기능입니다. 하지만 단순 URL은 자동으로 만들어지지 않으며 사용자가 직접 URL을 구성해야 합니다. 또한 각 URL에 대해 DNS(Domain Name System) 레코드를 만들고, 외부 액세스에 대한 역방향 프록시 규칙을 구성하고, 프런트 엔드 서버 인증서에 단순 URL을 추가하는 등의 작업을 수행해야 합니다.

Lync Server에서는 세 가지 유형의 단순 URL을 만들 수 있습니다.

Meet – 모임에 사용됩니다. 각 SIP 도메인에 대해 모임 URL이 하나 이상 있어야 합니다.

Admin - 관리자에게 Lync Server 제어판을 안내하는 데 사용됩니다.

Dialin - 전화 접속 회의 웹 페이지에 사용됩니다.

단순 URL은 단순 URL 구성 컬렉션에 저장됩니다. Lync Server를 설치하면 전역 컬렉션이 만들어지는데, 사이트 범위에서 사용자 지정 컬렉션을 만들 수도 있습니다. 이렇게 하면 사이트마다 다른 단순 URL을 사용할 수 있습니다.

단순 URL 컬렉션에 실제 URL을 추가하려면 먼저 **New-CsSimpleUrl** cmdlet 및 **New-CsSimpleUrlEntry** cmdlet을 사용하여 URL을 만들어야 합니다. **New-CsSimpleUrlEntry** cmdlet은 URL 항목, 즉 모임, 관리 또는 전화 접속 회의 용도의 단순 URL로 사용할 수 있는 URL(예: https://meet.litwareinc.com)을 만듭니다. **New-CsSimpleUrlEntry** cmdlet에서 만든 개체는 새 단순 URL의 SimpleUrlEntry 속성에 추가됩니다. SimpleUrlEntry 속성은 여러 URL을 포함할 수 있으므로 별도의 cmdlet을 사용하여 개체를 만들어야 합니다. 그러나 이러한 URL 중 하나만 활성 URL로 지정할 수 있습니다. 활성 URL은 모임, 관리 또는 전화 접속 회의에 사용되는 실제 URL을 나타냅니다.

단순 URL 항목을 만든 후 **New-CsSimpleUrl** cmdlet을 사용하여 단순 URL의 메모리 전용 인스턴스를 만들고 구성 요소(단순 URL의 유형), 도메인, 활성 URL 및 모든 단순 URL 항목을 정의합니다. 단순 URL을 나타내는 개체를 만든 후 새 단순 URL 컬렉션 또는 기존 단순 URL 컬렉션에 해당 개체를 추가할 수 있습니다. 단순 URL 컬렉션을 업데이트한 후에는 **Enable-CsComputer** cmdlet을 실행해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsSimpleUrlEntry** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSimpleUrlEntry"}

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
<td><p><em>Url</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>단순 URL의 SimpleUrlEntry 속성에 추가할 URL입니다. 예: -Url &quot;https://meet.litwareinc.com&quot;. URL은 &quot;https:&quot; 접두사로 시작해야 합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**New-CsSimpleUrlEntry** cmdlet은 Microsoft.Rtc.Management.WritableConfig.SimpleUtl.SimpleUrlEntry 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsSimpleUrl](new-cssimpleurl.md)  
[New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)

