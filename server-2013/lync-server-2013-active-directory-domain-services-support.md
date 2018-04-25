---
title: 'Lync Server 2013: Active Directory 도메인 서비스 지원'
TOCTitle: Active Directory 도메인 서비스 지원
ms:assetid: aeb62d5e-e424-473a-b795-9452150c98dd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412831(v=OCS.15)
ms:contentKeyID: 49304717
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Active Directory 도메인 서비스 지원

 

_**마지막으로 수정된 항목:** 2013-11-07_

Lync Server 2013는 중앙 관리 저장소를 사용하여 서버 및 서비스에 대한 구성 데이터를 저장합니다(이전 버전에서는 Active Directory 도메인 서비스가 사용됨). Lync Server 2013에서는 AD DS에 다음과 같은 데이터를 저장합니다.

  - **스키마 확장**
    
      - 사용자 개체 확장
    
      - 지원되는 이전 버전과의 호환성을 유지 관리하기 위한 Lync Server 2010 및 Office Communications Server 2007 R2 클래스에 대한 확장

  - **데이터**( Lync Server 2013 확장 스키마 및 기존 클래스에 저장됨)
    
      - 사용자 SIP URI 및 기타 사용자 설정
    
      - 응용 프로그램에 대한 연락처 개체(예: 응답 그룹 응용 프로그램 및 회의 길잡이 응용 프로그램)
    
      - 이전 버전과의 호환성을 위해 게시된 데이터
    
      - 중앙 관리 저장소에 대한 SCP(서비스 연결 지점)
    
      - Kerberos 인증 계정(선택적 컴퓨터 개체)

이 섹션에서는 Lync Server 2013에서의 AD DS 지원 요구 사항에 대해 설명합니다. 토폴로지 지원에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013에서 지원되는 Active Directory 토폴로지](lync-server-2013-supported-active-directory-topologies.md)를 참조하십시오.

## 지원되는 도메인 컨트롤러 운영 체제

Lync Server 2013에서는 다음 운영 체제를 실행하는 도메인 컨트롤러가 지원됩니다.

  - Windows Server 2012 R2 운영 체제

  - Windows Server 2012 운영 체제

  - Windows Server 2008 R2 운영 체제

  - Windows Server 2008 운영 체제

  - Windows Server 2008 Enterprise 32비트

  - 32비트 또는 64비트 버전의 Window Server 2003 R2 운영 체제

  - 32비트 또는 64비트 버전의 Windows Server 2003 운영 체제

## 포리스트 및 도메인 기능 수준

Lync Server 2013을 배포한 모든 도메인을 Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008 또는 Windows Server 2003 이상의 도메인 기능 수준으로 올려야 합니다.

Lync Server 2013을 배포한 모든 포리스트를 Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008 또는 Windows Server 2003 이상의 포리스트 기능 수준으로 올려야 합니다.

## 읽기 전용 도메인 컨트롤러 지원

Lync Server 2013에서는 쓰기 가능한 도메인 컨트롤러를 사용할 수 있는 경우 읽기 전용 도메인 컨트롤러나 읽기 전용 전역 카탈로그 서버를 포함하는 Active Directory 도메인 서비스를 배포할 수 있습니다.

## 도메인 이름

Lync Server는 단일 레이블 도메인을 지원하지 않습니다. 예를 들어 **contoso.local** 라는 루트 도메인으로 구성된 포리스트는 지원되지만 **local** 이라는 루트 도메인은 지원되지 않습니다. 자세한 내용은 Microsoft 기술 자료 문서 300684, "단일 레이블 DNS 이름을 사용하여 Active Directory 도메인을 구성하는 방법에 대한 정보"( [http://go.microsoft.com/fwlink/?LinkId=143752](http://go.microsoft.com/fwlink/?linkid=143752))를 참조하십시오.


> [!NOTE]
> Lync Server에서는 도메인 이름 바꾸기를 지원하지 않습니다. Lync Server가 배포된 도메인을 이름을 바꿔야 하는 경우에는 먼저 Lync Server를 제거하고 도메인 이름을 바꾼 후 Lync Server를 다시 설치해야 합니다.



## 잠겨 있는 AD DS 환경

잠겨 있는 AD DS에서는 관리 위임의 보안을 유지하고 보안 정책 적용을 위한 GPO(그룹 정책 개체) 사용을 활성화하기 위해 사용자 및 컴퓨터 개체를 권한 상속이 비활성화된 특정 OU(조직 구성 단위)에 두는 경우가 자주 있습니다. Lync Server 2013을 잠겨 있는 Active Directory 환경에 배포할 수 있습니다. 잠겨 있는 환경에서 Lync Server를 배포하는 데 필요한 항목에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 잠긴 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md)를 참조하십시오.

