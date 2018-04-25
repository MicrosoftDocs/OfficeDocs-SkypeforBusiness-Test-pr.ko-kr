---
title: 'Lync Server 2013: 지원되는 가상화 기술 및 알려진 제한 사항'
TOCTitle: 지원되는 가상화 기술 및 알려진 제한 사항
ms:assetid: 6d3d749d-e840-4c05-afae-d6e69e7616aa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204982(v=OCS.15)
ms:contentKeyID: 49303961
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 지원되는 가상화 기술 및 알려진 제한 사항

 

_**마지막으로 수정된 항목:** 2015-01-26_

Lync VDI 플러그 인을 사용하면 가상화 기술이 지원된 오디오 및 비디오 통화를 사용할 수 있습니다. 이는 [Microsoft Lync 2010의 클라이언트 가상화](http://go.microsoft.com/fwlink/?linkid=330447) 백서에 설명된 Microsoft Lync Server 2010 기능을 확장합니다. 표준 전화 규정을 준수하기 위한 E911 지원도 포함되어 있습니다. 다음 섹션에서는 Lync VDI 플러그 인이 지원하는 가상화 기술 및 알려진 기능 제한에 대해 설명합니다.

## 가상화 기술 지원

Lync VDI 플러그 인은 개인용 가상 데스크톱 시나리오에서 전체 데스크톱 원격을 지원하지만 원격 데스크톱 세션 시나리오에서는 이를 지원하지 않습니다. 이러한 시나리오에 대한 설명은 다음과 같습니다.

  - **지원됨: 개인용 가상 데스크톱 또는 VDI(가상 데스크톱 인프라).**   이 시나리오에서 각 사용자는 사용자 지정 가능한 가상 데스크톱에 로그온하고 세션 간 동일하게 유지되는 데스크톱에 파일을 저장할 수 있습니다. Microsoft 원격 데스크톱 서비스, VMware Horizon View, Citrix XenDesktop은 Lync에 사용하도록 테스트한 구현입니다. Microsoft의 테스트를 거친 공급업체별 VDI 환경 및 클라이언트 하드웨어에 대한 자세한 내용은 [Microsoft Lync 인증 인프라](http://go.microsoft.com/fwlink/?linkid=313435)를 참조하세요.

  - **지원되지 않음: 원격 데스크톱 세션.**   이 시나리오에서 각 사용자는 사용자 지정할 수 없는 일반 가상 데스크톱 세션에 로그인합니다. 예제 구현에는 RDSH(Microsoft 원격 데스크톱 세션) 및 Citrix Receiver와 결합된 Citrix XenApp이 있습니다.

Lync VDI 플러그 인은 응용 프로그램 가상화와 같이 로컬로 전체 응용 프로그램을 설치하지 않고도 해당 응용 프로그램을 사용할 수 있도록 하는 다른 가상화 기술을 지원하지 않습니다. 예제 구현에는 Citrix XenApp 및 App-V(Microsoft Application Virtualization)가 있습니다. 응용 프로그램 스트리밍, 응용 프로그램 원격, 혼합 가상화 모드(예: 전체 데스크톱 원격의 응용 프로그램 원격)는 지원되지 않습니다.

확장성이 가능하도록 Lync VDI 플러그 인은 DVC(동적 가상 채널)로 불리는 플랫폼 독립적 API를 사용하도록 설계되었습니다. Lync에서 명시적으로 지원하지 않는 시나리오는 VDI 솔루션 공급자의 지원 문을 참조하세요.

## 알려진 기능 제한

다음은 VDI 환경에서 Lync 2013을 사용할 때 알려진 제한 사항입니다.

  - 통화 위임 및 응답 그룹 에이전트 익명화 기능에 대한 지원은 제한적입니다.

  - 다음 기능은 지원되지 않습니다.
    
      - 통합 오디오 장치 및 비디오 장치 조정 페이지
    
      - 다중 보기 비디오
    
      - 대화 기록
    
      - 모임에 익명으로 참가(즉, 조직과 페더레이션되지 않은 다른 조직에서 호스팅되는 Lync 모임에 참가)
    
      - Lync Phone Edition 장치와 함께 Lync VDI 플러그인 사용
    
      - 네트워크 중단 시 통화 지속
    
      - 사용자 지정된 벨 소리 및 대기 음악 기능

  - Lync VDI 플러그 인은 Office 365 환경에서 지원되지 않습니다.

