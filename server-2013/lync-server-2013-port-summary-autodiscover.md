---
title: 포트 요약 - Lync Server 2013에서 자동 검색
TOCTitle: 포트 요약 - Lync Server 2013에서 자동 검색
ms:assetid: 8bd16363-5e18-4e4b-be99-b3e6457b4c99
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945642(v=OCS.15)
ms:contentKeyID: 52056901
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 포트 요약 - Lync Server 2013에서 자동 검색

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 자동 검색 서비스는 디렉터 및 프런트 엔드 풀 서버에서 실행되며, `lyncdiscover.<domain>` 및 `lyncdiscoverinternal.<domain>` 호스트 레코드를 사용하여 DNS에서 게시되는 경우 클라이언트가 Lync Server 기능을 찾는 데 사용될 수 있습니다. Lync Mobile을 실행하는 모바일 장치가 자동 검색을 사용하려면 먼저 자동 검색 서비스를 실행하는 모든 디렉터 및 프런트 엔드 서버에서 인증서 주체 대체 이름 목록을 수정해야 할 수 있습니다. 또한 역방향 프록시에 대한 외부 웹 서비스 게시 규칙에 사용되는 인증서에서도 주체 대체 이름 목록을 수정해야 할 수 있습니다.

자동 검색 서비스를 게시하는 포트(포트 80 또는 포트 443)에 따라 역방향 프록시에서 주체 대체 이름 목록을 사용할지 여부를 결정합니다.

  - **포트 80에 게시**   모바일 장치의 경우 자동 검색 서비스에 대한 초기 쿼리가 포트 80에서 수행되면 인증서를 변경할 필요가 없습니다. Lync를 실행하는 모바일 장치는 외부에서 포트 80의 역방향 프록시에 액세스한 다음 내부에서 포트 8080의 디렉터 또는 프런트 엔드 서버로 리디렉션되기 때문입니다.

  - **포트 443에 게시**   외부 웹 서비스 게시 규칙에서 사용하는 인증서의 주체 대체 이름 목록에 조직 내의 각 SIP 도메인에 대한 `lyncdiscover.<sipdomain>` 항목이 포함되어 있어야 합니다.
    

    > [!IMPORTANT]
    > 새 설치를 수행했거나 모바일 기능을 배포한 Lync Server 2010에서 업그레이드한 경우에는 Mobility Service의 자동 검색에 포트 80을 사용했거나 적절한 주체 이름 및 주체 대체 이름이 포함된 인증서를 다시 발급했을 것입니다. 디렉터 및 프런트 엔드 서버에서 인증서를 검토하여 선택한 경로를 확인하세요.



### 역방향 프록시 서버에 대한 방화벽 세부 정보: 외부 인터페이스

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP/80</p></td>
<td><p>모두</p></td>
<td><p>역방향 프록시 수신기</p></td>
<td><p>(선택 사항) 사용자가 http://<em>&lt;게시된 사이트 FQDN&gt;</em>을 입력하는 경우 HTTPS로의 리디렉션. 조직이 외부 웹 서비스 게시 규칙 인증서를 수정하지 않으려는 상황에서 회의용으로 Office Web Apps를 사용하고 Lync를 실행하는 모바일 장치용으로 자동 검색 서비스를 사용하는 경우에도 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>역방향 프록시 수신기</p></td>
<td><p>주소록 다운로드, 주소록 웹 쿼리 서비스, 자동 검색, 클라이언트 업데이트, 모임 콘텐츠, 장치 업데이트, 그룹 확장, 회의용 Office Web Apps, 전화 접속 회의 및 모임</p></td>
</tr>
</tbody>
</table>


### 역방향 프록시 서버에 대한 방화벽 세부 정보: 내부 인터페이스

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP/8080</p></td>
<td><p>내부 역방향 프록시 인터페이스</p></td>
<td><p>회의용 프런트 엔드 서버, 프런트 엔드 풀, 디렉터, 디렉터 풀, Office Web Apps</p></td>
<td><p>조직에서 외부 웹 서비스 게시 규칙 인증서를 수정하지 않으려는 상황에서 Lync를 실행하는 모바일 장치에 대해 자동 검색 서비스를 사용하는 경우 필요합니다. 역방향 프록시 외부 인터페이스에서 포트 80으로 전송된 트래픽은 풀 웹 서비스에서 내부 웹 트래픽과 구분할 수 있도록 역방향 프록시 내부 인터페이스에서 포트 8080을 통해 풀로 리디렉션됩니다.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>내부 역방향 프록시 인터페이스</p></td>
<td><p>회의용 프런트 엔드 서버, 프런트 엔드 풀, 디렉터, 디렉터 풀, Office Web Apps</p></td>
<td><p>역방향 프록시 외부 인터페이스에서 포트 443으로 전송된 트래픽은 풀 웹 서비스에서 내부 웹 트래픽과 구분할 수 있도록 역방향 프록시 내부 인터페이스에서 포트 4443을 통해 풀로 리디렉션됩니다.</p></td>
</tr>
</tbody>
</table>

