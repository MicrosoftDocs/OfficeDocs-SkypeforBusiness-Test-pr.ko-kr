---
title: 'Lync Server 2013: 에지 구성 요소에 대한 인증서 요청'
TOCTitle: 에지 구성 요소에 대한 인증서 요청
ms:assetid: 8c72b877-febc-428f-89dc-389e7a7ac849
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398708(v=OCS.15)
ms:contentKeyID: 49304323
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 에지 구성 요소에 대한 인증서 요청

 

_**마지막으로 수정된 항목:** 2013-11-07_

외부 사용자 액세스를 지원하는 데 필요한 인증서에는 공용 CA(인증 기관)에서 발급한 인증서와 내부 엔터프라이즈 CA에서 발급한 인증서가 포함됩니다.

  - 역방향 프록시 및 에지 서버의 외부 인터페이스에 필요한 인증서는 공용 CA에서 발급한 인증서여야 합니다.

  - 외부 인터페이스에 필요한 인증서는 공용 CA 또는 내부 엔터프라이즈 CA에서 발급한 인증서일 수 있습니다. 공용 인증서를 사용하지 않기 위해 이러한 인증서를 만들려면 내부 Windows Server 2008 CA, Windows Server 2008 R2 CA, Windows Server 2012 CA 또는 Windows Server 2012 R2 CA를 사용하는 것이 좋습니다.


> [!IMPORTANT]
> 인증서 요청(특히, 공용 CA에 대한 요청)을 처리하는 데는 시간이 걸릴 수 있으므로, 에지 서버 구성 요소 배포를 시작할 때 인증서를 사용할 수 있도록 충분한 시간 여유를 두고 에지 서버용 인증서를 요청해야 합니다. 에지 서버의 인증서 요구 사항에 대한 요약 정보를 보려면 <A href="lync-server-2013-certificate-requirements-for-external-user-access.md">Lync Server 2013의 외부 사용자 액세스에 대한 인증서 요구 사항</A>를 참조하십시오.



내부 에지 인증서에 공용 CA를 사용하도록 선택할 수 있긴 하지만 인증서 비용을 최소화하는 대신 그러한 다른 인증서에 내부 엔터프라이즈 CA를 사용하는 것이 좋습니다. 에지 서버에 대한 인증서 요구 사항 요약 정보를 보려면 [Lync Server 2013의 외부 사용자 액세스에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-external-user-access.md)을 참조하십시오.


> [!NOTE]
> 에지 서버 설치 시 설치 프로그램에는 <A href="lync-server-2013-set-up-edge-certificates.md">Lync Server 2013의 에지 인증서 설정</A> 섹션에 설명된 대로 인증서 요청, 지정 및 설치 작업을 용이하게 해주는 인증서 마법사가 포함되어 있습니다. 에지 서버 설치 전에 인증서를 요청하려면(예: 에지 서버 구성 요소의 실제 배포 시 시간을 절약하기 위해) 인증서가 내보내기 가능하고 필요한 모든 주제 대체 이름을 포함하고 있는 한 내부 서버를 사용하여 에지 서버 설치 전에 인증서를 요청할 수 있습니다. 이 설명서에서는 내부 서버를 사용하여 인증서를 요청하는 절차는 제공하지 않습니다.



## 공용 CA에서 인증서 요청

에지 서버 배포에는 에지 서버의 외부 인터페이스에 대한 단일 공용 인증서가 필요합니다. 이 인증서는 액세스 에지 서비스, 웹 회의 에지 서비스 및 A/V 인증 서비스에 사용됩니다. 이 인증서는 A/V 인증 서비스에서 풀의 모든 에지 서버에 대해 동일한 키를 사용하도록 보장하기 위해 내보낼 수 있는 개인 키가 포함되어 있어야 합니다. Microsoft Internet Security and Acceleration(ISA) Server 2006 또는 Microsoft Forefront Threat Management Gateway 2010에 사용되는 역방향 프록시에도 공용 인증서가 필요합니다.

## 내부 엔터프라이즈 CA에서 인증서 요청

내부 에지 인터페이스에 필요한 인증서는 공용 CA(인증 기관) 또는 내부 CA에서 발급한 인증서일 수 있습니다. 내부 엔터프라이즈 CA를 사용하면 인증서 비용을 최소화할 수 있습니다. 조직에 내부 CA가 배포되어 있는 경우에는 내부 에지용 인증서를 내부 CA에서 발급해야 합니다. 내부 인증서에 대해 내부 엔터프라이즈 CA를 사용하면 인증서 비용을 줄일 수 있습니다.

에지 구성 요소의 인증서 요구 사항 요약 정보에 대한 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-external-user-access.md)을 참조하십시오. 공용 CA를 사용해서 인증서를 가져오는 방법에 대한 자세한 내용은 [Lync Server 2013에서 에지 구성 요소에 대한 인증서 요청](lync-server-2013-request-certificates-for-edge-components.md)을 참조하십시오. 인증서 요청, 설치 및 지정에 대한 자세한 내용은 [Lync Server 2013의 에지 인증서 설정](lync-server-2013-set-up-edge-certificates.md)을 참조하십시오.

