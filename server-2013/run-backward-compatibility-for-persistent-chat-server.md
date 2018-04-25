---
title: 영구 채팅 서버에 대한 이전 버전과의 호환성 실행
TOCTitle: 영구 채팅 서버에 대한 이전 버전과의 호환성 실행
ms:assetid: 53f1a706-3104-4a94-8b4e-8badd9a066d6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204901(v=OCS.15)
ms:contentKeyID: 49303648
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 영구 채팅 서버에 대한 이전 버전과의 호환성 실행

 

_**마지막으로 수정된 항목:** 2013-02-21_

Lync Server 2013, 영구 채팅 서버 끝점은 영구 채팅 서버 풀을 가리키는 단순 URL을 만드는 방법을 제공합니다. 사용자가 레거시 클라이언트를 Lync 2013, 영구 채팅 실행 컴퓨터로 지정하려고 할 때 수동 구성에 단순 URL을 입력할 수 있기 때문에 이 기능은 레거시 클라이언트( Microsoft Office Communications Server 2007 R2그룹 채팅 서버 또는 Lync Server 2010, 그룹 채팅)에 유용합니다. 이 끝점은 영구 채팅에서 사용되지 않으며 레거시 클라이언트에만 필요합니다. 따라서 방은 마이그레이션했지만 조직 전체에 Lync 2013 클라이언트가 아직 배포되지 않은 중도 기간 중에 유용합니다. Lync 2010그룹 채팅(클라이언트)을 실행하는 사용자는 영구 채팅 서버백 엔드 서버에 계속 연결할 수 있습니다.

영구 채팅 서버 끝점을 여러 개 만들 필요는 없습니다. 각 영구 채팅 서버 풀에 대해 하나만 필요합니다. 관리자는 끝점을 여러 개(풀당 하나씩) 만들 수 있지만 레거시 클라이언트는 한 번에 하나의 풀에만 연결하도록 구성할 수 있습니다. 일반적인 시나리오 또는 주요 시나리오에서 레거시 배포는 한 개의 풀 전용입니다. 새로운 배포에서는 일반적으로 해당 풀을 새로운 Lync Server 2013으로 마이그레이션하고 일부 새로운 영구 채팅 서버 풀을 추가할 수 있습니다.

주요 시나리오에서는 일반적으로 다음 패턴을 따릅니다.

  - 하나의 Lync Server 2010, 그룹 채팅 풀로 사용자를 관리하고 Lync 2010 그룹 채팅 클라이언트는 잘 알려진 사용자(기본값인 sip:ocschat@ *\<domainName\>* .com 또는 이와 비슷한 항목)를 사용해서 해당 풀에 연결합니다. 사용자는 SIP 지원 Active Directory 도메인 서비스이며 조회 서비스가 수신 요청을 받도록 AD DS에 등록합니다.

  - 이후에 Lync Server 2013영구 채팅 서버 및 영구 채팅 서버 풀을 설치합니다.

  - 사용자가 일반적으로 오프라인인 시간 중에는(예: 주말) 다음을 수행합니다.
    
      - Lync Server 2010, 그룹 채팅을 해제합니다.
    
      - Lync Server 2010, 그룹 채팅 풀에서 Lync Server 2013영구 채팅 서버 풀로 데이터를 마이그레이션합니다.
    
      - Active Directory 도메인 서비스에서 잘 알려진 사용자를 삭제합니다.
    
      - 이전에 삭제한 잘 알려진 사용자와 동일한 SIP URI를 사용하여 새로운 *레거시 끝점* 을 만듭니다.
    
      - Lync Server 2013, 영구 채팅 서버를 시작합니다.

  - 사용자가 자신의 Lync 2010 그룹 채팅(클라이언트)을 사용해서 다시 로그온하고 구성을 변경할 필요 없이 자신의 데이터에 연결합니다.

  - 나중에 Lync Server 2010, 그룹 채팅을 해제할 수 있습니다. 이후에 Lync Server 2013, 영구 채팅 서버를 배포하고 새로운 Lync Server 2013영구 채팅 서버 풀을 설치할 수 있습니다.

Lync Server 2010, 그룹 채팅에서 Lync Server 2013, 영구 채팅 서버로 마이그레이션하는 방법에 대한 자세한 내용은 [Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2 그룹 채팅에서 Lync Server 2013, 영구 채팅 서버로 마이그레이션](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)을 참조하십시오.

이전 버전과의 호환성을 실행하려면(레거시 그룹 채팅 풀 클라이언트에서 사용할 수 있는 영구 채팅 서버 풀을 가리키는 영구 채팅 서버 끝점을 만들려면):

    New-CsPersistentChatEndpoint -SipAddress <CO name, ex. persistentchat@contoso.com> -PersistentChatPoolFqdn <pool FQDN, like pcpool.contoso.com>

그런 다음 SIP 주소를 연락처 개체로 사용하도록 영구 채팅 클라이언트를 구성합니다. SIP 주소는 특정 영구 채팅 서버 풀에 대해 **New-CsPersistentChatEndpoint** cmdlet으로 만들어집니다.

Windows PowerShell 명령줄 인터페이스를 사용하여 영구 채팅 서버 끝점을 추가하려면 다음 예를 고려하십시오. 여기에서는 풀의 FQDN(정규화된 도메인 이름)이 "pcpool.contoso.com"인 "contoso.com" 토폴로지에서 연락처 개체의 이름이 "persistentchat"로 지정되도록 연락처 개체를 구성합니다.

    New-CsPersistentChatEndpoint -SipAddress sip:persistentchat@contoso.com -PersistentChatPoolFqdn pcpool.contoso.com

## 참고 항목

#### 개념

[Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2 그룹 채팅에서 Lync Server 2013, 영구 채팅 서버로 마이그레이션](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)

