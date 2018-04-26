---
title: Lync Server 2013의 IPsec 예외
TOCTitle: Lync Server 2013의 IPsec 예외
ms:assetid: 241f1eca-6f2f-44de-90b1-2cb659cbe27c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425719(v=OCS.15)
ms:contentKeyID: 49303064
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 IPsec 예외

 

_**마지막으로 수정된 항목:** 2015-03-09_

IPsec(인터넷 프로토콜 보안: IETF RFC 4301-4309 참조)가 배포된 엔터프라이즈 네트워크의 경우 오디오, 비디오 및 파노라마 비디오의 배달에 사용되는 포트 범위에서 IPSec를 사용하지 않도록 설정해야 합니다. IPsec 협상으로 인해 미디어 포트 할당이 지연되는 것을 방지하기 위해 이 작업이 필요합니다.

다음 표에는 권장되는 IPsec 예외 설정이 설명되어 있습니다.

### 권장 IPsec 예외

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>규칙 이름</th>
<th>원본 IP</th>
<th>대상 IP</th>
<th>프로토콜</th>
<th>원본 포트</th>
<th>대상 포트</th>
<th>인증 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A/V 에지 서버 내부 인바운드</p></td>
<td><p>모두</p></td>
<td><p>A/V 에지 서버 내부</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="even">
<td><p>A/V 에지 서버 외부 인바운드</p></td>
<td><p>모두</p></td>
<td><p>A/V 에지 서버 외부</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="odd">
<td><p>A/V 에지 서버 내부 아웃바운드</p></td>
<td><p>A/V 에지 서버 내부</p></td>
<td><p>모두</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="even">
<td><p>A/V 에지 서버 외부 아웃바운드</p></td>
<td><p>A/V 에지 서버 외부</p></td>
<td><p>모두</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="odd">
<td><p>중재 서버 인바운드</p></td>
<td><p>모두</p></td>
<td><p>중재</p>
<p>서버</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="even">
<td><p>중재 서버 아웃바운드</p></td>
<td><p>중재</p>
<p>서버</p></td>
<td><p>모두</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="odd">
<td><p>회의 길잡이 인바운드</p></td>
<td><p>모두</p></td>
<td><p>회의 길잡이를 실행하는 프런트 엔드 서버</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="even">
<td><p>회의 길잡이 아웃바운드</p></td>
<td><p>회의 길잡이를 실행하는 프런트 엔드 서버</p></td>
<td><p>모두</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="odd">
<td><p>A/V 회의 인바운드</p></td>
<td><p>모두</p></td>
<td><p>프런트 엔드 서버</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="even">
<td><p>A/V 회의 아웃바운드</p></td>
<td><p>프런트 엔드 서버</p></td>
<td><p>모두</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="odd">
<td><p>Exchange 인바운드</p></td>
<td><p>모두</p></td>
<td><p>Exchange 통합 메시징</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="even">
<td><p>응용 프로그램 공유 서버 인바운드</p></td>
<td><p>모두</p></td>
<td><p>응용 프로그램 공유 서버</p></td>
<td><p>TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 공유 서버 아웃바운드</p></td>
<td><p>응용 프로그램 공유 서버</p></td>
<td><p>모두</p></td>
<td><p>TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="even">
<td><p>Exchange 아웃바운드</p></td>
<td><p>Exchange 통합 메시징</p></td>
<td><p>모두</p></td>
<td><p>UDP 및 TCP</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
<tr class="odd">
<td><p>클라이언트</p></td>
<td><p>모두</p></td>
<td><p>모두</p></td>
<td><p>UDP</p></td>
<td><p>지정된 미디어 포트 범위</p></td>
<td><p>모두</p></td>
<td><p>인증 안 함</p></td>
</tr>
</tbody>
</table>

