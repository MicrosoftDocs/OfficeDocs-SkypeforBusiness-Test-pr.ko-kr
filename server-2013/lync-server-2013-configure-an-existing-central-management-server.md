---
title: 'Lync Server 2013: 기존 중앙 관리 서버 구성'
TOCTitle: 기존 중앙 관리 서버 구성
ms:assetid: d715b24a-1256-4a7c-a5ef-1cee41d6b733
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205315(v=OCS.15)
ms:contentKeyID: 49305180
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 기존 중앙 관리 서버 구성

 

_**마지막으로 수정된 항목:** 2013-02-21_

기존 Lync Server 2013 배포에서 중앙 관리 서버를 다시 사용하는 경우 Lync Server 제어판 및 Windows PowerShell 기능이 올바로 작동할 수 있도록 아래 설명된 절차를 실행해야 합니다.

## 기존 중앙 관리 서버를 구성하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  **Update-CsAdminRole** cmdlet을 사용하여 중앙 관리 서버에 저장된 RBAC(역할 기반 액세스 제어)를 업데이트합니다.
    

    > [!NOTE]
    > 오류가 있는 경우를 제외하고 출력되는 내용이 없습니다.


