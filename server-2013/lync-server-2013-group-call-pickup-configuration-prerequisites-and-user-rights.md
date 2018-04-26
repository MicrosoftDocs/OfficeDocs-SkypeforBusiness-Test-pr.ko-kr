---
title: 그룹 호출 받기 구성 필수 구성 요소 및 사용자 권한
TOCTitle: 그룹 호출 받기 구성 필수 구성 요소 및 사용자 권한
ms:assetid: 8757b1d3-751d-49c3-b1b8-b678f663f18e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945641(v=OCS.15)
ms:contentKeyID: 52056885
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 그룹 호출 받기 구성 필수 구성 요소 및 사용자 권한

 

_**마지막으로 수정된 항목:** 2013-01-30_

그룹 호출 받기는 Enterprise Voice를 배포할 때 기본적으로 설치되는 통화 관리 기능입니다. 이 항목에서는 그룹 호출 받기를 구성하기 위해 필요한 항목과 구성 작업을 수행하는 데 필요한 사용자 권한에 대해 설명합니다.

이 섹션에서는 그룹 호출 받기 관련 계획 설명서([Lync Server 2013의 그룹 호출 받기 계획](lync-server-2013-planning-for-group-call-pickup.md) 참조)를 읽어 두었다고 가정합니다.

## 그룹 호출 받기 구성 필요 조건

그룹 호출 받기를 사용하려면 다음 구성 요소가 필요합니다.

  - 응용 프로그램 서비스

  - 통화 대기 응용 프로그램

이러한 응용 프로그램은 Enterprise Voice를 배포할 때 자동으로 설치됩니다.

## 그룹 호출 받기 구성 사용자 권한

다음 관리 도구를 사용하여 그룹 호출 받기를 구성합니다.

  - Lync Server 관리 셸

  - SEFAUtil 리소스 키트 도구

Lync Server 관리 셸을 사용하여 통화 대기 파킹된 통화 번호 테이블에서 호출 받기 그룹을 만들고 관리합니다. 호출 받기 그룹을 할당하고 사용자에 대해 그룹 호출 받기를 사용하거나 사용하지 않도록 설정하려면 SEFAUtil 리소스 키트 도구를 사용합니다.

그룹 호출 받기를 구성하려면 작업에 따라 다음과 같은 관리 역할이 필요합니다.

  - **CsVoiceAdministrator:** 이 관리자 역할은 모든 음성 관련 설정 및 정책을 만들고 구성하고 관리할 수 있습니다.

  - **CsUserAdministrator:** 이 관리자 역할은 음성 정책에서 사용자에 대해 그룹 호출 받기를 사용하도록 설정할 수 있습니다. 또한 이 관리자 역할은 모든 음성 구성에 대한 읽기 전용 액세스 권한을 가집니다.

  - **CsServerAdministrator:** 이 관리자 역할은 서버 및 서비스를 관리 및 모니터링하고 관련 문제를 해결할 수 있습니다.

  - **CsAdministrator:** 이 관리자 역할은 CsVoiceAdministrator, CsServerAdministrator 및 CsUserAdministrator 역할이 수행하는 모든 작업을 수행할 수 있습니다.


> [!NOTE]
> 관리 권한에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-planning-for-role-based-access-control.md">Lync Server 2013의 역할 기반 액세스 제어 계획</A>를 참조하십시오.



## 참고 항목

#### 개념

[Lync Server 2013에서 Enterprise Voice 배포](lync-server-2013-deploying-enterprise-voice.md)  

#### 기타 리소스

[Lync Server 2013의 통화 관리 기능 계획](lync-server-2013-planning-for-call-management-features.md)

