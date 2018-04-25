---
title: 'Lync Server 2013: 알림 구성 필수 구성 요소 및 역할'
TOCTitle: 알림 구성 필수 구성 요소 및 역할
ms:assetid: 82f2dfe9-4c5e-4d65-96a1-96495d506ea4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398658(v=OCS.15)
ms:contentKeyID: 49304226
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 알림 구성 필수 구성 요소 및 역할

 

_**마지막으로 수정된 항목:** 2013-02-25_

알림은 Enterprise Voice 통화 관리 기능입니다. 이 항목에서는 구성 작업을 수행하는 데 필요한 알림 및 역할 지정을 구성하기 전에 충족해야 할 사항에 대해 설명합니다.

이 섹션에서는 알림 관련 계획 설명서( [Lync Server 2013의 통화 관리 기능 계획](lync-server-2013-planning-for-call-management-features.md) 참조)를 읽어 두었다고 가정합니다.

## 알림 구성 필수 구성 요소

알림 응용 프로그램에는 다음 구성 요소가 필요합니다.

  - 응용 프로그램 서비스

  - 응답 그룹 응용 프로그램

  - 오디오 파일을 보관할 파일 저장소

이러한 구성 요소는 모두 Enterprise Voice를 배포할 때 기본적으로 설치됩니다.

## 알림 구성 역할

다음 관리 도구를 사용하여 알림을 구성할 수 있습니다.

  - Lync Server 제어판

  - Lync Server 관리 셸

알림 응용 프로그램 구성에는 다음 관리 역할 중 하나가 필요합니다.

  - **CsVoiceAdministrator**   이 관리자 역할은 알림 설정을 비롯한 모든 음성 관련 설정 및 정책을 만들고 구성하고 관리할 수 있습니다.

  - **CsServerAdministrator**   이 관리자 역할은 서버 및 서비스의 관리, 모니터링 및 문제 해결을 수행하고 모든 알림 설정을 구성할 수 있습니다.

  - **CsAdministrator**   이 관리자 역할은 모든 관리 작업을 수행하고 모든 설정을 수정할 수 있습니다.

  - **CsViewOnlyAdministrator**   이 관리자 역할은 배포를 보고 배포 상태를 모니터링할 수 있습니다.


> [!NOTE]
> 관리 사용자 권한에 대한 자세한 내용은 계획 설명서의 <A href="lync-server-2013-planning-for-role-based-access-control.md">Lync Server 2013의 역할 기반 액세스 제어 계획</A>를 참조하십시오.



## 참고 항목

#### 개념

[Lync Server 2013에서 Enterprise Voice 배포](lync-server-2013-deploying-enterprise-voice.md)  

#### 기타 리소스

[Lync Server 2013의 통화 관리 기능 계획](lync-server-2013-planning-for-call-management-features.md)

