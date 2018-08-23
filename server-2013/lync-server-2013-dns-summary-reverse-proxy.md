---
title: 'Lync Server 2013: DNS 요약 - 역방향 프록시'
TOCTitle: DNS 요약 - 역방향 프록시
ms:assetid: 3073affa-4d92-4453-9974-3a82ca0c6445
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204781(v=OCS.15)
ms:contentKeyID: 49303208
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 DNS 요약 - 역방향 프록시

 

_**마지막으로 수정된 항목:** 2015-03-09_

다음과 같이 역방향 프록시에 네트워크 어댑터 두 개를 구성합니다.

## 역방향 프록시 네트워크 어댑터 요구 사항

  - **네트워크 어댑터 1(내부 인터페이스)** 예
    
    172.25.33.40이 할당된 내부 인터페이스입니다.
    
    기본 게이트웨이가 정의되어 있지 않습니다.
    
    역방향 프록시 내부 인터페이스가 포함된 네트워크에서 Lync Server  프런트 엔드 풀 서버가 포함된 네트워크로의 경로(예: 172.25.33.0에서 192.168.10.0으로)가 있는지 확인합니다.

  - **네트워크 어댑터 2(외부 인터페이스)** 예
    
    이 네트워크 어댑터에는 최소 하나의 공용 IP 주소가 할당됩니다.
    
    게이트웨이는 외부 경계의 통합 방화벽 또는 라우터를 가리키도록 정의됩니다(시나리오 예에서는 10.45.16.1).

### 역방향 프록시에 필요한 DNS 레코드

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>위치/유형/포트</th>
<th>FQDN</th>
<th>IP 주소</th>
<th>매핑 대상/설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>외부 DNS/A</p></td>
<td><p>webext.contoso.com</p></td>
<td><p>외부에 게시된 리소스에 할당되는 수신기</p></td>
<td><p>내부 배포의 외부 웹 서비스입니다. 이 역방향 프록시를 사용하며 외부 웹 서비스를 정의한 모든 SIP 도메인에 대해 모든 풀과 단일 서버용으로 추가 레코드를 정의하고 만들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>webdirext.contoso.com</p></td>
<td><p>외부에 게시된 리소스에 할당되는 수신기</p></td>
<td><p>배포의 디렉터 또는 디렉터 풀에 대한 외부 웹 서비스입니다. 고유한 디렉터의 수만큼 디렉터를 정의할 수 있으며, 디렉터는 다른 SIP 도메인과 연결될 수 있습니다.</p>


> [!IMPORTANT]
> 디렉터에 대해 DNS 레코드를 정의하고 디렉터를 게시하는 것은 프런트 엔드 풀 또는 디렉터 관련 결정 사항이 아닙니다. 디렉터를 사용하는 경우에는 디렉터 및 프런트 엔드 풀 외부 웹 서비스를 모두 정의 및 게시해야 합니다. 인증 및 기타 용도의 특정 트래픽 유형은 디렉터로 먼저 전송됩니다(토폴로지에 정의된 경우).


</td>
</tr>
<tr class="odd">
<td><p>외부 DNS/A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>외부에 게시된 리소스에 할당되는 수신기</p></td>
<td><p>전화 접속 회의를 외부적으로 게시하는 데 사용됨</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>외부에 게시된 리소스에 할당되는 수신기</p></td>
<td><p>전화 회의를 외부적으로 게시하는 데 사용됨</p></td>
</tr>
<tr class="odd">
<td><p>외부 DNS/A</p></td>
<td><p>officewebapps01.contoso.com</p></td>
<td><p>Office Web Apps 서버에 할당되는 수신기</p></td>
<td><p>내부 또는 경계에 배포되며 외부 클라이언트 액세스용으로 게시되는 Office Web Apps 서버</p></td>
</tr>
<tr class="even">
<td><p>외부 DNS/A</p></td>
<td><p>lyncdiscover.contoso.com</p></td>
<td><p>외부에 게시된 리소스에 할당되는 수신기</p></td>
<td><p>외부에 게시된 자동 검색용 Lync Discover External 레코드로 모바일 기능, Microsoft Lync Web App 및 스케줄러 웹 응용 프로그램을 포함합니다.</p></td>
</tr>
</tbody>
</table>

