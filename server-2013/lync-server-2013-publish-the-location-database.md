---
title: Lync Server 2013에서 위치 데이터베이스 게시
TOCTitle: Lync Server 2013에서 위치 데이터베이스 게시
ms:assetid: dd032b5b-df0e-4017-ac46-e17570c1ab1e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398974(v=OCS.15)
ms:contentKeyID: 49305261
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 위치 데이터베이스 게시

 

_**마지막으로 수정된 항목:** 2012-10-30_

위치 데이터베이스에 추가한 새 위치는 게시되어야 클라이언트에서 사용할 수 있습니다.

자세한 내용은 Lync Server 관리 셸 설명서에서 다음 cmdlet를 참조하십시오.

  - **Publish-CsLisConfiguration**

ELIN(Emergency Location Identification Number) 게이트웨이를 사용하는 경우 PSTN(공중 전화망) 사업자의 ALI(Automatic Location Identification) 데이터베이스에도 ELIN을 업로드해야 합니다. PSTN 사업자가 특정 ELIN 레코드 형식을 사용하도록 요구할 수 있습니다. 자세한 내용은 PSTN 사업자에게 문의하십시오. 위치 정보 서비스 데이터베이스에서 레코드를 내보내고 필요에 따라 레코드 형식을 지정할 수 있습니다.

## 위치 데이터베이스를 게시하려면

  - Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

  - 다음 cmdlet를 실행하여 위치 데이터베이스를 게시할 수 있습니다.
    
        Publish-CsLisConfiguration

