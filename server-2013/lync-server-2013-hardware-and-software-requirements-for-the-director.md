---
title: 'Lync Server 2013: 디렉터에 대한 하드웨어 및 소프트웨어 요구 사항'
TOCTitle: 디렉터에 대한 하드웨어 및 소프트웨어 요구 사항
ms:assetid: 747b701e-7f97-46fe-91c5-1e8d9addf9f7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398560(v=OCS.15)
ms:contentKeyID: 49304041
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 디렉터에 대한 하드웨어 및 소프트웨어 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 섹션에서는 디렉터에 대한 하드웨어 및 소프트웨어 요구 사항과 디렉터에 대해 지원되는 배치 시나리오에 대해 자세하게 설명합니다.

## 디렉터에 대한 하드웨어 요구 사항

다음 표에는 디렉터에 대한 하드웨어 요구 사항이 나와 있습니다.

### 디렉터에 대한 하드웨어 요구 사항

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>하드웨어 구성 요소</th>
<th>최소 요구 사항</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><ul>
<li><p>64비트 프로세서, 쿼드 코어, 2.0 GHz 이상</p></li>
<li><p>64비트 듀얼 프로세서, 듀얼 코어, 2.0GHz 이상</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>메모리</p></td>
<td><p>4GB(기가바이트)</p></td>
</tr>
<tr class="odd">
<td><p>디스크</p></td>
<td><ul>
<li><p>10K RPM HDD(하드 디스크 드라이브)</p></li>
<li><p>성능이 10K RPM HDD 이상인 고성능 SDD(반도체 드라이브)</p></li>
<li><p>2x RAID 10(스트라이프 및 미러) 15K RPM 디스크(데이터베이스 데이터 파일용)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>네트워크</p></td>
<td><ul>
<li><p>1Gbps(초당 기가비트) 네트워크 어댑터 2개(권장)</p></li>
<li><p>1Gbps 네트워크 어댑터 1개(지원)</p></li>
</ul></td>
</tr>
</tbody>
</table>


## 디렉터에 대한 소프트웨어 요구 사항

디렉터 역할은 Lync Server 2013 Enterprise Edition을 실행하는 서버에만 배포할 수 있습니다.

디렉터에는 다음 64비트 운영 체제 중 하나가 필요합니다.

  - Windows Server 2008 R2 Standard 운영 체제 서비스 팩 1

  - Windows Server 2008 R2 Enterprise 운영 체제 서비스 팩 1

  - Windows Server 2008 R2 Datacenter 운영 체제 서비스 팩 1

  - Windows Server 2012 Standard 운영 체제

  - Windows Server 2012 Datacenter 운영 체제

Lync Server 2013에는 [Lync Server 2013의 추가 서버 지원 및 요구 사항](lync-server-2013-additional-server-support-and-requirements.md) 항목에 설명된 다음과 같은 프로그램 및 업데이트도 설치되어야 합니다.

## 지원되는 배치

디렉터 서버 역할은 Lync Server 2013에서 다른 서버 역할과 함께 배치할 수 없습니다. 하지만 디렉터를 배포하지 않을 경우 프런트 엔드 서버가 이 역할을 가정합니다.

