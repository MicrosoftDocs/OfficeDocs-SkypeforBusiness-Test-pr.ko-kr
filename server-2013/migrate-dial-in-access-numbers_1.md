---
title: 전화 접속 액세스 번호 마이그레이션
TOCTitle: 전화 접속 액세스 번호 마이그레이션
ms:assetid: 568a94b7-a697-4ab2-9008-dc9ecc1c87c8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204898(v=OCS.15)
ms:contentKeyID: 49303674
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전화 접속 액세스 번호 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-09-26_

전화 접속 액세스 번호를 마이그레이션하려면 **Import-CsLegacyConfiguration** cmdlet( [정책 및 설정 가져오기](import-policies-and-settings.md) 참조)을 실행하여 다이얼 플랜 및 기타 전화 접속 액세스 번호 설정을 마이그레이션하고 **Move-CsApplicationEndpoint** cmdlet을 실행하여 대화 상대 개체를 마이그레이션하는 두 단계를 수행해야 합니다.

## 전화 접속 액세스 번호를 마이그레이션하려면

1.  Office Communications Server 2007 R2 관리 도구를 엽니다.

2.  콘솔 트리에서 포리스트 노드를 마우스 오른쪽 단추로 클릭하고 **속성** 을 클릭한 후 **회의 전화 교환 속성** 을 클릭합니다.

3.  **액세스 전화 번호** 탭에서 **풀별로 서비스됨** 을 클릭하여 연결된 풀별로 액세스 전화 번호를 정렬하고 마이그레이션하려는 풀에 대한 모든 액세스 번호를 식별합니다.

4.  각 액세스 번호에 대한 SIP URI를 식별하려면 액세스 번호를 두 번 클릭하여 **회의 전화 교환 번호 편집** 대화 상자를 열고 **SIP URI** 아래를 확인합니다.

5.  Lync Server 관리 셸를 엽니다.

6.  각 전화 접속 액세스 번호를 Lync Server 2013에 호스팅된 풀로 이동하려면 다음을 실행합니다.
    
        Move-CsApplicationEndpoint -Identity <SIP URI of the access number to be moved> -Target <FQDN of the pool to which the access number is moving>

7.  Office Communications Server 2007 R2 관리 도구의 **액세스 전화 번호** 탭에서 마이그레이션할 Office Communications Server 2007 R2 풀에 대한 전화 접속 액세스 번호가 남아 있지 않은지 확인합니다.

