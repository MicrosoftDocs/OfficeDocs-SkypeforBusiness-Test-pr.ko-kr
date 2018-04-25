---
title: 'Lync Server 2013: Windows PowerShell 및 Lync Server 관리 도구'
TOCTitle: Windows PowerShell 및 Lync Server 2013 관리 도구
ms:assetid: 6a285f7c-0ef5-4cab-9976-d03be276e35d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn481130(v=OCS.15)
ms:contentKeyID: 59679293
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Windows PowerShell 및 Lync Server 2013 관리 도구

 

_**마지막으로 수정된 항목:** 2014-10-21_

Microsoft Lync Server 2013에서 관리 도구는 Windows PowerShell을 사용하여 구현됩니다. Windows PowerShell에는 명령줄 환경, 제품별 명령, 전체 스크립트 언어가 포함됩니다. Windows PowerShell을 사용하여 구현된 Lync Server 2013 도구에는 다음이 포함됩니다.

  - **토폴로지 작성기**. 토폴로지 작성기를 사용하여 계획한 토폴로지를 만들고 조정하고 게시할 수 있으며 서버 설치를 시작하기 전에 토폴로지의 유효성을 검사할 수 있습니다. 개별 서버에 Lync Server 2013을 설치하면 서버에서 설치 프로세스의 일환으로 게시한 토폴로지를 읽고 설치 프로그램에서는 토폴로지의 안내에 따라 서버를 배포합니다. 설치 후에는 구성 정보가 모든 서버에 자동으로 복제됩니다. 토폴로지 작성기를 사용해야 구성 요소를 배포에 추가할 수 있습니다.

  - **Lync Server 관리 셸**. 배포의 전체 명령줄 관리에 Lync Server 관리 셸을 사용할 수 있습니다.

  - **Lync Server 제어판**. Microsoft Lync Server 2013 제어판 사용자 인터페이스를 사용하여 배포에서 가장 일반적인 작업을 관리할 수 있습니다.

이러한 도구는 약 550개의 제품별 cmdlet을 포함하여 Windows PowerShell cmdlet을 배포의 관리에 사용합니다. Lync Server 2013에 포함된 보안 cmdlet은 기본적으로 인증, 사용자 권한 및 사용 권한에 사용됩니다. 인증서 및 개인식별번호(PIN) 인증에 필요한 cmdlet을 포함하여 다양한 cmdlet을 인증 관리에 사용할 수 있습니다. 또한 많은 수의 cmdlet을 사용하여 Lync Server 2013의 관리 권한을 위임할 수 있는 RBAC(역할 기반 액세스 제어) 기능을 사용할 수 있습니다. Lync Server cmdlet에 대한 자세한 내용은 작업 설명서의 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md)을 참고하세요. 토폴로지 작성기 및 Lync Server 2013 제어판을 사용하여 배포를 관리하는 방법에 대한 자세한 내용은 작업 설명서의 [Lync Server 2013 제어판](https://technet.microsoft.com/ko-kr/library/gg133224\(v=ocs.15\))을 참고하세요.

Windows PowerShell의 스크립트 보안 기능은 Microsoft Visual Basic Scripting Edition(VBScript) 등 이전 기술의 일부 스크립팅 관련 보안 문제를 예방하기 위해 특별히 설계되었습니다. Windows PowerShell 보안 기능은 사용자가 모르는 상태에서 부주의하게 스크립트를 실행할 수 없는 환경을 만듭니다. 기본적으로 Windows PowerShell 보안 기능을 사용하도록 설정되어 있습니다. 스크립팅 필요와 다양한 보안 목적에 맞게 해당 기능의 상태를 수정할 수 있습니다. 셸에서 사용자의 스크립트 실행이 불가능한 것이 아니라 사용자가 모르는 상태에서 스크립트를 실행하기가 어렵도록 기본 설정된 것입니다. 자세한 내용은 Windows PowerShell 스크립트 보안([http://go.microsoft.com/fwlink/p/?LinkId=213145](http://go.microsoft.com/fwlink/p/?linkid=213145))을 참고하세요.

