---
title: 외부 사용자 및 조직과의 통신 관리
TOCTitle: 외부 사용자 및 조직과의 통신 관리
ms:assetid: 8a64f0fe-1e79-47d8-835e-548d7ac0757e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362813(v=OCS.15)
ms:contentKeyID: 56270276
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 외부 사용자 및 조직과의 통신 관리

 

_**마지막으로 수정된 항목:** 2015-06-22_

다음 cmdlet은 외부 도메인 및 공용 메신저 공급자와의 페더레이션을 관리하는 데 사용할 수 있습니다.


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
<td><p><a href="new-csedgeallowallknowndomains.md">New-CsEdgeAllowAllKnownDomains</a></p></td>
<td><p>사용자가 차단된 도메인 목록에 지정된 도메인을 제외한 모든 도메인과 통신할 수 있도록 허용합니다.</p>
<p>페더레이션은 사용자가 다른 도메인의 사용자와 메신저 대화 및 현재 상태 정보를 주고받을 수 있도록 하는 서비스입니다. 일반적으로 관리자는 허용 및 차단 목록을 사용해 사용자가 통신할 수 있는 외부 도메인을 지정합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="new-csedgeallowlist.md">New-CsEdgeAllowList</a></p></td>
<td><p>사용자 통신을 지정된 도메인 모음으로 제한합니다.</p>
<p>사용자는 허용된 도메인 목록에 나타나는 도메인을 상대로만 통신할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="new-csedgedomainpattern.md">New-CsEdgeDomainPattern</a></p></td>
<td><p>허용되거나 차단된 도메인 목록을 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cstenantfederationconfiguration.md">Get-CsTenantFederationConfiguration</a><br />
<a href="set-cstenantfederationconfiguration.md">Set-CsTenantFederationConfiguration</a></p></td>
<td><p>다른 도메인 및 공용 공급자와의 페더레이션을 설정/해제합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-cstenanthybridconfiguration.md">Get-CsTenantHybridConfiguration</a><br />
<a href="set-cstenanthybridconfiguration.md">Set-CsTenantHybridConfiguration</a></p></td>
<td><p>하이브리드 구성 설정에 적절한 값을 할당합니다.</p>
<p>하이브리드 또는 &quot;분할 도메인&quot; 배포에서 조직의 일부 사용자는 비즈니스용 Skype Online에 속한 계정이 있고, 동시에 다른 사용자는 Lync Server 2013에 속한 계정이 있습니다. 기본적으로 비즈니스용 Skype Online에 속한 사용자는 Enterprise Voice에서 제공하는 전체 기능에 액세스할 수 없습니다. 비즈니스용 Skype Online 사용자가 이러한 Enterprise Voice 기능에 액세스할 수 있도록 하려면 관리자가 하이브리드 구성 설정에 적절한 값을 할당해야 합니다. 이러한 값은 <strong>CsTenantHybridConfiguration</strong> cmdlet을 사용하는 방법으로만 관리할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cstenantpublicprovider.md">Get-CsTenantPublicProvider</a><br />
<a href="set-cstenantpublicprovider.md">Set-CsTenantPublicProvider</a></p></td>
<td><p>공용 공급자와의 페더레이션을 관리합니다.</p>
<p>공용 공급자는 일반 대중에게 SIP 통신 서비스를 제공하는 조직입니다. 공용 공급자와 페더레이션 관계를 설정하면 해당 공급자가 호스팅하는 계정을 가진 사용자와의 페더레이션을 효과적으로 설정할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


비즈니스용 Skype Online 관리 센터를 사용하여 페더레이션된 도메인과 공용 공급자 모두에 대한 페더레이션 설정을 관리할 수도 있습니다.

![Lync Online 관리 센터 조직 설정](images/Dn362813.f860d03f-5906-49b0-bcc7-7634afe7005e(OCS.15).png "Lync Online 관리 센터 조직 설정")

## 참고 항목

#### 개념

[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)  
[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

