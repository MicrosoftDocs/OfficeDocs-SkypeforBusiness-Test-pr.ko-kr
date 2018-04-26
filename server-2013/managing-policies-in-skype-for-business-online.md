---
title: 정책 관리
TOCTitle: 정책 관리
ms:assetid: 91372888-a96e-44db-a0dc-d08facbfce87
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362826(v=OCS.15)
ms:contentKeyID: 56270268
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 정책 관리

 

_**마지막으로 수정된 항목:** 2015-06-22_

다음 cmdlet은 비즈니스용 Skype Online 정책을 관리합니다. 정책은 사용자와 조직에게 전체적으로 제공되는 비즈니스용 Skype Online 기능을 결정하는 데 도움이 됩니다.


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
<td><p><a href="get-csclientpolicy.md">Get-CsClientPolicy</a><br />
<a href="grant-csclientpolicy.md">Grant-CsClientPolicy</a></p></td>
<td><p>클라이언트 정책은 사용자에게 제공되는 Lync 클라이언트 기능을 결정하는 데 사용됩니다. 예를 들어 파일을 전송하는 기능을 일부 사용자에게만 제공하고 다른 사용자에게는 제공하지 않을 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csconferencingpolicy.md">Get-CsConferencingPolicy</a><br />
<a href="grant-csconferencingpolicy.md">Grant-CsConferencingPolicy</a></p></td>
<td><p>전화 회의 정책은 전화 회의에서 사용할 수 있는 기능을 결정합니다. 여기에는 회의에 IP 오디오와 비디오를 포함할 수 있는지 여부, 모임에 참석할 수 있는 최대 인원 수 등 모든 것이 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csexternalaccesspolicy.md">Get-CsExternalAccessPolicy</a><br />
<a href="grant-csexternalaccesspolicy.md">Grant-CsExternalAccessPolicy</a></p></td>
<td><p>외부 액세스 정책은 사용자가 페더레이션된 도메인의 사용자와 통신할 수 있는지, 사용자가 공용 메신저 공급자(예: Windows Live 또는 AOL) 계정이 있는 사용자와 통신할 수 있는지 여부를 결정하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csvoicepolicy.md">Get-CsVoicePolicy</a><br />
<a href="grant-csvoicepolicy.md">Grant-CsVoicePolicy</a><br />
<a href="remove-csvoicepolicy.md">Remove-CsVoicePolicy</a></p></td>
<td><p>음성 정책은 동시 연결(사무실 전화로 전화가 올 때마다 두 번째 전화기에서도 신호가 울리도록 하는 기능)과 착신 전환 같은 Enterprise Voice 기능을 관리하는 데 사용됩니다.</p></td>
</tr>
</tbody>
</table>


비즈니스용 Skype Online 관리 센터를 사용하여 선택한 회의 정책 설정을 관리할 수도 있습니다.

![Lync 관리 센터 일반 옵션 속성](images/Dn362833.acf90793-7ee4-4faf-b791-f149dd5df2a5(OCS.15).png "Lync 관리 센터 일반 옵션 속성")

비즈니스용 Skype Online 관리 센터를 사용하여 외부 액세스 정책 설정을 관리할 수도 있습니다.

![관리 센터 외부 통신 옵션](images/Dn362826.e5cfb159-b096-463e-b1ef-2b42eb29168a(OCS.15).png "관리 센터 외부 통신 옵션")

## 참고 항목

#### 개념

[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)  
[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

