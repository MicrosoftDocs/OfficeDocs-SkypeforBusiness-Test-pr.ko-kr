---
title: 'Lync Server 2013: Enterprise Voice로 사용자 이동'
TOCTitle: Enterprise Voice로 사용자 이동
ms:assetid: a2df6d51-5cf2-4d3e-8f97-496af5fd5e5e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412758(v=OCS.15)
ms:contentKeyID: 49304592
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Enterprise Voice로 사용자 이동

 

_**마지막으로 수정된 항목:** 2012-10-18_

기존 PBX 전화 통신 인프라에서 Enterprise Voice로 사용자를 이동할 경우, 배포 프로세스에는 [Lync Server 2013의 Enterprise Voice 계획](lync-server-2013-planning-for-enterprise-voice.md)에서 이미 설명한 계획 프로세스에 포함되지 않는 몇 가지 단계가 포함됩니다. 초기 Enterprise Voice 배포로부터 사용자를 마이그레이션하는 방법에 대한 자세한 내용은 설치 미디어에 포함된 마이그레이션 문서를 참조하십시오.

사용자를 기존 전화 통신 인프라에서 Enterprise Voice로 이동하는 프로세스는 다음 단계로 구성됩니다.

1.  기본 전화 번호 지정

2.  사용자가 Enterprise Voice를 사용할 수 있도록 설정

3.  사용자에 대한 다이얼 플랜 준비

4.  사용자 음성 정책 계획

5.  통화 경로 계획

6.  Enterprise Voice를 사용할 수 있는 사용자에 대한 통화를 다시 라우팅하도록 PBX 또는 SIP 트렁크 구성

7.  Exchange 통합 메시징(UM)으로 사용자 이동(권장)

이 항목에서는 각 단계에 필요한 계획에 대해 설명합니다.

## 1단계. 기본 전화 번호 지정

Enterprise Voice는 음성을 다른 메시징 미디어와 통합하며, 걸려오는 전화가 서버에 도착하면 서버에서 번호를 사용자의 SIP-URI에 매핑한 후 통화를 해당 SIP-URI에 연결된 모든 클라이언트 끝점으로 분기합니다. 이 프로세스에서는 각 사용자가 기본 전화 번호와 연결되어야 합니다.

기본 전화 번호는 다음 사항을 충족해야 합니다.

  - 전역적으로 고유하거나 내부 내선 번호의 경우 엔터프라이즈 내에서 고유해야 합니다.

  - 엔터프라이즈에서 소유하고 라우팅할 수 있어야 합니다. 개인 번호는 사용하면 안 됩니다.

Active Directory 도메인 서비스에는 엔터프라이즈 사용자의 전화 번호가 두 개 이상 나열될 수 있습니다. 특정 사용자와 연결된 모든 전화 번호는 Active Directory 사용자 및 컴퓨터 스냅인의 해당 사용자에 대한 속성 시트에서 보거나 변경할 수 있습니다.

**사용자 속성** 대화 상자의 **일반** 탭에 있는 **전화 번호** 상자에는 사용자의 기본 회사 전화 번호가 포함되어야 합니다. 일반적으로 이 번호가 사용자의 기본 전화 번호로 지정됩니다.

일부 사용자에게 특별한 요구 사항이 있을 수도 있지만(예: 걸려오는 모든 전화가 비서를 통해 라우팅되기를 원하는 중역) 이러한 예외는 요구가 분명하고 중요한 경우로만 제한되어야 합니다.

기본 전화 번호를 선택한 후 다음 작업을 수행해야 합니다.

  - 가능한 경우 기본 전화 번호를 E.164 형식으로 정규화해야 합니다.

  - 기본 전화 번호를 Active Directory **msRTCSIP-line** 특성에 복사해야 합니다.
    

    > [!NOTE]
    > <STRONG>RCC(원격 통화 제어)와 동시 사용</STRONG><BR>RCC는 Lync Server을 사용하여 일반 PBX 전화기를 모니터링하고 제어할 수 있는 기능입니다. 제어는 PBX에 대한 게이트웨이 역할을 하는 서버를 통해 라우팅됩니다. 사용자가 RCC 및 Enterprise Voice 둘 다를 사용할 수 있도록 구성할 수 없지만 줄 URI 설정은 어느 경우든 사용자의 기본 전화 번호를 지정합니다.<BR>선택한 사용자가 기존 PBX 인프라를 계속 사용하도록 하려면 조직에 단계적으로 Enterprise Voice를 도입할 수 있습니다. 이 배포 시나리오에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-direct-sip-deployment-options.md">Lync Server 2013의 직접 SIP 배포 옵션</A>을 참조하십시오.<BR>이전 버전에서는 사용자가 RCC 및 Enterprise Voice를 모두 사용하도록 설정할 수 있었습니다. 단, 이 기능은 사용자에 대해 걸려오는 전화가 사용자의 PBX 전화기 및 Communicator를 동시에 울리는 기능인 이중 분기가 구성된 경우에만 사용할 수 있습니다. Lync Server 2010에서는 이중 분기가 지원되지 않습니다.



**msRTCSIP-line** 특성을 채우는 세 가지 방법은 다음과 같습니다.

  - Microsoft Identity Integration Server(권장)

  - Lync Server 제어판의 **사용자** 페이지

많은 전화 번호를 처리해야 하는 경우 조직에서 사용자 지정하여 개발한 스크립트를 사용하는 것이 좋습니다. 조직이 AD DS(Active Directory 도메인 서비스)에 전화 번호를 표시하는 조직의 방식에 따라 스크립트에서 기본 전화 번호를 **msRTCSIP-line** 특성으로 복사하기 전에 E.164 형식으로 정규화해야 할 수 있습니다.

  - 조직이 AD DS(Active Directory 도메인 서비스)에서 모든 전화 번호를 단일 형식으로 유지 관리하고 해당 형식이 E.164이면 스크립트에서는 각 기본 전화 번호를 **msRTCSIP-line** 특성에 쓰기만 하면 됩니다.

  - 반면 조직이 AD DS(Active Directory 도메인 서비스)에서 모든 전화 번호를 단일 형식으로 유지 관리하지만 해당 형식이 E.164가 아니면 스크립트에서 기본 전화 번호를 **msRTCSIP-line** 특성에 쓰기 전에 기존 형식에서 E.164로 변환하는 정규화 규칙을 정의해야 합니다.

  - 조직이 AD DS(Active Directory 도메인 서비스)에서 전화 번호에 대해 표준 형식을 적용하지 않는 경우 스크립트에서 기본 전화 번호를 **msRTCSIP-line** 특성에 쓰기 전에 다양한 형식의 기본 전화 번호를 E.164 준수로 변환하는 적합한 정규화 규칙을 정의해야 합니다.

또한 스크립트에서 접두사 **Tel:**을 **msRTCSIP-line** 특성에 각 기본 전화 번호를 쓰기 전에 기본 전화 번호 앞에 삽입해야 합니다.

이 특성에 지정된 번호의 예상 형식은 다음과 같습니다.

  - Tel:+14255550100;ext=50100

  - Tel:5550100(엔터프라이즈 전체의 고유 내선)
    

    > [!IMPORTANT]
    > ABS에서는 Active Directory 도메인 서비스에 액세스할 수 없어 기본 전화 번호를 <STRONG>msRTCSIP-line</STRONG> 특성에 복사할 수 없으므로 ABS(주소록 서비스)에서 정규화를 수행하는 경우에도 Active Directory 도메인 서비스에 있는 각 사용자의 기본 전화 번호를 정규화해야 합니다.



## 2단계. 사용자가 Enterprise Voice를 사용할 수 있도록 설정

사용할 수 있도록 설정할 사용자를 식별하기만 하면 이 단계를 완료하는 데 다른 특별한 계획은 필요하지 않습니다.

## 3단계. 사용자에 대해 다이얼 플랜 준비

Enterprise Voice를 사용할 수 있도록 설정된 사용자는 적절한 다이얼 플랜이 있어야 PSTN에 전화를 걸 수 있습니다. 다이얼 플랜은 전화 인증 및 통화 라우팅을 위해 명명된 위치, 개별 사용자 또는 연락처 개체의 전화 번호를 하나의 표준(E.164) 형식으로 변환하는 명명된 정규화 규칙 집합입니다. 정규화 규칙은 다양한 형식으로 표현된 전화 번호를 지정된 각 위치, 사용자 또는 연락처 개체에 대해 라우팅하는 방법을 정의합니다.

다이얼 플랜을 준비하는 방법에 대한 자세한 내용은 [Lync Server 2013의 다이얼 플랜 및 정규화 규칙](lync-server-2013-dial-plans-and-normalization-rules.md)을 참조하십시오.

## 4단계. 사용자 음성 정책 계획

회사 전화에서 장거리 또는 국제 전화를 걸 수 있는 권한 등 기존 PBX에 대한 사용자의 서비스 클래스 설정은 사용자에 대한 VoIP 정책이 Enterprise Voice로 이동함에 따라 다시 구성되어야 합니다. Enterprise Voice에 대한 정책을 계획하고 만드는 방법에 대한 자세한 내용은 [Lync Server 2013의 음성 정책](lync-server-2013-voice-policies.md)을 참조하십시오.

## 5단계. 아웃바운드 통화 경로 계획

통화 경로는 Lync Server에서 Enterprise Voice 사용자가 걸어온 아웃바운드 통화를 처리하는 방법을 지정합니다. 사용자가 전화를 걸면 서버는 필요한 경우 전화 걸기 문자열을 E.164 형식으로 정규화하고 SIP URI에 일치시키려고 합니다. 일치시킬 수 없는 경우 서버는 해당 번호에 기초하여 아웃바운드 통화 라우팅 논리를 적용합니다. 해당 논리를 정의하는 마지막 단계는 각 다이얼 플랜에 나열된 각 대상 전화 번호 집합에 대한 별도의 명명된 통화 경로를 만드는 것입니다.

통화 경로를 계획하는 방법에 대한 자세한 내용은 [Lync Server 2013의 음성 경로](lync-server-2013-voice-routes.md)를 참조하십시오.

## 6단계. Enterprise Voice 사용자에 대한 통화를 다시 라우팅하도록 PBX 또는 SIP 트렁크 구성

ITSP(인터넷 전화 통신 서비스 공급자)에 연결된 일반 PBX 또는 SIP 트렁크 연결에서 이전에 호스팅된 사용자는 이동 후에도 전화 번호가 유지됩니다. 이동 후 Enterprise Voice 사용자에게 걸려온 전화를 중재 서버로 라우팅하도록 PBX 또는 SIP 트렁크를 다시 구성하기만 하면 됩니다.

## 7단계. Exchange 통합 메시징으로 사용자 이동(권장)

사용자를 Exchange 통합 메시징으로 이동하는 과정은 다음 작업으로 구성됩니다.

  - Exchange 통합 메시징 및 Lync Server가 함께 작동할 수 있도록 구성합니다.

  - 사용자가 Exchange 통합 메시징 통화 응답 및 Outlook Voice Access를 사용할 수 있도록 설정합니다. 이 작업은 Exchange 통합 메시징 서버에서 수행됩니다. 자세한 내용은 Exchange Server 2010 TechNet 라이브러리( [http://go.microsoft.com/fwlink/?linkid=139372\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=139372%26clcid=0x412))를 참조하십시오.

