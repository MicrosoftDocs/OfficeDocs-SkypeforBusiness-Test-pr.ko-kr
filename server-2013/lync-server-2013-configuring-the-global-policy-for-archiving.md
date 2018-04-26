---
title: 보관에 대한 글로벌 정책 구성
TOCTitle: 보관에 대한 글로벌 정책 구성
ms:assetid: 58341d6b-c3ff-4dd9-b1c7-0048f33861ca
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204906(v=OCS.15)
ms:contentKeyID: 49303699
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관에 대한 글로벌 정책 구성

 

_**마지막으로 수정된 항목:** 2012-10-09_

프런트 엔드 서버를 배포하면 Lync Server가 보관에 대한 글로벌 정책을 만듭니다. 기본적으로 보관은 글로벌 정책에서 사용하지 않도록 설정됩니다. 글로벌 정책은 글로벌 정책을 무시하는 사이트 또는 사용자 정책을 설정하지 않는 한 또는 전체 또는 일부 사용자에 대해 Microsoft Exchange 통합을 사용하지 않는 한 전체 배포의 내부 및 외부 통신에 대해 보관을 사용하도록 설정할지 여부를 제어합니다. Microsoft Exchange 통합을 사용할 경우 글로벌 정책은 Exchange 2013에 있고 사서함이 원본 위치 유지로 설정된 사용자에게 적용되지 않습니다.

전역, 사이트 및 사용자 정책의 계층을 포함하여 보관 정책의 작동 방법에 대한 자세한 내용은 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md) 계획 설명서, 배포 설명서 또는 작업 설명서를 참조하십시오.


> [!NOTE]
> 배포에 Microsoft Exchange 통합을 사용하도록 설정할 경우 Exchange 원본 위치 유지 정책은 Exchange 2013에 있고 사서함이 원본 위치 유지로 설정된 사용자에 대해 보관을 설정할지 여부를 제어합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.<BR>보관을 사용하도록 설정하기 전에 보관 구성에서 모든 적합한 옵션을 지정해야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-archiving-options.md">보관 옵션 구성</A>을 참조하십시오.



## Lync Server 보관 데이터베이스를 사용할 때 보관에 대한 글로벌 정책을 구성하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 지정된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 열고 관리 URL을 입력하여 Lync Server 2013 제어판을 엽니다. Lync Server 2013 제어판을 시작하기 위해 사용할 수 있는 여러 방법들에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 정책**을 클릭합니다.

4.  **보관 정책** 페이지에서 **전역**을 클릭하고 **편집**을 클릭한 후에 **세부 정보 표시**를 클릭합니다.

5.  **보관 정책 편집 - 전역**에서 다음을 수행합니다.
    
      - **이름**에서 기본 이름으로 "전역"을 사용하지 않으려는 경우 글로벌 정책에 대해 새 이름을 지정합니다.
    
      - **설명**에서 해당 정책에 대한 정보를 입력합니다(예: *divisionName*용 글로벌 정책).
    
      - 사이트 정책 또는 사용자 정책을 통해 제어되지 않는 모든 사이트 및 사용자에 대한 내부 통신 보관을 제어하려면 **내부 통신 보관** 확인란을 선택하거나 선택을 취소합니다.
    
      - 사이트 정책 또는 사용자 정책을 통해 제어되지 않는 모든 사이트 및 사용자에 대한 외부 통신 보관을 제어하려면 **외부 통신 보관** 확인란을 선택하거나 선택을 취소합니다.

6.  **커밋**을 클릭합니다.

