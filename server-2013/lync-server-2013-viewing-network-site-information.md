---
title: 네트워크 사이트 정보 보기
TOCTitle: 네트워크 사이트 정보 보기
ms:assetid: 24a97d98-b168-4016-81bf-c2c478092b87
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687996(v=OCS.15)
ms:contentKeyID: 49885684
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 사이트 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

네트워크 사이트는 CAC(통화 허용 제어) 또는 고급 9-1-1 배포의 각 지역 내에 구성된 사무실 또는 위치입니다. Lync Server 2013 제어판 또는 Lync Server 관리 셸에서 네트워크 사이트 정보를 확인할 수 있습니다. 네트워크 사이트를 만들거나 수정하는 방법에 대한 자세한 내용은 [네트워크 사이트 만들기 또는 수정](lync-server-2013-creating-or-modifying-network-sites.md)을 참조하십시오.

## Lync Server 제어판에서 네트워크 사이트 정보를 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **사이트**를 클릭합니다.

4.  **사이트** 페이지에서 보려는 사이트를 클릭합니다.
    

    > [!NOTE]
    > 한 번에 한 사이트에 대한 정보만 볼 수 있습니다.



5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 네트워크 사이트 정보를 보려면

Get-CsNetworkSite cmdlet을 사용하여 네트워크 사이트 정보를 확인할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 네트워크 사이트 정보를 보려면

  - 모든 네트워크 사이트에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsNetworkSite
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity          : Redmond
        NetworkSiteID     : Redmond
        Description       :
        NetworkRegionID   : Pacific Northwest
        BypassID          : 3b232b84-2c1d-4da2-8181-e9330bafebe9
        BWPolicyProfileID :
        LocationPolicy    :

자세한 내용은 [Get-CsNetworkSite](get-csnetworksite.md) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[네트워크 사이트 만들기 또는 수정](lync-server-2013-creating-or-modifying-network-sites.md)  
[기존 네트워크 사이트 삭제](lync-server-2013-deleting-an-existing-network-site.md)

