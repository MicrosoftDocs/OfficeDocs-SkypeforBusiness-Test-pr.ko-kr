---
title: 포트 요약 - XMPP(확장 가능 메시징 및 현재 상태 프로토콜) 페더레이션
TOCTitle: 포트 요약 - XMPP(확장 가능 메시징 및 현재 상태 프로토콜) 페더레이션
ms:assetid: 62e98fab-7add-4983-a3fa-dbe74e1c3849
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ618371(v=OCS.15)
ms:contentKeyID: 49303835
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 포트 요약 - XMPP(확장 가능 메시징 및 현재 상태 프로토콜) 페더레이션

 

_**마지막으로 수정된 항목:** 2015-03-09_

에지 서버에 배포된 XMPP(확장 가능 메시징 및 현재 상태 프로토콜)에 대해 정의된 포트 및 프로토콜을 통해 XMPP 페더레이션 파트너에서 에지 서버로의 통신을 허용하고 에지 서버에서 XMPP 페더레이션 파트너로의 통신도 허용합니다. 규칙은 또한 프런트 엔드 서버 또는 프런트 엔드 풀에서 에지 서버 또는 에지 풀로의 내부 연결 방화벽에서도 정의됩니다.

## XMPP(확장 가능 메시징 및 현재 상태 프로토콜)의 방화벽 요약


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
<th>원본(IP 주소)</th>
<th>대상(IP 주소)</th>
<th>참고 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>모두</p></td>
<td><p>액세스 에지 서비스 인터페이스 IP 주소</p></td>
<td><p>XMPP용 표준 서버 간 통신 포트입니다. 페더레이션된 XMPP 파트너로부터의 에지 서버 XMPP 프록시에 대한 통신을 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>액세스 에지 서비스 인터페이스 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>XMPP용 표준 서버 간 통신 포트입니다. 에지 서버 XMPP 프록시에서 페더레이션된 XMPP 파트너로의 통신을 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>XMPP/MTLS/23456</p></td>
<td><p>모두</p></td>
<td><p>내부 에지 서버 인터페이스 IP</p></td>
<td><p>프런트 엔드 서버 또는 프런트 엔드 풀의 XMPP 게이트웨이에서 에지 서버로의 내부 XMPP 트래픽</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 작업

[Lync Server 2013의 예제 XMPP 구성 - Google Talk와 XMPP 페더레이션](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### 기타 리소스

[Lync Server 2013에서 XMPP 페더레이션 파트너 관리](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)

