---
title: 'Lync Server 2013: 프런트 엔드 풀 및 Standard Edition 서버에 대한 IIS 요구 사항'
TOCTitle: 프런트 엔드 풀 및 Standard Edition 서버에 대한 IIS 요구 사항
ms:assetid: e8a6c7ac-b6d5-4c7e-abe9-d8ea5eedbc62
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399038(v=OCS.15)
ms:contentKeyID: 49305388
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 프런트 엔드 풀 및 Standard Edition 서버에 대한 IIS 요구 사항

 

_**마지막으로 수정된 항목:** 2015-03-09_

Standard Edition Server, 프런트 엔드 서버 및 디렉터에서 Lync Server 2013 설치 관리자는 IIS(인터넷 정보 서비스)에 다음 용도의 가상 디렉터리를 만듭니다.

  - 사용자가 주소록 서비스에서 파일을 다운로드할 수 있도록 하기 위해

  - 클라이언트가 업데이트를 받을 수 있도록 하기 위해

  - 회의를 사용하기 위해

  - 사용자가 모임 콘텐츠를 다운로드할 수 있도록 하기 위해

  - 사용자가 메일 그룹을 확장하도록 하기 위해

  - 전화 회의를 사용하기 위해

  - 응답 그룹 기능을 사용하기 위해

또한 Lync Server 2010용 누적 업데이트: 2011년 11월 설치 관리자는 다음과 같은 용도로 IIS에 가상 디렉터리를 만듭니다.

  - 프런트 엔드 서버 또는 Standard Edition Server에서 IM(인스턴트 메시징), 현재 상태 등의 모바일 기능을 모바일 장치에서 지원하기 위해

  - 프런트 엔드 서버 또는 Standard Edition Server와 디렉터에서 모바일 장치가 모바일 기능 리소스를 자동으로 검색할 수 있도록 하기 위해


> [!NOTE]
> 모바일 기능을 배포하는 경우에는 IIS 7.5를 사용하는 것이 좋습니다. Lync Server Mobility Service 설치 관리자는 성능을 개선하기 위해 몇 가지 ASP.NET 플래그를 설정합니다. IIS 7.5는 Windows Server 2008 R2에서 기본적으로 설치되며, Mobility Service 설치 관리자는 ASP.NET 설정을 자동으로 변경합니다. Windows Server 2008에서 IIS 7.0을 사용하는 경우에는 이러한 설정을 수동으로 변경해야 합니다.



Lync Server에는 다음과 같은 IIS 모듈이 설치되어야 합니다.


> [!IMPORTANT]
> 조직에서 IIS 및 모든 웹 서비스를 시스템 드라이브가 아닌 다른 드라이브에 배치해야 하는 경우 설치 프로그램 대화 상자에서 Lync Server 파일의 설치 위치 경로를 변경할 수 있습니다. 설치 파일(OCSCore.msi 포함)을 이 경로에 설치하면 남은 Lync Server 파일도 이 드라이브에 배포됩니다. IIS를 설치할 때 Windows Server Manager에서 배포되는 INETPUB를 재배치하는 방법에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=216888%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=216888&amp;clcid=0x412</A>를 참조하십시오.



  - 정적 콘텐츠

  - 기본 문서

  - HTTP 오류

  - ASP.NET

  - .NET 확장성

  - ISAPI(인터넷 서버 API) 확장

  - ISAPI 필터

  - HTTP 로깅

  - 로깅 도구

  - 추적

  - Windows 인증

  - 요청 필터링

  - 정적 콘텐츠 압축

  - 동적 콘텐츠 압축

  - IIS 관리 콘솔

  - IIS 관리 스크립트 및 도구

  - 익명 인증(IIS가 설치될 때 기본적으로 설치됨)

  - 클라이언트 인증서 매핑 인증

다음 표에서는 내부 액세스를 위한 가상 디렉터리의 URI과 이 디렉터리가 참조하는 파일 시스템 리소스를 나열합니다.

### 내부 액세스를 위한 가상 디렉터리

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>기능</th>
<th>가상 디렉터리 URI</th>
<th>참조 대상</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>주소록 서버</p></td>
<td><p>https:// <em>&lt;내부 FQDN&gt;</em> /ABS/int/Handler</p></td>
<td><p>내부 사용자용 주소록 서버 다운로드 파일의 위치</p></td>
</tr>
<tr class="even">
<td><p>자동 검색 서비스</p></td>
<td><p>https:// <em>&lt;내부 FQDN&gt;</em> /Autodiscover</p></td>
<td><p>내부 모바일 장치 사용자를 위해 모바일 기능 리소스를 찾는 Lync Server 자동 검색 서비스의 위치</p></td>
</tr>
<tr class="odd">
<td><p>클라이언트 업데이트</p></td>
<td><p>http:// <em>&lt;내부 FQDN&gt;</em> /AutoUpdate/Int</p></td>
<td><p>내부 컴퓨터 기반 클라이언트용 업데이트 파일의 위치</p></td>
</tr>
<tr class="even">
<td><p>회의</p></td>
<td><p>http:// <em>&lt;내부 FQDN&gt;</em> /Conf/Int</p></td>
<td><p>내부 사용자용 회의 리소스의 위치</p></td>
</tr>
<tr class="odd">
<td><p>장치 업데이트</p></td>
<td><p>http:// <em>&lt;내부 FQDN&gt;</em> /DeviceUpdateFiles_Int</p></td>
<td><p>내부 UC 장치용 UC(통합 통신) 장치 업데이트 파일의 위치</p></td>
</tr>
<tr class="even">
<td><p>모임</p></td>
<td><p>http:// <em>&lt;내부 FQDN&gt;</em> /etc/place/null</p></td>
<td><p>내부 사용자용 모임 콘텐츠 위치의 위치</p></td>
</tr>
<tr class="odd">
<td><p>Mobility Service</p></td>
<td><p>https:// <em>&lt;내부 FQDN&gt;</em> /Mcx</p></td>
<td><p>내부 모바일 장치 사용자를 위한 Mobility Service 리소스의 위치</p></td>
</tr>
<tr class="even">
<td><p>그룹 확장 및 주소록 웹 쿼리 서비스</p></td>
<td><p>http:// <em>&lt;내부 FQDN&gt;</em> /GroupExpansion/int/service.asmx</p></td>
<td><p>내부 사용자의 그룹 확장을 사용할 수 있도록 하는 웹 서비스의 위치. 또한 내부의 Lync MobileMicrosoft Lync 2010 Mobile 클라이언트에 전체 주소 목록 정보를 제공하는 주소록 웹 쿼리 서비스의 위치</p></td>
</tr>
<tr class="odd">
<td><p>전화 회의</p></td>
<td><p>http:// <em>&lt;내부 FQDN&gt;</em> /PhoneConferencing/Int</p></td>
<td><p>내부 사용자용 전화 회의 데이터의 위치</p></td>
</tr>
<tr class="even">
<td><p>장치 업데이트</p></td>
<td><p>http:// <em>&lt;내부 FQDN&gt;</em> /RequestHandler</p></td>
<td><p>내부 UC 장치가 로그를 업로드하고 업데이트를 확인할 수 있도록 하는 장치 업데이트 웹 서비스 요청 처리기의 위치</p></td>
</tr>
<tr class="odd">
<td><p>응답 그룹 응용 프로그램</p></td>
<td><p>http:// <em>&lt;내부 FQDN&gt;</em> /RgsConfig</p>
<p>http:// <em>&lt;내부 FQDN&gt;</em> /RgsClients</p></td>
<td><p>응답 그룹 구성 도구의 위치</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 통합된 구성의 프런트 엔드 풀의 경우 IIS를 배포해야 풀에 서버를 추가할 수 있습니다.



<table>
<thead>
<tr class="header">
<th><img src="images/Gg398321.security(OCS.15).gif" title="security" alt="security" />보안 참고:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IIS 관리 스냅인을 사용하여 IIS 웹 구성 요소 서버에서 사용하는 인증서를 할당해야 합니다.</td>
</tr>
</tbody>
</table>

