---
title: 'Lync Server 2013: 통화 대기 배포 프로세스'
TOCTitle: 통화 대기 배포 프로세스
ms:assetid: 2000d672-a85f-4262-9d69-0bee9ae3709a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398283(v=OCS.15)
ms:contentKeyID: 49303019
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 대기 배포 프로세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 통화 대기 응용 프로그램 배포 시 수행하는 단계를 간략하게 설명합니다. 통화 대기를 구성하기 전에 Enterprise Voice가 포함된 Enterprise Edition 또는 Standard Edition을 배포해야 합니다. 통화 대기에 필요한 구성 요소는 Enterprise Voice를 배포할 때 설치되고 사용하도록 설정됩니다.

### 통화 대기 배포 프로세스

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>단계</th>
<th>절차</th>
<th>필수 그룹 및 역할</th>
<th>배포 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>파킹된 통화 번호 표에서 통화 대기 파킹된 통화 번호 범위 구성</p></td>
<td><p>Lync Server 제어판 또는 <strong>New-CSCallParkOrbit</strong> cmdlet을 사용하여 통화 대기 파킹된 통화 번호 표에서 파킹된 통화 번호 범위를 만든 다음, 통화 대기 응용 프로그램을 호스팅하는 응용 프로그램 서비스에 해당 범위를 연결합니다.</p>


> [!NOTE]
> 기존 다이얼 플랜과 원활하게 통합할 수 있도록, 파킹된 통화 번호 범위는 일반적으로 가상 내선 번호 블록으로 구성됩니다. DID(Direct Inward Dialing) 번호를 통화 대기 파킹된 통화 번호 표에서 파킹된 통화 번호로 할당할 수는 없습니다.


</td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-create-or-modify-a-call-park-orbit-range.md">Lync Server 2013에서 통화 대기 번호 범위 만들기 또는 수정</a></p></td>
</tr>
<tr class="even">
<td><p>통화 대기 설정 구성</p></td>
<td><p><strong>Set-CsCpsConfiguration</strong> cmdlet을 사용하여 통화 대기 설정을 구성합니다. 최소한 <strong>OnTimeoutURI</strong> 옵션을 구성하여 대기된 통화의 시간이 초과되면 사용할 대체 대상을 구성하는 것이 좋습니다. 또한 다음 설정도 구성할 수 있습니다.</p>
<ul>
<li><p>(선택 사항) <strong>EnableMusicOnHold</strong> - 대기 음악을 사용하거나 사용하지 않도록 설정합니다.</p></li>
<li><p>(선택 사항) <strong>MaxCallPickupAttempts</strong> - 대기된 통화를 대체 URI(Uniform Resource Identifier)로 착신 전환할 때까지 해당 통화가 전화기에서 다시 울리는 횟수를 결정합니다.</p></li>
<li><p>(선택 사항) <strong>CallPickupTimeoutThreshold</strong> - 통화가 대기된 후부터 전화를 받은 전화기가 다시 울릴 때까지의 경과 시간을 결정합니다.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-call-park-settings.md">Lync Server 2013에서 통화 대기 설정 구성</a></p></td>
</tr>
<tr class="odd">
<td><p>원하는 경우 대기 음악을 사용자 지정합니다.</p></td>
<td><p><strong>Set-CsCallParkServiceMusicOnHoldFile</strong> cmdlet을 사용하여 오디오 파일을 사용자 지정하고 업로드합니다(기본 대기 음악을 사용하지 않으려는 경우)</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-customize-call-park-music-on-hold.md">Lync Server 2013에서 통화 대기 음악 사용자 지정</a></p></td>
</tr>
<tr class="even">
<td><p>사용자가 통화 대기를 사용할 수 있도록 음성 정책 구성</p></td>
<td><p>Lync Server 제어판 또는 <strong>Set-CSVoicePolicy</strong> cmdlet을 <strong>EnableCallPark</strong> 옵션과 함께 사용하여 음성 정책에서 사용자에 대해 통화 대기를 사용하도록 설정합니다.</p>


> [!NOTE]
> 기본적으로 모든 사용자가 통화 대기를 사용할 수 없도록 설정되어 있습니다.





> [!NOTE]
> 음성 정책이 여러 개인 경우에는 기본 정책뿐 아니라 각 음성 정책에 대해 EnableCallPark 속성이 설정되어 있는지 확인합니다.


</td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsUserAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-enable-call-park-for-users.md">Lync Server 2013에서 사용자에 대해 통화 대기를 사용하도록 설정</a></p></td>
</tr>
<tr class="odd">
<td><p>통화 대기에 대한 정규화 규칙 확인</p></td>
<td><p>통화 대기 파킹된 통화 번호는 정규화해서는 안 됩니다. 정규화 규칙에 파킹된 통화 번호 범위가 포함되어 있지 않은지 확인하고, 필요한 경우에는 파킹된 통화 번호가 정규화되지 않도록 추가 정규화 규칙을 만드십시오.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verify-normalization-rules-for-call-park.md">Lync Server 2013에서 통화 대기에 대한 정규화 규칙 확인</a></p></td>
</tr>
<tr class="even">
<td><p>통화 대기 배포를 확인합니다.</p></td>
<td><p>통화 대기 및 검색을 테스트하여 구성이 정상적으로 작동하는지 확인합니다.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-call-park-deployment.md">(선택 사항) Lync Server 2013에서 통화 대기 배포 확인</a></p></td>
</tr>
</tbody>
</table>

