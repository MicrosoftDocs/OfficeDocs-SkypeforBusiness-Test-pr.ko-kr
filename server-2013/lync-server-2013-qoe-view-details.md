---
title: Lync Server 2013의 QoE 보기 정보
TOCTitle: Lync Server 2013의 QoE 보기 정보
ms:assetid: 6a658318-a317-4546-a44c-a9c473d8e86a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688081(v=OCS.15)
ms:contentKeyID: 49885797
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 QoE 보기 정보

 

_**마지막으로 수정된 항목:** 2015-03-09_

보기에는 QoE SQL 데이터베이스에서 데이터를 반환하는 가장 일반적인 시나리오가 포함됩니다. 데이터베이스 테이블에 직접 액세스하기 보다는 사용자 지정 보고서를 작성하는 데 사용되는 권장 보기입니다. 보기는 이후 릴리스에서도 이전 버전과의 호환성을 유지 관리할 수 있는 가능성이 보다 높기 때문입니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>보기 이름</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-audiostreamdetail-view.md">AudioStreamDetail 보기</a></p></td>
<td><p>데이터베이스의 각 오디오 스트림에 대한 정보를 저장합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-medialine-view.md">MediaLine 보기</a></p></td>
<td><p>데이터베이스의 각 미디어 회선에 대한 정보를 저장합니다. 하나의 오디오 세션은 일반적으로 하나의 오디오 미디어 회선을 포함합니다. 회의 장치를 사용하거나 갤러리 보기를 사용할 경우 2개의 비디오 미디어 회선이 세션에 포함될 수도 있지만, 하나의 A/V(오디오 및 비디오) 세션은 일반적으로 오디오 미디어 회선 1개와 비디오 미디어 회선 1개가 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-networkconfigurationsettings-view.md">NetworkConfigurationSettings 보기</a></p></td>
<td><p>네트워크 구성에 대한 정보를 저장합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-session-view.md">Session 보기</a></p></td>
<td><p>데이터베이스의 레코드가 포함된 세션에 대한 정보를 저장합니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-useragent-view.md">UserAgent 보기</a></p></td>
<td><p>데이터베이스의 레코드를 포함하는 세션에 포함된 사용자 에이전트에 대한 정보를 저장합니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-videostreamdetail-view.md">VideoStreamDetail 보기</a></p></td>
<td><p>데이터베이스의 각 비디오 스트림에 대한 정보를 저장합니다.</p></td>
</tr>
</tbody>
</table>

