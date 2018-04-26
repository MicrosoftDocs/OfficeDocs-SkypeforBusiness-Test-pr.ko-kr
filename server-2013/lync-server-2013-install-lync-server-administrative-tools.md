---
title: 'Lync Server 2013: Lync Server 관리 도구 설치'
TOCTitle: Lync Server 관리 도구 설치
ms:assetid: 842b85e4-2eeb-464f-b1c1-ceb8cc04f8d5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398665(v=OCS.15)
ms:contentKeyID: 49304239
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 관리 도구 설치

 

_**마지막으로 수정된 항목:** 2013-02-21_

이 항목에서는 Lync Server 2013을 배포 및 관리하기 위해 사용해야 하는 관리 도구를 설치하는 방법을 설명합니다. 관리 도구는 기본적으로 Lync Server 2013을 실행하는 각 서버에 설치됩니다. 또한 전용 관리 콘솔과 같은 다른 컴퓨터에 관리 도구를 설치할 수도 있습니다. 관리 도구는 Lync Server 2013 배포와 동일한 도메인 또는 포리스트에 있는 컴퓨터에 설치하는 것이 좋습니다. 이렇게 할 경우 Active Directory 도메인 서비스 준비 단계가 이미 완료되어 해당 컴퓨터에서 나중에 관리 도구를 사용하여 토폴로지를 게시할 수 있습니다.

Lync Server 2013 관리 도구를 설치하거나 사용하기 전에 인프라, 운영 체제, 소프트웨어 및 관리자 권한 요구 사항을 검토하세요. 인프라 요구 사항에 대한 자세한 내용은 [Lync Server 2013의 관리 도구 인프라 요구 사항](lync-server-2013-administrative-tools-infrastructure-requirements.md)을 참고하세요. Lync Server 2013 관리 도구를 설치하기 위한 운영 체제 및 소프트웨어 요구 사항에 대한 자세한 내용은 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md), [Lync Server 2013에 대한 추가 소프트웨어 요구 사항](lync-server-2013-additional-software-requirements.md) 및 [Lync Server 2013의 추가 서버 지원 및 요구 사항](lync-server-2013-additional-server-support-and-requirements.md)을 참고하세요. 도구 설치 및 사용을 위해 필요한 사용자 권한에 대한 자세한 내용은 [Lync Server 2013의 설정 및 관리에 필요한 관리자 권한](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md)을 참고하세요.


> [!IMPORTANT]
> 조직에서 IIS(인터넷 정보 서비스)와 모든 웹 서비스를 시스템 드라이브가 아닌 다른 드라이브에 배치해야 하는 경우 설치 프로그램 대화 상자에서 Lync Server 2013 파일의 설치 위치 경로를 변경할 수 있습니다. 설치 파일(OCSCore.msi 포함)을 이 경로에 설치하면 남은 Lync Server 2010 파일도 이 드라이브에 배포됩니다.



## Lync Server 2013 관리 도구를 설치하려면

1.  관리 도구를 설치할 컴퓨터에 로컬 관리자(최소 요구 사항)로 로그온합니다. Windows Vista 또는 Windows 7 운영 체제에서 표준 사용자로 로그온하는 경우 UAC(사용자 계정 제어)가 사용하도록 설정되어 있으면 로컬 관리자 또는 도메인의 해당 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다.

2.  컴퓨터에서 설치 미디어를 찾은 후 \\Setup\\amd64\\Setup.exe를 두 번 클릭합니다.

3.  Microsoft Visual C++ 2008 배포 가능 파일을 설치할지 묻는 메시지가 표시되면 **예** 를 클릭합니다.

4.  **Microsoft Lync Server 2013 설치 위치** 페이지에서 **확인** 을 클릭합니다. 다른 위치에 파일을 설치해야 하는 경우 이 경로를 다른 위치나 드라이브로 변경합니다.
    

    > [!IMPORTANT]
    > 조직에서 IIS(인터넷 정보 서비스) 및 모든 웹 서비스를 시스템 드라이브가 아닌 다른 드라이브에 배치해야 하는 경우 설치 프로그램 대화 상자에서 Lync Server 2013 파일의 설치 위치 경로를 변경할 수 있습니다. 설치 파일(OCSCore.msi 포함)을 이 경로에 설치하면 남은 Lync Server 2013 파일도 이 드라이브에 배포됩니다.



5.  **최종 사용자 사용권 계약** 페이지에서 사용 조건을 검토하고 **동의함** , **확인** 을 차례로 클릭합니다. 계속하려면 이 단계를 수행해야 합니다.

6.  **Microsoft Lync Server 2013 - 배포 마법사** 페이지에서 **관리자 도구 설치** 를 클릭합니다.

7.  설치가 완료되면 **끝내기** 를 클릭합니다.

## 참고 항목

#### 작업

[Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)  

#### 개념

[Lync Server 2013 관리 도구](lync-server-2013-lync-server-administrative-tools.md)

