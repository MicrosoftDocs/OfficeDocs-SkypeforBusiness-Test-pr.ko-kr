---
title: 'Lync Server 2013: 관리 도구 소프트웨어 요구 사항'
TOCTitle: 관리 도구 소프트웨어 요구 사항
ms:assetid: 2fb172c3-7b84-4e49-981c-2a17e7a00a29
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg195653(v=OCS.15)
ms:contentKeyID: 49303202
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 관리 도구 소프트웨어 요구 사항

 

_**마지막으로 수정된 항목:** 2013-11-07_

이 항목에서는 운영 체제 요구 사항 외에도 Lync Server 2013 관리 도구를 설치 및 사용하기 위해 필요한 소프트웨어에 대해 설명합니다.

## Microsoft .NET Framework 4.5

Lync Server 2013에는 64비트 버전의 Microsoft .NET Framework 4.5가 필요합니다.

## Windows PowerShell 3.0

Microsoft Lync Server 2013 구성 요소를 실행하려면 Windows PowerShell 3.0이 필요합니다. 자세한 내용은 [Lync Server 2013용 Windows PowerShell 3.0 설치](lync-server-2013-installing-windows-powershell-3-0.md)를 참조하십시오.

## Windows Installer 버전 4.5

Lync Server 2013에서는 Windows Installer 기술을 사용하여 다양한 서버 역할을 설치, 제거 및 유지 관리합니다. Windows Installer 버전 4.5는 Windows Server 운영 체제의 재배포 가능 구성 요소로 사용될 수 있습니다. Windows Installer 4.5에는 Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2가 함께 제공되므로 Lync Server 2013을 실행하는 컴퓨터에 유틸리티를 다운로드하지 않아도 됩니다. Lync Server 2013은 Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2를 실행하는 컴퓨터에만 설치할 수 있습니다.)

관리자 워크스테이션에 Lync Server 관리 셸 또는 Lync Server 토폴로지 작성기를 설치하려는 경우 Windows Installer 4.5를 다운로드해야 할 수 있습니다. 해당 유틸리티는 Windows 7 및 Windows 2008 R2와 함께 제공되지만 이전 버전의 Windows 운영 체제와 함께 제공되지는 않습니다. Microsoft 다운로드 센터( [http://go.microsoft.com/fwlink/?linkid=197395\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=197395%26clcid=0x412))에서 Windows Installer 4.5를 다운로드할 수 있습니다.

## Microsoft Silverlight 5 브라우저 플러그 인

Lync Server 2013 제어판은 웹 기반 도구이며 이 도구를 사용하려면 Microsoft Silverlight 5 브라우저 플러그 인의 최신 버전을 설치해야 합니다. Lync Server 2013 제어판을 시작할 때 이 소프트웨어가 설치되어 있지 않거나 이전 버전이 설치되어 있으면 Lync Server 2013 제어판에서 필요한 버전을 설치하라는 메시지가 표시됩니다.

## 참고 항목

#### 개념

[Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)  

#### 기타 리소스

[Lync Server 2013의 관리 도구 인프라 요구 사항](lync-server-2013-administrative-tools-infrastructure-requirements.md)  
[Lync Server 2013의 설정 및 관리에 필요한 관리자 권한](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md)

