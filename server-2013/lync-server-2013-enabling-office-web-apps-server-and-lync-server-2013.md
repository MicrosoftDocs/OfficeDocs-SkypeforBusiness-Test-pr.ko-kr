---
title: 'Lync Server 2013: Office Online Server 및 Lync Server 2013 사용'
TOCTitle: Office Online Server 및 Lync Server 2013 사용
ms:assetid: 3370ab55-9949-4f32-b88b-5cffed6aaad8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204792(v=OCS.15)
ms:contentKeyID: 49303256
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Office Online Server 및 Lync Server 2013과 통합 구성

 

_**마지막으로 수정된 항목:** 2014-02-05_

Lync Server 2013은 Office Web Apps 서버를 사용하여 PowerPoint 프레젠테이션을 처리합니다. 이 방식의 이점에 대한 자세한 내용은 [Lync Server 2013의 웹 회의 개요](lync-server-2013-web-conferencing-overview.md)를 참고하세요.

이러한 새 기능을 사용하려면 관리자는 Office Web Apps 서버를 설치해야 하며 Lync Server 2013이 Office Web Apps 서버와 통신하도록 구성해야 합니다. 이 설명서에서는 Office Web Apps 서버와 함께 작동하도록 Lync Server 2013을 구성하는 방법에 대한 정보를 제공합니다. 그러나 Office Web Apps 서버 자체를 설치하는 방법에 대한 정보는 제공하지 않습니다. 해당 정보는 Microsoft Office Web Apps 배포 웹 사이트( [http://go.microsoft.com/fwlink/?linkid=257525\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=257525%26clcid=0x412))를 참고하세요. 이 가이드에는 Office Web Apps 서버의 전체 필수 구성 요소 정보가 포함되어 있습니다. Office Web Apps 서버는 Lync Server, Microsoft SQL Server 또는 기타 서버 응용 프로그램을 실행하고 있지 않은 독립 실행형 컴퓨터에 설치해야 합니다. 즉, 해당 컴퓨터에 어떤 버전의 Microsoft Office도 설치되어 있어서는 안 됩니다. Office Web Apps 서버를 실행하는 데 사용되는 컴퓨터에는 .NET Framework 4.5 및 Windows PowerShell 3.0을 비롯한 특정 소프트웨어 집합도 설치되어 있어야 합니다. 이러한 요구 사항 및 인증서와 IIS(인터넷 정보 서비스)를 구성하는 방법에 대한 정보는 Microsoft Office Web Apps 배포 웹 사이트( [http://go.microsoft.com/fwlink/?linkid=257525\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=257525%26clcid=0x412))에 자세하게 설명되어 있습니다.

이 문서에서는 다음 항목 영역을 다룹니다.

  - [Office Web Apps 서버와 함께 작동하도록 Lync Server 2013 구성](lync-server-2013-configuring-lync-server-2013-to-work-with-office-web-apps-server.md)

  - [역방향 프록시 서버를 사용하여 Lync Server 2013에서 Office Online Server 서버 게시](lync-server-2013-publishing-office-web-apps-server-using-a-reverse-proxy-server.md)

  - [Lync Server 2013에서 Office Web Apps 서버 구성의 유효성 검사](lync-server-2013-validating-the-configuration-of-office-web-apps-server.md)

  - [Office Web Apps 서버에 사용할 Lync Server 2013의 클라이언트 구성](lync-server-2013-configuring-clients-for-use-with-office-web-apps-server.md)

