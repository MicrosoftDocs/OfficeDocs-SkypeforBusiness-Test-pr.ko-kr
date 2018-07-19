---
title: 기존 네트워크 지역 경로 삭제
TOCTitle: 기존 네트워크 지역 경로 삭제
ms:assetid: 6256ff80-5f1e-48b4-928b-24aeb3c1a0e7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688074(v=OCS.15)
ms:contentKeyID: 49885787
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 네트워크 지역 경로 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

CAC(통화 허용 제어) 구성 내의 모든 지역에는 다른 모든 지역에 액세스할 수 있는 방법이 있어야 합니다. 지역 링크는 지역 간 연결에 대한 대역폭 제한을 설정하고 실제 링크를 나타내며, 경로는 한 지역에서 다른 지역으로 연결이 트래버스되는 연결된 경로를 결정합니다. Lync Server 제어판을 사용하여 네트워크 지역 경로를 구성할 수 있습니다. Lync Server 제어판에서 네트워크 지역 경로를 만들고 수정하거나 삭제할 수 있습니다. 이 항목을 사용하여 기존 네트워크 지역 경로를 삭제합니다. 네트워크 지역 경로 만들기 또는 수정에 대한 자세한 내용은 [네트워크 지역 경로 만들기 및 수정](lync-server-2013-creating-or-modifying-network-region-routes.md)을 참조하십시오.

## 네트워크 지역 경로를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **지역 경로**를 클릭합니다.

4.  **지역 경로** 페이지에서 삭제할 지역 경로를 클릭합니다.
    

    > [!NOTE]
    > 한 번에 둘 이상의 지역 경로를 삭제할 수 있습니다. 이렇게 하려면 Ctrl 키를 누른 상태에서 여러 지역 경로를 선택합니다. 또는 모든 지역 경로를 선택하려면 <STRONG>편집</STRONG> 메뉴에서 <STRONG>모두 선택</STRONG>을 클릭합니다.



5.  **편집** 메뉴에서 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.

## 참고 항목

#### 작업

[네트워크 지역 경로 만들기 및 수정](lync-server-2013-creating-or-modifying-network-region-routes.md)  

#### 개념

[네트워크 지역 경로 구성](https://technet.microsoft.com/ko-kr/library/gg133706\(v=ocs.15\))  

#### 기타 리소스

[New-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterRegionRoute)  
[Set-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterRegionRoute)  
[Remove-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterRegionRoute)  
[Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterRegionRoute)

