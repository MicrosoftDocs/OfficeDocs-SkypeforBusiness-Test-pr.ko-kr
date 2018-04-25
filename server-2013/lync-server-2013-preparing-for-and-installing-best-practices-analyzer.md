---
title: 모범 사례 분석기 준비 및 설치
TOCTitle: 모범 사례 분석기 준비 및 설치
ms:assetid: 550613dd-dc08-482e-9980-a3fe187cd162
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg591347(v=OCS.15)
ms:contentKeyID: 49303664
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모범 사례 분석기 준비 및 설치

 

_**마지막으로 수정된 항목:** 2013-11-07_

이 항목에 설명된 작업을 수행하려면 Administrators 그룹 구성원으로 로그온해야 합니다.

## 모범 사례 분석기 설치를 위한 시스템 요구 사항

Lync Server 2013 모범 사례 분석기를 실행해서 환경을 검색하려면 컴퓨터에서 다음 운영 체제 중 하나의 64비트 버전을 실행해야 합니다.

  - Windows Server 2008 R2 SP1(서비스 팩 1) Standard 운영 체제

  - Windows Server 2008 R2 SP1 Enterprise 운영 체제

  - Windows Server 2008 R2 SP1 Datacenter 운영 체제

  - Windows Server 2012 Datacenter 운영 체제

  - Windows Server 2012 Standard 운영 체제

  - Windows Server 2012 Enterprise 운영 체제

  - Windows Server 2012 R2 Datacenter 운영 체제

  - Windows Server 2012 R2 Standard 운영 체제

  - Windows Server 2012 R2 Enterprise 운영 체제

  - Windows 8 운영 체제

  - Windows 7 운영 체제

또한 컴퓨터에서 다음을 실행해야 합니다.

  - Microsoft .NET Framework 4.5. Lync Server 2013의 경우 Lync Server 2013을 설치하기 전에 서버에 Microsoft .NET Framework 4.5의 64비트 버전을 수동으로 설치해야 합니다.

  - Lync Server 2013, 핵심 구성 요소

  - WMI 이전 버전과의 호환성 패키지. 자세한 내용은 마이그레이션 설명서에서 [WMI 이전 버전과의 호환성 패키지 설치](install-wmi-backward-compatibility-package.md)를 참조하십시오.

  - Windows PowerShell 3.0. 자세한 내용은 배포 설명서에서 [Lync Server 2013용 Windows PowerShell 3.0 설치](lync-server-2013-installing-windows-powershell-3-0.md)를 참조하십시오.

지원되는 운영 체제가 포함되었지만 Lync Server 2013, 핵심 구성 요소 또는 WMI 이전 버전과의 호환성 패키지를 실행하지 않는 컴퓨터에 모범 사례 분석기를 설치할 수 있지만 이러한 컴퓨터에서는 모범 사례 분석기를 사용해서 보고서만 볼 수 있으며, 검색을 실행할 수 없습니다.

## 설치할 컴퓨터 선택

Lync Server 2013 관리 전용의 컴퓨터에 Lync Server 2013 모범 사례 분석기를 설치하는 것이 좋습니다. 이 도구는 Lync Server 2013 실행 서버 또는 Lync Server 2013 관리 도구를 실행하는 관리 컴퓨터에 설치할 수 있습니다. Lync Server를 실행하는 서버에 이 도구를 설치할 경우에는 이 도구를 사용하여 해당 서버만 검색하는 것이 좋습니다.

## 모범 사례 분석기 설치

Lync Server 2013용 모범 사례 분석기는 [http://go.microsoft.com/fwlink/?linkid=266539\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=266539%26clcid=0x412).

모범 사례 분석기를 설치하려면 도구를 설치하려는 컴퓨터에서 Microsoft Installer 파일 RtcBPA.msi를 시작하고 화면 지침을 따릅니다. 프로그램 파일을 설치하기 위한 기본 위치는 *\<system drive\>*\\Program Files\\Lync Server 2013\\BPA입니다.

