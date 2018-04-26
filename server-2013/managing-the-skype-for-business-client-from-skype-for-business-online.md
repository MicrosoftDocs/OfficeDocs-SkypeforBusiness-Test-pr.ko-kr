---
title: Lync 클라이언트 관리
TOCTitle: Lync 클라이언트 관리
ms:assetid: d1ccc7b6-99ff-4ffd-bd29-9088fb8fe837
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362847(v=OCS.15)
ms:contentKeyID: 56270301
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 클라이언트 관리

 

_**마지막으로 수정된 항목:** 2015-06-22_

다음 cmdlet은 Lync 클라이언트를 관리합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="get-csimfilterconfiguration.md">Get-CsImFilterConfiguration</a></p></td>
<td><p>조직에서 사용 중인 URI 제한에 대한 정보를 검색합니다.</p>
<p>메신저 대화를 보낼 때 사용자는 해당 메시지의 텍스트에 URI를 포함하여 대화의 다른 참가자를 특정 웹 사이트 또는 공유를 참조하도록 할 수 있습니다. 또한 특정 접두사가 포함된 하이퍼링크가 차단되거나 비활성화되도록 비즈니스용 Skype Online을 구성할 수 있습니다. 이렇게 하면 참가자가 링크를 클릭해 URI가 참조하는 사이트로 이동할 수 없으며, 대신 링크를 수동으로 복사해 브라우저에 붙여 넣어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cspresencepolicy.md">Get-CsPresencePolicy</a></p></td>
<td><p>현재 상태 구독의 중요한 두 가지 요소인 프롬프트 구독자와 범주 구독에 대한 정보를 반환합니다.</p>
<p>사용자가 다른 사람의 대화 상대 목록에 추가되면 기본적으로 해당 목록에 추가되었음을 알리는 팝업 메시지가 나타납니다. 팝업을 해제할 때까지 각 알림에서 프롬프트 구독자로 간주합니다.</p>
<p>범주 구독은 일정 데이터를 요청하는 응용 프로그램과 같은 특정 정보 범주에 대한 요청을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csprivacyconfiguration.md">Get-CsPrivacyConfiguration</a><br />
<a href="set-csprivacyconfiguration.md">Set-CsPrivacyConfiguration</a></p></td>
<td><p>사용자에게 개인 정보 값을 변경할 수 있는 옵션을 계속 제공하면서 비즈니스용 Skype Online의 기본 개인 정보 값을 구성합니다.</p>
<p>비즈니스용 Skype Online에서는 사용자에게 다양한 현재 상태 정보를 다른 사람들과 공유할 수 있는 기회를 제공합니다. 사용자는 자신의 사진을 게시하고, 자세한 위치 정보를 제공하고, 대화 상대 목록에 있는 사람들이 아닌 조직의 모든 사람들에게 자신의 현재 상태 정보를 자동으로 공개할 수 있습니다. <strong>CsPrivacyConfiguration</strong> cmdlet을 사용하면 사용자가 개인 정보 값을 변경할 수 있도록 계속 허용하면서 관리자가 비즈니스용 Skype Online의 기본 개인 정보 값을 구성할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


비즈니스용 Skype Online 관리 센터를 사용하여 개인 정보 구성 설정의 하위 집합을 관리할 수도 있습니다.

![Lync 관리 센터 현재 상태 전용 모드 설정](images/Dn362847.eb206b74-844d-4a7b-b1b3-0cfcb6e3614b(OCS.15).png "Lync 관리 센터 현재 상태 전용 모드 설정")

## 참고 항목

#### 개념

[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)  
[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

