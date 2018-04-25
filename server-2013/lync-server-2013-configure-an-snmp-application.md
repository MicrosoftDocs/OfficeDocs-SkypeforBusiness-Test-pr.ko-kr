---
title: Lync Server 2013에서 SNMP 응용 프로그램 구성
TOCTitle: Lync Server 2013에서 SNMP 응용 프로그램 구성
ms:assetid: c4b4a736-3b2e-45b9-a965-19d22161ad57
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412972(v=OCS.15)
ms:contentKeyID: 49304970
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SNMP 응용 프로그램 구성

 

_**마지막으로 수정된 항목:** 2012-10-03_

Lync Server 2013에는 MAC 주소를 포트 및 스위치 정보와 일치시키는 SNMP(Simple Network Management Protocol) 응용 프로그램에 위치 정보 서비스를 연결하는 데 사용할 수 있는 표준 웹 서비스 인터페이스가 포함됩니다.

SNMP 응용 프로그램이 설치되고 위치 정보 서비스가 위치 데이터베이스에서 일치하는 항목을 찾지 못한 경우 위치 정보 서비스는 클라이언트에서 제공한 MAC 주소를 사용하여 응용 프로그램을 자동으로 쿼리합니다. 그러면 위치 정보 서비스가 SNMP 응용 프로그램에서 반환한 포트 및 스위치 정보를 사용하여 위치 데이터베이스를 다시 쿼리합니다.

자세한 내용은 [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)을 참조하십시오.


> [!NOTE]
> MAC 주소는 Windows 8을 실행하는 컴퓨터에서 사용할 수 없습니다.



## SNMP 응용 프로그램 URL을 구성하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음 cmdlet를 실행하여 SNMP 응용 프로그램에 대한 URL을 구성합니다.
    
        Set-CsWebServiceConfiguration -MACResolverUrl "<SNMP application url>"

