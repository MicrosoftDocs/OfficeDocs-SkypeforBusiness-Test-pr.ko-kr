---
title: 'Lync Server 2013: E9-1-1 배포 검사 목록'
TOCTitle: E9-1-1 배포 검사 목록
ms:assetid: cc6a656a-6043-4b9b-85c2-5708b9bb1c06
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398864(v=OCS.15)
ms:contentKeyID: 49305054
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 E9-1-1 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

고급 9-1-1(E9-1-1)을 효과적으로 계획하려면 다음 배포 요구 사항을 포함해야 합니다.

  - E9-1-1을 배포하는 데 필요한 필수 구성 요소

  - E9-1-1을 배포하는 데 필요한 단계

## E9-1-1 배포 필수 구성 요소

E9-1-1을 배포하려면 먼저 중앙 관리 저장소, 프런트 엔드 풀 또는 Standard Edition Server, 하나 이상의 중재 서버 또는 중재 서버 풀 및 Lync Server 클라이언트를 포함하여 Lync Server 내부 서버가 배포되어 있어야 합니다. 또한 E9-1-1을 배포하려면 적합한 E9-1-1 서비스 공급자에 대한 SIP 트렁크 또는 PSTN(공중 전화망)에 대한 ELIN(Emergency Location Identification Number) 게이트웨이가 필요합니다. Lync Server은 미국 내에서만 E9-1-1 서비스 공급자의 사용을 지원합니다.

## 배포 프로세스

다음 표에는 E9-1-1 배포 프로세스에 대한 개요가 나와 있습니다. 배포 절차에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 고급 9-1-1 구성](lync-server-2013-configure-enhanced-9-1-1.md)을 참조하십시오.


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
<th>역할</th>
<th>배포 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>음성 사용, 경로 및 트렁크 구성</p></td>
<td><ol>
<li><p>새 PSTN 사용 레코드를 만듭니다. 위치 정책의 <strong>PSTN 사용</strong> 설정에 사용되는 이름과 동일한 이름입니다.</p></li>
<li><p>음성 경로를 만들어 이전 단계에서 만든 PSTN 사용 레코드에 할당한 후 게이트웨이 속성이 E9-1-1 SIP 트렁크 또는 ELIN 게이트웨이를 가리킵니다.</p></li>
<li><p>SIP 트렁크 E9-1-1 서비스 공급자의 경우 <strong>set-cstrunkconfiguration –EnablePIDFLOSupport</strong> cmdlet을 사용하여 SIP를 통한 E9-1-1 통화를 처리할 트렁크를 설정하여 PIDF-LO 데이터를 전달할 수 있습니다.</p></li>
<li><p>선택적으로, SIP 트렁크 E9-1-1 서비스 공급자의 경우 E9-1-1 서비스 공급자의 SIP 트렁크로 처리되지 않는 통화에 대해 로컬 PSTN 경로를 만들어 할당합니다. 이 경로는 E9-1-1 서비스 공급자로의 연결을 사용할 수 없는 경우에 사용됩니다. E9-1-1 서비스 공급자가 지원하는 경우 트렁크 구성 규칙을 게이트웨이에 할당합니다. 이 게이트웨이는 911 전화 번호 문자열을 국가/지역 ECRC(Emergency Call Response Center)의 DID(Direct Inward Dialing)로 변환합니다.</p></li>
</ol></td>
<td><p>CSVoiceAdmin</p></td>
<td><p><a href="lync-server-2013-configure-an-e9-1-1-voice-route.md">Lync Server 2013에서 E9-1-1 음성 경로 구성</a></p></td>
</tr>
<tr class="even">
<td><p>위치 정책을 만들고 이 정책을 사용자 및 서브넷에 할당합니다.</p></td>
<td><ol>
<li><p>전역 위치 정책을 검토합니다.</p></li>
<li><p>사용자 수준 범위로 위치 정책을 만들거나, 조직에 둘 이상의 사이트가 있고 서로 다른 긴급 통화 센터를 사용하는 경우 네트워크 수준 범위의 위치 정책을 만듭니다.</p></li>
<li><p>네트워크 사이트에 위치 정책을 할당합니다.</p></li>
<li><p>적합한 서브넷을 네트워크 사이트에 추가합니다.</p></li>
<li><p>(선택 사항) 위치 정책을 사용자 정책에 할당합니다.</p></li>
</ol>
<p></p></td>
<td><p>CSVoiceAdmin</p>
<p>CSLocationAdmin(위치 정책 만들기 제외)</p></td>
<td><p><a href="lync-server-2013-create-location-policies.md">Lync Server 2013에서 위치 정책 만들기</a></p>
<p><a href="lync-server-2013-add-a-location-policy-to-a-network-site.md">Lync Server 2013에서 네트워크 사이트에 위치 정책 추가</a></p>
<p><a href="lync-server-2013-associate-subnets-with-network-sites-for-e9-1-1.md">Lync Server 2013에서 E9-1-1을 위해 네트워크 사이트에 서브넷 연결</a></p></td>
</tr>
<tr class="odd">
<td><p>위치 데이터베이스 구성</p></td>
<td><ol>
<li><p>데이터베이스를 위치에 대한 네트워크 요소 매핑으로 채웁니다.</p></li>
<li><p>ELIN 게이트웨이의 경우 ELIN을 &lt;CompanyName&gt; 열에 추가합니다.</p></li>
<li><p>주소의 유효성 검사를 위해 E9-1-1 서비스 공급자에 대한 연결을 구성합니다.</p></li>
<li><p>E9-1-1 서비스 공급자를 통해 주소를 확인합니다.</p></li>
<li><p>업데이트된 데이터베이스를 게시합니다.</p></li>
<li><p>ELIN 게이트웨이의 경우 PSTN 통신사의 ALI(Automatic Location Identification) 데이터베이스에 ELIN을 업로드합니다.</p></li>
</ol></td>
<td><p>CSVoiceAdmin</p>
<p>CSLocationAdmin</p></td>
<td><p><a href="lync-server-2013-configure-the-location-database.md">Lync Server 2013에서 위치 데이터베이스 구성</a></p></td>
</tr>
<tr class="even">
<td><p>고급 기능 구성(선택 사항)</p></td>
<td><ol>
<li><p>SNMP 응용 프로그램에 대한 URL을 구성합니다.</p></li>
<li><p>대체 위치 정보 서비스의 위치에 대한 URL을 구성합니다.</p></li>
</ol></td>
<td><p>CSVoiceAdmin</p></td>
<td><p><a href="lync-server-2013-configure-an-snmp-application.md">Lync Server 2013에서 SNMP 응용 프로그램 구성</a></p>
<p><a href="lync-server-2013-configure-a-secondary-location-information-service.md">Lync Server 2013에서 보조 위치 정보 서비스 구성</a></p></td>
</tr>
</tbody>
</table>

