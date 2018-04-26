---
title: 사용자 및 사용자 계정 속성 관리
TOCTitle: 사용자 및 사용자 계정 속성 관리
ms:assetid: 5d13ab15-0e12-4bd0-a970-f130de980404
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362790(v=OCS.15)
ms:contentKeyID: 56270240
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자 및 사용자 계정 속성 관리

 

_**마지막으로 수정된 항목:** 2015-06-22_

다음 cmdlet은 비즈니스용 Skype Online 사용자 계정을 관리합니다.


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
<td><p><a href="get-csonlineuser.md">Get-CsOnlineUser</a></p></td>
<td><p>사용자의 비즈니스용 Skype Online 테넌트에 속한 계정이 있는 사용자의 정보를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csuseracp.md">Get-CsUserAcp</a><br />
<a href="remove-csuseracp.md">Remove-CsUserAcp</a><br />
<a href="set-csuseracp.md">Set-CsUserAcp</a></p></td>
<td><p>오디오 회의 공급자를 개별 사용자에게 할당, 수정 또는 할당 취소할 수 있도록 합니다.</p>
<p>오디오 회의 공급자란 실시간 번역, 기록, 회의별 실시간 운영자 지원 등의 고급 서비스를 포함한 회의 서비스를 조직에게 공급하는 타사입니다.</p>
<p>이 cmdlet은 해당 사용자에게 할당될 수 있는 오디오 공급자의 정보를 반환하지 않습니다. 해당 정보를 보려면 다음 명령을 대신 사용합니다.</p>
<pre><code>Get-CsAudioConferencingProvider</code></pre></td>
</tr>
</tbody>
</table>



> [!WARNING]
> Set-CsUser cmdlet은 비즈니스용 Skype Online 관리자가 사용할 수 있는 cmdlet 집합에도 포함되어 있습니다. 하지만 현재는 AudioVideoDisabled 매개 변수 설정을 제외하고는 비즈니스용 Skype Online을 관리하는 데 Set-CsUser를 사용할 수 없습니다. 다른 매개 변수를 사용하여 cmdlet 명령을 실행하는 경우 다음과 유사한 오류 메시지가 표시되며 실패하게 됩니다.<BR>"SipAddress"을(를) 설정할 수 없습니다. 원격 테넌트 PowerShell 내에서 이 매개 변수는 제한되어 있습니다.



오디오 회의 공급자는 비즈니스용 Skype Online 관리 센터를 사용하여 사용자 계정에 할당하거나 할당 취소할 수 있습니다.

![Lync 관리 센터 전화 접속 회의 속성](images/Dn362790.0c61f0c2-8aef-4020-a0a8-02580d43092a(OCS.15).png "Lync 관리 센터 전화 접속 회의 속성")

## 참고 항목

#### 개념

[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)  
[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

