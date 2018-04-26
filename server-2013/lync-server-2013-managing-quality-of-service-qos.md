---
title: Lync Server 2013에서 QoS(서비스 품질) 관리
TOCTitle: Lync Server 2013에서 QoS(서비스 품질) 관리
ms:assetid: ab1051c3-8380-4d72-86df-37a61b1e4a41
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg405409(v=OCS.15)
ms:contentKeyID: 49304688
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 QoS(서비스 품질) 관리

 

_**마지막으로 수정된 항목:** 2013-11-07_

QoS(서비스 품질)는 음성 및 화상 통신의 최종 사용자 경험을 최적화하기 위해 일부 조직에서 사용되는 네트워킹 기술입니다. QoS는 대부분 대역폭 제약이 있는 네트워크에서 사용됩니다. 다수의 네트워크 패킷이 비교적 적은 양의 가용 대역폭을 놓고 경합하는 경우 관리자가 QoS를 사용하여 오디오 또는 비디오 데이터를 전송하는 패킷에 보다 높은 우선 순위를 할당할 수 있습니다. 이러한 패킷에 보다 높은 우선 순위를 지정하면 음성 및 화상 통신이 파일 전송, 웹 브라우징, 데이터베이스 백업 등이 포함된 네트워크 세션보다 더욱 빠르게 수행되며 중단이 줄어듭니다. 파일 전송 또는 데이터베이스 백업에 사용되는 네트워크 패킷에 "최상의 노력" 우선 순위가 할당되어 있기 때문입니다.


> [!NOTE]
> 일반적으로 QoS는 내부 네트워크의 통신 세션에만 적용됩니다. QoS를 구현하는 경우 서버와 라우터가 패킷 표시를 지원하도록 구성하게 됩니다. 인터넷이나 기타 네트워크에서 QoS가 지원될 것이라고 가정할 수 없습니다. 다른 네트워크에서 QoS가 지원되더라도 조직의 네트워크에서 QoS 서비스를 구성한 것과 같은 방식으로 QoS가 구성된다는 보장이 없습니다.



Microsoft Lync Server 2013에는 QoS를 사용하지 않아도 됩니다. 현재 QoS를 사용하지 않는 경우 Lync Server 2013을 설치하기 전에 QoS 서비스를 설치할 필요가 없습니다. 네트워크에서 상당한 양의 패킷 손실을 경험하는 경우 이 문제를 완화하기 위해 대역폭을 추가하는 것이 좋으며, 대역폭을 추가하는 것이 불가능한 경우에 QoS를 대신 구현할 수 있습니다.

Lync Server 2013은 QoS를 완벽히 지원합니다. 즉, QoS를 이미 사용하고 있는 조직에서는 Lync Server을 기존 네트워크 인프라에 손쉽게 통합할 수 있습니다. 이렇게 하려면 다음 작업을 수행해야 합니다.

  - [Windows 기반이 아닌 장치에 QoS 사용](lync-server-2013-enabling-qos-for-devices-that-are-not-based-on-windows.md). 기본적으로 다른 운영 체제를 실행하는 컴퓨터 및 기타 장치(예: iPhone)에 대해서는 QoS를 사용하지 않도록 설정됩니다. Lync Server를 사용하여 장치에 QoS를 사용하거나 사용하지 않도록 설정할 수 있지만 일반적으로 해당 제품을 사용하여 이러한 장치에서 사용하는 DSCP 코드를 수정할 수 없습니다.

  - [회의, 응용 프로그램 및 중재 서버에 대한 포트 범위 구성](lync-server-2013-configuring-port-ranges-for-your-conferencing-application-and-mediation-servers.md). 오디오 및 비디오와 같은 서로 다른 패킷 유형에 대해 고유한 포트 집합을 예약해야 합니다. Lync Server 2013에서는 QoS를 사용하거나 사용하지 않도록 설정하기 위해 속성 값을 True 또는 False로 설정하는 등의 방식을 사용하지 않고 포트 범위를 구성한 후에 그룹 정책을 만들고 적용합니다. 이후에 QoS를 사용하지 않기로 결정하는 경우 단지 해당 그룹 정책 개체를 제거하여 QoS를 사용하지 않도록 설정할 수 있습니다.

  - [에지 서버에 대한 포트 범위 구성](lync-server-2013-configuring-port-ranges-for-your-edge-servers.md). 반드시 필요한 것은 아니지만 다른 서버와 동일한 포트 범위를 사용하도록 에지 서버를 구성할 수 있습니다.

  - [Microsoft Lync 클라이언트에 대한 포트 범위 구성](lync-server-2013-configuring-port-ranges-for-your-microsoft-lync-clients.md). 이러한 포트 범위는 클라이언트 컴퓨터에만 적용되며 일반적으로 서버에 구성된 포트 범위와 다릅니다.

  - [Lync Server 2013에서 회의, 응용 프로그램 및 중재 서버에 대한 서비스 품질 정책 구성](lync-server-2013-configuring-a-quality-of-service-policy-for-your-conferencing-application-and-mediation-servers.md). 이러한 정책은 서로 다른 패킷 유형에 적용되는 DSCP 코드를 결정합니다.

  - [A/V 에지 서버에 대한 서비스 품질 정책 구성](lync-server-2013-configuring-a-quality-of-service-policy-for-your-a-v-edge-servers.md). 이것은 에지 서버의 내부 쪽에 대해서만 수행해야 합니다. QoS는 인터넷이 아닌 내부 네트워크에서 사용하도록 설계되어 있기 때문입니다.

  - [Windows 7 또는 Windows 8에서 실행되는 클라이언트에 대한 서비스 품질 정책 구성](lync-server-2013-configuring-quality-of-service-policies-for-clients-running-on-windows-7-or-windows-8.md). Microsoft Lync Server 2013은 Windows Vista 또는 Windows XP 등의 다른 Windows 운영 체제에 대해서는 QoS를 지원하지 않습니다.

  - [Microsoft Lync Phone Edition 장치의 서비스 품질 구성](lync-server-2013-configuring-quality-of-service-on-microsoft-lync-phone-edition-devices.md). 기본적으로 QoS는 Lync Phone Edition 장치에 대해 사용하도록 설정되어 있습니다. 그러나 기본 DSCP 값을 변경하여 조직의 모든 오디오 패킷이 동일한 DSCP 코드를 사용하도록 할 수 있습니다.


> [!NOTE]
> Microsoft Windows Server 2012 또는 Windows Server 2012 R2를 사용 중인 경우 해당 플랫폼의 서비스 품질 관리에 사용할 수 있는 새 Windows PowerShell cmdlet 집합이 필요할 수 있습니다. 자세한 내용은 Windows PowerShell의 네트워크 서비스 품질 cmdlet(<A href="http://go.microsoft.com/fwlink/p/?linkid=285379">http://go.microsoft.com/fwlink/p/?LinkId=285379</A>)을 참고하세요.


