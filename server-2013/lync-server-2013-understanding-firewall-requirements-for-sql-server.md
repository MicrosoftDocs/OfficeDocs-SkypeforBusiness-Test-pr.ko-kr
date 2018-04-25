---
title: 'Lync Server 2013: SQL Server에 대한 방화벽 요구 사항 이해'
TOCTitle: SQL Server에 대한 방화벽 요구 사항 이해
ms:assetid: 31d7df2c-589f-465e-be74-cf6767db190d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425818(v=OCS.15)
ms:contentKeyID: 49303236
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 SQL Server에 대한 방화벽 요구 사항 이해

 

_**마지막으로 수정된 항목:** 2015-03-09_

Standard Edition 배포의 경우 Lync Server 2013 설치 중에 방화벽 예외가 자동으로 만들어집니다. 그러나 Enterprise Edition 배포의 경우에는 SQL Server 백 엔드 서버에서 방화벽 예외를 수동으로 구성해야 합니다. TCP/IP 프로토콜을 사용하는 경우 지정된 IP 주소에 대해 지정된 포트를 한 번 사용할 수 있습니다. 즉, SQL Server 기반 서버의 경우 기본 데이터베이스 인스턴스에 기본 TCP 포트 1433을 할당할 수 있습니다. 기타 모든 인스턴스의 경우에는 SQL Server 구성 관리자를 사용하여 고유한 미사용 포트를 할당해야 합니다. 이 항목에서는 다음에 대해 다룹니다.

  - 기본 인스턴스를 사용하는 경우의 방화벽 예외 요구 사항

  - SQL Server Browser 서비스를 사용하는 경우의 방화벽 예외 요구 사항

  - 명명된 인스턴스를 사용하는 경우의 정적 수신 대기 포트 요구 사항

## 기본 인스턴스를 사용하는 경우의 방화벽 예외 요구 사항

Lync Server 2013을 배포할 때 데이터베이스에 대해 SQL Server 기본 인스턴스를 사용하는 경우에는 다음과 같은 방화벽 규칙 요구 사항을 사용하여 프런트 엔드 풀에서 SQL Server 기본 인스턴스로의 통신을 확인합니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>프로토콜</th>
<th>포트</th>
<th>방향</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP</p></td>
<td><p>1433</p></td>
<td><p>SQL Server로 인바운드</p></td>
</tr>
</tbody>
</table>


## SQL Server Browser 서비스를 사용하는 경우의 방화벽 예외 요구 사항

SQL Server Browser 서비스는 데이터베이스 인스턴스를 찾아 해당 인스턴스(명명된 인스턴스 또는 기본 인스턴스)가 사용하도록 구성된 포트와 통신합니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>프로토콜</th>
<th>포트</th>
<th>방향</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UDP</p></td>
<td><p>1434</p></td>
<td><p>인바운드</p></td>
</tr>
</tbody>
</table>


## 명명된 인스턴스를 사용하는 경우의 정적 수신 대기 포트 요구 사항

Lync Server 2013을 지원하는 데이터베이스에 대해 SQL Server 구성에서 명명된 인스턴스를 사용하는 경우에는 SQL Server 구성 관리자를 사용하여 정적 포트를 구성합니다. 정적 포트를 각 명명된 인스턴스에 할당한 후에는 방화벽의 각 정적 포트에 대한 예외를 만듭니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>프로토콜</th>
<th>포트</th>
<th>방향</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP</p></td>
<td><p>정적으로 정의됨</p></td>
<td><p>인바운드</p></td>
</tr>
</tbody>
</table>


## SQL Server 설명서

Microsoft SQL Server 2012 설명서에서는 데이터베이스에 대한 방화벽 액세스를 구성하는 방법에 대한 자세한 지침을 제공합니다. Microsoft SQL Server 2012에 대한 자세한 내용은 "SQL Server 액세스를 허용하도록 Windows 방화벽 구성"( [http://go.microsoft.com/fwlink/?linkid=218031\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=218031%26clcid=0x412))을 참조하십시오.

