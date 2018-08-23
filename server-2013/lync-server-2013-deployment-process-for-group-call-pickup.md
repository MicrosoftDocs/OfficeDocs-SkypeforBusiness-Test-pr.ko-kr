---
title: 그룹 호출 받기 배포 프로세스
TOCTitle: 그룹 호출 받기 배포 프로세스
ms:assetid: 082daeac-e667-4e2d-b78d-8e0901f9f0e9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945615(v=OCS.15)
ms:contentKeyID: 52056783
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 그룹 호출 받기 배포 프로세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 그룹 호출 받기를 배포할 때 수행하는 단계를 간략하게 설명합니다. 그룹 호출 받기를 구성하기 전에 Enterprise Voice가 포함된 Enterprise Edition 또는 Standard Edition을 배포해야 합니다. 그룹 호출 받기에 필요한 구성 요소는 Enterprise Voice를 배포할 때 설치 및 설정됩니다.

### 그룹 호출 받기 배포 프로세스

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
<th>단계</th>
<th>필수 그룹 및 역할</th>
<th>배포 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>토폴로지에서 SEFAUtil 리소스 키트를 사용하도록 설정</p></td>
<td><ol>
<li><p><strong>New-CsTrustedApplicationPool</strong> cmdlet을 사용하여 신뢰할 수 있는 응용 프로그램 풀을 새로 만듭니다.</p></li>
<li><p><strong>New-CsTrustedApplication</strong> cmdlet을 사용하여 SEFAUtil 도구를 신뢰할 수 있는 응용 프로그램으로 지정합니다.</p></li>
<li><p><strong>Enable-CsTopology</strong> cmdlet을 실행하여 토폴로지를 사용하도록 설정합니다.</p></li>
<li><p>1단계에서 만든 신뢰할 수 있는 응용 프로그램 풀에 있는 프런트 엔드 서버에 리소스 키트 도구를 설치합니다.</p></li>
<li><p>SEFAUtil을 실행해 배포에 포함된 사용자의 착신 전환 설정을 표시하여 SEFAUtil이 정상적으로 실행되는지 확인합니다.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploy-the-sefautil-tool.md">SEFAUtil 도구 배포</a></p></td>
</tr>
<tr class="even">
<td><p>통화 대기 번호 테이블에서 호출 받기 번호 범위 구성</p></td>
<td><p><strong>New-CSCallParkOrbit</strong> cmdlet을 사용해 통화 대기 번호 테이블에서 호출 받기 번호 범위를 만들고 호출 받기 범위에 GroupPickup 유형을 할당합니다.</p>


> [!NOTE]
> 통화 대기 번호 테이블에서 그룹 호출 받기 번호 범위를 만들고 수정하고 제거하고 보려면 Lync Server 관리 셸을 사용해야 합니다. Lync Server 제어판에서는 그룹 호출 받기 번호 범위를 사용할 수 없습니다.




> [!NOTE]
> 기존 다이얼 플랜과 원활하게 통합할 수 있도록, 번호 범위는 일반적으로 가상 내선 번호 블록으로 구성됩니다. DID(Direct Inward Dialing) 번호를 통화 대기 번호 테이블에서 범위 번호로 할당할 수는 없습니다.


</td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-call-pickup-group-numbers.md">호출 받기 그룹 번호 구성</a></p></td>
</tr>
<tr class="odd">
<td><p>사용자에게 호출 받기 번호를 할당하고 사용자에 대해 그룹 호출 받기를 사용하도록 설정</p></td>
<td><p>SEFAUtil 리소스 키트 도구에서 /enablegrouppickup 매개 변수를 사용하여 그룹 호출 받기를 사용하도록 설정하고 사용자에 대해 호출 받기 번호를 할당합니다.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-enable-group-call-pickup-for-users-and-assign-a-group-number.md">사용자에 대해 그룹 호출 받기를 사용하도록 설정하고 그룹 번호 할당</a></p></td>
</tr>
<tr class="even">
<td><p>사용자에게 할당된 호출 받기 번호와 기타 관련 번호 알려 주기</p></td>
<td><p>모든 사용자가 그룹 호출 받기 사용자에게 걸려온 전화를 받을 수 있으므로 사용자가 둘 이상의 그룹을 모니터링할 수 있습니다.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-communicate-group-call-pickup-assignment-to-users.md">사용자에게 그룹 호출 받기 할당 전달</a></p></td>
</tr>
<tr class="odd">
<td><p>그룹 호출 받기 배포 확인</p></td>
<td><p>전화 걸기와 재개를 테스트하여 구성이 정상적으로 작동하는지 확인합니다.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-the-group-call-pickup-deployment.md">(선택 사항) 그룹 호출 받기 배포 확인</a></p></td>
</tr>
</tbody>
</table>

