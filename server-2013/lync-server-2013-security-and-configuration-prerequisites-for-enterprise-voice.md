---
title: 'Lync Server 2013: Enterprise Voice에 대한 보안 및 구성 필수 구성 요소'
TOCTitle: Enterprise Voice에 대한 보안 및 구성 필수 구성 요소
ms:assetid: 15354abe-733e-466b-bcd4-a6cfbf58caf8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398221(v=OCS.15)
ms:contentKeyID: 49302901
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Enterprise Voice에 대한 보안 및 구성 필수 구성 요소

 

_**마지막으로 수정된 항목:** 2012-10-18_

인프라가 다음과 같은 보안, 사용자 구성 및 시나리오별 하드웨어 필수 구성 요소를 충족하는지 확인합니다.

## 관리 권한 및 인증서 인프라

환경이 Enterprise Voice 배포 프로세스 중에 사용할 다음과 같은 관리 사용자 그룹 및 인증서 인프라로 구성되어 있는지 확인합니다.

  - Enterprise Voice를 배포하는 관리자는 RTCUniversalServerAdmins 그룹의 구성원이어야 합니다.

  - 구성 작업을 수행하는 관리자에게는 적절한 권한이 있어야 합니다.
    
      - **CsVoiceAdministrator:** 이 관리자 역할은 음성 구성 작업을 수행하고, 음성 응용 프로그램을 관리하고, 최종 사용자에게 음성 정책을 할당할 수 있습니다.
    
      - **CsUserAdministrator:** 이 관리자 역할은 사용자에 대해 Enterprise Voice를 사용하도록 설정하는 것과 같이 사용자 속성을 관리할 수 있습니다. 또한 이 관리자 역할은 사용자별 정책도 할당할 수 있습니다. 단, 보관 정책/사용자 이동/공통 영역 전화 및 아날로그 장치 관리는 예외입니다.
    
      - **CsAdministrator:** 이 관리자 역할은 CsVoiceAdministrator 및 CsUserAdministrator의 모든 작업을 수행할 수 있습니다.
    

    > [!NOTE]
    > 위임을 사용하면 리소스에 대한 액세스를 불필요하게 확대하지 않고도 더 많은 관리자가 Lync Server 배포에 참가할 수 있습니다.



  - Microsoft 또는 타사 CA(인증 기관) 인프라를 사용하여 MKI(관리 키 인프라)가 배포 및 구성됩니다.
    

    > [!NOTE]
    > Lync Server의 인증서 요구 사항에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-certificate-infrastructure-requirements.md">Lync Server 2013에 대한 인증서 인프라 요구 사항</A>을 참조하십시오.



## 사용자 구성

프런트 엔드 배포 중에 중재 서버를 각 프런트 엔드 풀 또는 Standard Edition 서버와 함께 배치한 경우에는 이러한 서버 역할용 파일을 설치하는 동안 Enterprise Voice에 필요한 사용자 설정이 자동으로 구성됩니다.

Enterprise Voice 작업을 새로 배포하는 경우에는 배포 프로세스를 시작하기 전에 Enterprise Voice를 사용하도록 설정할 각 사용자에 대해 기본 전화 번호를 지정합니다. 관리자는 이 번호가 고유한지 확인해야 합니다. 모든 기본 전화 번호는 구현 전에 정규화(올바른 형식으로 지정)한 다음 Lync Server 제어판을 사용하여 각 사용자의 **줄 URI** 속성으로 복사해야 합니다.


> [!NOTE]
> Enterprise Voice 배포에 필요한 기본 전화 번호의 예는 계획 설명서에서 <A href="lync-server-2013-dial-plans-and-normalization-rules.md">Lync Server 2013의 다이얼 플랜 및 정규화 규칙</A>의 <A href="lync-server-2013-dial-plans-and-normalization-rules.md">Lync Server 2013의 다이얼 플랜 및 정규화 규칙</A> 섹션을 참조하십시오.



## 다음 단계: 파일 설치 또는 PSTN 연결 구성

Enterprise Voice에 대한 소프트웨어 및 환경 필수 구성 요소를 확인한 후에는 다음 콘텐츠를 참조하여 아래와 같은 작업을 수행할 수 있습니다.

  - [Lync Server 2013에서 중재 서버용 파일 설치](lync-server-2013-install-the-files-for-mediation-server.md)에 설명된 대로 중재 서버를 설치합니다. 단, 중재 서버는 배치 시에 프런트 엔드 풀 또는 Standard Edition 서버 배포 프로세스의 일부로 설치되므로, 독립 실행형 중재 서버 또는 풀을 배포하려는 경우에만 중재 서버를 설치합니다.

  - 또는 [Lync Server 2013에서 트렁크 구성](lync-server-2013-configuring-trunks.md)에 설명된 대로 Enterprise Voice 사용자에 대해 통화를 라우팅하는 설정 구성을 시작합니다.

