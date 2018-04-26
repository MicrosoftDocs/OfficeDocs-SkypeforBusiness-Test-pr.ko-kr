---
title: Lync 클라이언트 배포
TOCTitle: Lync 클라이언트 배포
ms:assetid: 3d10abf2-d484-4fa0-8f10-4a5f9dfba4f5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204827(v=OCS.15)
ms:contentKeyID: 49303380
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 클라이언트 배포

 

_**마지막으로 수정된 항목:** 2012-10-03_

Lync 2013은 클라이언트 배포에 대한 다른 접근 방법을 소개합니다. 이전 릴리스와 달리 Lync 2013은 더 이상 고유 설치 프로그램을 갖고 있지 않습니다. 대신 Lync가 Office 2013 설치 프로그램에 포함됩니다. Lync 2013을 사용자에게 배포하려면 Office 2013 설치 방법과 사용자 지정 도구를 사용할 수 있습니다.

  - **Office 2013 Windows Installer**는 여러 개의 MSI 파일로 구성된 Windows Installer 기반의 설치 패키지입니다. 언어 중립적인 핵심 MSI 패키지는 완벽한 제품 구성을 위해 하나 이상의 언어별 패키지로 조합됩니다. 설치 프로그램은 개별 패키지를 조합하고 사용자 컴퓨터에 Office를 설치하는 동안 그리고 설치 후에 사용자 지정 및 유지 관리 작업을 수행합니다. 이 섹션의 항목에서는 Lync 2013 배포를 위해 Office 2013 Windows Installer를 사용하고 사용자 지정하는 방법에 대해 설명합니다.

  - **Office 2013 간편 실행**은 Microsoft Office 365 포털에서 Office 설치 파일을 사용자에게 스트리밍하는 설치 프로그램입니다. 관리자는 간편 실행을 위한 Office 배포 도구를 사용하여 설치를 사용자 지정할 수 있습니다. Office 2013 간편 실행은 주로 Microsoft Office 365 환경에서 사용되기 때문에 이 설치 방법은 이 섹션에서 자세히 설명하지 않습니다. 간편 실행 설치 사용 및 사용자 지정에 대한 자세한 내용은 Office 2013 리소스 키트 설명서에서 제공됩니다. 또한 관리자가 Office 2013 간편 실행 프로그램과 언어 소스 파일을 온-프레미스 위치에 다운로드할 수 있으므로 네트워크에 대한 요구를 최소화하거나 기업 보안 요구 사항으로 인해 사용자가 인터넷에서 소프트웨어를 설치할 수 없도록 방지하려는 경우에 도움이 될 수 있습니다.

이 섹션의 항목에서는 Office 2013 MSI 기반 설치 프로그램을 사용하여 클라이언트를 배포하는 방법에 대해 설명합니다. 여기에서는 인프라 준비, 설치 사용자 지정 및 Office 2013 배포 방법에 대해 자세히 설명하는 Office 2013 리소스 키트 설명서를 주로 참조해야 합니다. 하지만 이 섹션의 항목과 함께 Office 설명서를 사용해서 Lync 2013 관련 배포 고려 사항을 확인해야 합니다.


> [!NOTE]
> <UL>
> <LI>
> <P>Outlook 메시징 및 공동 작업 클라이언트 내에서 모임 관리를 지원하는 Lync 2013용 온라인 모임 추가 기능은 Lync 2013와 함께 자동으로 설치됩니다.</P>
> <LI>
> <P>Office 2013 설치 프로그램은 이전 버전의 Lync 또는 Office Communicator를 설치하지 않습니다. Lync 2013 클라이언트는 다른 Lync 또는 Office Communicator 클라이언트와 함께 수평적으로 설치됩니다.</P></LI></UL>



## 이 섹션의 내용

  - [클라이언트 설치 사용자 지정](lync-server-2013-customizing-client-installation.md)

  - [Lync 동작 및 사용자 인터페이스 사용자 지정](lync-server-2013-customizing-lync-behavior-and-the-user-interface.md)

  - [온라인 모임 추가 기능 사용자 지정](lync-server-2013-customizing-the-online-meeting-add-in.md)

  - [Lync Server 2013에서 모임 참가 페이지 구성](lync-server-2013-configuring-the-meeting-join-page.md)

  - [지원되는 클라이언트 버전 구성](lync-server-2013-configuring-supported-client-versions.md)

  - [현재 상태 사용자 지정 개인 정보 모드 구성](lync-server-2013-configuring-enhanced-presence-privacy-mode.md)

