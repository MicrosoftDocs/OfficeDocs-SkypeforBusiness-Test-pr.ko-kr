---
title: Lync Server 2013에서 보조 위치 정보 서비스 구성
TOCTitle: Lync Server 2013에서 보조 위치 정보 서비스 구성
ms:assetid: 083ffbc6-7c18-4141-85f9-8825b62c3d10
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398138(v=OCS.15)
ms:contentKeyID: 49302722
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 보조 위치 정보 서비스 구성

 

_**마지막으로 수정된 항목:** 2012-10-30_

Lync Server 2013에서는 위치 정보 서비스가 SLS(보조 위치 원본) 데이터베이스를 가리키도록 하는 데 사용할 수 있는 웹 서비스 인터페이스를 제공합니다. SLS 데이터베이스에 연결하는 웹 서비스 인터페이스는 위치 정보 서비스 WSDL을 따라야 합니다. 위치 데이터베이스와 보조 위치 데이터베이스가 둘 다 구성되어 있는 경우 위치 정보 서비스에서는 먼저 위치 데이터베이스를 쿼리한 후에 일치하는 항목이 없으면 클라이언트에서 SLS 데이터베이스로의 위치 요청을 보냅니다. SLS에 위치가 있는 경우 위치 정보 서비스에서는 해당 위치를 다시 클라이언트로 보냅니다.

자세한 내용은 Lync Server 관리 셸 설명서에서 다음 cmdlet을 참조하십시오.

  - **Set-CsWebServiceConfiguration**

## 보조 위치 데이터베이스를 구성하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음 cmdlet을 실행하여 보조 위치 데이터베이스의 위치에 대해 URL을 구성합니다.
    
        Set-CsWebServiceConfiguration -SecondaryLocationSourceURL "<web service url>"

