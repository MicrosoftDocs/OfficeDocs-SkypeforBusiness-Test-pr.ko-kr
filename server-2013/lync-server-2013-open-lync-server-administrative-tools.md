---
title: Lync Server 관리 도구 열기
TOCTitle: Lync Server 관리 도구 열기
ms:assetid: 8c58de94-9e0a-4368-9e14-9afcaa1142d0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg195741(v=OCS.15)
ms:contentKeyID: 49304320
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 관리 도구 열기

 

_**마지막으로 수정된 항목:** 2012-06-28_

이 항목의 절차에 따라 관리 도구를 열어서 Lync Server 2013 토폴로지를 배포, 구성 및 문제 해결할 수 있습니다.

  - 배포 마법사

  - 토폴로지 작성기

  - Lync Server 제어판

  - Lync Server 관리 셸

## 배포 마법사

다음 절차에 따라 배포 마법사를 로컬로 시작하여 Lync Server 2013 구성 요소 파일을 추가하거나 제거합니다.

## Lync Server 2013 배포 마법사를 시작하려면

1.  Lync Server Deployment Wizard가 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원으로 설치되어 있는 컴퓨터에 로그온합니다.

2.  **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 후 **Lync Server 배포 마법사**를 클릭합니다.

## 토폴로지 작성기

다음 절차를 사용하여 토폴로지 작성기를 열어서 Lync Server 2013 토폴로지에 배포하려는 서버를 정의합니다.

## Lync Server 2013 토폴로지 작성기를 열어서 토폴로지를 디자인하려면

1.  토폴로지 작성기가 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원으로 설치되어 있는 컴퓨터에 로그온합니다.
    

    > [!NOTE]
    > 로컬 Users 그룹의 구성원 계정을 사용하여 토폴로지를 정의할 수 있지만 서버에 Lync Server 2013을 설치하는 데 필요한 토폴로지를 읽거나 게시하거나 사용하도록 설정하려면 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원이고 토폴로지 작성기에서 필요한 DACL(임의 액세스 제어 목록)을 구성할 수 있도록 보관 파일 저장소에 사용할 파일 공유에 대한 모든 권한(즉, 읽기, 쓰기 및 수정)이 있는 계정 또는 이와 동등한 권한이 있는 계정을 사용해야 합니다.



2.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.

## Lync Server 2013 제어판

다음 절차 중 하나를 사용하여 Lync Server 2013 제어판을 열어서 사용자 환경의 서버, 사용자, 클라이언트 및 장치 구성을 관리합니다.


> [!NOTE]
> CsAdministrator 역할에 지정된 사용자 계정을 사용하면 Lync Server 2013 제어판에서 모든 작업을 수행할 수 있습니다. 수행해야 하는 작업에 따라 다른 역할을 사용하여 Lync Server 2013 제어판에 로그온하여 특정 관리 작업을 수행할 수 있습니다. 예를 들어 CSArchivingAdministrator를 사용하여 Lync Server 2013 제어판에서 보관을 관리할 수 있습니다. 역할에 대한 자세한 내용은 계획 설명서의 <A href="lync-server-2013-planning-for-role-based-access-control.md">Lync Server 2013의 역할 기반 액세스 제어 계획</A>를 참조하십시오. 특정 작업을 수행하기 위해 사용할 수 있는 역할에 대한 자세한 내용은 해당 작업에 대한 설명서를 참조하십시오.



## 조직의 방화벽 내의 컴퓨터에서 Lync Server 2013 제어판을 열려면

1.  CsAdministrator 역할 또는 수행할 작업에 적절한 사용자 권한이 있는 다른 역할에 지정된 사용자 계정에서 최소 화면 해상도 1024 x 768을 사용해서 내부 배포의 임의 컴퓨터에 로그온합니다.
    

    > [!IMPORTANT]
    > 관리 단순 URL(Uniform Resource Locator)을 구성한 경우 조직 방화벽 내의 컴퓨터에서 실행되는 인터넷 브라우저를 통해 Lync Server 2013 제어판에 액세스할 수 있습니다. 관리 단순 URL 구성에 대한 자세한 내용은 계획 설명서의 <A href="lync-server-2013-planning-for-simple-urls.md">Lync Server 2013의 단순 URL 계획</A> 및 배포 설명서의 <A href="lync-server-2013-edit-or-configure-simple-urls.md">Lync Server 2013에서 단순 URL 편집 또는 구성</A>을 참조하십시오.



2.  브라우저 창을 열고 조직에 구성된 관리 URL을 입력합니다.

## Lync Server 2013 실행 컴퓨터에서 Lync Server 2013 제어판을 열려면

1.  CsAdministrator 역할 또는 수행할 작업에 대해 적합한 사용자 권한이 있는 다른 역할의 구성원인 사용자 계정을 사용하여 Lync Server 2013 또는 최소한 Lync Server 2013 관리 도구가 설치된 컴퓨터에 로그온합니다. 설정을 구성하려면 컴퓨터의 최소 화면 해상도가 1024 x 768이어야 합니다.

2.  Lync Server 2013 제어판 시작: **시작**, **모든 프로그램**을 차례로 클릭하고 **관리 도구**, **Microsoft Lync Server 2013**을 차례로 가리킨 후 **Lync Server 2013 제어판**을 클릭합니다.

## Lync Server 2013 관리 셸

다음 절차를 사용하여 Lync Server 2013 관리 셸을 열어서 명령줄을 통해 환경에서 서버, 사용자, 클라이언트 및 장치를 관리합니다.


> [!NOTE]
> CsAdministrator 역할에 지정된 사용자 계정을 사용하면 Lync Server 2013 관리 셸에서 모든 작업을 수행할 수 있습니다. 수행해야 하는 작업에 따라 다른 역할을 사용하여 로그온해서 특정 관리 작업을 수행할 수 있습니다. 예를 들어 CSArchivingAdministrator를 사용하여 보관 관리와 관련된 cmdlet을 실행할 수 있습니다. 역할에 대한 자세한 내용은 계획 설명서의 <A href="lync-server-2013-planning-for-role-based-access-control.md">Lync Server 2013의 역할 기반 액세스 제어 계획</A>를 참조하십시오. 특정 cmdlet을 실행하기 위해 사용할 수 있는 역할에 대한 자세한 내용은 해당 cmdlet에 대한 설명서를 참조하십시오.<BR>또한 cmdlet에 따라 RTCUniversalServerAdmins, RTCUniversalUserAdmins 또는 RTCUniversalReadOnlyAdmins 그룹의 사용자 계정을 사용하여 특정 cmdlet을 실행할 수도 있습니다.



## Lync Server 2013 관리 셸을 열려면

  - Lync Server 2013 관리 셸을 열지 않고 Windows PowerShell 창을 열 경우 기본적으로 Lync Server 2013 cmdlet을 실행할 수 없습니다. Windows PowerShell 내에서 Lync Server 2013을 실행하려면 Windows PowerShell 명령 프롬프트에 다음을 입력합니다.
    
    `Import-Module Lync`

  - Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

## 참고 항목

#### 작업

[Lync Server 2013 관리 도구 설치](lync-server-2013-install-lync-server-administrative-tools.md)  

#### 개념

[Lync Server 2013 관리 도구](lync-server-2013-lync-server-administrative-tools.md)

