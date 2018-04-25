---
title: 'Lync Server 2013: 통화 대기에 대한 용량 계획'
TOCTitle: 통화 대기에 대한 용량 계획
ms:assetid: 75520310-760a-4b1b-bcc1-4d724d13f87a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg416493(v=OCS.15)
ms:contentKeyID: 49304056
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 대기에 대한 용량 계획

 

_**마지막으로 수정된 항목:** 2015-03-09_

다음 표에서는 용량 계획 요구 사항에 대한 기본으로 사용할 수 있는 통화 대기 사용자 모델에 대해 설명합니다.


> [!IMPORTANT]
> 재해 복구 용량을 계획하기 위해서는 쌍으로 연결된 각 풀에서 두 풀 모두의 통화 대기 서비스에 대한 작업 부하를 처리할 수 있어야 합니다.



### 통화 대기 사용자 모델

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>메트릭</th>
<th>프런트 엔드 풀당 (8개의 프런트 엔드 서버 포함)</th>
<th>Standard Edition 서버당</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>대기 속도</p></td>
<td><p>분당 8개</p></td>
<td><p>분당 1개</p></td>
</tr>
<tr class="even">
<td><p>대기 중인 통화 재개 속도</p></td>
<td><p>분당 8개</p></td>
<td><p>분당 1개</p></td>
</tr>
<tr class="odd">
<td><p>평균 대기 시간</p></td>
<td><p>60초</p></td>
<td><p>60초</p></td>
</tr>
</tbody>
</table>

