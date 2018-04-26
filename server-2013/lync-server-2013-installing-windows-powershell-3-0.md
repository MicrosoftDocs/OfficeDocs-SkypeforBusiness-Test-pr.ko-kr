---
title: 'Lync Server 2013: Windows PowerShell 3.0 설치'
TOCTitle: Windows PowerShell 3.0 설치
ms:assetid: d87bf21e-0a43-41cb-8fdc-626cedec8538
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205328(v=OCS.15)
ms:contentKeyID: 49305201
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013용 Windows PowerShell 3.0 설치

 

_**마지막으로 수정된 항목:** 2014-06-27_

Lync Server 2013을 성공적으로 배포하려면 Lync Server 토폴로지를 구성하는 각 컴퓨터에 Windows PowerShell 3.0이 있어야 합니다.

Windows Server 2012 또는 Windows Server 2012 R2를 실행하는 시스템의 경우 PowerShell 3.0이 이러한 운영 체제에 포함되어 있기 때문에 이 작업이 필요하지 않으며 다음 배포 단계를 진행할 수 있습니다.


> [!IMPORTANT]
> Windows Server 2008 R2 SP1을 실행하는 시스템의 경우 Lync Server 2013을 설치하기 전에 필수 구성 요소로서 PowerShell 3.0을 설치해야 합니다. 그렇지 않으면 프로그램이 작동하지 않습니다. PowerShell 3.0을 설치하려면 <A href="http://go.microsoft.com/fwlink/p/?linkid=329800">Windows Management Framework 3.0</A>을 참고하세요. 이 링크는 PowerShell 3.0 다운로드 페이지로 직접 연결되며 성공적인 설치와 관련한 정보도 함께 제공합니다.



설치를 완료했거나 Lync Server 배포를 계속하기 전에 확인하려는 경우, 다음 방법을 통해 PowerShell 3.0이 서버에 설치되어 있는지 간단하게 확인할 수 있습니다.

1.  확인하려는 서버에서 **시작**, **모든 프로그램**, **보조 프로그램**을 차례로 클릭하고 **Windows PowerShell**을 클릭한 다음 **Windows PowerShell**을 클릭합니다.

2.  Windows PowerShell 콘솔에서 명령 프롬프트에 다음 명령을 입력한 다음 Enter 키를 누릅니다.
    
        Get-Host | Select-Object Version

3.  Windows PowerShell 3.0이 설치되어 있으면 다음과 유사한 내용이 출력됩니다.
    
        Version
        -------
        3.0

