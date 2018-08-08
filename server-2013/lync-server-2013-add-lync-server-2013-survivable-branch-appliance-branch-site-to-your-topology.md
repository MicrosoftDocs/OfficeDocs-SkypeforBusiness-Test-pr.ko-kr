---
title: "Lync Server 2013: 토폴로지에 Lync Server 2013 SBA 분기 사이트 추가"
TOCTitle: 토폴로지에 Lync Server 2013 SBA(Survivable Branch Appliance) 분기 사이트 추가
ms:assetid: d3142a37-4606-456d-8ea9-6cc0e51e55f3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721896(v=OCS.15)
ms:contentKeyID: 49885999
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 토폴로지에 Lync Server 2013 SBA(Survivable Branch Appliance) 분기 사이트 추가

 

_**마지막으로 수정된 항목:** 2012-10-07_

Microsoft Lync Server 2013SBA(Survivable Branch Appliance)는 백업 등록자로 Microsoft Lync Server 2010프런트 엔드 풀에 연결할 수 없습니다. SBA는 Microsoft Lync Server 2013프런트 엔드 풀에 연결되어야 합니다. 다음 단계는 Microsoft Lync Server 2013 SBA를 전제로 하며, 중앙 사이트에서 수행해야 합니다.

## 토폴로지에 Microsoft Lync Server 2013 SBA와 함께 분기 사이트를 추가하려면

1.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.

2.  콘솔 트리에서 중앙 사이트를 확장하고 **분기 사이트** 를 확장한 다음 **새 분기 사이트** 를 클릭합니다.

3.  **새 분기 사이트 정의** 대화 상자에서 **이름** 을 클릭한 다음 새 분기 사이트의 이름을 입력합니다.

4.  (선택 사항) **설명** 을 클릭한 다음 분기 사이트에 대한 의미 있는 설명을 입력합니다.

5.  **다음** 을 클릭합니다.

6.  (선택 사항) 다음 **새 분기 사이트 정의** 대화 상자에서 다음 중 일부를 수행합니다.
    
      - **구/군/시** 를 클릭한 다음 분기 사이트가 있는 구/군/시의 이름을 입력합니다.
    
      - **시/도/지역** 을 클릭한 다음 분기 사이트가 있는 시/도/지역의 이름을 입력합니다.
    
      - **국가 코드**를 클릭한 다음 분기 사이트가 있는 국가/지역에 대한 두 자리 국가/지역 번호를 입력합니다.

7.  **다음** 을 클릭하고 다음 중 하나를 수행합니다.
    
      - 이 사이트에 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 사용하는 경우 **이 마법사가 닫히면 새 SBA(Survivable Branch Appliance) 마법사를 엽니다** 확인란을 선택해야 합니다.
    
      - 이 사이트에 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 사용하지 않는 경우 **이 마법사가 닫히면 새 SBA(Survivable Branch Appliance) 마법사를 엽니다** 확인란을 선택 취소해야 합니다.
    
      - **마침** 을 클릭한 다음 열린 마법사의 지침을 따릅니다. 마법사 항목에 대한 자세한 내용은 [Lync Server 2013에서 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 정의](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)를 참조하십시오.

8.  토폴로지에 추가할 각 분기 사이트에 대해 이전 단계를 반복합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 정의](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)  
[Lync Server 2013에서 분기 사이트에 대한 PSTN 게이트웨이 정의](lync-server-2013-define-a-pstn-gateway-for-a-branch-site.md)  
[Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Lync Server 2013에서 미디어 바이패스 없이 트렁크 구성](lync-server-2013-configure-a-trunk-without-media-bypass.md)

