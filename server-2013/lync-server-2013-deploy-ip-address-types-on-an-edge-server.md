---
title: 'Lync Server 2013: 에지 서버에 IP 주소 유형 배포'
TOCTitle: 에지 서버에 IP 주소 유형 배포
ms:assetid: 6e2fe7e8-6e90-4d1a-8fc5-e3be92c46571
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204984(v=OCS.15)
ms:contentKeyID: 49303972
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 에지 서버에 IP 주소 유형 배포

 

_**마지막으로 수정된 항목:** 2012-06-14_

토폴로지 작성기를 사용하여 다음 절차의 단계를 수행해서 에지 서버에 IP 주소 유형을 배포합니다.

## 에지 서버에 IP 주소 유형을 배포하려면

1.  토폴로지 작성기의 **에지 풀** 에서 풀 내의 서버를 마우스 오른쪽 단추로 클릭한 후 **속성 편집** 을 선택합니다. 또는 서버를 선택한 후 **동작** 메뉴에서 **속성 편집** 을 클릭합니다.

2.  **속성 편집** 창에서 지원하려는 IP 주소 구성을 선택합니다. 다음 그림에서는 내부 인터페이스 및 외부 인터페이스에 대한 이중 스택 구성을 보여줍니다.
    
    **이중 스택된 에지 서버 내부 인터페이스**
    
    ![Lync Server 일반 속성 페이지](images/JJ204984.5b0883ee-b9f2-4a21-91a9-3286d0beb63b(OCS.15).png "Lync Server 일반 속성 페이지")
    
    **이중 스택된 에지 서버 외부 인터페이스**
    
    ![Lync Server 다음 홉/외부 구성 페이지](images/JJ204984.2aa00ce2-ba50-40aa-bbf1-78636016daf9(OCS.15).png "Lync Server 다음 홉/외부 구성 페이지")

3.  선택한 각 주소 유형에 대해 적합한 내부 및 외부 주소를 제공해야 합니다.

