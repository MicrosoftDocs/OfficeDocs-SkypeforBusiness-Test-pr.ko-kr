---
title: 'Lync Server 2013: 영구 채팅 서버에 대한 기술 요구 사항'
TOCTitle: 영구 채팅 서버에 대한 기술 요구 사항
ms:assetid: 692b7d99-1bc9-4c99-a050-2bc2be8688b2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398495(v=OCS.15)
ms:contentKeyID: 49303913
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 영구 채팅 서버에 대한 기술 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 서버을 호스트할 각 컴퓨터는 다음 구성 요소가 포함된 기존 Lync Server 2013 토폴로지에 액세스할 수 있어야 합니다.

  - **Lync Server 2013, 프런트 엔드 서버.** 프런트 엔드 서버는 가능한 영구 채팅 서버 및 영구 채팅 기능을 실행하는 컴퓨터 사이에 통신을 수행하는 SIP(Session Initiation Protocol)의 기초입니다. 영구 채팅 서버 배포를 시작하기 전에 Lync Server 2013, Standard Edition, 또는 Lync Server프런트 엔드 풀 및 조직에 따라 Lync Server를 실행하는 다른 모든 내부 컴퓨터의 배포를 확인해야 합니다.

다음 섹션에서는 영구 채팅 서버 데이터를 저장하는 데이터베이스 및 영구 채팅에 대한 특정 요구 사항을 설명합니다.

## 영구 채팅 서버 요구 사항

Lync Server 및 최신 버전 영구 채팅 서버 배포를 위한 권장 하드웨어에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)을 참조하십시오.

Lync Server 및 영구 채팅 서버의 서버 및 도구 운영 체제 지원에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)을 참조하십시오.

영구 채팅 서버 배포를 위해 필요한 추가 소프트웨어에 대한 자세한 내용은 다음 표를 참조하십시오.

### 영구 채팅 서버 소프트웨어 필수 구성 요소

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>소프트웨어</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>메시지 큐</p></td>
<td><p>영구 채팅 서버 및 영구 채팅 준수 서비스에서 사용됩니다(배포된 경우).</p></td>
</tr>
</tbody>
</table>


## 영구 채팅 서버 데이터베이스 요구 사항

영구 채팅 서버에서는 영구 채팅 데이터베이스를 사용하여 채팅 기록, 구성 및 사용자 프로비저닝 데이터를 저장합니다. 선택적으로 영구 채팅 준수 데이터베이스를 사용하여 준수 데이터를 저장합니다.


> [!IMPORTANT]
> 영구 채팅 데이터베이스(mgc) 및 준수 데이터베이스(mgccomp)는 SQL Server 의 동일한 인스턴스 또는 다른 SQL Servers에 배치할 수 있습니다.



데이터베이스 서버 플랫폼을 준비하려면 각 컴퓨터가 하드웨어 요구 사항을 충족하는지 확인한 다음 필수 구성 요소 소프트웨어를 설치합니다.

영구 채팅 데이터베이스 서버의 서버 플랫폼에는 Lync Server 백 엔드 데이터베이스 서버와 동일한 하드웨어가 필요합니다. 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)을 참조하십시오.

데이터베이스 서버에서 다음 소프트웨어 응용 프로그램 중 하나가 설치되어 있는지 확인합니다.

  - Microsoft SQL Server 2012. Microsoft SQL Server 2012 설치 방법에 대한 자세한 내용은 "SQL Server 2012 설치"( <http://go.microsoft.com/fwlink/?linkid=248559>)를 참조하십시오.

  - Microsoft SQL Server 2008 R2. Microsoft SQL Server 2008 R2를 설치하는 방법에 대한 자세한 내용은 <http://go.microsoft.com/fwlink/?linkid=275702>에서 "SQL Server 설치(SQL Server 2008 R2)"를 참조하십시오.

## 영구 채팅 서버 인증서 요구 사항

인증서 얻기, SQL Server 데이터베이스 만들기, 파일 저장소 만들기에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)를 참고하세요.

