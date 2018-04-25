---
title: 그룹 호출 받기에 대한 용량 계획
TOCTitle: 그룹 호출 받기에 대한 용량 계획
ms:assetid: 0d654a19-6cf0-4118-903d-ec2c4e519253
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ984297(v=OCS.15)
ms:contentKeyID: 52056784
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 그룹 호출 받기에 대한 용량 계획

 

_**마지막으로 수정된 항목:** 2015-03-09_

다음 표에서는 용량 계획 요구 사항에 대한 기본으로 사용할 수 있는 그룹 호출 받기 사용자 모델에 대해 설명합니다.


> [!IMPORTANT]
> 그룹 호출 받기는 통화 대기 응용 프로그램을 기반으로 합니다. 재해 복구 용량을 계획하기 위해서는 쌍으로 연결된 각 풀에서 두 풀 모두의 통화 대기 서비스에 대한 작업 부하를 처리할 수 있어야 합니다(그룹 호출 받기 포함).



### 그룹 호출 받기 사용자 모델

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
<td><p>그룹당 권장 사용자 수</p></td>
<td><p>50</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>권장 그룹 수</p></td>
<td><p>500</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>그룹 호출 받기를 사용하도록 설정되는 풀당 최대 사용자 수</p></td>
<td><p>25,000</p></td>
<td><p>3,000</p></td>
</tr>
<tr class="even">
<td><p>분당 풀별로 그룹 호출 받기를 사용하도록 설정되는 총 사용자에 대한 최대 수신 전화 비율</p></td>
<td><p>500</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>분당 풀별로 그룹 호출 받기를 통해 사용자가 검색할 수 있는 최대 전화 비율</p></td>
<td><p>200</p></td>
<td><p>25</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <UL>
> <LI>
> <P>프런트 엔드 서버가 8대 미만인 프런트 엔드 풀의 경우 메트릭을 선형으로 계산합니다. 예를 들어 프런트 엔드 풀에 프런트 엔드 서버가 1대 포함된 경우 최대 로드를 위의 표에 표시된 값의 1/8로 계산합니다.</P>
> <LI>
> <P>풀당 최대 사용자 수만 초과하지 않으면 그룹당 권장 사용자 수와 그룹 수를 늘리거나 줄일 수 있습니다. 예를 들어 Standard Edition 서버는 120개 그룹과 그룹당 25명의 사용자를 포함할 수 있는데, 이렇게 해도 그룹 호출 받기를 사용하도록 설정되는 사용자의 수는 사용자 모델 최대값 범위 내로 유지되기 때문입니다(120개 그룹x사용자 25명=그룹 호출 받기를 사용하도록 설정되는 사용자 3천 명).</P></LI></UL>


