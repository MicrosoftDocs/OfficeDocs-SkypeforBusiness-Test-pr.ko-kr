---
title: 'Lync Server 2013: 토폴로지에 분기 사이트 추가'
TOCTitle: 토폴로지에 분기 사이트 추가
ms:assetid: b9c35fb0-0081-4aeb-8f95-ac2fcc6c3335
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412905(v=OCS.15)
ms:contentKeyID: 49304837
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 토폴로지에 분기 사이트 추가

 

_**마지막으로 수정된 항목:** 2012-10-05_

분기 사이트는 WAN 링크를 통해 본사에 연결되는 실제 지점을 나타냅니다. Lync 토폴로지에 분기 사이트를 추가하려면 중앙 사이트에서 다음 절차를 수행하십시오.

## 토폴로지에 분기 사이트를 추가하려면

1.  **시작** , **모든 프로그램** , **Microsoft Lync Server** 를 차례로 클릭한 다음 **Lync Server 토폴로지 작성기** 를 클릭합니다.

2.  콘솔 트리에서 중앙 사이트를 확장하고 **분기 사이트** 를 마우스 오른쪽 단추로 클릭한 다음 **새 분기 사이트** 를 클릭합니다.

3.  **새 분기 사이트 정의** 대화 상자에서 **이름** 을 클릭한 다음 분기 사이트의 이름을 입력합니다.

4.  (선택 사항) **설명** 을 클릭한 다음 분기 사이트에 대한 의미 있는 설명을 입력합니다.

5.  **다음** 을 클릭합니다.

6.  (선택 사항) 다음 **새 분기 사이트 정의** 대화 상자에서 다음 중 일부를 수행합니다.
    
      - **구/군/시** 를 클릭한 다음 분기 사이트가 있는 구/군/시의 이름을 입력합니다.
    
      - **시/도/지역** 을 클릭한 다음 분기 사이트가 있는 시/도/지역의 이름을 입력합니다.
    
      - **국가 코드**를 클릭한 다음 분기 사이트가 있는 국가/지역에 대한 두 자리 국가/지역 번호를 입력합니다.

7.  **다음** 을 클릭하고 다음 중 하나를 수행합니다.
    
      - 이 사이트에서 SBA(Survivable Branch Appliance) 또는 서버를 사용하는 경우 **이 마법사가 닫히면 새 지속 가능 마법사 열기** 확인란이 선택되어 있는지 확인하고 **마침** 을 클릭한 다음 열리는 마법사의 지침을 따릅니다. 마법사 항목에 대한 자세한 내용은 [Lync Server 2013에서 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 정의](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)를 참조하십시오.
    
      - 이 사이트에서 SBA(Survivable Branch Appliance) 또는 서버를 사용하지 않는 경우에는 **이 마법사가 닫히면 새 지속 가능 마법사 열기** 확인란의 선택을 취소한 다음 **마침** 을 클릭합니다.

8.  토폴로지에 추가할 각 분기 사이트에 대해 이전 단계를 반복합니다.

**다음 단계:**

SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버의 경우: [Lync Server 2013에서 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 정의](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)

복구 불가능한 PSTN 연결의 경우: [Lync Server 2013에서 분기 사이트에 대한 PSTN 게이트웨이 정의](lync-server-2013-define-a-pstn-gateway-for-a-branch-site.md), [Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md) 또는 [Lync Server 2013에서 미디어 바이패스 없이 트렁크 구성](lync-server-2013-configure-a-trunk-without-media-bypass.md)

