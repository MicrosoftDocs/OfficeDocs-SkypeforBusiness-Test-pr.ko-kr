---
title: 'Lync Server 2013: 통화 대기 구성 필수 구성 요소 및 사용자 권한'
TOCTitle: 통화 대기 구성 필수 구성 요소 및 사용자 권한
ms:assetid: 25b8cfe0-e4e7-487c-9e78-8c040f629059
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425730(v=OCS.15)
ms:contentKeyID: 49303084
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 대기 구성 필수 구성 요소 및 사용자 권한

 

_**마지막으로 수정된 항목:** 2012-09-10_

통화 대기는 Enterprise Voice를 배포할 때 기본적으로 설치되는 통화 관리 기능입니다. 이 항목에서는 통화 대기를 구성하기 위해 필요한 항목과 구성 작업을 수행하는 데 필요한 사용자 권한에 대해 설명합니다.


> [!IMPORTANT]
> 통화 대기 응용 프로그램에 대해 사용자 지정된 대기 음악 파일은 Lync Server 2013 재해 복구 프로세스의 일부분으로 백업되지 않으며 풀에 업로드된 파일이 손상되거나 지워지면 이러한 파일은 손실됩니다. 따라서 통화 대기용으로 업로드한 사용자 지정된 대기 음악 파일의 백업 복사본을 항상 별도로 보관해 두어야 합니다.



이 섹션에서는 통화 대기 관련 계획 설명서의 내용을 확인했다고 가정합니다( [Lync Server 2013의 통화 관리 기능 계획](lync-server-2013-planning-for-call-management-features.md) 참조).

## 통화 대기 구성 필수 구성 요소

통화 대기에는 다음 구성 요소가 필요합니다.

  - 응용 프로그램 서비스

  - 통화 대기 응용 프로그램

이러한 응용 프로그램은 Enterprise Voice를 배포할 때 자동으로 설치됩니다.

통화 대기 시 발신자에게 음악이 재생되도록 하려면 대기 음악 파일도 필요합니다. 기본 대기 음악 파일은 Enterprise Voice를 배포할 때 자동으로 설치됩니다. 기본 파일을 원하는 대기 음악 파일로 대체할 수 있습니다. 통화 대기에서는 파일 저장소를 사용하여 오디오 파일을 저장합니다.

## 통화 대기 구성 사용자 권한

다음 관리 도구를 사용하여 통화 대기을 구성할 수 있습니다.

  - Lync Server 제어판

  - Lync Server 관리 셸

이러한 도구를 사용하여 통화 대기 파킹된 통화 번호 테이블을 설정하고 통화 대기에 사용되는 기타 설정을 구성합니다.

통화 대기를 구성하려면 작업에 따라 다음과 같은 관리 역할이 필요합니다.

  - **CsVoiceAdministrator :** 이 관리자 역할은 모든 음성 관련 설정 및 정책을 만들고 구성하고 관리할 수 있습니다.

  - **CsUserAdministrator :** 이 관리자 역할은 음성 정책에서 통화 대기를 사용하도록 설정할 수 있습니다. 또한 이 관리자 역할은 모든 음성 구성에 대한 읽기 전용 액세스 권한을 가집니다.

  - **CsServerAdministrator :** 이 관리자 역할은 서버 및 서비스를 관리 및 모니터링하고 관련 문제를 해결할 수 있습니다.

  - **CsAdministrator :** 이 관리자 역할은 CsVoiceAdministrator, CsServerAdministrator 및 CsUserAdministrator 역할이 수행하는 모든 작업을 수행할 수 있습니다.


> [!NOTE]
> 관리 권한에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-planning-for-role-based-access-control.md">Lync Server 2013의 역할 기반 액세스 제어 계획</A>를 참조하십시오.



## 참고 항목

#### 개념

[Lync Server 2013에서 Enterprise Voice 배포](lync-server-2013-deploying-enterprise-voice.md)  

#### 기타 리소스

[Lync Server 2013의 통화 관리 기능 계획](lync-server-2013-planning-for-call-management-features.md)

