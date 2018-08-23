---
title: 'Lync Server 2013: 호스팅된 Exchange UM 통합을 위한 배포 프로세스'
TOCTitle: 호스팅된 Exchange UM과 Lync Server의 통합을 위한 배포 프로세스
ms:assetid: dbec9c38-7f66-419d-b8c3-c61380052cac
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398968(v=OCS.15)
ms:contentKeyID: 49305230
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 호스팅된 Exchange UM과 Lync Server 2013의 통합을 위한 배포 프로세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

호스팅된 Exchange UM(통합 메시징)과의 Lync Server 2013 통합을 효율적으로 계획하려면 다음 사항을 고려해야 합니다.

  - 호스팅된 Exchange UM과 Lync Server 2013을 통합하는 데 필요한 필수 구성 요소

  - 통합 프로세스 동안 필요한 단계

## 호스팅된 Exchange UM과 통합하는 데 필요한 배포 필수 구성 요소

통합 프로세스를 시작하려면 Lync Server 2013(최소한 프런트 엔드 풀이나 Standard Edition Server), 에지 서버, Lync 2013 또는 Lync 2010 클라이언트가 배포되어 있어야 합니다.

## 통합 프로세스

다음 표에는 호스팅된 Exchange UM 통합 프로세스에 대한 개요가 나와 있습니다. 배포 단계에 대한 자세한 내용은 배포 설명서에서 [호스팅된 Exchange UM에서 Lync Server 2013 사용자 음성 메일 제공](lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md)을 참조하십시오.


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
<th>권한 및 사용 권한</th>
<th>배포 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>에지 서버 구성</p></td>
<td><ol>
<li><p>에지 서버에서 페더레이션을 사용할 수 있도록 구성합니다.</p></li>
<li><p>에지 서버에 데이터를 수동으로 복제합니다.</p></li>
<li><p>에지 서버에 호스팅 공급자를 구성합니다.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configure-the-edge-server-for-integration-with-hosted-exchange-um.md">호스팅된 Exchange UM과의 통합을 위한 에지 서버 구성</a></p></td>
</tr>
<tr class="even">
<td><p>호스팅된 음성 메일 정책 구성</p></td>
<td><ol>
<li><p>호스팅된 전역 음성 메일 정책을 수정하거나 사이트 또는 사용자별 범위에서 호스팅된 새 음성 메일 정책을 만듭니다.</p></li>
<li><p>사용자별 범위에서 만든 정책의 경우 정책을 사용자나 그룹에 할당합니다.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-manage-hosted-voice-mail-policies.md">Lync Server 2013에서 호스팅된 음성 메일 정책 관리</a></p></td>
</tr>
<tr class="odd">
<td><p>사용자가 호스팅된 음성 메일을 사용할 수 있도록 설정</p></td>
<td><ul>
<li><p>사서함이 호스팅된 Exchange 서비스에 있는 사용자에 대한 사용자 계정을 구성합니다.</p></li>
</ul></td>
<td><p>RTCUniversalUserAdmins</p></td>
<td><p><a href="lync-server-2013-enable-users-for-hosted-voice-mail.md">Lync Server 2013에서 사용자가 호스팅된 음성 사서함을 사용할 수 있도록 설정</a></p></td>
</tr>
<tr class="even">
<td><p>호스팅된 대화 상대 개체 구성</p></td>
<td><ol>
<li><p>호스팅된 Exchange UM에 대한 자동 전화 교환 대화 상대 개체를 만듭니다.</p></li>
<li><p>호스팅된 Exchange UM에 대한 구독자 액세스 대화 상대 개체를 만듭니다.</p></li>
</ol></td>
<td><p>RTCUniversalUserAdmins</p>


> [!NOTE]
> 대화 상대 개체를 만들거나 수정하거나 또는 제거하려면 New-CsExUmContact, Set-CsExUmContact 또는 Remove-CsExUmContact cmdlet를 실행하는 사용자에게 새 대화 상대 개체가 저장된 Active Directory 조직 구성 단위에 대한 올바른 권한이 있어야 합니다. 이 사용 권한을 부여하려면 Grant-CsOUPermission cmdlet를 실행하면 됩니다. 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.


</td>
<td><p><a href="lync-server-2013-create-contact-objects-for-hosted-exchange-um.md">Lync Server 2013에서 호스팅된 Exchange UM에 대한 대화 상대 개체 만들기</a></p></td>
</tr>
</tbody>
</table>

