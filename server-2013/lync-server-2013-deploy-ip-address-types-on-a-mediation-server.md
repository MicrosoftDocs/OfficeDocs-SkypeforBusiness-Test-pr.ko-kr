---
title: 'Lync Server 2013: 중재 서버에 IP 주소 유형 배포'
TOCTitle: 중재 서버에 IP 주소 유형 배포
ms:assetid: 689ebed5-96ee-4cd4-b7ae-ee2a86a1d9b3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204964(v=OCS.15)
ms:contentKeyID: 49303907
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 중재 서버에 IP 주소 유형 배포

 

_**마지막으로 수정된 항목:** 2014-07-24_

중재 서버에서 IP 주소 유형을 배포하려면 토폴로지 작성기를 사용하여 다음 절차의 단계를 수행하세요.

## 중재 서버에 IP 주소 유형을 배포하려면

  - 토폴로지 작성기의 **중재 풀** 에서 풀 내의 서버를 마우스 오른쪽 단추로 클릭한 후 **속성 편집** 을 선택합니다. 또는 서버를 선택한 후 **동작** 메뉴에서 **속성 편집** 을 클릭합니다.

  - **속성 편집** 대화 상자에서 구성할 IP 주소 유형을 선택합니다. 이중 스택 구성의 경우 다음 그림과 같이 **IPv4 사용** 과 **IPv6 사용** 을 선택합니다.
    
    **중재 서버 풀에 대한 속성 편집 대화 상자**
    
    ![Lync Server 일반 속성 페이지(FQDN 포함)](images/JJ204964.4e650aca-dbff-4a86-b10d-f0162c032539(OCS.15).png "Lync Server 일반 속성 페이지(FQDN 포함)")
    
      - **구성된 모든 IP 주소**. 컴퓨터에 정의되어 있는 모든 IP 주소를 사용할 수 있도록 하려면 이 옵션을 선택합니다.
        

        > [!NOTE]
        > 이것이 IP 버전 6(IPv6) 구성에서 권장되는 옵션입니다.

    
      - **선택한 IP 주소로 서비스 사용 제한**. 새 서버에서 사용할 특정 주소를 지정하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 기본 IP 주소에 대한 값을 입력해야 합니다.
    
      - **기본 IP 주소**. 서버에서 PSTN(공중 전화망)을 제외한 모든 통신에 사용할 IP 주소를 입력합니다. 입력하는 IP 주소는 선택한 주소 유형의 형식과 일치해야 합니다.
    
      - **PSTN IP 주소**. 중재 서버가 프런트 엔드 서버에 배치되는 경우 PSTN IP 주소를 정의합니다. 이 주소는 선택한 주소 유형의 형식과 일치해야 합니다.
        

        > [!NOTE]
        > Lync Server 2013용 PSTN IP 주소 구성을 지원하는 추가 NIC(네트워크 인터페이스 카드)의 설치는 지원되지 않습니다. Lync Server 2013에 대해 지원되는 NIC 구성에 대한 자세한 내용은 <A href="lync-server-2013-server-hardware-platforms.md">Lync Server 2013의 서버 하드웨어 플랫폼</A>을 참고하세요.


