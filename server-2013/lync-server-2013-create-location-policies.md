---
title: Lync Server 2013에서 위치 정책 만들기
TOCTitle: Lync Server 2013에서 위치 정책 만들기
ms:assetid: f1878194-c756-4794-8fa1-15dd2118b4b3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413006(v=OCS.15)
ms:contentKeyID: 49305491
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 위치 정책 만들기

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server에서는 위치 정책을 사용하여 클라이언트 등록 중 E9-1-1에 대해 Lync 클라이언트를 사용하도록 설정합니다. 위치 정책은 E9-1-1을 구현할 방법을 정의하는 설정을 포함합니다.

전역 위치 정책을 편집하고 태그가 지정된 새 위치 정책을 만들 수 있습니다. 클라이언트는 연결된 위치 정책의 서브넷에 글로벌 정책이 없는 경우 또는 클라이언트가 위치 정책을 직접 할당하지 않은 경우 전역 정책을 가져옵니다. 태그가 지정된 정책이 서브넷이나 사용자에게 할당됩니다.

위치 정책을 만들려면 RTCUniversalServerAdmins 그룹의 구성원이거나 CsVoiceAdministrator 관리자 역할의 구성원이거나 또는 이와 동등한 관리자 권한 및 사용 권한이 있는 계정을 사용해야 합니다.

위치 정책에 대한 전체 설명을 보려면 [Lync Server 2013에 대한 위치 정책 정의](lync-server-2013-defining-the-location-policy.md)을 참조하십시오. 이 절차의 cmdlet은 다음 값을 사용하여 정의된 위치 정책을 사용합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>요소</th>
<th>값</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EnhancedEmergencyServicesEnabled</p></td>
<td><p><strong>True</strong></p></td>
</tr>
<tr class="even">
<td><p>LocationRequired</p></td>
<td><p><strong>고지 사항</strong></p></td>
</tr>
<tr class="odd">
<td><p>EnhancedEmergencyServiceDisclaimer</p></td>
<td><p>회사 정책상 사용자는 위치를 설정해야 합니다. 위치를 설정하지 않으면 응급 서비스에서 응급 상황 시 귀하를 찾을 수 없습니다. 위치를 설정하십시오.</p></td>
</tr>
<tr class="even">
<td><p>UseLocationForE911Only</p></td>
<td><p><strong>False</strong></p></td>
</tr>
<tr class="odd">
<td><p>PstnUsage</p></td>
<td><p><strong>EmergencyUsage</strong></p></td>
</tr>
<tr class="even">
<td><p>EmergencyDialString</p></td>
<td><p><strong>911</strong></p></td>
</tr>
<tr class="odd">
<td><p>EmergencyDialMask</p></td>
<td><p><strong>112</strong></p></td>
</tr>
<tr class="even">
<td><p>NotificationUri</p></td>
<td><p><strong>sip:security@litwareinc.com</strong></p></td>
</tr>
<tr class="odd">
<td><p>ConferenceUri</p></td>
<td><p><strong>sip:+14255550123@litwareinc.com</strong></p></td>
</tr>
<tr class="even">
<td><p>ConferenceMode</p></td>
<td><p><strong>twoway</strong></p></td>
</tr>
<tr class="odd">
<td><p>LocationRefreshInterval</p></td>
<td><p><strong>2</strong></p></td>
</tr>
</tbody>
</table>


위치 정책 작업에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 다음 cmdlet을 참조하십시오.

  - New-CsLocationPolicy

  - Get-CsLocationPolicy

  - Set-CsLocationPolicy

  - Remove-CsLocationPolicy

  - Grant-CsLocationPolicy

## 위치 정책을 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.
    

    > [!NOTE]
    > <STRONG>PstnUsage</STRONG>에 대한 설정이 PstnUsages의 전역 목록에 없을 경우 CsLocationPolicy가 실패합니다.



2.  (선택 사항) 다음 cmdlet를 실행하여 전역 위치 정책을 편집합니다.
    
        Set-CsLocationPolicy -Identity Global -EnhancedEmergencyServicesEnabled $true -LocationRequired "disclaimer" -EnhancedEmergencyServiceDisclaimer "Your company policy requires you to set a location. If you do not set a location emergency services will not be able to locate you in an emergency. Please set a location." -PstnUsage "emergencyUsage" -EmergencyDialString "911" -ConferenceMode "twoway" -ConferenceUri "sip:+14255550123@litwareinc.com" -EmergencyDialMask "112" NotificationUri "sip:security@litwareinc.com" -UseLocationForE911Only $true -LocationRefreshInterval 2

3.  다음을 실행하여 태그가 지정된 위치 정책을 만듭니다.
    
        New-CsLocationPolicy -Identity Tag:Redmond - EnhancedEmergencyServicesEnabled $true -LocationRequired "disclaimer" -EnhancedEmergencyServiceDisclaimer "Your company policy requires you to set a location. If you do not set a location emergency services will not be able to locate you in an emergency. Please set a location." -UseLocationForE911Only $false -PstnUsage "EmergencyUsage" -EmergencyDialString "911" -EmergencyDialMask "112" -NotificationUri "sip:security@litwareinc.com" -ConferenceUri "sip:+14255550123@litwareinc.com" -ConferenceMode "twoway" -LocationRefreshInterval 2

4.  다음 cmdlet를 실행하여 3단계에서 만든 태그가 지정된 위치 정책을 사용자 정책에 적용합니다.
    
        (Get-CsUser | where { $_.Name -match "UserName" }) | Grant-CsLocationPolicy -PolicyName Redmond

