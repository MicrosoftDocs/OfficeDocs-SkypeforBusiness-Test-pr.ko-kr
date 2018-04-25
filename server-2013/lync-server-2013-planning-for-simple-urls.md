---
title: 'Lync Server 2013: 단순 URL 계획'
TOCTitle: 단순 URL 계획
ms:assetid: 20e4f4b6-b7ff-4297-b00d-d1211ee800ac
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398287(v=OCS.15)
ms:contentKeyID: 49303038
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 단순 URL 계획

 

_**마지막으로 수정된 항목:** 2015-03-09_

단순 URL은 사용자가 모임에 보다 쉽게 참가하고 관리자가 Lync Server 관리 도구를 보다 쉽게 사용할 수 있도록 합니다.

Lync Server에서는 세 가지 단순 URL을 지원합니다.

  - **모임** 은 사이트 또는 조직의 모든 전화 회의에 대한 기준 URL로 사용됩니다. 모임 단순 URL의 예로는 https://meet.contoso.com 등이 있습니다. 특정 모임에 대한 URL은 https://meet.contoso.com/ *사용자 이름* /7322994와 같을 수 있습니다.
    
    모임 단순 URL을 사용하면 모임에 참가할 링크를 쉽게 이해하고 전달하고 배포할 수 있습니다.

  - **전화 접속** 은 전화 접속 회의 설정 웹 페이지에 액세스할 수 있게 합니다. 이 페이지에는 사용 가능한 언어, 할당된 전화 회의 정보(즉, 예약할 필요가 없는 모임에 대한 정보) 및 전화 회의 내에서의 DTMF 제어와 함께 전화 회의 전화 접속 번호가 표시됩니다. 이 페이지에서 개인 ID 번호(PIN) 및 할당된 회의 정보를 관리할 수 있습니다. 전화 접속 단순 URL은 모든 모임 초대에 포함되므로 모임에 전화 접속하려는 사용자가 필요한 전화 번호 및 PIN 정보에 액세스할 수 있습니다. 전화 접속 단순 URL의 예를 들면 https://dialin.contoso.com과 같습니다.

  - **관리** 는 Lync Server 제어판에 빠르게 액세스할 수 있도록 합니다. 조직 방화벽 내의 모든 컴퓨터에서 관리자는 관리 단순 URL을 브라우저에 입력하여 Lync Server 제어판을 열 수 있습니다. 관리 단순 URL은 조직의 내부 URL입니다. 관리 단순 URL의 예로는 https://admin.contoso.com이 있습니다.

## 단순 URL 범위

전역 범위에서 적용되도록 단순 URL을 구성하거나 조직의 각 중앙 사이트에 대해 서로 다른 단순 URL을 지정할 수 있습니다. 전역 단순 URL과 사이트 단순 URL이 둘 다 지정된 경우에는 사이트 단순 URL이 우선적으로 적용됩니다.

대부분의 경우 전역 수준에서만 단순 URL을 설정하여 사이트 간에 이동하더라도 사용자의 모임 단순 URL이 변경되지 않도록 하는 것이 좋습니다. 단, 여러 사이트의 전화 접속 사용자에 서로 다른 전화 번호를 사용해야 하는 조직은 예외입니다. 사이트에서 하나의 단순 URL(예: 전화 접속 단순 URL)을 사이트 수준 단순 URL로 설정한 경우에는 해당 사이트의 다른 단순 URL도 사이트 수준으로 설정해야 합니다.

전역 단순 URL은 토폴로지 작성기에서 설정할 수 있습니다. 사이트 수준에서 단순 URL을 설정하려면 Set-CsSimpleURLConfiguration cmdlet을 사용해야 합니다.

## 단순 URL 이름 지정

단순 URL의 이름을 지정할 때 권장되는 세 가지 옵션이 있습니다. 선택한 옵션에 따라 단순 URL을 지원하는 DNS A 레코드 및 인증서 설정 방법이 결정됩니다. 각 옵션에서는 조직의 각 SIP 도메인에 대해 하나의 모임 단순 URL을 구성해야 합니다.

보유한 SIP 도메인 수에 관계없이 전화 접속 단순 URL과 관리 단순 URL은 항상 전체 조직에서 각각 하나씩만 있으면 됩니다.

필요한 DNS A 레코드 및 인증서에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 단순 URL에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-simple-urls.md) 및 [Lync Server 2013의 내부 서버에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-internal-servers.md)을 참조하십시오.

옵션 1에서는 각 단순 URL에 대한 새 SIP 도메인 이름을 만듭니다.

이 옵션을 사용하는 경우 각 단순 URL에 대해 별도의 DNS A 레코드가 필요하며 각 모임 단순 URL의 이름이 인증서에 지정되어 있어야 합니다.

### 단순 URL 이름 지정 옵션 1

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>단순 URL</strong></p></td>
<td><p><strong>예</strong></p></td>
</tr>
<tr class="even">
<td><p>모임</p></td>
<td><p>https://meet.contoso.com, https://meet.fabrikam.com 등(조직의 각 SIP 도메인당 하나)</p></td>
</tr>
<tr class="odd">
<td><p>전화 접속</p></td>
<td><p>https://dialin.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>관리</p></td>
<td><p>https://admin.contoso.com</p></td>
</tr>
</tbody>
</table>


옵션 2를 사용하는 경우에는 단순 URL이 도메인 이름 lync.contoso.com을 기반으로 하므로 세 가지 유형의 단순 URL 모두에서 사용할 수 있는 DNS A 레코드가 하나만 있으면 됩니다. 이 DNS A 레코드는 lync.contoso.com을 참조합니다. 조직의 다른 SIP 도메인에 대해서는 여전히 별도의 DNS A 레코드가 필요합니다.

### 단순 URL 이름 지정 옵션 2

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>단순 URL</strong></p></td>
<td><p><strong>예</strong></p></td>
</tr>
<tr class="even">
<td><p>모임</p></td>
<td><p>https://lync.contoso.com/Meet, https://lync.fabrikam.com/Meet 등(조직의 각 SIP 도메인당 하나)</p></td>
</tr>
<tr class="odd">
<td><p>전화 접속</p></td>
<td><p>https://lync.contoso.com/Dialin</p></td>
</tr>
<tr class="even">
<td><p>관리</p></td>
<td><p>https://lync.contoso.com/Admin</p></td>
</tr>
</tbody>
</table>


옵션 3은 많은 SIP 도메인이 있고 각각에 별도의 모임 단순 URL을 사용하지만 이러한 단순 URL에 필요한 DNS 레코드 및 인증서를 최소화하려는 경우에 가장 유용합니다.

### 단순 URL 이름 지정 옵션 3

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>단순 URL</strong></p></td>
<td><p><strong>예</strong></p></td>
</tr>
<tr class="even">
<td><p>모임</p></td>
<td><p>https://lync.contoso.com/contosoSIPdomain/Meet</p>
<p>https://lync.contoso.com/fabrikamSIPdomain/Meet</p></td>
</tr>
<tr class="odd">
<td><p>전화 접속</p></td>
<td><p>https://lync.contoso.com/Dialin</p></td>
</tr>
<tr class="even">
<td><p>관리</p></td>
<td><p>https://lync.contoso.com/Admin</p></td>
</tr>
</tbody>
</table>


## 단순 URL 이름 지정 및 유효성 검사 규칙

토폴로지 작성기 및 Lync Server 관리 셸 cmdlet은 단순 URL에 대한 여러 가지 유효성 검사 규칙을 적용합니다. 모임 및 전화 접속 단순 URL은 필수 설정이지만 관리 단순 URL은 선택 사항입니다. 모임 단순 URL은 SIP 도메인마다 별도의 URL이 있어야 하지만 전화 접속 단순 URL과 관리 단순 URL은 전체 조직에 하나만 있으면 됩니다.

조직의 각 단순 URL은 고유한 이름을 사용해야 하며 다른 단순 URL의 접두사가 될 수 없습니다(예: lync.contoso.com/Meet를 모임 단순 URL로 설정하고 lync.contoso.com/Meet/Dialin을 전화 접속 단순 URL로 설정할 수는 없음). 단순 URL 이름에는 풀의 FQDN 또는 풀 정보를 포함할 수 없습니다(예: https://FQDN:88/meet는 허용되지 않음). 모든 단순 URL은 https:// 접두사로 시작해야 합니다.

단순 URL은 영숫자(즉, a-z, A-Z, 0-9 및 마침표(.))만 포함할 수 있습니다. 다른 문자를 사용하면 단순 URL이 예상대로 작동하지 않을 수 있습니다.

## 배포 후 단순 URL 변경

초기 배포 후 단순 URL을 변경하려면 단순 URL의 DNS 레코드 및 인증서가 이러한 변경으로 인해 받을 수 있는 영향을 파악해야 합니다. 단순 URL의 기준이 변경되면 DNS 레코드 및 인증서도 변경해야 합니다. 예를 들어 https://lync.contoso.com/Meet에서 https://meet.contoso.com으로 변경하는 경우 기준 URL이 lync.contoso.com에서 meet.contoso.com으로 변경되므로, DNS 레코드와 인증서가 meet.contoso.com을 참조하도록 변경해야 합니다. 단순 URL을 https://lync.contoso.com/Meet에서 https://lync.contoso.com/Meetings로 변경하는 경우에는 기준 URL인 lync.contoso.com이 동일하게 유지되므로 DNS 또는 인증서를 변경하지 않아도 됩니다.

그러나 단순 URL 이름을 변경할 때마다 각 디렉터 및 프런트 엔드 서버에서 **Enable-CsComputer**를 실행하여 변경 내용을 등록해야 합니다.

## 참고 항목

#### 개념

[Lync Server 2013의 단순 URL에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-simple-urls.md)

