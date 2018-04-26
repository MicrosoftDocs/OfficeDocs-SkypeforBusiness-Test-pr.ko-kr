---
title: 'Lync Server 2013: IP 주소 유형의 개요'
TOCTitle: Lync Server에 대한 IP 주소 유형의 개요
ms:assetid: ee9a695f-5cf5-441e-94fb-6adeca50e8d8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205363(v=OCS.15)
ms:contentKeyID: 49305450
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 IP 주소 유형의 개요

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013에서 IP 주소를 구성할 때 세 가지 옵션이 있습니다. IP 버전 4(IPv4), IP 버전 6(IPv6) 또는 두 버전의 조합( *이중 스택* 이라고 함)을 지원하도록 Lync Server 2013을 구성할 수 있습니다. 구성 유형마다 고려해야 할 몇 가지 사항이 있습니다.

  - **IPv4 전용**   세계적으로 ipv4 주소가 고갈되고 있기에 IPv6 주소가 개발되었습니다. 궁극적으로는 전 세계에서 IPv6이 완전하게 지원되겠지만, 현재는 회사에서 통신해야 할 여러 회사와 장치에서 아직 IPv6을 지원하지 않을 수도 있으므로 IPv4 전용 구성을 사용하면 Lync Server 구현에서 대부분의 기존 장치와 통신할 수 있습니다.

  - **IPv6 전용**   위와는 달리, 현재 완전 IPv6 구현에서는 여러 기존 장치와의 통신이 배제됩니다.

  - **이중 스택**   이중 스택은 IPv4 및 IPv6 주소를 둘 다 사용할 수 있는 네트워크입니다. 대부분의 경우 완전 IPv4에서 완전 IPv6으로의 전환에는 몇 년이 걸리므로 Lync Server 2013에서 이 구성이 지원됩니다.

다음 섹션에서는 다양한 Lync Server 기능에 대한 다음과 같은 세 가지 구성 간의 호환에 대해 설명합니다.


> [!NOTE]
> IPv6를 사용한 클라이언트 또는 서버 구성은 연구 또는 검사 목적으로만 지원됩니다. IPv6 전용 구성은 프로덕션 배포에는 지원되지 않습니다.



## 클라이언트 등록


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트 끝점 네트워크</th>
<th>서버 네트워크</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>이중 스택</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>이중 스택</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>이중 스택</p></td>
<td><p>IPv6</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


## 피어 투 피어 클라이언트

피어 투 피어 통신에는 오디오, 오디오/비디오, 응용 프로그램 공유 및 파일 전송이 포함됩니다. 두 클라이언트가 성공적으로 등록된 후에는 다음 조합이 지원됩니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트 끝점 1</th>
<th>클라이언트 끝점 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>이중 스택</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


## 회의

회의에는 오디오/비디오, 응용 프로그램 공유 및 데이터 공동 작업(화이트보드 및 파일 공유)이 포함됩니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>클라이언트 끝점 네트워크</th>
<th>서버 네트워크</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>이중 스택</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>이중 스택</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>이중 스택</p></td>
<td><p>IPv6</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


## 중재 서버/PSTN

Lync Server 2013에서는 트래픽이 IPv6 인터페이스를 통해 이루어지는 경우 PSTN(공중 전화망) 통화에 대한 미디어 바이패스를 지원하지 않습니다. 미디어 바이패스가 필요할 경우 PSTN 게이트웨이를 IPv4로 구성하는 것이 좋습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>기본 인터페이스*</th>
<th>PSTN 인터페이스(중재 서버)</th>
<th>PSTN 게이트웨이 설정</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>이중 스택</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>이중 스택</p></td>
<td><p>이중 스택</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="odd">
<td><p>이중 스택</p></td>
<td><p>이중 스택</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


\* 기본 인터페이스는 Lync Server 구성 요소와 통신하는 인터페이스입니다.

## 원격 사용자 피어 투 피어 통신

원격 사용자와의 피어 투 피어 통신에는 인스턴트 메시징, 오디오/비디오, 응용 프로그램 공유 및 파일 전송이 포함됩니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>원격 사용자 네트워크</th>
<th>에지 서버(외부 에지)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IPv4</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="even">
<td><p>이중 스택</p></td>
<td><p>IPv4</p></td>
</tr>
<tr class="odd">
<td><p>이중 스택</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="even">
<td><p>IPv6</p></td>
<td><p>이중 스택</p></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>IPv6</p></td>
</tr>
</tbody>
</table>


## 프런트 엔드 풀과 에지 풀 구성

다음 표에서는 프런트 엔드 서버 풀과 내부 에지 서버 풀 간의 지원 매트릭스를 보여 줍니다.

### 프런트 엔드 풀과 에지 풀(내부 에지) 매트릭스

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>에지 풀: IPv4</strong></p></td>
<td><p><strong>에지 풀: 이중 스택</strong></p></td>
<td><p><strong>에지 풀: IPv6</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>프런트 엔드 풀: IPv4</strong></p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p><strong>프런트 엔드 풀: 이중 스택</strong></p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p><strong>프런트 엔드 풀: IPv6</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>예*</p></td>
</tr>
</tbody>
</table>


\* 이 조합은 랩 환경에서만 사용하십시오.

다음 표는 지원되는 내부 및 외부 에지 인터페이스 조합 매트릭스입니다.

### 에지 풀(내부 에지)과 에지 풀(외부 에지) 매트릭스

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>에지 풀(외부 에지) : IPv4</strong></p></td>
<td><p><strong>에지 풀(외부 에지): 이중 스택</strong></p></td>
<td><p><strong>에지 풀(외부 에지) : IPv6</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>에지 풀(내부 에지) : IPv4</strong></p></td>
<td><p>예</p></td>
<td><p>예</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="odd">
<td><p><strong>에지 풀(내부 에지): 이중 스택</strong></p></td>
<td><p>아니요</p></td>
<td><p>예</p></td>
<td><p>아니요</p></td>
</tr>
<tr class="even">
<td><p><strong>에지 풀(내부 에지) : IPv6</strong></p></td>
<td><p>아니요</p></td>
<td><p>아니요</p></td>
<td><p>예*</p></td>
</tr>
</tbody>
</table>


\* 이 조합은 랩 환경에서만 사용하십시오.

## IPv6에 대한 고급 Enterprise Voice 지원

CAC(통화 허용 제어 서비스), E9-1-1(고급 9-1-1) 또는 미디어 바이패스를 포함하는 배포는 IPv4 전용 또는 이중 스택 구현으로 구성해야 합니다.


> [!NOTE]
> 이중 스택 배포에서는 Lync 클라이언트가 IPv6을 사용하여 Lync Server에 연결되어도 Lync에서는 해당 IPv4 주소를 매핑하여 E9-1-1을 지원하기 위해 최대한 노력합니다.



IPv6 주소를 사용하는 위치 정보 서비스는 지원되지 않습니다.

Exchange UM(통합 메시징)에서는 IPv6을 지원하지 않습니다. Exchange UM의 경우 DNS 확인 시 IPv6 주소가 반환되지 않습니다. IPv6을 사용하면 통화가 음성 사서함으로 올바르게 전송될 때 실패할 수도 있습니다.

## IPv6에 대한 기타 Lync Server 2013 기능 지원

앞에서 설명한 기능과 구성 요소 외에도, Lync Server 2013에서는 다음 기능에 대한 IPv6을 지원합니다.

  - **영구 채팅**
    
    토폴로지 작성기를 사용하여 영구 채팅에 대해 IPv6을 구성할 수 있습니다. 영구 채팅 구성에 대한 자세한 내용은 영구 채팅 서버 배포 설명서를 참조하십시오.

  - **QoE(체감 품질)과 CDR(통화 정보 기록) 보고서**
    
    모니터링 보고서에는 IPv4 형식인지 IPv6 형식인지에 관계 없이 모니터링 서버 데이터베이스에 저장된 IP 주소가 포함됩니다.

