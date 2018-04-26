---
title: 네트워크 서브넷 정보 보기
TOCTitle: 네트워크 서브넷 정보 보기
ms:assetid: 46f165f2-efe3-4cc1-9fee-a78b7f2ed41e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688044(v=OCS.15)
ms:contentKeyID: 49885747
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 서브넷 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

다음 절차에 따라 네트워크 서브넷을 볼 수 있습니다. Lync Server 제어판에서는 네트워크 서브넷을 만들거나, 수정하거나, 삭제할 수 있습니다. 네트워크 서브넷을 만들거나 수정하는 방법에 대한 자세한 내용은 [네트워크 서브넷 만들기 또는 수정](lync-server-2013-create-or-modify-network-subnets.md)을 참조하십시오.

## 네트워크 서브넷을 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **서브넷**을 클릭합니다.

4.  **서브넷** 페이지에서 보려는 서브넷을 클릭합니다.
    

    > [!NOTE]
    > 서브넷을 한 번에 하나만 볼 수 있습니다.



5.  **편집** 메뉴에서 **세부 정보 표시**를 클릭합니다.

## Lync Server PowerShell Cmdlet을 사용하여 네트워크 서브넷 구성 정보 보기

네트워크 서브넷 정보는 Lync Server PowerShell 및 Get-CsNetworkSubnet cmdlet을 사용하여 볼 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요..

## 네트워크 서브넷 정보 보기

  - 모든 네트워크 서브넷에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsNetworkSubnet
    
    그러면 다음과 비슷한 정보가 표시됩니다.
    
        Identity      : 172.11.15.0
        MaskBits      : 28
        Description   :
        NetworkSiteID : Redmond
        SubnetID      : 172.11.15.0

자세한 내용은 [Get-CsNetworkSubnet](get-csnetworksubnet.md) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[네트워크 서브넷 만들기 또는 수정](lync-server-2013-create-or-modify-network-subnets.md)  
[네트워크 서브넷 삭제](lync-server-2013-deleting-network-subnets.md)

