---
title: 보관용 사이트 정책 설정
TOCTitle: 보관용 사이트 정책 설정
ms:assetid: dc2ea206-8b9c-44dd-a479-efb217593c89
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205325(v=OCS.15)
ms:contentKeyID: 49305235
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관용 사이트 정책 설정

 

_**마지막으로 수정된 항목:** 2012-10-09_

특정 사이트에 대한 보관 기능을 사용하거나 사용하지 않도록 설정하려면 각 사이트에 대한 보관 정책을 만들고 구성합니다. 사이트 정책은 글로벌 정책을 재정의하지만 사용자 정책은 사이트 정책을 재정의합니다. 보관 정책은 Microsoft Exchange 통합을 사용하지 않는 경우나 Microsoft Exchange 통합을 사용하지만 일부 사용자가 Exchange 2013로 이동되지 않으며 해당 사서함이 원본 위치 유지 상태인 경우에만 적용됩니다.

전역, 사이트 및 사용자 정책의 계층 구조를 비롯한 보관 정책의 작동 방식에 대한 자세한 내용은 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md) 계획 설명서, 배포 설명서 또는 운영 설명서를 참조하십시오.


> [!NOTE]
> 배포에 대해 Microsoft Exchange 통합을 사용하도록 설정하면 Exchange 원본 위치 유지 정책에 의해 Exchange 2013로 이동되는 사용자에 대해 보관을 사용할 수 있는지 여부가 제어되고 해당 사서함이 원본 위치 유지 상태가 됩니다. 자세한 내용은 배포 설명서의 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.<BR>보관 정책에서 내부 또는 외부 통신 보관을 사용하도록 설정하기 전에 보관 구성에서 적절한 옵션을 모두 지정해야 합니다. 자세한 내용은 배포 설명서의 <A href="lync-server-2013-configuring-archiving-options.md">보관 옵션 구성</A>을 참조하십시오.



## 사이트에 대한 보관 정책을 만들려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정으로 내부 배포의 컴퓨터에 로그인합니다.

2.  브라우저 창을 열고 관리 URL을 입력하여 Lync Server 2013 제어판을 엽니다.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 정책**을 클릭합니다.
    
    전역, 사이트 및 사용자 정책의 계층 구조를 비롯한 보관 정책의 작동 방식에 대한 자세한 내용은 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md) 계획 설명서, 배포 설명서 또는 운영 설명서를 참조하십시오.

4.  **새로 만들기**를 클릭하고 **사이트 정책**을 클릭합니다.

5.  **사이트 선택**에서 정책을 적용할 사이트를 클릭합니다.

6.  **새 보관 정책**에서 다음을 수행합니다.
    
      - **이름**에 사이트 정책의 이름을 지정합니다.
    
      - **설명**에 사이트 정책에 대한 정보(예: Redmond용 사이트 정책)를 입력합니다.
    
      - 지정된 사이트의 내부 통신 보관을 제어하려면 **내부 통신 보관** 확인란을 선택하거나 선택을 취소합니다.
    
      - 지정된 사이트의 외부 통신 보관을 제어하려면 **외부 통신 보관** 확인란을 선택하거나 선택을 취소합니다.

7.  **커밋**을 클릭합니다.

