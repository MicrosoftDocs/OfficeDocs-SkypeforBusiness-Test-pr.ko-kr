---
title: 네트워크 지역 정보 보기
TOCTitle: 네트워크 지역 정보 보기
ms:assetid: 665740d0-a3ed-460f-8337-5ed945f90589
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688076(v=OCS.15)
ms:contentKeyID: 49885789
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 지역 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

네트워크 지역은 여러 지역의 많은 네트워크 부분을 교차합니다. 모든 네트워크 지역은 중앙 사이트와 연결되어야 합니다. 중앙 사이트는 CAC(통화 허용 제어) 대역폭 정책 서비스가 실행되는 데이터 센터 사이트입니다. 네트워크 지역은 Lync Server 제어판을 사용하여 볼 수 있습니다. 네트워크 지역에는 오디오 및 비디오 연결에 대해 인터넷을 통한 대체 경로가 허용되는지 여부를 결정하는 설정이 포함됩니다. 이 항목을 사용하여 기존 네트워크 지역을 확인합니다. 기존 네트워크 지역을 만들거나 수정하는 방법에 대한 자세한 내용은 [네트워크 영역 만들기 또는 수정](lync-server-2013-creating-or-modifying-network-regions.md)을 참조하십시오.

## Lync Server 제어판을 사용하여 네트워크 지역에 대한 정보를 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **네트워크 구성**을 클릭한 다음 **지역**을 클릭합니다.

4.  **지역** 페이지에서 보려는 지역을 클릭합니다.
    

    > [!NOTE]
    > 한 번에 한 지역만 볼 수 있습니다.



5.  **편집** 메뉴에서 **세부 정보 표시**를 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 네트워크 지역 정보 보기

Windows PowerShell 및 **Get-CsNetworkRegion** cmdlet을 사용하여 네트워크 지역 정보를 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 네트워크 지역 정보를 보려면

  - 모든 네트워크 지역에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsNetworkRegion
    
    그러면 다음과 비슷한 정보가 표시됩니다.
    
        Identity         : Pacific Northwest
        Description      :
        BypassID         : 3b232b84-2c1d-4da2-8181-e9330bafebe9
        CentralSite      : Site:Redmond1
        BWAlternatePaths : {BWPolicyModality=Audio;AlternatePath=True, 
                           BWPolicyModality=Video;AlternatePath=True}
        NetworkRegionID  : Pacific Northwest

자세한 내용은 [Get-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[네트워크 영역 만들기 또는 수정](lync-server-2013-creating-or-modifying-network-regions.md)  
[기존 네트워크 지역 삭제](lync-server-2013-deleting-existing-network-regions.md)

