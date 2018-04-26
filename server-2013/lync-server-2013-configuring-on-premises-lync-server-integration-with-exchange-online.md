---
title: 'Lync Server 2013: Exchange Online과 온-프레미스 Lync Server 통합 구성'
TOCTitle: Exchange Online과 온-프레미스 Lync Server 2013 통합 구성
ms:assetid: 95a20117-2064-43c4-94fe-cac892cadb6f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh533880(v=OCS.15)
ms:contentKeyID: 49304432
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exchange Online과 온-프레미스 Lync Server 2013 통합 구성

 

_**마지막으로 수정된 항목:** 2014-07-02_

온-프레미스 Lync Server 2013 배포를 사용하는 고객은 하이브리드 배포 모드로 Microsoft Exchange Online에서 Microsoft Outlook Web App과의 상호 운용성을 구성할 수 있습니다. 상호 운용성 기능에는 Outlook Web App 인터페이스와 통합된 Single Sign-On, IM(인스턴트 메시징), 현재 상태 등이 있습니다. 이 통합을 사용하려면 다음 작업을 완료하여 온-프레미스 Lync Server 배포에서 에지 서버를 구성해야 합니다.

  - 공유 SIP 주소 공간 구성

  - 에지 서버에서 호스팅 공급자 구성

  - 업데이트된 중앙 관리 저장소의 복제 확인

## 공유 SIP 주소 공간 구성

온-프레미스 Lync Server 2013을 Exchange Online과 통합하려면 공유 SIP 주소 공간을 구성해야 합니다. Lync Server와 Exchange Online 서비스에서 모두 같은 SIP 도메인 주소 공간이 지원됩니다.

Lync Server 관리 셸을 사용하여 페더레이션을 위해 에지 서버를 구성합니다. 이렇게 하려면 아래 예제에 나와 있는 매개 변수를 사용하여 **Set-CSAccessEdgeConfiguration** cmdlet을 실행합니다.

    Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True

  - **AllowFederatedUsers** 매개 변수는 내부 사용자가 페더레이션 도메인의 사용자와 통신하도록 허용되는지 여부를 지정합니다. 또한 이 속성은 내부 사용자가 Lync Server 및 Exchange Online을 통해 공유 SIP 주소 공간 시나리오의 사용자와 통신할 수 있는지 여부도 결정합니다.

Lync Server 관리 셸 사용에 대한 자세한 내용은 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md)을 참조하십시오.

## 에지 서버에서 호스팅 공급자 구성

Lync Server 관리 셸을 사용하여 에지 서버에서 호스팅 공급자를 구성합니다. 이렇게 하려면 아래 예제에 나와 있는 매개 변수를 사용하여 **New-CsHostingProvider** cmdlet을 실행합니다.

    New-CsHostingProvider -Identity "Exchange Online" -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFqdn "exap.um.outlook.com" -IsLocal $False -VerificationLevel UseSourceVerification


> [!NOTE]
> 중국의 21Vianet에서 운영하는 Office 365를 사용 중인 경우 이 예제에서 <STRONG>ProxyFqdn</STRONG> 매개 변수의 값("exap.um.outlook.com")을 21Vianet에서 운영하는 FQDN("exap.um.partner.outlook.cn")으로 바꿉니다.



  - **Identity**는 만들 호스팅 공급자의 고유 문자열 값 식별자(예: “Exchange Online”)를 지정합니다. 공백이 포함된 값은 큰따옴표로 묶어야 합니다.

  - **Enabled**는 도메인과 호스팅 공급자 간의 네트워크 연결을 사용할 수 있는지 여부를 나타냅니다. True로 설정해야 합니다.

  - **EnabledSharedAddressSpace**는 호스팅 공급자를 공유 SIP 주소 공간 시나리오에서 사용할지 여부를 나타냅니다. True로 설정해야 합니다.

  - **HostsOCSUsers**는 호스팅 공급자를 사용하여 Office Communications Server 또는 Lync Server를 호스팅할지 여부를 나타냅니다. False로 설정해야 합니다.

  - **ProxyFQDN**은 호스팅 공급자에서 사용하는 프록시 서버의 FQDN(정규화된 도메인 이름)을 지정합니다. Exchange Online의 경우 FQDN은 exap.um.outlook.com입니다.

  - **IsLocal**은 호스팅 공급자에서 사용하는 프록시 서버가 Lync Server 토폴로지 내에 포함되는지 여부를 나타냅니다. False로 설정해야 합니다.

  - **VerificationLevel**은 호스팅된 공급자에 대해 보내고 받는 메시지에 허용되는 확인 수준을 나타냅니다. **UseSourceVerification**(호스팅 공급자에서 보내는 메시지에 포함된 확인 수준 사용)을 지정합니다. 이 수준을 지정하지 않으면 메시지가 확인할 수 없는 항목으로 간주되어 거부됩니다.

## 업데이트된 중앙 관리 저장소의 복제 확인

위 섹션에서 cmdlet을 통해 적용하는 변경 내용은 에지 서버에 자동으로 적용되며, 보통 1분 이내에 복제됩니다. 다음 cmdlet을 사용하여 복제 상태를 확인한 다음 변경 내용이 에지 서버에 적용되었는지 확인할 수 있습니다.

복제 업데이트를 확인하려면 Lync Server 배포 내의 서버에서 다음 cmdlet을 실행합니다.

    Get-CsManagementStoreReplicationStatus

변경 내용이 적용되었는지 확인하려면 에지 서버에서 다음 cmdlet을 실행합니다.

    Get-CsHostingProvider -LocalStore

## 참고 항목

#### 기타 리소스

[호스팅된 Exchange UM에서 Lync Server 2013 사용자 음성 메일 제공](lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md)  
[Lync Server 2013의 호스팅된 Exchange 통합 메시징 통합](lync-server-2013-hosted-exchange-unified-messaging-integration.md)

