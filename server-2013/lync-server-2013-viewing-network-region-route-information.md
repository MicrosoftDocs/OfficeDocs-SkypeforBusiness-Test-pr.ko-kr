---
title: 네트워크 지역 경로 정보 보기
TOCTitle: 네트워크 지역 경로 정보 보기
ms:assetid: 34dd9fa3-e695-4680-b244-3019298b5009
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688021(v=OCS.15)
ms:contentKeyID: 49885722
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 지역 경로 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

CAC(통화 허용 제어) 구성 내의 모든 지역에는 다른 모든 지역에 액세스할 수 있는 방법이 있어야 합니다. 지역 링크는 지역 간 연결에 대한 대역폭 제한을 설정하고 실제 링크를 나타내며, 경로는 연결이 지역 간을 통과하는 링크된 경로를 결정합니다. 다음 절차에 따라 Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸에서 기존 네트워크 지역 경로를 봅니다. 네트워크 지역 경로를 만들거나 수정하는 방법에 대한 자세한 내용은 [네트워크 지역 경로 만들기 및 수정](lync-server-2013-creating-or-modifying-network-region-routes.md)을 참조하십시오.

## Lync Server 제어판에서 네트워크 지역 경로 정보를 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **지역 경로**를 클릭합니다.

4.  **지역 경로** 페이지에서 보려는 지역 경로를 클릭합니다.
    

    > [!NOTE]
    > 한 번에 하나의 지역 경로만 볼 수 있습니다.



5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

## Lync Server PowerShell cmdlet을 사용하여 네트워크 지역 경로 정보 확인

Lync Server PowerShell 및 Get-CsNetworkInterRegionRoute cmdlet을 사용하여 네트워크 지역 경로 정보를 확인할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 네트워크 지역 경로 정보 보기

  - 모든 네트워크 지역 경로에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsNetworkInterRegionRoute
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity                  : TransAmericaRoute
        NetworkRegionLinks        : {NorthwestToNortheast}
        InterNetworkRegionRouteID : TransAmericaRoute
        NetworkRegionID1          : Pacific Northwest
        NetworkRegionID2          : Northeast

자세한 내용은 [Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[네트워크 지역 경로 만들기 및 수정](lync-server-2013-creating-or-modifying-network-region-routes.md)  
[기존 네트워크 지역 경로 삭제](lync-server-2013-deleting-existing-network-region-routes.md)

