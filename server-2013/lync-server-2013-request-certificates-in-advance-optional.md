---
title: 'Lync Server 2013: 사전 인증서 요청(선택 사항)'
TOCTitle: 사전 인증서 요청(선택 사항)
ms:assetid: 9d6d7de6-ff2a-46da-b1b7-a354c8e383e4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412733(v=OCS.15)
ms:contentKeyID: 49304531
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 사전 인증서 요청(선택 사항)

 

_**마지막으로 수정된 항목:** 2013-02-21_

인증서는 각 Enterprise Edition프런트 엔드 서버, Standard Edition 서버, 디렉터, 에지 서버 및 독립 실행형 중재 서버를 비롯하여 Lync Server 2013을 실행 중인 모든 내부 서버에 필요합니다. 내부 서버에는 내부 엔터프라이즈 CA(인증 기관)를 사용하는 것이 좋지만 공용 CA를 사용할 수도 있습니다. 인증서 요구 사항 및 공용 CA 사용에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 내부 서버에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-internal-servers.md)을 참조하십시오.

Lync Server 2013 설치 프로그램에는 서버를 배포하는 동안 인증서를 요청, 할당 및 설치하는 작업을 도와 주는 인증서 마법사가 포함됩니다. 예를 들어 실제로 서버를 배포하는 시간을 절약하기 위해 서버를 설치하기 전에 인증서를 요청하려면 Lync Server 2013 관리 도구가 설치된 컴퓨터를 사용하거나 조직에서 정의한 인증서 요청 절차를 사용하여 원하는 작업을 수행할 수 있습니다. 단, 인증서가 내보낼 수 있는 상태여야 하며 필요한 주체 대체 이름을 모두 포함해야 합니다. 인증서를 사전에 요청할지 여부는 선택 사항이며, 인증서를 사전에 요청하지 않을 경우에는 인증서가 필요한 각 서버의 설치 과정으로 인증서를 요청해야 합니다.

이 배포 설명서는 이 배포 설명서의 [Lync Server 2013에서 서버에 대한 인증서 구성](lync-server-2013-configure-certificates-for-servers.md), [Lync Server 2013에서 디렉터에 대한 인증서 구성](lync-server-2013-configure-certificates-for-the-director.md) 및 [Lync Server 2013에서 중재 서버용 파일 설치](lync-server-2013-install-the-files-for-mediation-server.md) 섹션에서 설명한 대로 설치 프로세스의 과정으로 인증서를 요청할 수 있도록 인증서 마법사를 사용하는 절차를 제공합니다. 인증서를 사전에 요청하려면 배포 시 인증서를 요청하는 대신 인증서를 가져오고 할당하는 관련 섹션에서 인증서 배포 절차를 수정해야 합니다.


> [!NOTE]
> Lync Server 2013에는 Windows Vista, Windows Server&nbsp;2008, Windows Server&nbsp;2008&nbsp;R2, Windows 7 운영 체제 및 Lync Phone Edition을 실행하는 클라이언트에서 연결할 수 있도록 SHA-256 인증서에 대한 지원이 포함됩니다. SHA-256을 사용한 외부 액세스를 지원하기 위해 SHA-256을 사용하여 공용 CA에서 외부 인증서가 발급됩니다.


