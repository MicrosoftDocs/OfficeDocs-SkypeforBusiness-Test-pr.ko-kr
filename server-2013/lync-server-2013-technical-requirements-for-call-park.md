---
title: 'Lync Server 2013: 통화 대기에 대한 기술 요구 사항'
TOCTitle: 통화 대기에 대한 기술 요구 사항
ms:assetid: 38bcf302-2b72-4492-9266-f6dc31b566e1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204818(v=OCS.15)
ms:contentKeyID: 49303331
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 대기에 대한 기술 요구 사항

 

_**마지막으로 수정된 항목:** 2013-11-07_

이 섹션에서는 통화 대기에 대한 다음과 같은 기술 요구 사항을 설명합니다.

  - 하드웨어 요구 사항

  - 소프트웨어 요구 사항

  - 포트 요구 사항

  - 오디오 파일 요구 사항

## 하드웨어 요구 사항

통화 대기 응용 프로그램의 하드웨어 요구 사항은 프런트 엔드 서버와 동일합니다. 하드웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 하드웨어 플랫폼](lync-server-2013-server-hardware-platforms.md)을 참조하십시오.

## 소프트웨어 요구 사항

통화 대기 응용 프로그램의 운영 체제 요구 사항 및 소프트웨어 필수 구성 요소는 프런트 엔드 서버와 동일합니다. 소프트웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)을 참조하십시오.

통화 대기 응용 프로그램을 배포하는 모든 프런트 엔드 서버 및 Standard Edition 서버에는 Windows Media 형식 런타임( Windows Server 2008 R2 실행 서버의 경우) 또는 Microsoft 미디어 파운데이션( Windows Server 2012 또는 Windows Server 2012 R2 실행 서버의 경우)이 설치되어 있어야 합니다. Windows Server 2008 R2의 경우 Windows Media 형식 런타임은 Windows 데스크톱 경험의 일부로 설치됩니다. Windows Media 형식 런타임 또는 Microsoft 미디어 파운데이션은 통화 대기에서 대기 음악으로 재생하는 Windows Media 오디오(.wma) 파일에 필요합니다.

## 포트 요구 사항

통화 대기 응용 프로그램에는 다음 포트가 사용됩니다.

  - **포트 5075**   SIP 수신 대기 요청에 사용됩니다.


> [!NOTE]
> 이 포트는 <STRONG>Set-CsApplicationServer</STRONG> cmdlet을 사용하여 변경할 수 있는 기본 설정입니다. 이 cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.



## 오디오 파일 요구 사항

통화 대기 응용 프로그램은 대기 음악으로 Windows Media 오디오(.wma) 파일만 지원합니다. Microsoft Expression Encoder 4를 사용하여 대기 음악용으로 파일을 사용자 지정할 수 있습니다. Expression Encoder 4를 다운로드하려면 "Expression Encoder 4"([http://go.microsoft.com/fwlink/p/?linkId=202843](http://go.microsoft.com/fwlink/p/?linkid=202843))를 참조하십시오. 이 도구를 사용하여 파일을 .wma 형식으로 변환합니다. 통화 대기 대기 음악 파일로 권장되는 형식은 Media Audio 9, 44kHz, 16비트, 모노, CBR, 32kbps입니다.


> [!NOTE]
> 변환된 파일은 44kHz로 녹음되었더라도 전화에서는 16kHz로만 재생됩니다.


