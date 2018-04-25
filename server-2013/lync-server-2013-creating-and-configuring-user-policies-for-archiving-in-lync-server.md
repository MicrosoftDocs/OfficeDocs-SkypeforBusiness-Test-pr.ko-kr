---
title: Lync Server에서 보관용 사용자 정책 만들기 및 구성
TOCTitle: Lync Server에서 보관용 사용자 정책 만들기 및 구성
ms:assetid: 5af0e605-3563-4d6f-a3c6-511d204a3165
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204923(v=OCS.15)
ms:contentKeyID: 49303738
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server에서 보관용 사용자 정책 만들기 및 구성

 

_**마지막으로 수정된 항목:** 2012-10-09_

Lync Server에 있는 특정 사용자에 대해 보관을 사용하거나 사용하지 않도록 설정하려면 먼저 사용자 정책을 만들고 하나 이상의 사용자 또는 사용자 그룹에 정책을 적용해야 합니다. 특정 사용자 및 사용자 그룹에 사용자 정책을 적용하는 방법에 대한 자세한 내용은 배포 설명서에서 [사용자에게 Lync Server 보관 정책 적용](lync-server-2013-applying-a-lync-server-archiving-policy-to-a-user.md)을 참조하십시오.

전역, 사이트 및 사용자 프로필에 대한 계층을 포함하여 보관 정책의 작동 방법에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 배포에 Microsoft Exchange 통합을 사용하도록 설정할 경우 Exchange 원본 위치 유지 정책은 Exchange 2013에 있고 사서함이 원본 위치 유지로 설정된 사용자에 대해 보관을 설정할지 여부를 제어합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.<BR>보관을 사용하도록 설정하기 전에 보관 구성에서 모든 적합한 옵션을 지정해야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-archiving-options.md">보관 옵션 구성</A>을 참조하십시오.



## Lync Server에 있는 사용자에 대한 보관 정책을 구성하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 지정된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 열고 관리 URL을 입력하여 Lync Server 2013 제어판을 엽니다. Lync Server 2013 제어판을 시작하기 위해 사용할 수 있는 여러 방법들에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 정책**을 클릭합니다.

4.  **새로 만들기**를 클릭하고 **사용자 정책**을 클릭합니다.

5.  **새 보관 정책**에서 다음을 수행합니다.
    
      - **이름**에 사용자 정책의 이름을 지정합니다.
    
      - **설명**에서 사용자 정책에 대한 정보를 입력합니다(예: 법률 부서용 사용자 정책).
    
      - 사용자 정책에 대한 내부 통신 보관을 제어하려면 **내부 통신 보관** 확인란을 선택하거나 선택을 취소합니다.
    
      - 사용자 정책에 대한 외부 통신 보관을 제어하려면 **외부 통신 보관** 확인란을 선택하거나 선택을 취소합니다.

6.  **커밋**을 클릭합니다.

사용자 정책은 해당 정책을 지정한 사용자에게만 적용됩니다. 사용자 정책을 특정 사용자에게 적용하는 방법에 대한 자세한 내용은 배포 설명서에서 [사용자에게 Lync Server 보관 정책 적용](lync-server-2013-applying-a-lync-server-archiving-policy-to-a-user.md)을 참조하십시오.

