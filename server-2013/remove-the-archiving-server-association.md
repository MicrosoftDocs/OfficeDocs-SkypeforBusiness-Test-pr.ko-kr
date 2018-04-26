---
title: 보관 서버 연결 제거
TOCTitle: 보관 서버 연결 제거
ms:assetid: dabac157-71ee-4afe-b0b6-4a083d165ffb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721903(v=OCS.15)
ms:contentKeyID: 49886012
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관 서버 연결 제거

 

_**마지막으로 수정된 항목:** 2012-10-04_

보관 서버를 제거하려면 연관된 프런트 엔드 풀, 프런트 엔드 서버, SBA(Survivable Branch Appliance) 및 지속 가능 분기 서버에 대한 종속성을 변경하거나 해제해야 합니다. 프런트 엔드 풀, 프런트 엔드 서버, SBA(Survivable Branch Appliance) 및 지속 가능 분기 서버의 속성을 편집하여 종속성을 제거합니다. 종속성을 해제하고 토폴로지 작성기에서 서버를 삭제한 후에는 토폴로지 작성기의 연관된 데이터베이스 저장소 개체도 삭제된다는 메시지가 표시됩니다.

## 보관 서버 연결을 제거하려면

1.  Lync Server 2013 프런트 엔드 서버를 열고 토폴로지 작성기를 엽니다.

2.  Lync Server 2010 노드로 이동합니다.

3.  토폴로지 작성기에서 보관 서버가 정의된 위치에 따라 **Enterprise Edition 프런트 엔드 풀** , **Standard Edition 프런트 엔드 서버** 또는 **분기 사이트** 를 확장합니다.

4.  연관된 지속 가능 분기 서버가 있으면 **분기 사이트** 를 확장하여 분기 사이트 이름을 확장한 후 **SBA(Survivable Branch Appliances)** 를 확장합니다.
    

    > [!NOTE]
    > 사용자 인터페이스에서 <STRONG>SBA(Survivable Branch Appliance)</STRONG> 는 지속 가능 분기 서버 및 SBA(Survivable Branch Appliance)에 모두 적용됩니다.



5.  보관 서버와 연관된 풀, 서버 또는 장치를 마우스 오른쪽 단추로 클릭한 후 **속성 편집**을 클릭합니다.

6.  **속성 편집** 의 **일반** 아래에 있는 **연결** 에서 **보관 서버 연결** 확인란의 선택을 취소한 후 **확인** 을 클릭합니다.

7.  제거하려는 보관 서버와 연관된 다른 모든 풀, 서버 또는 장치에 대해 이전 단계를 반복합니다.

8.  보관 서버를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.

9.  **종속 저장소 삭제** 에서 **확인** 을 클릭합니다.

10. 토폴로지를 게시하고, 복제 상태를 확인하고 필요에 따라 Lync Server 배포 마법사를 실행합니다.

