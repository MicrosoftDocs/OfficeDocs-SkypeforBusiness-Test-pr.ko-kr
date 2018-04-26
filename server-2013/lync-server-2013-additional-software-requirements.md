---
title: 'Lync Server 2013: 추가 소프트웨어 요구 사항'
TOCTitle: 추가 소프트웨어 요구 사항
ms:assetid: 87b318e3-03ae-41f7-af5e-29bb294f6af0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398686(v=OCS.15)
ms:contentKeyID: 49304285
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 추가 소프트웨어 요구 사항

 

_**마지막으로 수정된 항목:** 2014-06-20_

서버 플랫폼에 대한 하드웨어 및 운영 체제 요구 사항 외에 Lync Server 2013을 사용하려면 배포한 서버에 추가 소프트웨어를 설치해야 합니다.


> [!NOTE]
> Lync Server을 실행하는 서버의 플랫폼 요구 사항에 대한 자세한 내용은 <A href="lync-server-2013-server-hardware-platforms.md">Lync Server 2013의 서버 하드웨어 플랫폼</A> 및 <A href="lync-server-2013-server-and-tools-operating-system-support.md">Lync Server 2013의 서버 및 도구 운영 체제 지원</A>을 참조하십시오. 클라이언트 컴퓨터 및 장치의 시스템 요구 사항에 대한 자세한 내용은 계획 설명서의 <A href="lync-server-2013-planning-for-clients-and-devices.md">Lync Server 2013에서 클라이언트 및 장치 계획</A>을 참조하십시오. 관리 도구의 소프트웨어 요구 사항에 대한 자세한 내용은 <A href="lync-server-2013-administrative-tools-software-requirements.md">Lync Server 2013의 관리 도구 소프트웨어 요구 사항</A>을 참조하십시오.



## 모든 내부 서버 역할에 필요한 추가 소프트웨어

이 섹션에서는 모든 내부 서버 역할, 즉 에지 서버를 제외한 모든 Lync Server 서버 역할에 필요한 소프트웨어를 나열합니다. 에지 서버 및 에지 풀에 대한 요구 사항은 이 항목 뒷부분의 **에지 서버용 추가 소프트웨어**에 나와 있습니다.

## Windows PowerShell 3.0

Lync Server 2013을 실행하는 각 서버에는 올바른 버전의 Windows PowerShell 3.0이 설치되어 있어야 합니다. 자세한 내용은 [Lync Server 2013용 Windows PowerShell 3.0 설치](lync-server-2013-installing-windows-powershell-3-0.md)를 참조하십시오.

## Microsoft .NET Framework 4.5

모든 내부 서버 역할과 Lync Server 관리 도구 또는 Microsoft Lync Server 2013, 계획 도구를 실행하는 모든 컴퓨터의 Lync Server에는 Microsoft .NET Framework 4.5가 필요합니다. Lync Server 2013의 경우 Lync Server 2013을 설치하기 전에 서버에 64비트 버전의 Microsoft .NET Framework 4.5를 수동으로 설치해야 합니다. 수동으로 설치하려면 Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/p/?LinkId=268529](http://go.microsoft.com/fwlink/p/?linkid=268529))에서 Microsoft .NET 4.5 Framework를 다운로드하세요.

## Windows Server 2012 실행 서버에 Microsoft .NET Framework 4.5 설치

Lync Server 2013 및 Windows Server 2012를 실행하는 서버에 Microsoft .NET Framework 4.5를 설치할 때는 추가 단계를 하나 더 수행해야 합니다. .NET Framework 4.5를 설치한 후 서버 관리자를 사용해서 HTTP 활성화를 설치해야 합니다.

**.NET 4.5 HTTP 활성화를 Windows Server 2012에 설치하려면**

1.  **시작** 메뉴에서 **프로그램** , **관리 도구** 를 차례로 클릭한 후 **서버 관리자** 를 클릭합니다.

2.  서버 관리자의 **기능 요약** 에서 **기능 추가** 를 선택합니다.

3.  **.NET Framework 4.5** 를 확장합니다.

4.  아직 선택하지 않았으면 **WCF 활성화** 를 선택한 후 **HTTP 활성화** 를 선택합니다.

5.  **다음** 을 클릭하고 프롬프트에 따라 설치를 완료합니다.

## Windows Identity Foundation

Lync Server 2013의 **Windows Identity Foundation**을 사용하려면 서버 간 인증 시나리오 지원용으로 Windows Identity Foundation을 설치해야 합니다. Windows Server 2008 R2 및 Windows Server 2012에서는 각기 다른 절차를 수행하여 Windows Identity Foundation을 설치해야 합니다. 다음 목록에서 서버 운영 체제를 선택하십시오.

  - Windows Server 2008 R2    Windows Server 2008 R2가 컴퓨터에 이미 설치되었는지 확인합니다. 이렇게 하려면 **프로그램 추가/제거** , **설치된 업데이트 보기** 로 이동한 다음 **Windows** 아래에서 **Windows Identity Foundation (KB974405)** 항목이 있는지 확인합니다. Windows Identity Foundation을 설치하는 방법에 대한 자세한 내용은 <http://go.microsoft.com/fwlink/?linkid=204657>를 참조하십시오.

  - Windows Server 2012    Windows Server 2012의 경우에는 **서버 관리자** 를 사용하여 Windows Identity Foundation을 설치합니다. 이렇게 하려면 서버 관리자의 **역할 및 기능 추가 마법사** 에서 **기능** 을 선택합니다. 그런 후에 목록에서 **Windows Identity Foundation 3.5** 를 선택합니다. 그리고 나서 **다음** , **설치** 를 차례로 클릭합니다.

## 모든 프런트 엔드 서버 및 Standard Edition 서버용 추가 소프트웨어

모든 프런트 엔드 서버 및 Standard Edition 서버에서는 특정 모듈이 포함된 IIS(인터넷 정보 서비스)도 실행해야 합니다. 또한 회의, 통화 대기 응용 프로그램, 알림 또는 응답 그룹이 배포된 모든 프런트 엔드 서버 및 Standard Edition 서버에서는 Windows Media 형식 런타임을 실행해야 합니다.

## IIS(인터넷 정보 서비스)

프런트 엔드 서버 및 Standard Edition 서버에서는 다음 모듈이 포함된 IIS(인터넷 정보 서비스)를 실행해야 합니다.

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

  - 익명 인증(IIS 설치 시 기본적으로 설치됨)

  - 클라이언트 인증서 매핑 인증

## Windows Media 형식 런타임 및 Windows Desktop Experience

**Windows Desktop Experience** 회의를 배포할 모든 프런트 엔드 서버 및 Standard Edition 서버에 Windows Media 형식 런타임이 설치되어 있어야 합니다. 단, Windows Server 2012는 Windows Desktop Experience의 일부로 설치됩니다. Windows Server 2012에는 Microsoft Media Foundation이 필요합니다. 통화 대기, 알림, 및 응답 그룹 응용 프로그램이 알림 및 음악용으로 재생하는 Windows Media 오디오(.wma) 파일을 실행하려면 Windows Media 형식 런타임이 필요합니다.

Lync Server 2013을 설치하기 전에 Windows 데스크톱 경험을 설치하는 것이 좋습니다. Lync Server 2013이 서버에서 이 소프트웨어를 찾지 못하는 경우 이 소프트웨어를 설치하라는 메시지가 표시되며 소프트웨어를 설치한 후에는 서버를 다시 시작해야 설치가 완료됩니다.

## Windows Server 2012에서 실행되는 프런트 엔드 서버 및 Standard Edition 서버용 추가 소프트웨어

프런트 엔드 서버에는 Windows Server 2012에서 기본적으로 설치되지 않는 .NET 3.5가 필요합니다. 이를 설치하려면 Windows Server 2012 설치 미디어를 D 드라이브에 넣고 다음을 입력합니다.

    Add-WindowsFeature RSAT-ADDS, Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Compat, Desktop-Experience, Telnet-Client, BITS -Source D:\sources\sxs

Windows Server 2012 실행 서버에 .NET 3.5를 설치하는 방법에 대한 자세한 내용은 <http://go.microsoft.com/fwlink/?linkid=275032>에서 "Microsoft .NET Framework 3.5 배포 고려 사항"을 참조하십시오.

## 디렉터용 추가 소프트웨어

디렉터에서는 다음 모듈이 포함된 IIS(인터넷 정보 서비스)를 실행해야 합니다.

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

  - IIS 관리 콘솔

  - IIS 관리 스크립트 및 도구

  - 익명 인증(IIS 설치 시 기본적으로 설치됨)

  - 클라이언트 인증서 매핑 인증

## 영구 채팅 프런트 엔드 서버를 위한 추가 소프트웨어

영구 채팅 프런트 엔드 서버는 Windows Server의 구성 요소인 메시지 큐(MSMQ라고도 함)를 실행해야 합니다.

MSMQ 실행에 대한 자세한 내용은 [여기를 클릭하세요.](http://technet.microsoft.com/en-us/library/cc771474.aspx)

## 에지 서버용 추가 소프트웨어

에지 서버에는 다음 소프트웨어가 필요합니다.

  - Lync Server 2013을 실행하는 각 서버에는 올바른 버전의 Windows PowerShell 3.0이 설치되어 있어야 합니다. 자세한 내용은 [Lync Server 2013용 Windows PowerShell 3.0 설치](lync-server-2013-installing-windows-powershell-3-0.md)를 참조하십시오.

  - Lync Server에는 Microsoft .NET Framework 4.5가 필요합니다. Windows Server 2008 R2에 설치된 Lync Server 2013의 경우에는 Lync Server 2013을 설치하기 전에 서버에 64비트 버전의 Microsoft .NET Framework 4.5를 수동으로 설치해야 합니다. 수동으로 설치하려면 Microsoft 다운로드 센터( <http://go.microsoft.com/fwlink/?linkid=268529>)에서 Microsoft .NET 4.5 Framework를 다운로드하십시오.

  - Lync Server 2013의 **Windows Identity Foundation**을 사용하려면 서버 간 인증 시나리오 지원용으로 Windows Identity Foundation을 설치해야 합니다. Windows Server 2008 R2 및 Windows Server 2012에서는 각기 다른 절차를 수행하여 Windows Identity Foundation을 설치해야 합니다. 다음 목록에서 서버 운영 체제를 선택하십시오.
    
      - Windows Server 2008 R2    Windows Server 2008 R2가 컴퓨터에 이미 설치되었는지 확인합니다. 이렇게 하려면 **프로그램 추가/제거** , **설치된 업데이트 보기** 로 이동한 다음 **Windows** 아래에서 **Windows Identity Foundation (KB974405)** 항목이 있는지 확인합니다. Windows Identity Foundation을 설치하는 방법에 대한 자세한 내용은 <http://go.microsoft.com/fwlink/?linkid=204657>를 참조하십시오.
    
      - Windows Server 2012    Windows Server 2012의 경우에는 **서버 관리자** 를 사용하여 Windows Identity Foundation을 설치합니다. 이렇게 하려면 서버 관리자의 **역할 및 기능 추가 마법사** 에서 **기능** 을 선택합니다. 그런 후에 목록에서 **Windows Identity Foundation 3.5** 를 선택합니다. 그리고 나서 **다음** , **설치** 를 차례로 클릭합니다.

## 미디어 서버에 LSP(Layered Service Provider) 설치 금지

Microsoft Internet Security and Acceleration(ISA) Server 클라이언트 소프트웨어 또는 다른 Winsock LSP(Layered Service Provider) 소프트웨어는 프런트 엔드 서버 또는 독립 실행형 중재 서버에 설치하지 마십시오. 이러한 소프트웨어를 설치하면 미디어 트래픽 성능이 저하될 수 있습니다.

## 참고 항목

#### 개념

[Lync Server 2013의 관리 도구 소프트웨어 요구 사항](lync-server-2013-administrative-tools-software-requirements.md)

