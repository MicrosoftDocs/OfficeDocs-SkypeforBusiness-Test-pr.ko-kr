---
title: 'Lync Server 2013: Lync Server 관리 도구'
TOCTitle: Lync Server 관리 도구
ms:assetid: 9b006f93-4f3d-461d-89b8-e80a34fdb3c5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg195756(v=OCS.15)
ms:contentKeyID: 49304500
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 관리 도구

 

_**마지막으로 수정된 항목:** 2013-02-21_

이 항목에서는 Lync Server 2013의 관리 도구에 대해 설명합니다.

관리 도구는 기본적으로 각 Lync Server 서버에 설치됩니다. 또한 전용 관리 콘솔과 같은 다른 컴퓨터에 관리 도구를 설치할 수도 있습니다. 관리 도구 설치 절차는 [Lync Server 2013 관리 도구 설치](lync-server-2013-install-lync-server-administrative-tools.md)를 참조하십시오. 관리 작업 수행을 위한 도구 열기 절차는 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오.

Lync Server 관리 도구를 설치하거나 사용하기 전에 인프라, 운영 체제, 소프트웨어 및 관리자 권한 요구 사항을 검토하십시오. 인프라 요구 사항에 대한 자세한 내용은 [Lync Server 2013의 관리 도구 인프라 요구 사항](lync-server-2013-administrative-tools-infrastructure-requirements.md)을 참조하십시오. Lync Server 관리 도구를 설치하기 위한 운영 체제 및 소프트웨어 요구 사항에 대한 자세한 내용은 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md), [Lync Server 2013에 대한 추가 소프트웨어 요구 사항](lync-server-2013-additional-software-requirements.md) 및 [Lync Server 2013의 추가 서버 지원 및 요구 사항](lync-server-2013-additional-server-support-and-requirements.md)을 참조하십시오. 도구 설치 및 사용을 위해 필요한 사용자 권한에 대한 자세한 내용은 [Lync Server 2013의 설정 및 관리에 필요한 관리자 권한](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md)을 참조하십시오.

관리 도구는 다음 항목으로 구성됩니다.

  - **Lync Server 배포 마법사**    Lync Server을 배포하고 모든 관리 도구를 설치하는 데 사용됩니다.

  - **Lync Server토폴로지 작성기**   배포에서 구성 요소를 정의하는 데 사용됩니다.

  - **Lync Server 제어판**   웹 기반 인터페이스를 사용하여 배포를 지속적으로 관리하는 데 사용됩니다.

  - **Lync Server 관리 셸**   명령줄을 사용하여 배포를 지속적으로 관리하는 데 사용됩니다.

  - **Lync Server 로깅 도구**   배포 문제를 해결하는 데 사용됩니다.

  - **중앙 로깅 서비스**   단일 컴퓨터, 풀, 사이트에서 또는 전역적으로 로그 및 추적 파일을 수집합니다. 공급자, 플래그 및 추적 수준을 포함하는 시나리오를 선택하여 정의하십시오. 텍스트 기반 도구나 Snooper.exe와 같은 도구를 통해 로깅이 수집, 집계 및 표시됩니다.

주로 토폴로지 작성기 및 Lync Server 제어판을 사용하여 배포를 관리할 수 있습니다.

## 배포 마법사

아직 Lync Server를 설치하지 않은 컴퓨터에 모든 관리 도구를 설치하려면 설치 미디어에 포함된 Lync Server 배포 마법사를 사용해야 합니다. 관리 도구를 설치하는 중에는 나중에 추가 구성 요소를 위한 파일을 설치할 때 사용하거나 컴퓨터에서 사용할 필요가 없는 구성 요소의 파일을 제거할 수 있도록 Lync Server 배포 마법사가 다른 도구와 함께 설치됩니다.

Lync Server 설치 미디어에서 Lync Server 배포 마법사를 처음 실행하는 방법에 대한 자세한 내용은 [Lync Server 2013 관리 도구 설치](lync-server-2013-install-lync-server-administrative-tools.md)를 참조하십시오.

## 토폴로지 작성기

토폴로지 작성기를 사용하여 수행할 수 있는 배포 작업에 대한 자세한 내용은 각 서버 역할에 대한 배포 설명서를 참조하십시오.

## Lync Server 제어판

Lync Server 2013 제어판을 사용하여 Lync Server 2013을 관리하고 유지하는 데 필요한 대부분의 관리 작업을 수행할 수 있습니다. Lync Server 제어판에서는 조직의 사용자, 클라이언트 및 장치 외에도 Lync Server을 실행하는 서버의 구성을 관리하기 위한 GUI(그래픽 사용자 인터페이스)를 제공합니다. Lync Server 관리 셸은 Lync Server 제어판을 기본 메커니즘으로 사용하여 Lync Server 구성을 수행합니다.

Lync Server 제어판은 모든 Lync Server 프런트 엔드 서버 또는 Standard Edition Server에 자동으로 설치됩니다. 이번 릴리스에서는 에지 서버를 원격으로 관리합니다. 또한 Lync Server를 중앙에서 관리하기 위한 관리 콘솔을 비롯한 다른 컴퓨터에 Lync Server 제어판을 설치할 수 있습니다. 자세한 내용은 [Lync Server 2013 관리 도구 설치](lync-server-2013-install-lync-server-administrative-tools.md)를 참조하십시오.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>Lync Server 제어판을 사용하여 설정을 구성하려면 CsAdministrator 역할에 할당된 계정을 사용하여 로그인해야 합니다. Lync Server 2013에서 사용 가능한 미리 정의된 관리 역할에 대한 자세한 내용은 <A href="lync-server-2013-planning-for-role-based-access-control.md">Lync Server 2013의 역할 기반 액세스 제어 계획</A>을 참조하세요.</P>
> <LI>
> <P>또한 Lync Server 제어판을 사용하여 설정을 구성하려면 최소 화면 해상도가 1024 x 768인 컴퓨터를 사용해야 합니다.</P></LI></UL>



## Lync Server 관리 셸

Lync Server에서 Lync Server 관리 셸은 새로운 관리 방법을 제공합니다. Lync Server 관리 셸은 Windows PowerShell 명령줄 인터페이스를 기반으로 하는 강력한 관리 인터페이스로서, Lync Server에 특정한 포괄적인 cmdlet 집합을 제공합니다. Lync Server 관리 셸에는 다양한 구성 및 자동화 컨트롤이 있습니다. 토폴로지 작성기와 Lync Server 제어판 둘 다 이러한 cmdlet의 하위 집합을 구현하여 Lync Server 관리를 지원합니다. Lync Server 관리 셸에는 모든 Lync Server 관리 작업에 대한 cmdlet이 있으며, 각 cmdlet을 개별적으로 사용하여 배포를 관리할 수 있습니다. 자세한 내용은 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md) 설명서 또는 각 cmdlet에 대한 명령줄 도움말을 참조하십시오.

## 로깅 도구

Lync Server 로깅 도구를 사용하면 제품을 실행하는 동안 제품에서 로깅 및 추적 정보를 캡처하여 문제 해결을 지원할 수 있습니다. 이 도구를 사용하여 모든 Lync Server 서버 역할에서 디버그 세션을 실행할 수 있습니다. 로깅 도구에 대한 자세한 내용은 TechNet 라이브러리의 Lync Server 2010 로깅 도구 설명서( <http://go.microsoft.com/fwlink/?linkid=199265>)를 참조하십시오.


> [!IMPORTANT]
> 어떠한 상황에서든 모든 로깅 수집을 수행할 때는 Lync Server 로깅 도구보다 중앙 로깅 서비스를 사용하는 것이 좋습니다. Lync Server 로깅 도구도 계속 작동하기는 하지만 중앙 로깅 서비스가 이미 실행 중이면 해당 실행을 방해하거나 효율성이 저하될 가능성이 큽니다. 중앙 로깅 서비스 또는 Lync Server 로깅 도구 중 하나만 사용해야 하며 두 항목을 동시에 사용해서는 안 됩니다. 중앙 로깅 서비스에 대한 자세한 내용과 이 서비스를 단독으로 사용해야 하는 이유는 <A href="lync-server-2013-using-the-centralized-logging-service.md">중앙화된 로깅 서비스 사용</A>을 참조하십시오.



## 이 섹션의 내용

  - [Lync Server 2013의 관리 도구 인프라 요구 사항](lync-server-2013-administrative-tools-infrastructure-requirements.md)

  - [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)

  - [Lync Server 2013의 관리 도구 소프트웨어 요구 사항](lync-server-2013-administrative-tools-software-requirements.md)

  - [Lync Server 2013의 설정 및 관리에 필요한 관리자 권한](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md)

  - [Lync Server 2013의 토폴로지 게시 요구 사항](lync-server-2013-requirements-to-publish-a-topology.md)

  - [Lync Server 2013 관리 도구 설치](lync-server-2013-install-lync-server-administrative-tools.md)

  - [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)

  - [Lync Server 2013 제어판 문제 해결](lync-server-2013-troubleshooting-lync-server-2013-control-panel.md)

  - [중앙화된 로깅 서비스 사용](lync-server-2013-using-the-centralized-logging-service.md)

## 참고 항목

#### 기타 리소스

[Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md)

