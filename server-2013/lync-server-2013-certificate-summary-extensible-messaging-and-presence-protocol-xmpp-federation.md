---
title: 인증서 요약 - XMPP(Extensible Messaging and Presence Protocol) 페더레이션
TOCTitle: 인증서 요약 - XMPP(Extensible Messaging and Presence Protocol) 페더레이션
ms:assetid: b059a34e-99df-40af-91fe-fe2aa52841f6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ618374(v=OCS.15)
ms:contentKeyID: 49304733
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 인증서 요약 - XMPP(Extensible Messaging and Presence Protocol) 페더레이션

 

_**마지막으로 수정된 항목:** 2015-03-09_

XMPP(Extensible Messaging and Presence Protocol) 파트너와의 통신을 사용하도록 설정하고 통신을 설정하기 위한 인증서 요구 사항에 따라 XMPP 도메인에 대한 추가 레코드가 필요합니다. SAN(주체 대체 이름)으로 인증서에 포함되는 레코드는 XMPP 통신에 참여할 수 있는 도메인이 됩니다. 이 도메인은 전체 도메인에 XMPP를 사용하도록 설정하려는 경우 루트 수준 도메인(예: contoso.com)이 될 수 있고, 일부 사용자에 대해 XMPP를 사용하도록 설정하는 경우 선택한 자식 도메인(예: corp.contoso.com, finance.contoso.com)이 될 수 있습니다.

## XMPP(Extensible Messaging and Presence Protocol)에 대한 인증서 요약


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>구성 요소</th>
<th>주체 이름</th>
<th>SAN(주체 대체 이름)/순서</th>
<th>참고 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>에지 서버 또는 에지 풀의 액세스 에지 서비스에 할당</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p>
<p>contoso.com</p></td>
<td><p>첫 번째 세 SAN 항목은 전체 에지 서버에 대한 일반 SAN 항목입니다. contoso.com은 루트 도메인 수준에서 XMPP 파트너와 페더레이션하는 데 필요한 항목입니다. 이 항목은 접미사 contoso.com이 있는 모든 도메인에 XMPP를 허용합니다.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 작업

[Lync Server 2013의 예제 XMPP 구성 - Google Talk와 XMPP 페더레이션](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### 개념

[Lync Server 2013의 에지 서버 인증서 계획](lync-server-2013-plan-for-edge-server-certificates.md)  

#### 기타 리소스

[Lync Server 2013의 에지 인증서 설정](lync-server-2013-set-up-edge-certificates.md)  
[Request-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Request-CsCertificate)  
[Set-CsCertificate](set-cscertificate.md)

