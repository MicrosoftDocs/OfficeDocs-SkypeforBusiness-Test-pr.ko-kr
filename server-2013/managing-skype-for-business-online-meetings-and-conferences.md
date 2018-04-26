---
title: Lync Online 모임 및 회의 관리
TOCTitle: Lync Online 모임 및 회의 관리
ms:assetid: a4d0c070-4df2-47df-a1e2-6ce62600a287
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362833(v=OCS.15)
ms:contentKeyID: 56270281
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online 모임 및 회의 관리

 

_**마지막으로 수정된 항목:** 2015-06-22_

다음 cmdlet은 모임 및 회의 설정을 관리하는 데 사용할 수 있습니다.


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
<td><p><a href="disable-csmeetingroom.md">Disable-CsMeetingRoom</a><br />
<a href="enable-csmeetingroom.md">Enable-CsMeetingRoom</a><br />
<a href="get-csmeetingroom.md">Get-CsMeetingRoom</a><br />
<a href="set-csmeetingroom.md">Set-CsMeetingRoom</a></p></td>
<td><p>회의실의 끝점 장치를 관리합니다.</p>
<p>비즈니스용 Skype Online에서 회의실이란 회의실에 설치되어 고급 모임 기능을 제공하는 자립적인 컴퓨터 어플라이언스를 말합니다. 이러한 새 끝점 장치를 관리하기 위해서는 무엇보다도 장치에 대한 Exchange 리소스 사서함 계정을 만들어 설정한 다음 해당 리소스 계정을 비즈니스용 Skype Online에 사용할 수 있도록 설정해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csaudioconferencingprovider.md">Get-CsAudioConferencingProvider</a></p></td>
<td><p>조직이 계약을 체결한 오디오 회의 공급자에 대한 정보를 반환합니다.</p>
<p>오디오 회의 공급자란 실시간 번역, 기록, 회의별 실시간 운영자 지원 등의 고급 서비스를 포함한 회의 서비스를 조직에게 공급하는 타사입니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csmeetingconfiguration.md">Get-CsMeetingConfiguration</a><br />
<a href="set-csmeetingconfiguration.md">Set-CsMeetingConfiguration</a></p></td>
<td><p>사용자가 만들 수 있는 모임의 유형을 관리하고 익명의 사용자 및 전화 접속 회의 사용자와 모임을 진행하는 방법을 결정합니다.</p>
<p>모임(전화 회의라고도 함)은 비즈니스용 Skype Online의 핵심적인 부분입니다. 예를 들어, 이러한 cmdlet을 사용하여 전화 접속 사용자가 모임에 자동으로 입장되지 않고 모임 대기실로 연결되도록 모임을 구성할 수 있습니다. 해당 전화 접속 사용자는 발표자가 모임에 입장하도록 허용할 때까지 대기실에서 대기 상태로 유지됩니다.</p></td>
</tr>
</tbody>
</table>


비즈니스용 Skype Online 관리 센터를 사용해 모임 구성 속성의 작은 하위 집합을 관리할 수도 있습니다.

![Lync 관리 센터 일반 옵션 속성](images/Dn362833.acf90793-7ee4-4faf-b791-f149dd5df2a5(OCS.15).png "Lync 관리 센터 일반 옵션 속성")

## 참고 항목

#### 개념

[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)  
[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

