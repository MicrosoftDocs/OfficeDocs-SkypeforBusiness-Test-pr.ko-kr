---
title: 'Lync Server 2013: 포트 요약 - 단일 디렉터'
TOCTitle: 포트 요약 - 단일 디렉터
ms:assetid: 079c1414-723f-4499-b7d4-a0d7121c1626
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204648(v=OCS.15)
ms:contentKeyID: 49302711
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 포트 요약 - 단일 디렉터

 

_**마지막으로 수정된 항목:** 2015-03-09_

단일 디렉터에 대한 방화벽 포트 요구 사항은 역방향 프록시의 내부 연결 네트워크 또는 내부 인터페이스에서 디렉터와의 통신을 설정하는 데 사용되는 포트로 구성됩니다. Microsoft Lync Server 2013은 기본적으로 역방향 프록시에서 디렉터는 물론 프런트 엔드 풀 및 프런트 엔드 서버로의 HTTP/TCP 8080 및 HTTPS/TCP 4443 포트가 열려 있다고 가정합니다. 또한 에지 서버 내부 인터페이스에서 디렉터 및 프런트 엔드 풀과 프런트 엔드 서버로의 SIP(Session Initiation Protocol) 통신도 필요합니다. SIP 프로토콜은 에지 서버에서 프런트 엔드 풀 및 프런트 엔드 서버로의 SIP/MTLS/TCP 5061을 사용합니다. 디렉터, 프런트 엔드 풀 및 프런트 엔드 서버에서 에지 서버 내부 인터페이스로의 SIP/MTLS/TCP 5061 통신을 허용하는 규칙도 만들어야 합니다.

### 단일 디렉터의 방화벽 포트 및 프로토콜 정의

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>역할/프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP 8080</p></td>
<td><p>역방향 프록시 내부 인터페이스</p></td>
<td><p>디렉터</p></td>
<td><p>역방향 프록시의 외부 쪽에서 처음 수신되는 통신은 디렉터 및 프런트 엔드 서버 웹 서비스로 전송됩니다.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP 4443</p></td>
<td><p>역방향 프록시 내부 인터페이스</p></td>
<td><p>디렉터</p></td>
<td><p>역방향 프록시의 외부 쪽에서 처음 수신되는 통신은 디렉터 및 프런트 엔드 서버 웹 서비스로 전송됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 444</p></td>
<td><p>디렉터</p></td>
<td><p>프런트 엔드 서버 또는 프런트 엔드 풀</p></td>
<td><p>디렉터 및 프런트 엔드 서버 간의 서버 간 통신</p></td>
</tr>
<tr class="even">
<td><p>HTTP/TCP 80</p></td>
<td><p>내부 클라이언트</p></td>
<td><p>디렉터 웹 서비스</p></td>
<td><p>디렉터에서는 내부 및 외부 클라이언트에 대해 웹 서비스를 제공합니다.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 443</p></td>
<td><p>내부 클라이언트</p></td>
<td><p>디렉터 웹 서비스</p></td>
<td><p>디렉터에서는 내부 및 외부 클라이언트에 대해 웹 서비스를 제공합니다.</p></td>
</tr>
<tr class="even">
<td><p>SIP/MTLS/TCP 5061</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>디렉터</p></td>
<td><p>에지 서버에서 디렉터 및 프런트 엔드 서버로의 SIP 통신</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50001</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>중앙 로깅 서비스 컨트롤러(ClsController.exe) 또는 에이전트(ClasAgent.exe) 명령 및 로그 수집</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50002</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>중앙 로깅 서비스 컨트롤러(ClsController.exe) 또는 에이전트(ClasAgent.exe) 명령 및 로그 수집</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50003</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>중앙 로깅 서비스 컨트롤러(ClsController.exe) 또는 에이전트(ClasAgent.exe) 명령 및 로그 수집</p></td>
</tr>
</tbody>
</table>

