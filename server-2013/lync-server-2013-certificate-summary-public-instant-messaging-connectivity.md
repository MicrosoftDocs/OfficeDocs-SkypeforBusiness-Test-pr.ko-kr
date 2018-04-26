---
title: 인증서 요약 - 공용 인스턴트 메시징 연결
TOCTitle: 인증서 요약 - 공용 인스턴트 메시징 연결
ms:assetid: 2b3687ee-50c2-4c1c-880e-8dcf8bd4f309
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ618370(v=OCS.15)
ms:contentKeyID: 49303146
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 인증서 요약 - 공용 인스턴트 메시징 연결

 

_**마지막으로 수정된 항목:** 2015-03-09_

공용 인스턴트 메시징 연결을 위한 인증서를 구성하려면 먼저 이러한 인증서가 다른 SIP 페더레이션 유형 또는 표준 에지 서버 인증서와 다른 점이 없음을 인지해야 합니다(고유한 인증서 구성을 요구하는 AOL(America Online)은 예외). America Online의 경우 일반 서버 EKU(확장된 키 사용) 외에 클라이언트 EKU도 포함하는 하나 이상의 인증서(에지 풀의 경우 인증서가 여러 개임)를 요구합니다. 클라이언트 EKU는 인증서와 함께 추가로 제공되며, 에지 서버에 할당되는 외부 공용 인증서의 일부분입니다.

## 인증서 요약 - 공용 인스턴트 메시징 연결


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
<td><p>외부/액세스 에지</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>sip.contoso.com</p>
<p>webcon.contoso.com</p>
<p>sip.fabrikam.com</p></td>
<td><p>인증서는 공용 CA에서 발급한 것이어야 하며, AOL과의 공용 IM 연결을 배포하려는 경우 서버 EKU 및 클라이언트 EKU를 포함해야 합니다. 다음 항목에 대한 외부 에지 서버 인터페이스에 인증서가 할당됩니다.</p>
<ul>
<li><p>액세스 에지 서비스</p></li>
<li><p>웹 회의 에지 서비스</p></li>
<li><p>A/V 에지 서비스</p></li>
</ul>
<p>SAN은 토폴로지 작성기의 정의에 따라 인증서에 자동으로 추가됩니다. 지원해야 하는 추가 SIP 도메인 및 기타 항목에 대해 필요한 대로 SAN 항목을 추가합니다. 주체 이름은 SAN에서 복제되며, 인증서가 올바르게 작동하려면 주체 이름이 있어야 합니다.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)

