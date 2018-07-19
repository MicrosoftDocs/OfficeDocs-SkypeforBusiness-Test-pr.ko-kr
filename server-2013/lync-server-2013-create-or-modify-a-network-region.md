---
title: 'Lync Server 2013: 네트워크 지역 만들기 또는 수정'
TOCTitle: 네트워크 지역 만들기 또는 수정
ms:assetid: bf7a3dc4-71a2-4559-a547-d90305d4f904
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412933(v=OCS.15)
ms:contentKeyID: 49304902
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 네트워크 지역 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2012-10-19_

*네트워크 지역* 은 통화 허용 제어, E9-1-1 및 미디어 바이패스를 구성하는 데 사용되는 네트워크 허브나 백본입니다. 다음 절차를 사용하여 네트워크 지역을 만들거나 수정할 수 있습니다. 예를 들어 특정 음성 정책에 대해 네트워크 지역을 이미 만든 경우에는 새 네트워크 지역을 만들지 않아도 됩니다. 그 이외의 다른 고급 Enterprise Voice 기능에서도 동일한 네트워크 지역이 사용됩니다. 그러나 기능별 설정을 적용하기 위해 기존 네트워크 지역 정의를 수정해야 하는 경우가 있을 수 있습니다. 예를 들어 연결된 중앙 사이트가 필요하지 않은 E9-1-1에 대한 네트워크 지역을 만들고 통화 허용 제어를 배포한 경우에는 네트워크 지역 정의를 수정하여 중앙 사이트를 지정해야 합니다. 자세한 내용은 [Lync Server 2013에서 CAC에 대한 네트워크 지역 구성](lync-server-2013-configure-network-regions-for-cac.md)을 참조하십시오.


> [!NOTE]
> 네트워크 지역 정의에 대한 기능별 요구 사항은 해당 기능의 배포 항목에 설명되어 있습니다.



네트워크 지역을 사용하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - [New-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkRegion)

  - [Get-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink)

  - [Set-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkRegion)

  - [Remove-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkRegion)

## 네트워크 지역 만들기

통화 허용 제어, E9-1-1 또는 미디어 바이패스에서 사용할 수 있는 네트워크 지역을 만듭니다.

## Lync Server 관리 셸을 사용하여 네트워크 지역을 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  New-CsNetworkRegion cmdlet을 실행하여 네트워크 지역을 만듭니다.
    
        New-CsNetworkRegion -Identity <String> -CentralSite <String>
    
    예를 들면 다음과 같습니다.
    
        New-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "All North America Locations"
    
    이 예에서는 사이트 ID가 CHICAGO인 중앙 사이트와 연결된 “NorthAmerica”라는 네트워크 지역이 만들어졌습니다.

3.  토폴로지에 대한 네트워크 지역 만들기를 종료하려면 각 네트워크 지역에 대한 설정을 사용하여 2단계를 반복합니다.

## Lync Server 제어판을 사용하여 네트워크 지역을 만들려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성** 을 클릭합니다.

3.  **지역** 을 클릭합니다.

4.  **새로 만들기** 를 클릭합니다.

5.  **새 지역** 페이지에서 **이름** 을 클릭한 다음 네트워크 지역에 대한 이름을 입력합니다.

6.  **중앙 사이트** 를 클릭한 다음 목록에서 중앙 사이트를 클릭합니다.

7.  필요한 경우 **설명** 을 클릭한 다음 이 네트워크 사이트를 설명하는 추가 정보를 입력합니다.

8.  **커밋** 을 클릭합니다.

9.  토폴로지에 대한 네트워크 지역 만들기를 종료하려면 다른 지역에 대한 설정을 사용하여 4-8단계를 반복합니다.

## 네트워크 지역 수정

기존 네트워크 지역에 대한 설정을 수정하여 새 기능에 필요한 변경 내용이나 기본 지역 정보에 대한 변경 내용을 포함할 수 있습니다.

## Lync Server 관리 셸을 사용하여 네트워크 지역을 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  Set-CsNetworkRegion cmdlet을 실행하여 기존 네트워크 지역을 수정합니다.
    
        Set-CsNetworkRegion -Identity <String> -CentralSite <String>
    
    예를 들면 다음과 같습니다.
    
        Set-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "North American Region"
    
    이 예에서는 설명을 변경함으로써 이 항목의 앞 부분에 나온 절차를 사용하여 만든 “NorthAmerica”라는 기존의 네트워크 지역을 수정했습니다. 이 명령은 “NorthAmerica” 지역에 설명이 있는 경우 이 값으로 해당 설명을 덮어쓰고, 설정된 설명이 없는 경우 설명을 설정합니다.

3.  다른 네트워크 지역을 수정하려면 다른 지역에 대한 설정을 사용하여 2단계를 반복합니다.

## Lync Server 제어판을 사용하여 네트워크 지역을 수정하려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성** 을 클릭합니다.

3.  **지역** 탐색 단추를 클릭합니다.

4.  테이블에서 수정할 네트워크 지역을 클릭합니다.

5.  **편집** 을 클릭한 다음 **자세한 정보 표시...** 를 클릭합니다.

6.  **지역 편집** 페이지에서 이 네트워크 지역의 설정에 대한 값을 적절하게 변경합니다.

7.  **커밋** 을 클릭합니다.

8.  네트워크 지역 수정을 완료하려면 다른 지역에 대한 설정을 사용하여 4-7단계를 반복합니다.

