---
title: 사용자에게 Lync Server 보관 정책 적용
TOCTitle: 사용자에게 Lync Server 보관 정책 적용
ms:assetid: a23e4876-aa8d-4f49-a3bd-3696616e8290
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205143(v=OCS.15)
ms:contentKeyID: 49304580
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자에게 Lync Server 보관 정책 적용

 

_**마지막으로 수정된 항목:** 2012-10-10_

Lync Server 사용자 정책을 만든 후에는 Lync Server 2013에 속한 특정 사용자 또는 사용자 그룹에 정책을 적용해야 정책이 실제로 적용될 수 있습니다. 특정 사용자에 대한 사용자 정책을 만드는 방법에 대한 자세한 내용은 배포 설명서에서 [Lync Server에서 보관용 사용자 정책 만들기 및 구성](lync-server-2013-creating-and-configuring-user-policies-for-archiving-in-lync-server.md)을 참조하십시오.

전역, 사이트 및 사용자 정책의 계층 구조를 포함하여 보관 정책이 작동하는 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 보관을 구성 및 사용하려면 먼저 배포해야 합니다. 자세한 내용은 배포 문서에서 <A href="lync-server-2013-deploying-archiving.md">Lync Server 2013에서 보관 배포</A>를 참조하세요.<BR>배포에 Microsoft Exchange 통합을 사용하도록 설정한 경우 Exchange 원본 위치 유지 정책이 Exchange 2013에 속해 있고 사서함을 원본 위치 유지로 설정한 사용자에 대해 보관을 사용할지 여부를 제어합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.<BR>보관을 사용하도록 설정하기 전에 보관 구성에서 모든 해당 옵션을 지정해야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-archiving-options.md">보관 옵션 구성</A>를 참조하십시오.



## 사용자에게 Lync Server 보관 정책을 적용하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 2013 제어판을 엽니다. Lync Server 2013 제어판을 사용하여 시작할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭하고 구성할 사용자 계정을 검색합니다.

4.  검색 결과가 나열된 표에서 사용자 계정을 클릭하고 **편집**을 클릭한 후에 **자세한 정보 표시**를 클릭합니다.

5.  **보관 정책** 아래의 **Lync Server 사용자 편집**에서 적용할 보관 사용자 정책을 선택합니다.
    

    > [!NOTE]
    > <STRONG>&lt;자동&gt;</STRONG> 설정을 선택하면 기본 서버 설치 설정이 적용됩니다. 이러한 설정은 서버에 의해 자동으로 적용됩니다.



6.  **커밋**을 클릭합니다.

