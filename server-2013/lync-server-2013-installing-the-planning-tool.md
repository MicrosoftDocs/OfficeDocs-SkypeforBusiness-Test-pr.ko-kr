---
title: 'Lync Server 2013: 계획 도구 설치'
TOCTitle: 계획 도구 설치
ms:assetid: ebdc9e26-4b22-4b02-85b9-7462bcfe7c93
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615046(v=OCS.15)
ms:contentKeyID: 52056986
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 계획 도구 설치

 

_**마지막으로 수정된 항목:** 2013-11-07_

Microsoft Lync Server 2013, 계획 도구를 사용하여 Lync Server 2013 인프라를 설계 및 계획하려면 먼저 계획 도구를 설치해야 합니다. 계획 도구는 Lync Server 2013을 설치할 도메인이나 인프라에 속한 워크스테이션이나 서버에 배포하지 않아도 됩니다. 계획 도구와 함께 제공되는 추가 정보 파일에 도구를 설치하고 사용하는 방법에 대한 중요한 정보가 나와 있습니다. 추가 정보 파일의 내용 중 일부는 여기에도 반복되어 설명됩니다.


> [!IMPORTANT]
> 계획 도구는 도구가 설치될 컴퓨터의 관리자 권한 및 사용 권한을 가진 사용자가 설치해야 합니다.



계획 도구를 설치하고 작업할 수 있는 운영 체제는 다음과 같습니다.

  - Windows 8

  - Windows 8.1

  - Windows Server 2012

  - Windows Server 2012 R2

  - Windows 7, 32비트 버전

  - WOW(Windows on Win32)를 사용하는 Windows 7, 64비트 버전

  - WOW를 사용하는 Windows Server 2008 R2

또한 계획 도구를 설치하려면 Microsoft .NET Framework 4.5가 필요합니다.

사전 설치 요구 사항이 충족되면 계획 도구를 설치할 수 있습니다.

## 계획 도구를 설치하려면

1.  Administrators 그룹의 구성원으로 로컬 컴퓨터에 로그온합니다.

2.  Windows 탐색기나 명령 창을 사용하여 계획 도구 설치 파일을 다운로드한 디렉터리를 찾습니다.

3.  LyncPlanningTool.msi를 찾습니다. Windows 탐색기에서 파일을 두 번 클릭합니다. 명령 창에 파일의 이름을 입력한 후 **Enter** 키를 눌러 파일을 실행합니다.

4.  **Microsoft Lync Server 2013, 계획 도구 설치 마법사** 시작 페이지에서 **다음** 을 클릭합니다.

5.  **최종 사용자 사용권 계약** 을 검토하고 사용권 계약의 사용 약관에 동의하면 **동의함** 을 선택하고 **다음** 을 클릭합니다.

6.  계획 도구 파일을 설치할 위치를 선택합니다. 기본 위치는 C:\\Program Files (x86)\\Microsoft Lync Server 2013\\Planning Tool입니다. 설치 위치를 변경하려면 **변경** 을 클릭합니다. **대상 폴더 변경** 에서 파일을 설치할 위치를 찾거나 입력한 다음 **확인** , **다음** 을 차례로 클릭합니다.

7.  계획 도구를 설치할 준비가 되었습니다. **설치** 를 클릭하여 설치 프로세스를 시작합니다.

8.  설치가 시작되고 진행 상태가 표시됩니다. 설치가 완료되면 **마침** 을 클릭합니다.

9.  계획 도구를 사용할 준비가 되었습니다.

## 참고 항목

#### 개념

[Lync Server 2013에서 선택적 소프트웨어 설치](lync-server-2013-installing-optional-software.md)

