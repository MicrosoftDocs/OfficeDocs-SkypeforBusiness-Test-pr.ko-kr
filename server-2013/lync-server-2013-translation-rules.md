---
title: 'Lync Server 2013: 변환 규칙'
TOCTitle: 변환 규칙
ms:assetid: 6e067bd4-4931-4385-81ac-2acae45a16d8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398520(v=OCS.15)
ms:contentKeyID: 49303967
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 변환 규칙

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013Enterprise Voice에서는 RNL(역방향 번호 조회)을 수행하기 위한 목적으로 모든 전화 걸기 문자열이 E.164 형식으로 정규화될 것을 요구합니다. Microsoft Lync Server 2010에서 변환 규칙은 호출되는 번호에 대해서만 지원됩니다. Microsoft Lync Server 2013에서 새롭게 제공되는 변환 규칙은 호출하는 번호에 대해서도 지원됩니다. *트렁크 피어* (즉, 연결된 게이트웨이, PBX(Private Branch Exchange) 또는 SIP 트렁크)에서는 번호가 로컬 전화 번호 형식일 것을 요구할 수 있습니다. E.164 형식에서 로컬 전화 걸기 형식으로 변환하려면 요청 URI를 트렁크 피어로 라우팅하기 전에 요청 URI를 조작하기 위한 하나 이상의 변환 규칙을 정의할 수 있습니다. 예를 들어 전화 걸기 문자열의 시작 부분에서 +44를 제거하고 대신 0144를 넣는 변환 규칙을 작성할 수 있습니다.

서버에서 아웃바운드 경로 변환을 수행하여 전화 번호를 로컬 전화 걸기 형식으로 변환하기 위한 각 개별 트렁크 피어에 대한 구성 요구 사항을 줄일 수 있습니다. 해당 중재 서버 클러스터와 연결할 게이트웨이와 게이트웨이 수를 계획할 때는 로컬 전화 걸기 요구 사항이 유사한 트렁크 피어를 그룹화하는 것이 유용할 수 있습니다. 이렇게 하면 필요한 변환 규칙 수와 이러한 규칙을 작성하는 데 필요한 시간을 줄일 수 있습니다.


> [!IMPORTANT]
> 하나 이상의 변환 규칙을 Enterprise Voice 트렁크 구성과 연결하는 기능은 트렁크 피어에 대한 변환 규칙을 구성하는 방법의 대안으로 사용하기 위한 것입니다. 트렁크 피어에 대한 변환 규칙을 구성한 경우 변환 규칙을 Enterprise Voice 트렁크 구성과 연결하지 마십시오. 두 규칙이 충돌할 수 있기 때문입니다.



## 예제 변환 규칙

다음 변환 규칙 예제에서는 서버에서 번호를 E.164 형식에서 트렁크 피어에 대한 로컬 형식으로 변환하기 위한 규칙을 개발할 수 있는 방법을 보여 줍니다.

변환 규칙 구현 방법에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 변환 규칙 정의](lync-server-2013-defining-translation-rules.md)를 참조하십시오.


<table>
<colgroup>
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th>설명</th>
<th>시작 숫자</th>
<th>길이</th>
<th>제거할 숫자</th>
<th>추가할 숫자</th>
<th>일치 패턴</th>
<th>변환</th>
<th>예</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>미국 내에서의 일반적인 시외 전화 걸기</p>
<p>(&quot;+&quot; 제거)</p></td>
<td><p>+1</p></td>
<td><p>정확히 12</p></td>
<td><p>1</p></td>
<td><p>0</p></td>
<td><p>^\+(1\d{10})$</p></td>
<td><p>$1 키</p></td>
<td><p>+14255551010이 14255551010이 됨</p></td>
</tr>
<tr class="even">
<td><p>미국 국제 시외 전화 걸기</p>
<p>(&quot;+&quot; 제거 및 011 추가)</p></td>
<td><p>+</p></td>
<td><p>11 이상</p></td>
<td><p>1</p></td>
<td><p>011</p></td>
<td><p>^\+(\d{9}\d+)$</p></td>
<td><p>011$1</p></td>
<td><p>+441235551010이 011441235551010이 됨</p></td>
</tr>
</tbody>
</table>

