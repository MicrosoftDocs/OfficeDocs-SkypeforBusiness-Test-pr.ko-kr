---
title: 네트워크 지역 연결 정보 보기
TOCTitle: 네트워크 지역 연결 정보 보기
ms:assetid: 7b6b2ea2-83d8-4376-afb2-70e5d2cf6444
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688102(v=OCS.15)
ms:contentKeyID: 49885832
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 지역 연결 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

CAC(통화 허용 제어)의 일환으로 두 네트워크 지역 간의 링크를 볼 수 있습니다. 네트워크 내의 지역은 실제 WAN(Wide Area Network) 연결을 통해 연결됩니다. Lync Server 제어판을 사용하여 두 네트워크 지역 간의 기존 링크를 볼 수 있습니다. 네트워크 지역 링크를 만들거나 수정하는 방법에 대한 자세한 내용은 [네트워크 지역 링크 구성](lync-server-2013-configuring-network-region-links.md)을 참조하십시오.

## Lync Server 제어판에서 네트워크 지역 링크를 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **지역 링크**를 클릭합니다.

4.  **지역 링크** 페이지에서 보려는 지역 링크를 클릭합니다.
    

    > [!NOTE]
    > 한 번에 하나의 지역 링크에 대한 정보만 볼 수 있습니다.



5.  **편집** 메뉴에서 **세부 정보 표시**를 선택합니다.

## Lync Server 관리 셸 Cmdlet을 사용하여 네트워크 지역 링크 정보 보기

Lync Server 관리 셸 및 **Get-CsNetworkRegionLink** cmdlet을 사용하여 네트워크 지역 링크를 볼 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 네트워크 지역 링크 정보를 보려면

  - 모든 네트워크 지역 링크에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsNetworkRegionLink
    
    이 명령은 다음과 비슷한 정보를 반환합니다.
    
        Identity            : NorthwestToCalifornia
        BWPolicyProfileID   :
        NetworkRegionLinkID : NorthwestToCalifornia
        NetworkRegionID1    : Pacific Northwest
        NetworkRegionID2    : California

자세한 내용은 [Get-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink)을 참조하십시오.

## 참고 항목

#### 작업

[네트워크 사이트 링크 구성](lync-server-2013-configuring-network-site-links.md)

