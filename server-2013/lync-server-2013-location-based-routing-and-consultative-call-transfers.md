---
title: 위치 기반 라우팅 및 협의 통화 전송
TOCTitle: 위치 기반 라우팅 및 협의 통화 전송
ms:assetid: b12460c2-36c8-481f-b867-fe10dc1c0bdf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362836(v=OCS.15)
ms:contentKeyID: 56270289
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 위치 기반 라우팅 및 협의 통화 전송

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync 모임에 위치 기반 라우팅을 적용하는 것 외에도 위치 기반 라우팅 회의 응용 프로그램은 PSTN 끝점으로 향하는 협의 통화 전송에 위치 기반 라우팅 제한을 적용합니다. 협의 통화 전송은 두 사람 사이에 설정된 통화로, 이 중 하나가 새로운 사용자에게 통화를 전송합니다. 예를 들어 PSTN 끝점에서 사용자 A(Lync 수신자)에게 전화를 겁니다. 사용자 A는 PSTN 사용자를 사용자 B(Lync 사용자)에게 전달해야 한다고 결정합니다. 사용자 A는 대기 중인 PSTN 사용자에게 전화를 걸고 사용자 B에게 전화를 겁니다. 사용자 B가 PSTN 사용자와의 통화를 수락합니다. 사용자 A는 대기 중인 통화를 사용자 B에게 전송합니다.

**협의 통화 전송 통화 흐름**

![회의에 대한 위치 기반 라우팅 다이어그램](images/Dn362836.e4d43d6f-23d2-49c9-b12b-15248a743f92(OCS.15).jpg "회의에 대한 위치 기반 라우팅 다이어그램")

위치 기반 라우팅을 사용할 수 있는 사용자가 PSTN 끝점(앞에 나온 그림 참고)의 협의 통화 전송을 시작할 경우 2건의 활성 통화가 만들어지는데, 하나는 PSTN 사용자와 Lync 사용자 A 간의 통화이고, 다른 하나는 Lync 사용자 A와 Lync 사용자 B 간의 통화입니다. 다음 동작은 위치 기반 라우팅 회의 응용 프로그램에 의해 실행됩니다.

  - PSTN 통화를 라우팅하는 SIP 트렁크가 PSTN 통화를 Lync 사용자 B(예: 전송 대상)가 있는 네트워크 사이트로 다시 라우팅할 수 있는 경우 통화 전송이 허용됩니다. 그렇지 않으면 협의 통화 전송은 차단됩니다. 이러한 권한은 전송 대상 사용자의 위치가 활성 통화를 PSTN 끝점으로 라우팅하는 SIP 트렁크와 같은 네트워크 사이트에 있는 경우에 부여됩니다.

  - 인바운드 PSTN 통화를 라우팅하는 SIP 트렁크가 전송 대상 사용자(Lync 사용자 B)가 있는 네트워크 사이트로 통화를 라우팅할 수 없거나 전송 대상 사용자가 알 수 없는 네트워크 사이트에 있는 경우, PSTN 끝점(예: 통화 전송 대상)으로 협의 통화 전송이 차단됩니다.

다음 표에는 협의 통화 전송을 위해 위치 기반 라우팅 회의 응용 프로그램에서 위치 기반 라우팅 제한이 어떻게 적용되는지 나타나 있습니다. PBX 끝점이 네트워크 사이트와 직접 연결되어 있지는 않지만 PBX가 연결되어 있는 SIP 트렁크에 네트워크 사이트가 할당될 수 있습니다. 따라서 PBX 끝점은 간접적으로 네트워크 사이트와 연결될 수 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>통화를 전송 받는 사용자의 네트워크 사이트</p></td>
<td><p>통화 전송 대상의 네트워크 사이트</p></td>
<td><p>동작</p></td>
</tr>
<tr class="even">
<td><p>PSTN 끝점</p></td>
<td><p>같은 네트워크(예: 사이트 1)에 있는 Lync 사용자</p></td>
<td><p>협의 전송이 허용됨</p></td>
</tr>
<tr class="odd">
<td><p>PSTN 끝점</p></td>
<td><p>다른 네트워크 사이트(예: 사이트 2)에 있는 Lync 사용자</p></td>
<td><p>협의 전송이 허용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>PSTN 끝점</p></td>
<td><p>알 수 없는 네트워크 사이트에 있는 Lync 사용자</p></td>
<td><p>협의 전송이 허용되지 않음</p></td>
</tr>
<tr class="odd">
<td><p>PSTN 끝점</p></td>
<td><p>페더레이션된 Lync 사용자</p></td>
<td><p>협의 전송이 허용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>PSTN 끝점</p></td>
<td><p>같은 사이트(예: 사이트 1)의 PBX 끝점</p></td>
<td><p>협의 전송이 허용됨</p></td>
</tr>
<tr class="odd">
<td><p>PSTN 끝점</p></td>
<td><p>다른 사이트(예: 사이트 2)의 PBX 끝점</p></td>
<td><p>협의 전송이 허용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>같은 사이트(예: 사이트 1)의 PBX 끝점</p></td>
<td><p>PSTN 끝점</p></td>
<td><p>협의 전송이 허용됨</p></td>
</tr>
<tr class="odd">
<td><p>다른 사이트(예: 사이트 2)의 PBX 끝점</p></td>
<td><p>PSTN 끝점</p></td>
<td><p>협의 전송이 허용되지 않음</p></td>
</tr>
<tr class="even">
<td><p>임의의 사이트에 있는 PBX 끝점</p></td>
<td><p>같은 네트워크(예: 사이트 1)에 있는 Lync 사용자</p></td>
<td><p>협의 전송이 허용됨</p></td>
</tr>
<tr class="odd">
<td><p>임의의 사이트에 있는 PBX 끝점</p></td>
<td><p>다른 네트워크 사이트(예: 사이트 2)에 있는 Lync 사용자</p></td>
<td><p>협의 전송이 허용됨</p></td>
</tr>
<tr class="even">
<td><p>임의의 사이트에 있는 PBX 끝점</p></td>
<td><p>알 수 없는 네트워크 사이트에 있는 Lync 사용자</p></td>
<td><p>협의 전송이 허용됨</p></td>
</tr>
<tr class="odd">
<td><p>임의의 사이트에 있는 PBX 끝점</p></td>
<td><p>페더레이션된 Lync 사용자</p></td>
<td><p>협의 전송이 허용됨</p></td>
</tr>
</tbody>
</table>

