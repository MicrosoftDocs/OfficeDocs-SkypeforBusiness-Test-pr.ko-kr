---
title: 'Lync Server 2013: Lync Server 2013을 실행하는 서버의 시스템 요구 사항'
TOCTitle: Lync Server 2013을 실행하는 서버의 시스템 요구 사항
ms:assetid: 781d487d-5958-416a-becb-904d9af3cc0a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398588(v=OCS.15)
ms:contentKeyID: 49304094
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013을 실행하는 서버의 시스템 요구 사항

 

_**마지막으로 수정된 항목:** 2014-07-24_


> [!NOTE]
> 하드웨어 요구 사항에 대한 자세한 내용은 <A href="lync-server-2013-server-hardware-platforms.md">Lync Server 2013의 서버 하드웨어 플랫폼</A>을 참고하세요.



Standard Edition 및 Enterprise Edition 서버는 소프트웨어 요구 사항이 동일합니다.

Lync Server 2013, Enterprise Edition을 실행하는 서버는 기본 조직 배포로 대규모 조직을 지원하기 위한 서버입니다. Enterprise Edition 서버는 풀당 약 80,000명의 사용자까지 확장할 수 있도록 디자인되었습니다. Lync Server 2013, Standard Edition을 실행하는 서버는 기본 조직 배포로부터 소규모 조직 및 원격 위치를 지원하기 위한 서버입니다. Standard Edition 서버 한 쌍은 최대 5,000명의 사용자를 지원할 수 있습니다. Standard Edition 서버와 Enterprise Edition 서버 간의 차이점에 대한 자세한 내용은 [Lync Server 2013에 대한 배포 개요](lync-server-2013-deployment-overview.md)를 참고하세요.

## 운영 체제 설치


> [!IMPORTANT]
> Lync Server 2013은 64비트 버전에서만 사용 가능하므로, Windows Server 운영 체제의 64비트 버전 및 64비트 하드웨어가 필요합니다. 이번 릴리스에서는 32비트 버전 Lync Server 2013을 사용할 수 없습니다.



Standard Edition 및 Enterprise Edition 서버는 다음 중 하나를 사용할 수 있습니다.

  - Windows Server 2008 R2 SP1 또는 최신 서비스 팩

  - Windows Server 2012

  - Windows Server 2012 R2

Standard Edition 서버 또는 Enterprise Edition 프런트 엔드 서버에 운영 체제 소프트웨어를 설치합니다. 운영 체제를 최신 업데이트 상태 및 조직 표준에 맞는 필수 업데이트 수준으로 유지하는 데 필요한 모든 업데이트를 적용합니다. 운영 체제에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)을 참고하세요.


> [!NOTE]
> Lync Server 2013이 Windows Server 2012 R2에서 작동하려면 Windows Server에서 레지스트리 키 값을 변경해야 할 수 있습니다. 이러한 변경 작업은 인증서가 올바르게 작동하고 클라이언트가 SBA(Survivable Branch Appliance)에 등록하는 데 필요할 수 있습니다. 자세한 내용은 <A class=uri href="http://support.microsoft.com/kb/2901554">http://support.microsoft.com/kb/2901554</A>를 참고하세요.



## Lync Server 2013용 추가 소프트웨어

운영 체제에 필요한 업데이트 외에도 Lync Server 2013을 작동하려면 운영 체제 역할, 기능 및 소프트웨어가 필요합니다. 토폴로지를 게시하고 Lync Server 2013을 설치하기 전에 설치해야 하는 추가 소프트웨어에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013에 대한 추가 소프트웨어 요구 사항](lync-server-2013-additional-software-requirements.md)을 참고하세요.

## 모든 서버 역할에 필요한 추가 소프트웨어

모든 서버 역할에서 Windows PowerShell 명령줄 인터페이스 3.0 및 Microsoft .NET Framework 4.5가 설치되었는지도 확인해야 합니다.

또한 Lync Server 관리 도구를 실행하는 모든 컴퓨터에 Windows PowerShell 명령줄 인터페이스 3.0 및 Microsoft .NET Framework 4.5가 필요합니다.

## Windows PowerShell 3.0

Lync Server 2013을 사용하려면 Lync Server 토폴로지에 포함되는 모든 컴퓨터에 Windows PowerShell 3.0을 설치해야 합니다. Windows PowerShell 3.0 설치에 대한 자세한 내용은 [Lync Server 2013용 Windows PowerShell 3.0 설치](lync-server-2013-installing-windows-powershell-3-0.md)를 참고하세요.


> [!NOTE]
> Windows Server&nbsp;2008&nbsp;R2 SP1에서는 Microsoft .NET Framework 4.5를 설치하기 전에 Windows PowerShell 명령줄 인터페이스 3.0을 설치할 수 없습니다.



## Microsoft .NET Framework 4.5

Windows Server 2012 또는 Windows Server 2012 R2에서 Lync Server 2013을 실행하는 서버에 Microsoft .NET Framework 4.5를 설치할 때는 추가 단계를 하나 더 수행해야 합니다. .NET Framework 4.5를 설치한 후 서버 관리자를 사용해서 HTTP 활성화를 설치해야 합니다.

**.NET 4.5 HTTP 활성화를 Windows Server 2012 또는 Windows Server 2012 R2에 설치하려면 다음을 수행합니다.**

1.  **시작** 메뉴에서 **프로그램** , **관리 도구** 를 차례로 클릭한 후 **서버 관리자** 를 클릭합니다.

2.  서버 관리자의 **기능 요약** 에서 **기능 추가** 를 선택합니다.

3.  **.NET Framework 4.5** 를 확장합니다.

4.  아직 선택하지 않았으면 **WCF 활성화** 를 선택한 후 **HTTP 활성화** 를 선택합니다.

5.  **다음** 을 클릭하고 프롬프트에 따라 설치를 완료합니다.

