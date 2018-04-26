---
title: 'Lync Server 2013: 하이브리드 Lync Server 배포 계획'
TOCTitle: 하이브리드 Lync Server 배포 계획
ms:assetid: f8b3d240-bc2e-42c9-acf8-d532d641a14c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205403(v=OCS.15)
ms:contentKeyID: 49305605
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 하이브리드 배포 계획

 

_**마지막으로 수정된 항목:** 2015-08-19_

하이브리드 배포를 계획할 때는 사용자 및 네트워크 인프라에 대해 다음과 같은 요구 사항을 고려해야 합니다.

## 인프라 요구 사항

Lync Server 2013 하이브리드 배포를 구현하고 구성하려면 환경에서 다음 항목을 사용할 수 있어야 합니다.

  - Lync Online을 사용하도록 설정된 Office 365 테넌트

  - 온-프레미스 또는 Microsoft Azure를 사용하는 AD FS(Active Directory Federation Services) 서버. AD FS에 대한 자세한 내용은 [AD FS(Active Directory Federation Services) 2.0](http://go.microsoft.com/fwlink/p/?linkid=393795) 또는 [Windows Azure Pack용 Active Directory Federation Services 구성](http://go.microsoft.com/fwlink/p/?linkid=522475)을 참조하세요.

  - Lync Server 2010에 대한 누적 업데이트(2013년 3월 이후)가 적용된 Lync Server 2013 또는 Lync Server 2010의 온-프레미스 배포

  - Lync Server 2013 관리 도구

  - 디렉터리 동기화. 디렉터리 동기화에 대한 자세한 내용은 [하이브리드 ID 관리](http://go.microsoft.com/fwlink/p/?linkid=231010)를 참조하세요.

## Lync 클라이언트 지원

Lync 클라이언트에서 지원되는 기능과 온-프레미스 및 온라인 환경에서 사용 가능한 기능에는 다소 차이가 있습니다. 조직의 사용자를 포함할 위치를 결정하기 전에 다양한 Lync Server 구성에 대한 클라이언트 지원을 확인할 수 있습니다. Lync 하이브리드 배포에서 비즈니스용 Skype Online과 함께 다음 클라이언트가 지원됩니다.

  - Lync 2010

  - Lync 2013

  - Lync Windows 스토어 앱

  - Lync Web App

  - Lync Mobile

  - Mac 2011용 Lync

  - Lync 채팅방 시스템

  - Lync Basic 2013

클라이언트 지원에 대한 자세한 내용은 다음 항목을 참조하세요.

  - [Lync Online 클라이언트](http://go.microsoft.com/fwlink/?linkid=281902)

  - [Lync Server 2013 의 클라이언트 비교 표](lync-server-2013-desktop-client-comparison-tables.md)

  - [Lync Server 2013 의 모바일 클라이언트 비교 표](lync-server-2013-mobile-client-comparison-tables.md)

## 토폴로지 요구 사항

비즈니스용 Skype Online과의 하이브리드 방식 배포용으로 Lync Server 2013 배포를 구성하려면 다음의 지원되는 토폴로지 중 하나가 필요합니다.

  - Microsoft Office Communications Server 2007 R2(Lync Server 2013 온-프레미스 포함). Lync Server 2013 페더레이션에지 서버 및 페더레이션 에지 서버의 다음 홉 서버는 Lync Server 2013을 실행해야 하며 중앙 관리 저장소가 배포되어 있어야 합니다. 에지 서버 및 풀은 온-프레미스에 배포해야 합니다.
    

    > [!IMPORTANT]
    > 이 토폴로지가 지원되기는 하지만 일부 기능이 제한될 수 있습니다. 예를 들어 Microsoft Lync Online 사용자와 온-프레미스 Office Communications Server 2007 R2 사용자 간의 현재 상태 정보가 예상대로 작동하지 않을 수 있습니다.



  - Lync Server 2010에 대한 누적 업데이트(2013년 3월 이후)가 적용된 Microsoft Lync Server 2010 및 온-프레미스에 설치된 Lync Server 2013 관리 도구. 페더레이션 에지 서버 및 페더레이션 에지 서버의 다음 홉 서버는 2013년 3월 이후의 누적 업데이트가 적용된 Microsoft Lync Server 2010이나 Lync Server 2013을 실행해야 합니다.
    

    > [!IMPORTANT]
    > 기존 Lync Server 2010 배포에 연결할 수 있는 권한이 있는 별도의 서버에 Lync Server 2013 관리 도구가 설치되어야 합니다. 사용자를 온-프레미스 배포에서 Lync Online으로 이동하는 Move-CsUser cmdlet을 온-프레미스 배포에 연결된 Lync Server 2013 관리 도구에서 실행해야 합니다.



  - 모든 서버가 Lync Server 2013을 실행하는 Lync Server 2013 배포

지원되는 토폴로지에 대한 자세한 내용은 [Lync Server 2013의 지원되는 토폴로지](lync-server-2013-supported-topologies.md) 및 [엔터프라이즈 하이브리드 배포를 위한 Lync Server 2013 참조 토폴로지](http://go.microsoft.com/fwlink/p/?linkid=398709)를 참조하세요.

하이브리드 배포 및 Lync Online에 PowerShell 연결에 관한 문제 해결 정보는 [Lync Online: Lync PowerShell 및 하이브리드 문제 해결](http://go.microsoft.com/fwlink/p/?linkid=306718)을 참조하세요.

## 페더레이션 허용/차단 목록 요구 사항

허용 도메인 목록에는 파트너 에지 FQDN(정규화된 도메인 이름)이 구성된 도메인이 포함되어 있습니다. 이러한 도메인을 *허용된 파트너 서버* 또는 *직접 페더레이션 파트너*라고도 합니다. 온-프레미스 배포에서 열려 있는 페더레이션과 닫혀 있는 페더레이션(각각 *파트너 검색*과 *허용된 파트너 도메인 목록*이라고 함) 간의 차이를 파악해야 합니다.

하이브리드 배포를 올바르게 구성하려면 다음 요구 사항이 충족되어야 합니다.

  - 온-프레미스 배포와 Office 365 테넌트에 대해 도메인 일치를 동일하게 구성해야 합니다. 온-프레미스 배포에서 파트너 검색을 사용하도록 설정한 경우에는 온라인 테넌트에 대해 열려 있는 페더레이션을 구성해야 합니다. 파트너 검색을 사용하도록 설정하지 않은 경우에는 온라인 테넌트에 대해 닫혀 있는 페더레이션을 구성해야 합니다.

  - 온-프레미스 배포의 차단된 도메인 목록은 온라인 테넌트의 차단된 도메인 목록과 정확하게 일치해야 합니다.

  - 온-프레미스 배포의 허용된 도메인 목록은 온라인 테넌트의 허용된 도메인 목록과 정확하게 일치해야 합니다.

  - 온라인 테넌트에 대해 페더레이션에서 외부 통신을 사용하도록 설정해야 합니다(Lync Online 제어판을 사용하여 구성함).

## DNS 설정

하이브리드 배포용으로 DNS SRV 레코드를 만들 때 \_sipfederationtls.\_tcp.\<도메인\> 및 \_sip.\_tls.\<도메인\> 레코드는 온-프레미스 액세스 프록시를 가리켜야 합니다.

## 방화벽 고려 사항

네트워크의 컴퓨터는 표준 인터넷 DNS 조회를 수행할 수 있어야 합니다. 이러한 컴퓨터가 표준 인터넷 사이트에 연결할 수 있으면 네트워크는 이 요구 사항을 충족하는 것입니다.

Microsoft Online Services 데이터 센터의 위치에 따라 와일드카드 도메인 이름(예: \*.outlook.com의 모든 트래픽)을 기준으로 연결을 수락하도록 네트워크 방화벽 장치도 구성해야 합니다. 조직의 방화벽에서 와일드카드 이름 구성을 지원하지 않는 경우에는 지정된 포트를 허용하려는 IP 주소 범위를 수동으로 결정해야 합니다.

도움말 항목 [Office 365 URL 및 IP 주소 범위](http://go.microsoft.com/fwlink/p/?linkid=252942)를 참조하세요.

## 포트 및 프로토콜 요구 사항

내부 Lync Server 2013 통신을 위한 포트 요구 사항 외에 다음 포트도 구성해야 합니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>프로토콜/포트</th>
<th>응용 프로그램</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP 443</p></td>
<td><p>인바운드 열기</p>
<ul>
<li><p>Active Directory Federation Services(페더레이션 서버 역할)</p>
<p>자세한 내용은 <a href="http://go.microsoft.com/fwlink/p/?linkid=281899">AD FS 역할 서비스 이해</a>를 참조하세요.</p></li>
<li><p>Active Directory Federation Services(프록시 서버 역할)</p></li>
<li><p>Microsoft Online Services 포털</p></li>
<li><p>내 회사 포털</p></li>
<li><p>Outlook Web App</p></li>
<li><p>Lync 클라이언트(온-프레미스 Lync Server에서 Lync Online으로의 통신)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>TCP 80 및 443</p></td>
<td><p>인바운드 열기</p>
<ul>
<li><p>Microsoft Online Services 디렉터리 동기화 도구</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>TCP 5061</p></td>
<td><p>에지 서버에서 인바운드/아웃바운드 열기</p></td>
</tr>
<tr class="even">
<td><p>PSOM/TLS 443</p></td>
<td><p>데이터 공유 세션용으로 인바운드/아웃바운드 열기</p></td>
</tr>
<tr class="odd">
<td><p>STUN/TCP 443</p></td>
<td><p>오디오, 비디오, 응용 프로그램 공유 세션용으로 인바운드/아웃바운드 열기</p></td>
</tr>
<tr class="even">
<td><p>STUN/UDP 3478</p></td>
<td><p>오디오 및 비디오 세션용으로 인바운드/아웃바운드 열기</p></td>
</tr>
<tr class="odd">
<td><p>RTP/TCP 50000-59999</p></td>
<td><p>오디오 및 비디오 세션용으로 아웃바운드 열기</p></td>
</tr>
<tr class="even">
<td><p>TCP 443</p></td>
<td><p>인바운드 열기</p>
<ul>
<li><p>Active Directory Federation Services(페더레이션 서버 역할)</p>
<p>자세한 내용은 <a href="http://go.microsoft.com/fwlink/p/?linkid=281899">AD FS 역할 서비스 이해</a>를 참조하세요.</p></li>
<li><p>Active Directory Federation Services(프록시 서버 역할)</p></li>
<li><p>Microsoft Online Services 포털</p></li>
<li><p>내 회사 포털</p></li>
<li><p>Outlook Web App</p></li>
<li><p>Lync 클라이언트(온-프레미스 Lync Server에서 Lync Online으로의 통신)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>TCP 80 및 443</p></td>
<td><p>인바운드 열기</p>
<ul>
<li><p>Microsoft Online Services 디렉터리 동기화 도구</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>TCP 5061</p></td>
<td><p>에지 서버에서 인바운드/아웃바운드 열기</p></td>
</tr>
<tr class="odd">
<td><p>PSOM/TLS 443</p></td>
<td><p>데이터 공유 세션용으로 인바운드/아웃바운드 열기</p></td>
</tr>
<tr class="even">
<td><p>STUN/TCP 443</p></td>
<td><p>오디오, 비디오, 응용 프로그램 공유 세션용으로 인바운드/아웃바운드 열기</p></td>
</tr>
<tr class="odd">
<td><p>STUN/UDP 3478</p></td>
<td><p>오디오 및 비디오 세션용으로 인바운드/아웃바운드 열기</p></td>
</tr>
<tr class="even">
<td><p>RTP/TCP 50000-59999</p></td>
<td><p>오디오 및 비디오 세션용으로 아웃바운드 열기</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Office Communications Server 2007을 실행하는 파트너와의 페더레이션을 수행해야 하는 경우에는 인바운드/아웃바운드 RTP/UDP 및 RTP/TCP 포트 50000-59999를 열어야 합니다. A/V 방화벽 요구 사항에 대한 자세한 내용은 <A href="lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md">Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인</A>을 참조하세요. 포트 및 프로토콜에 대한 자세한 내용은 <A href="lync-server-2013-port-summary-scaled-consolidated-edge-with-hardware-load-balancers.md">Lync Server 2013의 포트 요약 - 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지</A>를 참조하세요.



## 사용자 계정 및 데이터

Lync Server 2013 하이브리드 배포에서는 Lync Online에 포함하려는 모든 사용자를 먼저 온-프레미스 배포에서 만들어 Active Directory 도메인 서비스에서 사용자 계정을 만들어야 합니다. 그런 후에 사용자를 비즈니스용 Skype Online으로 이동할 수 있으며, 그러면 사용자의 대화 상대 목록도 이동됩니다.

Lync 온-프레미스와 AD FS 및 Dirsync가 포함된 Lync Online 배포 간에 사용자 계정을 동기화할 때, 사용자를 Lync Online으로 이동하지 않더라도 조직에 있는 모든 Lync 사용자의 AD 계정을 온-프레미스와 온라인 Lync 배포 간에 동기화해야 합니다. 모든 사용자를 동기화하지 않은 경우 조직의 온-프레미스와 온라인 사용자 간의 통신이 정상적으로 작동하지 않을 수 있습니다.


> [!IMPORTANT]
> Office 365용 온라인 포털을 통해 사용자를 만드는 경우에는 사용자 계정이 온-프레미스 Active Directory와 동기화되지 않으며 사용자가 온-프레미스 Active Directory에 존재하지 않습니다. Lync Online에서 이미 사용자를 만들었고 온-프레미스 Lync Server를 하이브리드로 구성하려면 <A href="lync-server-2013-moving-users-from-lync-online-to-lync-on-premises.md">Lync Server 2013에서 Lync Online과 Lync 온-프레미스 간 사용자 이동</A>을 참조하세요.



하이브리드 배포를 계획할 때는 다음과 같은 사용자 관련 문제도 고려해야 합니다.

  - **사용자 대화 상대**    Lync Online 사용자의 대화 상대 제한은 250명입니다. 이 값을 초과하는 대화 상대는 Lync로 계정이 이동될 때 사용자의 대화 상대 목록에서 제거됩니다.

  - **메신저 대화 및 현재 상태**   사용자 대화 상대 목록, 그룹 및 ACL(액세스 제어 목록)은 사용자 계정과 함께 마이그레이션됩니다.

  - **회의 데이터, 모임 콘텐츠 및 예약된 모임**   이 콘텐츠는 사용자 계정과 함께 마이그레이션되지 않습니다. 사용자는 해당 계정이 Lync Online으로 마이그레이션된 후 모임을 다시 예약해야 합니다.

## 사용자 정책 및 기능

  - Lync Server 2013 하이브리드 환경에서는 사용자가 온-프레미스 또는 온라인 중 하나에서 메신저 대화, 음성 및 모임을 사용하도록 설정할 수는 있지만 둘 다에서 이러한 항목을 사용하도록 설정할 수는 없습니다.

  - **Lync 클라이언트**    일부 사용자의 경우 Lync Online으로 이동하면 새로운 클라이언트 버전이 필요할 수 있습니다. Office Communications Server 2007 R2의 경우에는 사용자를 Lync Online으로 마이그레이션하기 전에 Lync Server 2013 풀로 이동해야 합니다.
    
    클라이언트 지원에 대한 자세한 내용은 [Lync Online 클라이언트](http://go.microsoft.com/fwlink/p/?linkid=281902) 및 [지원되는 Lync 클라이언트 및 네트워크 포트 구성](http://go.microsoft.com/fwlink/p/?linkid=281901)을 참조하세요.

  - **온-프레미스 정책 및 구성(비사용자)**   온라인 및 온-프레미스 정책에는 별도의 구성이 필요합니다. 온라인과 온-프레미스에 모두 적용되는 전역 정책을 설정할 수는 없습니다.

