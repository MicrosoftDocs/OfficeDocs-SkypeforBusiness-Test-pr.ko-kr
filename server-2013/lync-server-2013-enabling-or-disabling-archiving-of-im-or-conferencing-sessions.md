---
title: IM 또는 회의 세션 보관 사용 또는 사용 안 함
TOCTitle: IM 또는 회의 세션 보관 사용 또는 사용 안 함
ms:assetid: aa4b5983-dbe1-4d64-8a18-fe2c33994e94
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182567(v=OCS.15)
ms:contentKeyID: 49304677
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# IM 또는 회의 세션 보관 사용 또는 사용 안 함

 

_**마지막으로 수정된 항목:** 2012-10-10_

Lync Server 2013 제어판에서는 보관 구성을 사용하여 IM, 회의 세션 또는 둘 다의 보관을 사용하거나 사용하지 않도록 설정할 수 있습니다. 여기에는 다음과 같은 보관 구성이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 전역 구성

  - 특정 사이트 또는 풀에 대해 보관이 구현되는 방식을 지정하도록 만들어서 사용하는 선택적인 사이트 수준 및 풀 수준 구성

보관을 배포할 때 처음으로 보관 구성을 설정하게 되며, 배포 후에 구성을 변경, 추가 및 삭제할 수 있습니다 지정할 수 있는 옵션과 보관 구성의 계층 구조를 비롯하여 보관 구성이 구현되는 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 보관을 사용하려면 Lync Server 2013에 속한 사용자가 내부 통신, 외부 통신 또는 둘 다에 대해 보관을 사용할 수 있도록 할지를 지정하는 보관 정책을 구성해야 합니다. 기본적으로 내부 통신 또는 외부 통신에 대한 보관이 사용할 수 없도록 설정됩니다. 정책에 보관을 사용할 수 있도록 설정하기 전에 이 섹션에 설명된 대로 배포 및 선택적으로 특정 사이트와 풀에 대해 적절한 보관 구성을 지정해야 합니다. 보관을 사용할 수 있도록 설정하는 방법에 대한 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">보관 정책 구성 및 할당</A>을 참조하십시오.<BR>보관을 배포한 후에 Microsoft Exchange 통합을 사용하여 보관 데이터 및 파일을 Exchange 2013 서버에 저장하도록 결정하고 모든 사용자가 Exchange 2013 서버에 속해 있는 경우 SQL Server 데이터베이스 구성을 토폴로지에서 제거해야 합니다. 이 작업을 수행하려면 토폴로지 작성기를 사용해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-changing-archiving-database-options.md">Lync Server 2013에서 데이터베이스 보관 옵션 변경</A>을 참조하십시오.



## IM 또는 전화 회의 세션 보관을 사용하거나 사용하지 않도록 설정하려면

1.  CsArchivingAdministrator 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **보관 구성**을 클릭합니다.

4.  보관 구성에서 적합한 전역, 사이트 또는 풀 구성을 선택하고 **편집**, **자세한 정보 표시**를 차례로 클릭한 후 다음을 수행합니다.
    
      - IM(인스턴트 메시징) 세션에 대해서만 보관을 사용하도록 설정하려면 **IM 세션 보관**을 클릭합니다.
    
      - IM 세션 및 전화 회의 모두에 대해 보관을 사용하도록 설정하려면 **IM 및 전화 회의 세션 보관**을 클릭합니다.
    
      - 정책에 대해 보관을 사용하지 않도록 설정하려면 **보관 사용 안 함**을 클릭합니다.

5.  **커밋**을 클릭합니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)  
[보관 정책 구성 및 할당](lync-server-2013-configuring-and-assigning-archiving-policies.md)

