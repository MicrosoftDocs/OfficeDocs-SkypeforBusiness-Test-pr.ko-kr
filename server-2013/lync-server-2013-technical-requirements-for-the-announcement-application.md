---
title: 'Lync Server 2013: 알림 응용 프로그램에 대한 기술 요구 사항'
TOCTitle: 알림 응용 프로그램에 대한 기술 요구 사항
ms:assetid: fbd8c204-3765-4b22-a0c9-a781b5126366
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205413(v=OCS.15)
ms:contentKeyID: 49305614
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 알림 응용 프로그램에 대한 기술 요구 사항

 

_**마지막으로 수정된 항목:** 2013-11-07_

이 섹션에서는 다음과 같은 알림 응용 프로그램에 대한 기술적 요구 사항에 대해 설명합니다.

  - 하드웨어 요구 사항

  - 소프트웨어 요구 사항

  - 포트 요구 사항

  - 오디오 파일 요구 사항

## 하드웨어 요구 사항

알림 응용 프로그램의 하드웨어 요구 사항은 프런트 엔드 서버와 동일합니다. 하드웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)을 참조하십시오.

## 소프트웨어 요구 사항

알림 응용 프로그램의 운영 체제 요구 사항 및 소프트웨어 필수 구성 요소는 프런트 엔드 서버와 동일합니다. 소프트웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)을 참조하십시오.

알림 응용 프로그램을 실행하는 모든 Standard Edition Server 또는 프런트 엔드 서버에는 Windows Server 2008 R2를 실행하는 서버에 대해 Windows Media Format Runtime이 설치되어 있거나 Windows Server 2012 또는 Windows Server 2012 R2를 실행하는 서버에 대해 Microsoft Media Foundation이 설치되어 있어야 합니다. Windows Server 2008 R2의 경우 Windows Media Format Runtime이 Windows Desktop Experience의 일부로 설치됩니다. Windows Media Format Runtime 또는 Microsoft Media Foundation은 알림 응용 프로그램에서 알림 및 음악용으로 재생하는 Windows Media 오디오(.wma) 파일에 필요합니다.

## 포트 요구 사항

알림 응용 프로그램에는 다음 포트가 사용됩니다.

  - **포트 5071**   SIP 수신 대기 요청에 사용됩니다.


> [!NOTE]
> 이 포트는 기본 설정이며 <STRONG>Set-CsApplicationServer</STRONG> cmdlet을 사용하여 변경할 수 있습니다. 이 cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.



## 오디오 파일 요구 사항

알림 응용 프로그램에서는 음악과 알림용으로 웨이브(.wav) 파일 형식과 Windows Media 오디오(.wma) 파일 형식을 지원합니다. 알림 응용 프로그램의 오디오 파일 요구 사항은 응답 그룹 응용 프로그램과 동일합니다. 자세한 내용은 [Lync Server 2013의 응답 그룹에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-response-group.md)을 참조하십시오.

