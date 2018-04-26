---
title: 사용자에 대한 전화 통신 구성
TOCTitle: 사용자에 대한 전화 통신 구성
ms:assetid: 4546432e-c839-4517-a2c5-bc0d4d8c6a03
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520988(v=OCS.15)
ms:contentKeyID: 49303491
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자에 대한 전화 통신 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

전화 통신 설정은 사용자에 대해 Lync Server 제어판에서 구성할 수 있는 사용자 계정의 개별 설정 중 일부입니다(개별 사용자가 Lync Server 2013에 대해 사용하도록 설정되었으며 조직에서 전화 통신을 지원하는 경우).

Lync Server 사용자 전화 통신 옵션에는 다음이 포함됩니다.

  - **오디오/비디오 사용 안 함**   사용자가 음성과 화상을 사용하여 전화를 할 수 없습니다.

  - **PC 대 PC 전용**   사용자가 PC 대 PC 음성 통화 또는 화상 통화만 할 수 있습니다.

  - **Enterprise Voice**   사용자가 Lync Server 2013 인프라를 사용하여 수신 전화와 발신 전화를 모두 라우팅할 수 있으며, PC 대 PC 통화도 할 수 있습니다.

  - **원격 통화 제어** 사용자가 Lync Server 2013을 사용하여 데스크톱 전화를 제어하고 PC 대 PC 통화도 할 수 있습니다.

조직의 전화 통신 구성에 대한 자세한 내용은 배포 설명서에서 [사용자에 대한 전화 통신 구성](lync-server-2013-configure-telephony-for-a-user.md) 및 [Lync Server 2013에서 Enterprise Voice 배포](lync-server-2013-deploying-enterprise-voice.md)를 참조하십시오.

## 특정 사용자 계정에 대해 전화 통신을 구성하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **사용자 검색** 상자에 원하는 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 처음 부분을 입력하고 **찾기**를 클릭합니다.

5.  표에서 수정할 사용자 계정을 클릭합니다.

6.  **편집** 메뉴에서 **수정**을 클릭합니다.

7.  **전화 통신**에서 다음을 수행합니다.
    
      - 사용자에 대해 음성 및 화상 통화를 사용하지 않도록 설정하려면 **오디오/비디오 사용 안 함**을 클릭합니다.
    
      - 사용자에 대해 PC 대 PC 음성 통신을 사용하도록 설정하고 원격 통화 제어 또는 Enterprise Voice는 사용하도록 설정하지 않으려면 **PC 대 PC 전용**을 클릭합니다. 사용자가 PC 대 PC 음성 통신에 사용하는 전화에 대해 **줄 URI**의 값을 지정합니다.
    
      - 서비스 정책 클래스에 따라 Lync Server 2010 인프라를 사용하여 사용자의 전화 통화(PC 대 PC 음성 통신 포함)를 라우팅하려면 **Enterprise Voice**를 클릭합니다. **줄 URI**에서 Enterprise Voice의 전화 번호를 지정합니다. **다이얼 플랜 정책** 및 **음성 정책**에서 사용자에게 적절한 정책을 지정합니다. 사용자가 건 전화 번호를 E.164 형식으로 변환하는 정규화 규칙을 지정하려면 **위치 정책**에서 적절한 위치 프로필을 선택합니다.
    
      - 사용자가 Lync Server 2013에서 일반 전화선을 제어하여 PC 대 PC 통화 및 PC 대 전화기 통화를 할 수 있도록 원격 통화 제어를 사용하도록 설정하려면 **원격 통화 제어**를 클릭합니다. **줄 URI**에서 원격 통화 제어에 대해 전화 번호를 지정합니다. 사용자에게는 데스크톱 전화가 있어야 하며 통화 라우팅을 위한 PBX(Private Branch Exchange) 연결을 사용할 수 있어야 합니다.

## 참고 항목

#### 기타 리소스

[사용자 계정 속성 수정](lync-server-2013-modifying-user-account-properties.md)

