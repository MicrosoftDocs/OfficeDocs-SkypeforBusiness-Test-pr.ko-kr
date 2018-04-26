---
title: Lync Server 2013의 A/V(오디오/비디오) 에지 서버
TOCTitle: Lync Server 2013의 A/V(오디오/비디오) 에지 서버
ms:assetid: b0cc538b-77eb-47fb-be82-5ab0631c6219
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721852(v=OCS.15)
ms:contentKeyID: 49885933
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 A/V(오디오/비디오) 에지 서버

 

_**마지막으로 수정된 항목:** 2012-11-01_

A/V 에지 서버를 사용하면 내부 사용자(조직 네트워크에 로그온한 사용자)가 외부 사용자(조직 네트워크에 로그온하지 않은 사용자)와 오디오 및 비디오를 공유할 수 있습니다. A/V 에지 서비스는 오디오 및 비디오뿐만 아니라 데스크톱 공유 및 파일 전송도 지원합니다.

A/V 에지 서비스는 주로 A/V 에지 구성을 사용하여 관리됩니다. 이러한 설정을 사용하면 포트 및 사용자당 할당할 수 있는 최대 대역폭 크기를 관리하고, 인증 토큰을 갱신해야 하기까지 인증 토큰을 사용할 수 있는 최대 시간을 지정할 수 있습니다. A/V 이제 구성 설정은 사이트 또는 개별 A/V 에지 서버에 적용할 수 있습니다. 우선 순위를 갖는 설정 컬렉션을 결정할 때는 다음 지침을 따르십시오.

  - 서비스 범위(즉, 개별 서버)에서 구성된 설정이 다른 모든 것보다 우선 순위를 갖습니다.

  - 사이트 범위에서 구성된 설정이 전역 범위에서 구성된 설정보다 우선 순위를 갖습니다. 그러나 서비스 범위 설정이 사이트 범위 설정보다 우선합니다.

  - 전역 범위의 설정은 개별 서버에 대해 구성된 서비스 설정이 없거나 서버가 있는 사이트에 대한 사이트 설정이 없는 경우에만 사용됩니다.

A/V 에지 서비스는 Lync Server PowerShell 및 CsAVEdgeConfiguration cmdlet을 사용해서만 관리할 수 있습니다.

## 이 단원의 내용

  - [A/V 에지 서버 구성 정보 반환](lync-server-2013-return-a-v-edge-server-configuration-information.md)

  - [A/V 에지 서버 구성 설정 모음 만들기 또는 수정](lync-server-2013-create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)

  - [기존 A/V 에지 서버 구성 설정 모음 삭제](lync-server-2013-delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)

