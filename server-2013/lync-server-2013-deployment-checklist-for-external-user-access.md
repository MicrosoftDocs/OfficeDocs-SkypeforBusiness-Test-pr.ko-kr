---
title: 'Lync Server 2013: 외부 사용자 액세스를 위한 배포 검사 목록'
TOCTitle: 외부 사용자 액세스를 위한 배포 검사 목록
ms:assetid: 3f55f502-88a0-4315-8783-45a32a0b78ea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425910(v=OCS.15)
ms:contentKeyID: 49303417
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 외부 사용자 액세스를 위한 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

경계 네트워크를 배포하고 외부 사용자에 대한 지원을 구현하려면 먼저 프런트 엔드 풀 또는 Standard Edition 서버를 포함하여 Microsoft Lync Server 2013 내부 서버를 배포해야 합니다. 내부 네트워크에서 선택적인 디렉터를 배포하려는 경우 이것도 에지 서버를 배포하기 전에 배포해야 합니다. 디렉터 배포 프로세스에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 디렉터 시나리오](lync-server-2013-scenarios-for-the-director.md)를 참고하세요.

Microsoft Lync Server 2013에는 내부 서버 및 에지 서버의 계획 및 배포를 용이하게 하는 도구가 포함되어 있습니다. 토폴로지를 완료한 후 결과 토폴로지 정의를 프로덕션 환경으로 게시합니다. 이렇게 하려면 **Domain Admins** 그룹 및 **RTCUniversalServerAdmins** 그룹의 구성원이어야 합니다.

  - **계획 도구**    Office Communications Server 2007 R2에는 토폴로지 설계에 사용할 수 있는 계획 도구 및 에지 계획 도구가 포함되어 있습니다. Lync Server 2010에서 이러한 두 도구는 계획된 사용자 수, 음성 요구 사항, 외부 사용자 액세스 유형 및 페더레이션 옵션 수집과 같은 추가 기능이 포함된 단일 계획 도구로 통합되었습니다. 또한 IP 주소, 부하 분산 장치 유형 및 기타 경계 네트워크 고려 사항과 같은 인프라의 네트워크 매개 변수를 계획할 수 있습니다.

  - **토폴로지 작성기**    Lync Server 2013  토폴로지 작성기에서는 토폴로지 및 구성 요소를 정의할 수 있습니다. 토폴로지 작성기는 Lync Server 2013 실행 서버를 배포하는 데 필수적입니다. 토폴로지 작성기는 조직에서 Lync Server 2013을 실행하는 모든 서버를 구성하는 데 사용되는 중앙 관리 저장소에 결과를 게시합니다. 토폴로지 작성기를 사용하지 않으면 서버에 Lync Server 2013을 설치할 수 없습니다.

토폴로지 작성기를 실행하여 에지 토폴로지를 정의하는 작업을 비롯하여 계획 프로세스 동안 에지 토폴로지를 디자인한 경우 해당 결과를 사용하여 에지 서버 배포를 시작할 수 있습니다. 이전에 에지 토폴로지 작성을 마치지 않았거나 이전에 지정한 정보를 변경하려는 경우 다른 배포 단계를 진행하기 전에 토폴로지 작성기 실행을 마쳐야 합니다. 토폴로지 작성에 대한 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)를 참고하세요.

계획 도구 및 토폴로지 작성기에 대한 자세한 내용은 계획 설명서의 [Lync Server 2013에 대한 계획 프로세스 시작](lync-server-2013-beginning-the-planning-process.md)을 참고하세요.

다음 표에는 에지 서버 배포 프로세스에 대한 개요가 나와 있습니다. 외부 사용자 액세스를 배포하기 전에 수행해야 하는 계획시 결정할 사항을 검토하려면 [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)를 참고하세요.


> [!WARNING]
> 다음 표에서는 새 배포를 중심으로 관련 정보를 설명합니다. Lync Server 2010, Office Communications Server 2007 R2 또는 Office Communications Server 2007 환경에 에지 서버를 배포한 경우, Lync Server 2013으로 마이그레이션하는 방법에 대한 자세한 내용은 <A href="migration.md">마이그레이션</A>을 참고하세요. Office Communications Server 2007, Live Communications Server 2005, Live Communications Server 2003을 포함하여 Office Communications Server 2007 R2 이전 버전에서는 마이그레이션이 지원되지 않습니다.



에지 서버 성능과 보안을 향상시키고 배포를 용이하게 하려면 경계 네트워크 및 에지 서버를 배포할 때 다음의 모범 사례를 적용하세요.

  - 조직 내에서 Lync Server 2013이 작동하는지를 테스트 및 확인한 후에만 에지 서버를 배포합니다.

  - 도메인이 아닌 작업 그룹에서 에지 서버를 배포하는 것이 좋습니다. 이렇게 하면 설치가 간단해지고 AD DS(Active Directory 도메인 서비스)가 경계 네트워크에 포함되지 않습니다. AD DS를 경계 네트워크 내에 배치하면 상당한 보안 위험이 초래될 수 있습니다.

  - 완전히 경계 네트워크에 있는 도메인에 에지 서버를 가입시킬 수는 있지만 권장되지 않습니다. 내부 도메인의 일부인 에지 서버가 신뢰할 수 있는 네트워크 경계를 위반하게 됩니다. 인터넷은 신뢰 수준이 가장 낮고, 경계 네트워크는 인터넷보다 신뢰 수준이 높으며, 내부 네트워크는 신뢰 수준이 가장 높습니다. 도메인의 구성원인 에지 서버는 자동적으로 가장 신뢰할 수 있는 네트워크의 일부가 되지만 신뢰 수준이 낮은 네트워크(경계 네트워크)에 존재하기 때문입니다.

## 에지 서버 배포 프로세스


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
<th>사용 권한</th>
<th>설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>적절한 에지 토폴로지를 만들고 해당 구성 요소 확인</p></td>
<td><ul>
<li><p>토폴로지 작성기를 실행하여 에지 서버 설정을 구성하고 토폴로지를 생성 및 게시한 다음 Lync Server 관리 셸을 사용하여 토폴로지 구성 파일을 내보냅니다.</p></li>
</ul>
<p></p></td>
<td><p><strong>Domain Admins</strong> 그룹 및 <strong>RTCUniversalServerAdmins</strong> 또는 <strong>CsAdmins</strong> 그룹</p>


> [!NOTE]
> 로컬 사용자 그룹의 구성원인 계정을 사용하여 토폴로지를 정의할 수 있지만 토폴로지를 게시하려면 <STRONG>Domain Admins</STRONG> 그룹 및 <STRONG>RTCUniversalServerAdmins</STRONG> 그룹의 구성원인 계정이 필요합니다.


</td>
<td><p>배포 설명서의 <a href="lync-server-2013-building-an-edge-and-director-topology.md">Lync Server 2013에서 에지 및 디렉터 토폴로지 구성</a></p></td>
</tr>
<tr class="even">
<td><p>설치 준비</p></td>
<td><ol>
<li><p>시스템 필수 구성 요소를 충족하는지 확인합니다.</p></li>
<li><p>각 에지 서버에서 내부 인터페이스와 공용 네트워크 인터페이스에 대한 IP 주소(IPv4 및 IPv6)를 구성합니다.</p></li>
<li><p>에지 서버로 배포할 컴퓨터에 대한 DNS 접미사 구성을 포함하여 내부 및 외부 DNS 레코드(IPv4 및 IPv6의 경우 호스트 A 및 AAAA)를 구성합니다.</p></li>
<li><p>(선택 사항) 공용 인증서를 만들고 설치합니다. 인증서를 얻는 데 소용되는 시간은 인증서를 발급하는 CA(인증 기관)에 따라 다릅니다. 지금 이 단계를 수행하지 않은 경우 에지 서버 설치 시 이 단계를 수행해야 합니다. 인증서를 얻고 설치할 때까지 에지 서버 서비스를 시작할 수 없습니다.</p></li>
<li><p>Windows Live, AOL 또는 Yahoo! 사용자와의 통신을 지원하려면 공용 메신저 연결에 대한 지원을 프로비전합니다.</p>


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>


</li>
<li><p>XMPP에 대한 지원 및 Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 파트너에 대한 페더레이션 지원을 프로비전합니다(배포에 사용되는 경우).</p></li>
<li><p>방화벽을 구성합니다.</p></li>
</ol></td>
<td><p>조직에 적절한 권한</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-preparing-for-installation-of-servers-in-the-perimeter-network.md">Lync Server 2013의 경계 네트워크에 서버 설치 준비</a></p></td>
</tr>
<tr class="odd">
<td><p>역방향 프록시 설정</p></td>
<td><ul>
<li><p>경계 네트워크에 역방향 프록시(예: Microsoft Forefront Threat Management Gateway 2010 또는 Microsoft Internet Security and Acceleration(ISA) Server 서비스 팩 1용)를 설치하고 필요한 공용 인증서를 얻은 다음 역방향 프록시 서버에 대한 웹 게시 규칙을 구성합니다.</p>
<p>이동성을 계획하고 Mobility Service를 프런트 엔드 풀 또는 Standard Edition 서버에 배포 중인 경우 Mobility Service에 대한 역방향 프록시를 준비합니다.</p></li>
</ul></td>
<td><p><strong>Administrators</strong> 그룹 또는 역방향 프록시 관리자</p></td>
<td><p></p>
<p>배포 설명서의 <a href="lync-server-2013-setting-up-reverse-proxy-servers.md">Lync Server 2013에 대한 역방향 프록시 서버 설치</a></p></td>
</tr>
<tr class="even">
<td><p>디렉터를 설치합니다(선택 사항).</p></td>
<td><ul>
<li><p>(선택 사항) 내부 네트워크에 하나 이상의 디렉터를 설치 및 구성합니다.</p></li>
</ul></td>
<td><p><strong>Administrators</strong> 그룹</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-setting-up-the-director.md">Lync Server 2013에서 디렉터 설치</a></p></td>
</tr>
<tr class="odd">
<td><p>에지 서버 설정</p></td>
<td><ol>
<li><p>필수 소프트웨어를 설치합니다.</p></li>
<li><p>내보낸 토폴로지 구성 파일을 각 에지 서버로 전송합니다.</p></li>
<li><p>각 에지 서버에 Lync Server 2013 소프트웨어를 설치합니다.</p></li>
<li><p>에지 서버를 구성합니다.</p></li>
<li><p>각 에지 서버에 대한 인증서를 요청하고 설치합니다.</p></li>
<li><p>에지 서버 서비스를 시작합니다.</p></li>
</ol></td>
<td><p><strong>Administrators</strong> 그룹</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-setting-up-edge-servers.md">Lync Server 2013에서 에지 서버 설정</a></p></td>
</tr>
<tr class="even">
<td><p>외부 사용자 액세스에 대한 배포를 구성합니다.</p></td>
<td><ol>
<li><p>Lync Server 제어판을 사용하여 다음 각 대상에 대한 지원을 구성합니다(해당되는 경우).</p>
<ul>
<li><p>미디어 중계</p></li>
<li><p>페더레이션 경로</p></li>
<li><p>원격 사용자 액세스</p></li>
<li><p>Lync Server, Office Communications Server 및 Live Communications Server와 페더레이션</p></li>
<li><p>공용 메신저 연결</p></li>
<li><p>XMPP 페더레이션</p></li>
<li><p>익명 사용자</p></li>
</ul></li>
<li><p>원격 사용자 액세스, 페더레이션, 공용 메신저 연결, XMPP 및 익명 사용자 지원을 구성합니다(적용 가능한 경우).</p></li>
</ol></td>
<td><p><strong>RTCUniversalServerAdmins</strong> 그룹 또는 <strong>CSAdministrator</strong> 역할에 지정된 사용자 계정</p>
<p></p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-configuring-support-for-external-user-access.md">Lync Server 2013에서 외부 사용자 액세스에 대한 지원 구성</a></p></td>
</tr>
<tr class="odd">
<td><p>에지 서버 구성 확인</p></td>
<td><ol>
<li><p>서버 연결 및 내부 서버의 구성 데이터 복제를 확인합니다.</p></li>
<li><p>원격 사용자, 페더레이션 도메인의 사용자, 공용 메신저 사용자 및 익명 사용자를 포함하여 배포에 해당되는 외부 사용자가 연결할 수 있는지 확인합니다.</p></li>
<li><p>Lync Server 원격 연결 분석기( <a href="https://www.testocsconnectivity.com" class="uri">https://www.testocsconnectivity.com</a>)를 사용하여 구성 및 통신을 확인합니다.</p></li>
<li><p>구성 및 통신 문제를 해결합니다.</p></li>
</ol></td>
<td><p>복제 확인의 경우 <strong>RTCUniversalServerAdmins</strong> 그룹 또는 <strong>CSAdministrator</strong> 역할에 지정된 사용자 계정</p>
<p>사용자 연결 확인의 경우 지원할 각 외부 사용자 액세스 유형의 사용자</p>
<p>원격 사용자</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-verifying-your-edge-deployment.md">Lync Server 2013에서 에지 배포 확인</a></p></td>
</tr>
</tbody>
</table>

