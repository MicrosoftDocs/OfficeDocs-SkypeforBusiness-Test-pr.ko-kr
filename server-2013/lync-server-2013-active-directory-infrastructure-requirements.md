---
title: 'Lync Server 2013: Active Directory 인프라 요구 사항'
TOCTitle: Active Directory 인프라 요구 사항
ms:assetid: c2086f7b-662f-4179-ab99-2c0311ebd903
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412955(v=OCS.15)
ms:contentKeyID: 49304930
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 Active Directory 인프라 요구 사항

 

_**마지막으로 수정된 항목:** 2013-11-07_

Lync Server 2013에 대해 Active Directory 도메인 서비스 준비 프로세스를 시작하려면 Active Directory 인프라가 다음 필수 구성 요소를 충족해야 합니다.

  - Lync Server을 배포하는 포리스트의 모든 도메인 컨트롤러(모든 전역 카탈로그 서버 포함)에서 다음 운영 체제 중 하나를 실행해야 합니다.
    
      - Windows Server 2012 R2 운영 체제
    
      - Windows Server 2012 운영 체제
    
      - Windows Server 2008 R2 운영 체제
    
      - Windows Server 2008 운영 체제
    
      - Windows Server 2008 Enterprise 32비트
    
      - 32비트 또는 64비트 버전의 Windows Server 2003 R2 운영 체제
    
      - 32비트 또는 64비트 버전의 Windows Server 2003 운영 체제

  - Lync Server를 배포한 모든 도메인을 Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008 또는 Windows Server 2003 이상의 도메인 기능 수준으로 올려야 합니다.

  - Lync Server를 배포한 포리스트를 Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008 또는 Windows Server 2003 이상의 포리스트 기능 수준으로 올려야 합니다.
    

    > [!NOTE]
    > 도메인 또는 포리스트 기능 수준을 변경하려면 "도메인 및 포리스트 기능 수준 올리기"( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=263775">http://go.microsoft.com/fwlink/?linkid=263775</A>)를 참조하십시오.



  - Lync Server 컴퓨터나 사용자를 배포하는 모든 도메인에 전역 카탈로그가 배포되어야 합니다.

Lync Server 2013은 Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008 및 Windows Server 2003 운영 체제에서 유니버설 그룹을 지원합니다. 유니버설 그룹의 구성원은 도메인 트리 또는 포리스트에 있는 도메인의 다른 그룹 및 계정을 포함할 수 있고 도메인 트리 또는 포리스트에 있는 도메인의 사용 권한이 할당될 수 있습니다. 관리자 위임과 결합된 유니버설 그룹 지원을 통해 Lync Server 배포를 매우 간단하게 관리할 수 있습니다. 예를 들어 한 도메인을 다른 도메인에 추가하지 않아도 관리자가 둘 다 관리할 수 있습니다.

