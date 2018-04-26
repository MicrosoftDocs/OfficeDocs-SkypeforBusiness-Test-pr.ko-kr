---
title: 'Lync Server 2013: 포트 요약 - 역방향 프록시'
TOCTitle: 포트 요약 - 역방향 프록시
ms:assetid: 59b9ac3c-3e6f-4776-b366-174f0dd1f2eb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204932(v=OCS.15)
ms:contentKeyID: 49303729
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 포트 요약 - 역방향 프록시

 

_**마지막으로 수정된 항목:** 2015-03-09_

역방향 프록시는 방화벽 및 포트/프로토콜에 대한 최소 요구 사항을 갖고 있습니다.

  - 외부 방화벽 요구 사항은 HTTPS/TCP/443 및 HTTP/TCP/80(선택 사항)입니다. HTTPS는 역방향 프록시를 통한 SSL 및 TLS 보안 통신에 사용됩니다. 인증서를 수정하기가 어렵거나 비용상 적절하지 않을 때 자동 검색 서비스 액세스를 허용하려면 HTTP를 사용합니다.

  - 클라이언트는 HTTPS를 통해 Office Web Apps 서버에 연결합니다. Office Web Apps 서버는 HTTPS/TCP/443에서 내부 클라이언트로부터의 통신을 수락합니다. 권장 구성은 역방향 프록시에서 Office Web Apps 서버로의 통신에 HTTPS/TCP/443을 사용하도록 허용하는 것입니다.

  - 포트 8080은 역방향 프록시 내부 인터페이스에서 프런트 엔드 서버, 프런트 엔드 풀 VIP(가상 IP) 또는 선택 사항인 디렉터 또는 디렉터 풀 VIP로 트래픽을 라우팅하는 데 사용됩니다. 포트 TCP 8080은 규칙 인증서를 게시하는 외부 웹 서비스를 수정하기 어려운 경우(예: SIP 도메인의 수가 많은 경우) Lync를 실행하는 모바일 장치가 자동 검색 서비스를 찾는 데 필요합니다. 필요한 SAN 항목이 포함된 새 인증서를 가져오도록 선택한 경우 포트 TCP 8080은 필수가 아니라 선택 사항입니다.

  - 포트 4443은 역방향 프록시 내부 인터페이스에서 프런트 엔드 서버, 프런트 엔드 풀 VIP(가상 IP) 또는 선택 사항인 디렉터 또는 디렉터 풀 VIP로의 트래픽에 사용됩니다.
    
    ![역방향 프록시 및 외부 웹 서비스](images/JJ204932.13142405-d5c9-45b7-a8b7-a8c89f09c97c(OCS.15).jpg "역방향 프록시 및 외부 웹 서비스")  
    

    > [!WARNING]
    > 역방향 프록시에서 내부 배포로의 4443 over TCP를 Standard Edition 서버 또는 중앙 관리 저장소 역할을 관리하는 프런트 엔드 풀로부터의 포트 4443 over TCP 트래픽과 혼동하지 마십시오.



## 포트 및 프로토콜 세부 정보

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
<td><p>(선택 사항) 사용자가 http:// <em>&lt;게시된 사이트 FQDN&gt;</em> 을 입력한 경우 HTTPS로 리디렉션</p>
<p>조직에서 외부 웹 서비스 게시 규칙 인증서를 수정하지 않으려는 상황에서 회의에 Office Web Apps를 사용하며 Lync를 실행하는 모바일 장치에 대해 자동 검색 서비스를 사용하는 경우에도 필요합니다.</p></td>
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
<td><p>프런트 엔드 서버, 프런트 엔드 풀, 디렉터, 디렉터 풀</p></td>
<td><p>조직에서 외부 웹 서비스 게시 규칙 인증서를 수정하지 않으려는 상황에서 Lync를 실행하는 모바일 장치에 대해 자동 검색 서비스를 사용하는 경우 필요합니다.</p>
<p>역방향 프록시 외부 인터페이스에서 포트 80으로 전송된 트래픽은 풀 웹 서비스에서 내부 웹 트래픽과 구분할 수 있도록 역방향 프록시 내부 인터페이스에서 포트 8080을 통해 풀로 리디렉션됩니다.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>내부 역방향 프록시 인터페이스</p></td>
<td><p>프런트 엔드 서버, 프런트 엔드 풀, 디렉터, 디렉터 풀</p></td>
<td><p>역방향 프록시 외부 인터페이스에서 포트 443으로 전송된 트래픽은 풀 웹 서비스에서 내부 웹 트래픽과 구분할 수 있도록 역방향 프록시 내부 인터페이스에서 포트 4443을 통해 풀로 리디렉션됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP/443</p></td>
<td><p>내부 역방향 프록시 인터페이스</p></td>
<td><p>회의용 Office Web Apps</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

