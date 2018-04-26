---
title: Lync Server 관리 셸
TOCTitle: Lync Server 관리 셸
ms:assetid: 674b523b-c0b7-4ed6-9e67-afa6e8ac7e12
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398474(v=OCS.15)
ms:contentKeyID: 49303877
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 관리 셸

 

_**마지막으로 수정된 항목:** 2012-06-20_

Microsoft Office Communications Server 2007 R2와 비교할 때, Microsoft Lync Server 2010에는 새로운 기능과 개선된 기능이 많이 도입되었습니다. 개선된 기능 중 하나는 구현을 관리하는 방식입니다. 예를 들어, 대부분의 사용자가 Microsoft Management Console에서 사용했던 인터페이스와 크게 달라진 Lync Server 제어판이라는 새로운 사용자 인터페이스가 제공됩니다. 또한, Windows PowerShell이 포함되어 관리 용이성도 크게 향상되었습니다.

Windows PowerShell에서는 명령줄을 통해 Microsoft 응용 프로그램을 관리할 수 있습니다. 여기에는 명령줄 환경, 제품별 명령 및 전체 스크립팅 언어가 포함됩니다. Windows PowerShell은 2006년 말에 Windows 운영 체제용 다운로드 가능한 릴리스로 처음 소개되었으며, Microsoft Exchange Server 2007을 쉽게 관리할 수 있도록 명령줄 인터페이스로 통합되었습니다. 그 이래로 Windows PowerShell은 계속해서 확장되었으며 대부분의 Microsoft Server 제품에 통합되었습니다. Windows PowerShell이 통합된 최신 제품이 Microsoft Lync Server 2013입니다. Lync Server 2010에는 배포의 모든 측면을 관리하는 데 사용할 수 있는 550개에 가까운 제품별 cmdlet이 도입되었습니다.

다음 섹션에는 cmdlet 및 해당 설명 목록이 나와 있습니다. 이 정보는 명령줄에서 직접 확인할 수도 있습니다. 이렇게 하려면 Lync Server 관리 셸 명령 프롬프트에 다음 명령을 입력하면 됩니다.

    Get-Help <cmdlet name> -Full

예를 들어 명령 프롬프트에서 **New-CsVoicePolicy** cmdlet에 대한 도움말을 검색하려면 다음을 입력합니다.

    Get-Help New-CsVoicePolicy -Full

다음은 Lync Server 2013의 Windows PowerShell에 대해 고려할 사항입니다.

  - Lync Server cmdlet을 실행하려면 Lync Server 관리 셸을 엽니다.
    

    > [!WARNING]
    > Lync Server 관리 셸을 열지 않고 Windows PowerShell 창을 여는 경우에는 기본적으로 Lync Server cmdlet을 실행할 수 없습니다. Windows PowerShell 내에서 Lync Server cmdlet을 실행하려면 먼저 Windows PowerShell 명령 프롬프트에 다음을 입력합니다.<BR>Import-Module Lync



  - Lync Server 관리 셸은 모든 Lync Server Enterprise Edition 프런트 엔드 서버 또는 Standard Edition 서버에 자동으로 설치됩니다.

  - 새로운 정보와 업데이트된 정보, 샘플 스크립트 그리고 Windows PowerShell 및 Microsoft Lync Server 2013 cmdlet을 실행하고 cmdlet에 대해 자세히 알아보는 데 사용할 수 있는 도움말은 Lync Server Windows PowerShell 블로그([http://go.microsoft.com/fwlink/?linkid=203150\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412))에서 확인할 수 있습니다.

