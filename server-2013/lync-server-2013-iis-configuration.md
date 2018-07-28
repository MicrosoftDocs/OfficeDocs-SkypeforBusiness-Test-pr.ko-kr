---
title: 'Lync Server 2013: IIS 구성'
TOCTitle: IIS 구성
ms:assetid: b458babf-bf64-43f0-8a8e-612f5096b63c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412871(v=OCS.15)
ms:contentKeyID: 49304776
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 IIS 구성

_**마지막으로 수정된 항목:** 2015-03-09_

이 절차를 완료하려면 최소한 로컬 관리자나 도메인 사용자로 서버에 로그온해야 합니다.

Lync Server 2013, Standard Edition 또는 풀의 첫 번째 프런트 엔드 서버에 대해 프런트 엔드 서버를 구성하거나 설치하기 전에 IIS(인터넷 정보 서비스)에 대해 서버 역할 및 웹 서비스를 설치 및 구성합니다.


> [!IMPORTANT]
> 조직에서 IIS와 모든 웹 서비스를 시스템 드라이브가 아닌 다른 드라이브에 배치해야 하는 경우 Lync Server 2013 관리 도구를 처음 설치할 때 설치 프로그램 대화 상자에서 Lync Server 2013 파일의 설치 위치 경로를 변경할 수 있습니다. IIS를 설치하기 전에 관리 도구를 설치합니다. 설치 파일(OCSCore.msi 포함)을 이 경로에 설치하면 남은 Lync Server 2013 파일도 이 드라이브에 배포됩니다. 자세한 내용은 <A href="lync-server-2013-install-lync-server-administrative-tools.md">Lync Server 2013 관리 도구 설치</A>를 참조하십시오. IIS를 설치할 때 Windows Server Manager에서 배포되는 INETPUB를 재배치하는 방법에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=216888">http://go.microsoft.com/fwlink/?linkid=216888</A>를 참조하십시오.



다음 표에 필요한 IIS 7.5 역할 서비스가 나와 있습니다.

### IIS 7.5 역할 서비스

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>역할 제목</th>
<th>역할 서비스</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>공통 HTTP 기능 설치</p></td>
<td><p>정적 콘텐츠</p></td>
</tr>
<tr class="even">
<td><p>공통 HTTP 기능 설치</p></td>
<td><p>기본 문서</p></td>
</tr>
<tr class="odd">
<td><p>공통 HTTP 기능 설치</p></td>
<td><p>HTTP 오류</p></td>
</tr>
<tr class="even">
<td><p>응용 프로그램 개발</p></td>
<td><p>ASP.NET</p>
<p>Windows Server 2012에는 ASP.NET4.5도 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 개발</p></td>
<td><p>.NET 확장성</p></td>
</tr>
<tr class="even">
<td><p>응용 프로그램 개발</p></td>
<td><p>ISAPI(인터넷 서버 API) 확장</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 개발</p></td>
<td><p>ISAPI 필터</p></td>
</tr>
<tr class="even">
<td><p>상태 및 진단</p></td>
<td><p>HTTP 로깅</p></td>
</tr>
<tr class="odd">
<td><p>상태 및 진단</p></td>
<td><p>로깅 도구</p></td>
</tr>
<tr class="even">
<td><p>상태 및 진단</p></td>
<td><p>추적</p></td>
</tr>
<tr class="odd">
<td><p>보안</p></td>
<td><p>익명 인증(기본적으로 설치 및 사용하도록 설정됨)</p></td>
</tr>
<tr class="even">
<td><p>보안</p></td>
<td><p>Windows 인증</p></td>
</tr>
<tr class="odd">
<td><p>보안</p></td>
<td><p>클라이언트 인증서 매핑 인증</p></td>
</tr>
<tr class="even">
<td><p>보안</p></td>
<td><p>요청 필터링</p></td>
</tr>
<tr class="odd">
<td><p>성능</p></td>
<td><p>정적 콘텐츠 압축</p>
<p>동적 콘텐츠 압축</p></td>
</tr>
<tr class="even">
<td><p>관리 도구</p></td>
<td><p>IIS 관리 콘솔</p></td>
</tr>
<tr class="odd">
<td><p>관리 도구</p></td>
<td><p>IIS 관리 스크립트 및 도구</p></td>
</tr>
</tbody>
</table>


또는 Windows Server 2008 R2 SP1 x64 운영 체제에서 Windows PowerShell 2.0을 사용할 수 있습니다. 이 경우 먼저 ServerManager 모듈을 설치한 다음 IIS 7.5 역할 및 역할 서비스를 설치해야 합니다.

```
    Import-Module ServerManager
```
```
    Add-WindowsFeature Web-Server, Web-Static-Content, Web-Default-Doc, Web-Scripting-Tools, Web-Windows-Auth, Web-Asp-Net, Web-Log-Libraries, Web-Http-Tracing, Web-Stat-Compression, Web-Dyn-Compression, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Errors, Web-Http-Logging, Web-Net-Ext, Web-Client-Auth, Web-Filtering, Web-Mgmt-Console
```


> [!NOTE]
> IIS 서버 역할에는 익명 인증이 기본적으로 설치됩니다. IIS를 설치한 후 익명 인증을 관리할 수 있습니다. 자세한 내용은 "익명 인증 사용(IIS 7)"( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=203935">http://go.microsoft.com/fwlink/?linkid=203935</A>)을 참조하십시오.



다음 표에는 Windows Server 2012 및 Windows Server 2012 R2에 필요한 IIS 8.0 및 IIS 8.5 역할 서비스가 나와 있습니다.


> [!NOTE]
> Windows Server 2012 및 Windows Server 2012 R2의 경우 Add-WindowsFeature cmdlet이 the Install-WindowsFeature cmdlet으로 바뀌었습니다. 자세한 내용은 <A href="http://go.microsoft.com/fwlink/p/?linkid=392274">Install-WindowsFeature</A>를 참고하세요.



### IIS 8.0 및 IIS 8.5 역할 서비스

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>역할 제목</th>
<th>역할 서비스</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>웹 서버(IIS)</p></td>
<td><p>웹 서버</p></td>
</tr>
<tr class="even">
<td><p>일반 HTTP 기능</p></td>
<td><p>기본 문서</p></td>
</tr>
<tr class="odd">
<td><p>일반 HTTP 기능</p></td>
<td><p>디렉터리 검색</p></td>
</tr>
<tr class="even">
<td><p>일반 HTTP 기능</p></td>
<td><p>HTTP 오류</p></td>
</tr>
<tr class="odd">
<td><p>일반 HTTP 기능</p></td>
<td><p>정적 콘텐츠</p></td>
</tr>
<tr class="even">
<td><p>일반 HTTP 기능</p></td>
<td><p>HTTP 리디렉션</p></td>
</tr>
<tr class="odd">
<td><p>상태 및 진단</p></td>
<td><p>HTTP 로깅</p></td>
</tr>
<tr class="even">
<td><p>상태 및 진단</p></td>
<td><p>로깅 도구</p></td>
</tr>
<tr class="odd">
<td><p>상태 및 진단</p></td>
<td><p>요청 모니터</p></td>
</tr>
<tr class="even">
<td><p>상태 및 진단</p></td>
<td><p>추적</p></td>
</tr>
<tr class="odd">
<td><p>보안</p></td>
<td><p>요청 필터링</p></td>
</tr>
<tr class="even">
<td><p>보안</p></td>
<td><p>기본 인증</p></td>
</tr>
<tr class="odd">
<td><p>보안</p></td>
<td><p>클라이언트 인증서 매핑 인증</p></td>
</tr>
<tr class="even">
<td><p>보안</p></td>
<td><p>Windows 인증</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 개발</p></td>
<td><p>.NET 확장성 3.5</p></td>
</tr>
<tr class="even">
<td><p>응용 프로그램 개발</p></td>
<td><p>.NET 확장성 4.5</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 개발</p></td>
<td><p>ASP.NET 3.5</p></td>
</tr>
<tr class="even">
<td><p>응용 프로그램 개발</p></td>
<td><p>ASP.NET 4.5</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 개발</p></td>
<td><p>ISAPI 확장</p></td>
</tr>
<tr class="even">
<td><p>응용 프로그램 개발</p></td>
<td><p>ISAPI 필터</p></td>
</tr>
<tr class="odd">
<td><p>응용 프로그램 개발</p></td>
<td><p>SSI(Server Side Includes)</p></td>
</tr>
<tr class="even">
<td><p>관리 도구</p></td>
<td><p>IIS 관리 콘솔</p></td>
</tr>
<tr class="odd">
<td><p>관리 도구</p></td>
<td><p>IIS 6 메타베이스 호환성</p></td>
</tr>
<tr class="even">
<td><p>관리 도구</p></td>
<td><p>IIS 관리 스크립트 및 도구</p></td>
</tr>
<tr class="odd">
<td><p>.NET 3.5 Framework 기능</p></td>
<td><p>.NET 3.5 Framework</p></td>
</tr>
<tr class="even">
<td><p>.NET 4.5 Framework 기능</p></td>
<td><p>.NET Framework 4.5</p></td>
</tr>
<tr class="odd">
<td><p>.NET 4.5 Framework 기능</p></td>
<td><p>ASP.NET 4.5</p></td>
</tr>
<tr class="even">
<td><p>.NET 4.5 Framework 기능</p></td>
<td><p>HTTP 활성화</p></td>
</tr>
<tr class="odd">
<td><p>.NET 4.5 Framework 기능</p></td>
<td><p>TCP 포트 공유</p></td>
</tr>
<tr class="even">
<td><p>Background Intelligent Transfer Service</p></td>
<td><p>IIS 서버 확장</p></td>
</tr>
<tr class="odd">
<td><p>잉크 및 필기 서비스</p></td>
<td><p>잉크 및 필기 서비스</p></td>
</tr>
<tr class="even">
<td><p>미디어 파운데이션</p></td>
<td><p>미디어 파운데이션</p></td>
</tr>
<tr class="odd">
<td><p>사용자 인터페이스 및 인프라</p></td>
<td><p>그래픽 관리 도구 및 인프라</p></td>
</tr>
<tr class="even">
<td><p>사용자 인터페이스 및 인프라</p></td>
<td><p>데스크톱 경험</p></td>
</tr>
<tr class="odd">
<td><p>사용자 인터페이스 및 인프라</p></td>
<td><p>서버 그래픽 셸</p></td>
</tr>
<tr class="even">
<td><p>Windows Identity Foundation 3.5</p></td>
<td><p>Windows Identity Foundation 3.5</p></td>
</tr>
<tr class="odd">
<td><p>Windows Process Activation Service</p></td>
<td><p>프로세스 모델</p></td>
</tr>
<tr class="even">
<td><p>Windows Process Activation Service</p></td>
<td><p>구성 API</p></td>
</tr>
</tbody>
</table>


Windows Server 2012 및 Windows Server 2012 R2에서는 Windows PowerShell 3.0을 사용하여 IIS 요구 사항을 설치할 수 있습니다. Windows PowerShell 3.0의 ServerManager 모듈을 사용하여 다음을 입력합니다.

```
    Import-Module ServerManager
```
```
    Add-WindowsFeature Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-Framework-45-Core, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Console, Web-Mgmt-Compat, Windows-Identity-Foundation, Server-Media-Foundation, BITS -Source D:\sources\sxs
```


> [!IMPORTANT]
> Windows Server 2012에는 Windows Server 2012 원본 미디어를 찾을 수 있는 위치를 정의하는 -Source 매개 변수가 새롭게 도입되었습니다. 미디어는 DVD 드라이브(예: D:\Sources\Sxs) 또는 미디어 파일이 복사된 네트워크 공유(예: \\fileserver\windows2012\sources\Sxs)로 정의할 수 있습니다.



## 참고 항목

#### 개념

[Lync Server 2013의 프런트 엔드 풀 및 Standard Edition 서버에 대한 IIS 요구 사항](lync-server-2013-iis-requirements-for-front-end-pools-and-standard-edition-servers.md)

