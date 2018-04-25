---
title: 'Lync Server 2013: 보관 서버, 모니터링 서버 및 그룹 채팅 준수 서버 데이터베이스에서 전송 중인 데이터 보호'
TOCTitle: Lync Server 2013의 보관 서버, 모니터링 서버 및 그룹 채팅 준수 서버 데이터베이스에서 전송 중인 데이터 보호
ms:assetid: ea219705-1015-43a7-890b-e7e67b451e7c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn518336(v=OCS.15)
ms:contentKeyID: 60504745
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 보관 서버, 모니터링 서버 및 그룹 채팅 준수 서버 데이터베이스에서 전송 중인 데이터 보호

 

_**마지막으로 수정된 항목:** 2013-12-05_

Microsoft Lync Server 2013 보관 서버와 모니터링 서버는 모두 메시지 큐(MSMQ라고도 함) 서비스를 사용하여 데이터 메시지를 수집한 다음 안전하게 수집 지점에서 리포지토리 서버로 이동합니다. 준수 서비스는 그룹 채팅 서버와 함께 데이터를 수집하며, 이 서버도 메시지 큐를 사용합니다.

Lync Server 2013에는 데이터를 내부적으로 보호하는 기능이 없습니다. 그러나 이 트래픽을 보호해야 하는 요구 사항이 있는 경우에는 메시지 큐 서비스가 보내는 메시지 큐의 메시지 수준에서 암호화를 제공할 수 있습니다. 이 작업은 Active Directory 도메인 서비스에서 관리되는 인증서를 사용하여 수행됩니다. 자세한 내용은 부록 D: Windows Server 2008의 메시지 큐 및 인터넷 통신([http://go.microsoft.com/fwlink/p/?LinkId=145238](http://go.microsoft.com/fwlink/p/?linkid=145238)) 또는 Windows Server 2008 R2를 위한 부록 I: Windows Server 2008 R2의 메시지 큐 및 인터넷 통신([http://go.microsoft.com/fwlink/p/?LinkId=211883](http://go.microsoft.com/fwlink/p/?linkid=211883))을 참조하세요.

