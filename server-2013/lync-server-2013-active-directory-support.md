---
title: Lync Server 2013 Active Directory 지원
TOCTitle: Active Directory 지원
ms:assetid: 28ed9ac4-586d-4803-ad45-99c4fa793f54
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425756(v=OCS.15)
ms:contentKeyID: 49303125
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Active Directory 지원

 

_**마지막으로 수정된 항목:** 2012-12-04_

Lync Server 2013에서 지원하는 Active Directory 도메인 서비스 온-프레미스 토폴로지는 다음과 같습니다.

  - 도메인이 하나인 단일 포리스트

  - 트리가 하나이고 도메인이 여러 개인 단일 포리스트

  - 트리 여러 개와 연결되지 않은 네임스페이스가 포함된 단일 포리스트

  - 중앙 포리스트 토폴로지의 다중 포리스트

  - 리소스 포리스트 토폴로지의 다중 포리스트


> [!NOTE]
> Lync Server 2013은 단일 레이블 도메인을 지원하지 않습니다. 예를 들어 <STRONG>contoso.local</STRONG> 이라는 루트 도메인으로 구성된 포리스트는 지원되지만 <STRONG>local</STRONG> 이라는 단일 레이블 루트 도메인은 지원되지 않습니다. 자세한 내용은 Microsoft 기술 자료 문서 300684, "단일 레이블 DNS 이름을 사용하여 Windows에서 도메인을 구성하는 방법에 대한 정보"( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=143752%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=143752&amp;clcid=0x412</A>)를 참조하십시오.




> [!NOTE]
> Lync Server 2013에서는 도메인 이름 바꾸기를 지원하지 않습니다. Lync Server가 배포된 도메인을 이름을 바꿔야 하는 경우에는 먼저 Lync Server를 제거하고 도메인 이름을 바꾼 후 Lync Server를 다시 설치해야 합니다.



지원되는 토폴로지 및 온-프레미스 배포 요구 사항에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 Active Directory 도메인 서비스 요구 사항, 지원 및 토폴로지](lync-server-2013-active-directory-domain-services-requirements-support-and-topologies.md)를 참조하십시오.

