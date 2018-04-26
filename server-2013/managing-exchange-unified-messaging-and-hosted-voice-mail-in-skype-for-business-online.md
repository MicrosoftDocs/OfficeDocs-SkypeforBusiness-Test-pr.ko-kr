---
title: Exchange 통합 메시징 및 호스트된 음성 메일 관리
TOCTitle: Exchange 통합 메시징 및 호스트된 음성 메일 관리
ms:assetid: 844bf8d5-e093-4dcd-abcf-48dc70e8c73c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362822(v=OCS.15)
ms:contentKeyID: 56270271
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exchange 통합 메시징 및 호스트된 음성 메일 관리

 

_**마지막으로 수정된 항목:** 2015-06-22_

다음 cmdlet은 Exchange UM(통합 메시징)과 호스팅된 음성 메일 정책을 관리하는 데 사용할 수 있습니다.


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
<td><p><a href="get-csexumcontact.md">Get-CsExUmContact</a></p>
<p><a href="new-csexumcontact.md">New-CsExUmContact</a></p>
<p><a href="remove-csexumcontact.md">Remove-CsExUmContact</a></p>
<p><a href="set-csexumcontact.md">Set-CsExUmContact</a></p></td>
<td><p>Exchange UM이 호스팅된 서비스인 경우, 자동 전화 교환 및 구독자 액세스 서비스에 사용되는 연락처 개체를 만들고 관리합니다.</p>
<p>비즈니스용 Skype Online은 Exchange UM과 상호 작용하여 자동 전화 교환 및 구독자 액세스를 비롯한 몇 가지 음성 관련 기능을 제공합니다. 자동 전화 교환은 자동으로 전화를 받아 올바른 대상에게 라우팅하는 방법을 제공합니다. 구독자 액세스를 사용하면 사용자가 Exchange UM에 연결해 전자 메일, 음성 메시지, 연락처, 일정 정보를 검색할 수 있습니다.</p>
<p>Exchange UM이 호스팅된 서비스로 제공되는 경우, 자동 전화 교환 및 구독자 액세스 서비스에 사용되는 연락처 개체는 Windows PowerShell을 사용하여 만들어야 합니다. 이러한 개체는 CsExUmContact cmdlet을 사용해 만들고 관리합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cshostedvoicemailpolicy.md">Get-CsHostedVoicemailPolicy</a></p>
<p><a href="grant-cshostedvoicemailpolicy.md">Grant-CsHostedVoicemailPolicy</a></p></td>
<td><p>조직에서 사용하는 호스팅된 음성 메일 정책을 관리합니다. 호스팅된 음성 메일 정책은 받지 못한 전화가 Exchange UM 서비스로 라우팅되는 방법을 지정합니다. 이러한 정책은 Exchange UM 호스팅된 음성 메일을 사용하도록 설정된 사용자에게만 적용됩니다. 사용자가 호스팅된 음성 메일을 사용할 수 있는지 확인하려면 Windows PowerShell 프롬프트에서 다음과 같은 명령을 실행합니다.</p>
<pre><code>Get-CsOnlineUser -Identity &quot;kenmyer@litwareinc.com&quot; | Select-Object HostedVoiceMail</code></pre></td>
</tr>
</tbody>
</table>


Exchange UM 설정과 호스팅된 음성 메일 정책은 비즈니스용 Skype Online 관리 센터를 사용해 관리할 수 없습니다.

## 참고 항목

#### 개념

[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)  
[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

