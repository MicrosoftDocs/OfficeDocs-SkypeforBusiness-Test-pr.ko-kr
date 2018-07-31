---
title: 'Lync Server 2013: 온-프레미스 통합 메시징 통합을 위한 배포 프로세스'
TOCTitle: 온-프레미스 통합 메시징과 Lync Server의 통합을 위한 배포 프로세스
ms:assetid: 269a4436-f09f-415b-96ab-49a64370a385
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425737(v=OCS.15)
ms:contentKeyID: 49303101
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 온-프레미스 통합 메시징과 Lync Server 2013의 통합을 위한 배포 프로세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

Exchange 통합 메시징(UM)을 Lync Server 2013과 통합하려면 이 항목에 설명된 작업을 수행해야 합니다. 또한 [온-프레미스 통합 메시징과 Lync Server 2013의 통합에 대한 지침](lync-server-2013-guidelines-for-integrating-on-premises-unified-messaging.md)에 설명된 계획 및 배포 모범 사례를 검토해야 합니다. 이 항목에서는 중재 서버가 배치된 상태로 Lync Server 2013을 배포하고 사용자들이 Lync Server 2013을 사용할 수 있도록 설정했다고 가정하지만, 배포 설명서의 [Lync Server 2013에서 Enterprise Voice 배포](lync-server-2013-deploying-enterprise-voice.md)에 설명된 대로 Enterprise Voice를 사용하도록 설정하는 데 필요한 모든 배포 및 구성 단계를 수행했다고 가정하지는 않습니다.

## 통합 메시징 통합 프로세스


> [!IMPORTANT]
> 조직의 Exchange 관리자와 함께 원활하고 성공적인 통합을 위해 각자가 수행할 작업을 확인해야 합니다.




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
<td><p>다음 중 하나를 배포합니다.</p>
<ul>
<li><p>Microsoft Exchange Server 2007 서비스 팩 1(SP2) 또는 최신 서비스 팩</p></li>
<li><p>Microsoft Exchange Server 2010 또는 최신 서비스 팩</p></li>
<li><p>Microsoft Exchange Server 2013</p></li>
</ul></td>
<td><p>Microsoft Exchange Server 2013을 사용 중인 경우 Lync Server 2013과 동일한 포리스트 또는 다른 포리스트에 다음 Exchange Server 역할을 설치합니다.</p>
<ul>
<li><p>클라이언트 액세스</p></li>
<li><p>사서함</p></li>
</ul>
<p>Microsoft Exchange Server 2013 및 Exchange 통합 메시징(UM)이 서로 다른 포리스트에 설치되어 있으면 Lync Server 2013 포리스트를 신뢰하도록 각 Exchange 포리스트를 구성합니다.</p>
<p>Exchange 2010을 사용 중인 경우 Lync Server 2013과 동일한 포리스트 또는 다른 포리스트에 다음 Exchange Server 역할을 설치합니다.</p>
<ul>
<li><p>통합 메시징</p></li>
<li><p>허브 전송</p></li>
<li><p>클라이언트 액세스</p></li>
<li><p>사서함</p></li>
</ul>
<p>Lync Server 2013 및 Exchange 통합 메시징(UM)이 서로 다른 포리스트에 설치되어 있으면 Lync Server 2013 포리스트를 신뢰하도록 각 Exchange 포리스트를 구성합니다.</p></td>
<td><p>엔터프라이즈 관리자(조직의 첫 번째 Exchange Server인 경우)</p>
<p>-또는-</p>
<p>Exchange 조직 관리자(조직의 첫 번째 Exchange Server가 아닌 경우)</p></td>
<td><p>Exchange Server 버전에 적절한 설명서를 참조하십시오.</p>
<dl>
<dt><span></span></dt>
<dd><p>Exchange Server 2007 배포 설명서( <a href="http://go.microsoft.com/fwlink/?linkid=268694%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268694&amp;clcid=0x412</a>)</p>
</dd>
<dt><span></span></dt>
<dd><p>Exchange Server 2010 또는 최신 서비스 팩 배포 설명서( <a href="http://go.microsoft.com/fwlink/?linkid=268695%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268695&amp;clcid=0x412</a>)</p>
</dd>
<dt><span></span></dt>
<dd><p>Microsoft Exchange Server 2013 계획 및 배포( <a href="http://go.microsoft.com/fwlink/?linkid=266569%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=266569&amp;clcid=0x412</a>)</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>인증서를 설치합니다.</p></td>
<td><p>신뢰할 수 있는 루트 CA(인증 기관)에서 각 Exchange UM 서버에 대한 인증서를 다운로드하여 설치합니다. 인증서는 Exchange UM 및 Lync Server 2013을 실행하는 서버 간의 MTLS(Mutual TLS)에 필요합니다.</p></td>
<td><p>Administrators</p></td>
<td><p><a href="lync-server-2013-configure-certificates-on-the-server-running-microsoft-exchange-server-unified-messaging.md">Microsoft Exchange Server 통합 메시징을 실행하는 서버에서 인증서 구성</a></p></td>
</tr>
<tr class="odd">
<td><p>새 Exchange UM SIP 다이얼 플랜을 만들고 구성합니다.</p></td>
<td><p>Exchange UM 서버에서 조직의 특정 배포 요구 사항에 따라 SIP 다이얼 플랜을 만듭니다.</p></td>
<td><p>Exchange 조직 관리자</p></td>
<td><p>Exchange 2007 SP1 또는 최신 서비스 팩의 경우 &quot;통합 메시징 SIP URI 다이얼 플랜을 만드는 방법&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268632%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268632&amp;clcid=0x412</a>)을 참조하십시오.</p>
<p>Exchange 2010 또는 최신 서비스 팩의 경우 &quot;UM 다이얼 플랜 만들기&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268674%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268674&amp;clcid=0x412</a>)를 참조하십시오.</p>
<p>Exchange 2013의 경우 통합 메시징( <a href="http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=266579&amp;clcid=0x412</a>)을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p>Exchange UM SIP 다이얼 플랜에 대한 보안 설정을 구성합니다.</p></td>
<td><p>Enterprise Voice 트래픽을 암호화하려면 Exchange UM SIP 다이얼 플랜의 보안 설정을 <strong>SIP 보안</strong> 또는 <strong>보안</strong>으로 구성합니다. 이 단계는 Lync Phone Edition 장치를 환경에 배포했거나 배포하려는 경우에 특히 중요합니다. Lync Phone Edition 장치가 Exchange UM과 통합된 환경에서 작동하려면 Lync Server 암호화 설정이 Exchange UM 다이얼 플랜 보안 설정과 일치해야 합니다. 자세한 내용은 배포 설명서를 참조하십시오.</p></td>
<td><p>Exchange 조직 관리자</p></td>
<td><p><a href="lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md">Microsoft Exchange에서 Lync Server 2013용 통합 메시징 구성</a></p>
<p>Exchange 2007 SP1 또는 최신 서비스 팩의 경우 다음을 참조하십시오.</p>
<p>&quot;통합 메시징 다이얼 플랜의 보안 설정 구성&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268696%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268696&amp;clcid=0x412</a>)</p>
<p></p>
<p>Exchange 2010 또는 최신 서비스 팩의 경우 다음을 참조하십시오.</p>
<p>&quot;UM 다이얼 플랜에서 VoIP 보안 구성&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268697%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268697&amp;clcid=0x412</a>)</p>
<p></p>
<p>Exchange 2013의 경우 통합 메시징( <a href="http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=266579&amp;clcid=0x412</a>)을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p>통합 메시징 서버를 Exchange UM SIP 다이얼 플랜에 추가합니다.</p></td>
<td><p>새로 설치한 통합 메시징 서버에서 수신 전화에 응답하고 통화를 처리하도록 하려면 통합 메시징 서버를 UM 다이얼 플랜에 추가해야 합니다. 이 경우 서버를 Exchange UM SIP 다이얼 플랜에 추가합니다.</p></td>
<td><p>Administrators</p>
<p>Exchange Server 관리자</p></td>
<td><p>Exchange 2007 SP1 또는 최신 서비스 팩의 경우 &quot;다이얼 플랜에 통합 메시징 서버를 추가하는 방법&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268681%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268681&amp;clcid=0x412</a>)을 참조하십시오.</p>
<p>Exchange 2010 또는 최신 서비스 팩의 경우 &quot;UM 서버 속성 보기 또는 구성&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268682%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268682&amp;clcid=0x412</a>)을 참조하십시오.</p>
<p></p>
<p>Exchange 2013의 경우 통합 메시징( <a href="http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=266579&amp;clcid=0x412</a>)을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p>SIP 주소를 사용하여 사서함을 구성합니다.</p></td>
<td><p>Exchange UM 기능을 사용할 Enterprise Voice 사용자의 사서함에 SIP 주소를 할당합니다.</p></td>
<td><p>Lync Server 2013 관리자</p>
<p>Exchange 받는 사람 관리자</p></td>
<td><p>Exchange 2007 SP1 또는 최신 서비스 팩의 경우 &quot;UM 사용 가능 사용자에 대해 SIP 주소를 추가, 제거 및 수정하는 방법&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268698%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268698&amp;clcid=0x412</a>)을 참조하십시오.</p>
<p>Exchange 2010 또는 최신 서비스 팩의 경우 &quot;UM 사용 가능 사용자의 SIP 주소 수정&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268699%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268699&amp;clcid=0x412</a>)을 참조하십시오.</p>
<p></p>
<p>Exchange 2013의 경우 통합 메시징( <a href="http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=266579&amp;clcid=0x412</a>)을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p>exchucutil.ps1 스크립트를 실행합니다.</p></td>
<td><p>Exchange UM 서비스를 실행하는 서버에서 Exchange 관리 셸을 열고 exchucutil.ps1 스크립트를 실행하면 다음 작업이 수행됩니다.</p>
<ul>
<li><p>Lync Server 2013에 Exchange UM  Active Directory 도메인 서비스 개체, 특히 이전 작업에서 만든 SIP 다이얼 플랜을 읽을 수 있는 권한을 부여합니다.</p></li>
<li><p>Active Directory에 Enterprise Voice를 사용하도록 설정된 사용자를 호스팅하는 각 Lync Server 2013 Enterprise Edition 풀 또는 Standard Edition 서버에 대한 통합 메시징 IP 게이트웨이를 만듭니다.</p></li>
<li><p>각 게이트웨이에 대한 Exchange UM 헌트 그룹을 만듭니다. 헌트 그룹 파일럿 식별자는 해당 게이트웨이에 연결된 다이얼 플랜의 이름이 됩니다. 둘 이상의 다이얼 플랜이 있는 경우 이러한 식별자는 1:1 매핑되어야 합니다.</p></li>
</ul></td>
<td><p>Exchange 조직 관리자</p>
<p>Exchange 받는 사람 관리자</p></td>
<td><p><a href="lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md">Microsoft Exchange에서 Lync Server 2013용 통합 메시징 구성</a></p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 다이얼 플랜을 구성합니다.</p></td>
<td><p>Exchange 2007 SP1 또는 최신 서비스 팩이나 Exchange 2010과 통합하는 경우 Exchange UM 다이얼 플랜 FQDN(정규화된 도메인 이름)과 일치하는 이름으로 새 Enterprise Voice 다이얼 플랜을 만듭니다.</p>


> [!NOTE]
> 각 UM 다이얼 플랜에 대해 이 작업을 수행해야 합니다.



<p>Exchange 2010 SP1과 통합하는 경우 적절한 전역/사이트 수준 또는 풀 수준 Enterprise Voice 다이얼 플랜이 구성되었는지 확인합니다.</p>


> [!NOTE]
> Exchange 2010 SP1과 통합하는 경우에는 Lync Server 다이얼 플랜 이름과 Exchange UM SIP 다이얼 플랜 이름이 일치하지 않아도 됩니다.


</td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configuring-dial-plans.md">Lync Server 2013에서 다이얼 플랜 구성</a></p></td>
</tr>
<tr class="odd">
<td><p>Exchange UM 통합 풀을 실행합니다.</p></td>
<td><p>Lync Server 2013에서 <strong>ocsumutil.exe</strong>를 실행합니다. 다음 작업이 수행됩니다.</p>
<ul>
<li><p>구독자 액세스 및 자동 전화 교환 대화 상대 개체를 만듭니다.</p></li>
<li><p>Exchange UM 다이얼 플랜과 이름이 일치하는 Enterprise Voice 다이얼 플랜이 있는지 확인합니다. Exchange 2010 SP1 이상을 실행하는 경우에는 다이얼 플랜 이름이 일치하지 않아도 되므로 이와 관련된 도구 경고를 무시할 수 있습니다.</p></li>
</ul>
<p>이 도구는 Active Directory에서 Exchange UM 설정을 검색하며 Lync Server 2013 관리자가 연락처 개체를 보고 만들고 편집할 수 있도록 합니다.</p></td>
<td><p>RTCUniversalServerAdmins <em>및</em> RTCUniversalUserAdmins</p>


> [!IMPORTANT]
> ocsumutil.exe를 실행하려면 사용자가 이 두 그룹 모두에 속해 있어야 합니다.





> [!NOTE]
> 대화 상대 개체를 만들려면 ocsumutil.exe를 실행하는 사용자에게 새 대화 상대 개체를 저장할 Active Directory OU(조직 구성 단위)에 대한 올바른 권한이 있어야 합니다. 이 사용 권한을 부여하려면 <STRONG>Grant-CsOUPermission</STRONG> cmdlet을 실행하면 됩니다. 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.


</td>
<td><p><a href="lync-server-2013-configure-lync-server-2013-to-work-with-unified-messaging-on-microsoft-exchange-server.md">Microsoft Exchange Server의 통합 메시징과 함께 작동하도록 Lync Server 2013 구성</a></p></td>
</tr>
<tr class="even">
<td><p>필요한 경우 다른 Enterprise Voice 구성 단계를 수행합니다.</p></td>
<td><p>서버 또는 사용자에 대해 Enterprise Voice 설정을 아직 구성하지 않은 경우 다음 중 하나 이상을 수행합니다.</p>
<ul>
<li><p>공중 전화망(PSTN)</p>
<p>게이트웨이와 중재 서버 배포 및 구성</p></li>
<li><p>음성 정책, PSTN 사용 레코드 및 아웃바운드 통화 경로 정의</p></li>
<li><p>사용자가 Enterprise Voice를 사용할 수 있도록 설정</p></li>
<li><p>(선택 사항) 다이얼 플랜을 사용하여 특정 사용자 구성</p></li>
</ul>
<p>사용하도록 설정한 Enterprise Voice 기능에 따라 다른 구성 단계가 필요할 수도 있습니다.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>RTCUniversalUserAdmins</p></td>
<td><p>다음 섹션의 항목을 참조하십시오.</p>
<ul>
<li><p><a href="lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md">Lync Server 2013에서 음성 정책, PSTN 사용 레코드 및 음성 경로 구성</a></p></li>
<li><p><a href="lync-server-2013-deploying-enterprise-voice.md">Lync Server 2013에서 Enterprise Voice 배포</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Exchange UM 사용자에 대해 Enterprise Voice를 사용하도록 설정합니다.</p></td>
<td><p>Exchange UM 서버에서 통합 메시징 사서함 정책이 만들어져 있고 각 사용자에게 고유 내선 번호가 할당되어 있는지 확인한 다음 사용자가 통합 메시지를 사용할 수 있도록 설정합니다.</p></td>
<td><p>Exchange 받는 사람 관리자</p></td>
<td><p>Exchange 2007 SP1 또는 최신 서비스 팩의 경우 &quot;통합 메시징을 사용하도록 설정하는 방법&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268700%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268700&amp;clcid=0x412</a>)을 참조하십시오.</p>
<p>Exchange 2010 또는 최신 서비스 팩의 경우 &quot;사용자가 통합 메시징을 사용하도록 설정&quot;( <a href="http://go.microsoft.com/fwlink/?linkid=268701%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=268701&amp;clcid=0x412</a>)을 참조하십시오.</p>
<p></p>
<p>Exchange 2013의 경우 통합 메시징( <a href="http://go.microsoft.com/fwlink/?linkid=266579%26clcid=0x412" class="uri">http://go.microsoft.com/fwlink/?linkid=266579&amp;clcid=0x412</a>)을 참조하십시오.</p></td>
</tr>
</tbody>
</table>

