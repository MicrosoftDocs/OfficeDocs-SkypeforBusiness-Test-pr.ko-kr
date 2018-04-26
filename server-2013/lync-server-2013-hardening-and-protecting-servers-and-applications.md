---
title: 'Lync Server 2013: 서버 및 응용 프로그램 강화 및 보호'
TOCTitle: Lync Server 2013에 대한 서버 및 응용 프로그램 강화 및 보호
ms:assetid: 9ca2b233-26f1-4d72-96e7-81a82c727806
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn518331(v=OCS.15)
ms:contentKeyID: 60504741
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 서버 및 응용 프로그램 강화 및 보호

 

_**마지막으로 수정된 항목:** 2013-12-05_

특정 구성 요소에 대해 권장되는 사용 방법에 따라 운영 체제 및 응용 프로그램을 강화하고 보호해야 합니다. 이 섹션에서는 응용 프로그램 서버를 강화하고 그룹 정책을 사용하여 보안 잠금을 구현하는 방법에 대해 설명합니다.


> [!NOTE]
> 또한 Microsoft Lync Server 2013 배포에 대해 사용된 데이터베이스를 강화하고 보호할 수도 있습니다. 자세한 내용은 <A href="lync-server-2013-hardening-and-protecting-databases.md">Lync Server 2013의 데이터베이스 강화 및 보호</A>를 참조하세요.



## 응용 프로그램 서버 보호

응용 프로그램 서버의 경우에는 운영 체제와 응용 프로그램을 강화해야 합니다. 예를 들어 Microsoft Internet Security and Acceleration (ISA) Server 2008 실행 전용 Windows Server 2003 컴퓨터는 운영 체제와 응용 프로그램 측면을 강화해야 합니다. 궁극적으로는 서버에서 제공되는 실행 서비스 수를 최소화해야 합니다.

## 가상 서버 보호

가상 서버 스냅숏에는 서버의 데이터 디스크 복사본이 포함되며 메모리 내 데이터의 덤프도 포함됩니다. 이러한 두 데이터는 공격으로 이어질 수 있는 민감한 암호화 데이터가 포함될 수 있습니다. 가상화를 사용하여 구현된 프로덕션 서버의 경우 모든 서버 스냅숏을 비활성화하고 이를 매우 제한된 방식으로 관리해야 합니다. Hyper-V 가상 서버 보호에 대한 자세한 내용은 Hyper-V 보안 설명서([http://go.microsoft.com/fwlink/p/?LinkId=214176](http://go.microsoft.com/fwlink/p/?linkid=214176))를 참조하세요.

## 그룹 정책

Windows Server 2008 및 Windows Server 2008 R2에서 그룹 정책은 디렉터리 기반 데스크톱 구성 관리를 제공합니다. 그룹 정책을 사용하여 다음 항목에 대해 GPO(그룹 정책 개체) 내에서 컴퓨터 및 사용자 설정을 정의함으로써 보안 잠금을 구현할 수 있습니다.

  - 레지스트리 기반 정책

  - 보안

  - 소프트웨어 설치

  - 스크립트

  - 폴더 리디렉션

  - 원격 설치 서비스

관리자가 이러한 설정을 구성하는 데 사용하는 사용자 인터페이스를 제공하기 위해 운영 체제 버전, 서비스 팩 버전 및 Lync Server 2013을 비롯한 일부 응용 프로그램에는 관리 템플릿이 포함되어 있습니다.

Lync Server 2013과 함께 제공되는 관리 템플릿인 Communicator.adm 파일은 *%windir%*\\inf\\ 디렉터리에 설치되며, 그룹 정책 설정에 대한 인터페이스를 제공합니다. Communicator.adm의 각 설정은 응용 프로그램 동작에 영향을 주는 레지스트리의 설정에 해당합니다.

이러한 설정은 GPedit.dll에서 액세스할 수 있으며, 이 파일은 Active Directory 사용자 및 컴퓨터 콘솔과 GPMC(그룹 정책 관리 콘솔)에서 제공됩니다.

## 그룹 정책 보안 설정

그룹 정책에는 GPedit.dll에서 액세스한 경우 컴퓨터 구성/Windows 설정/보안 설정 아래에 GPO에 대한 보안 설정이 포함되어 있습니다. 보안 템플릿을 가져와 GPO에 대한 보안 설정을 구성할 수 있습니다. Windows Server 2008 보안 설명서([http://go.microsoft.com/fwlink/p/?LinkId=145186](http://go.microsoft.com/fwlink/p/?linkid=145186)) 및 Windows Server 2008 R2 보안 준수 관리 툴킷([http://go.microsoft.com/fwlink/p/?LinkId=211882](http://go.microsoft.com/fwlink/p/?linkid=211882))에는 사용자의 요구를 충족하기 위해 수정할 수 있는 여러 예제 템플릿이 포함되어 있습니다.

## 유용한 정보

  - 모든 서버 운영 체제 및 응용 프로그램을 강화합니다.

  - 서버 스냅숏을 보호하고 모든 가상 서버의 보안을 향상시킵니다.

  - 그룹 정책을 사용하여 보안 잠금을 구현합니다.

