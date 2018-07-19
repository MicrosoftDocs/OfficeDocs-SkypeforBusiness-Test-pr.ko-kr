---
title: 'Lync Server 2013: 네트워크 사이트 만들기 또는 수정'
TOCTitle: 네트워크 사이트 만들기 또는 수정
ms:assetid: 14e24856-9996-4da4-9f31-300940bdf5aa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398218(v=OCS.15)
ms:contentKeyID: 49302896
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 네트워크 사이트 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-02-24_

CAC(통화 허용 제어), E9-1-1 및 미디어 바이패스 배포는 네트워크 지역 내에 정의되고 항상 네트워크 지역과 연결되는 *네트워크 사이트* 의 구성을 기반으로 합니다. 네트워크 사이트는 건물 또는 캠퍼스 집합인 지점 위치를 나타냅니다. 또한 네트워크 사이트는 유사한 대역폭을 가진 서브넷의 모음을 나타냅니다.

다음 절차를 사용하여 네트워크 사이트를 만들거나 수정할 수 있습니다. 예를 들어 하나의 음성 기능에 대한 네트워크 사이트를 이미 만든 경우 새 네트워크 사이트를 만들 필요가 없습니다. 다른 음성 기능에서도 같은 사이트를 사용하기 때문입니다. 그러나 기능별 설정을 적용하기 위해 기존 네트워크 사이트 정의를 수정해야 하는 경우가 있을 수 있습니다. 예를 들어 E9-1-1에 대한 네트워크 사이트를 만든 경우 대역폭 정책 프로필을 적용하려면 통화 허용 제어 배포 과정에서 네트워크 사이트를 수정해야 합니다.


> [!NOTE]
> 네트워크 사이트가 있는 경우 각 기능에 대한 배포 설명서의 고급 음성 기능에 네트워크 사이트가 속해 있으므로 네트워크 사이트에 대한 특정 예와 요구 사항을 찾을 수 있습니다. 
> <UL>
> <LI>
> <P><A href="lync-server-2013-configure-network-sites-for-cac.md">Lync Server 2013에서 CAC에 대한 네트워크 사이트 구성</A></P></LI></UL>



네트워크 사이트 작업에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - [New-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSite)

  - [Get-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkSite)

  - [Set-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkSite)

  - [Remove-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkSite)

## 네트워크 사이트 만들기

통화 허용 제어, E9-1-1 또는 미디어 바이패스에서 사용할 수 있는 네트워크 지역을 만듭니다.

## 관리 셸을 사용하여 네트워크 사이트를 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  New-CsNetworkSite cmdlet을 실행하여 네트워크 사이트를 만듭니다.
    
        New-CsNetworkSite -NetworkSiteID <string>
    
    예를 들면 다음과 같습니다.
    
        New-CsNetworkSite -NetworkSiteID Chicago -Description "Corporate headquarters"-NetworkRegionID NorthAmerica
    
    이 예에서는 "북미" 네트워크 지역에 있는 "시카고"라는 네트워크 사이트를 만들었습니다.
    

    > [!NOTE]
    > 이 명령을 실행하려면 북미 네트워크 지역이 이미 존재해야 합니다.



3.  토폴로지에 대한 네트워크 사이트 만들기를 종료하려면 다른 사이트에 대한 설정을 사용하여 2단계를 반복합니다.

## Lync Server 제어판을 사용하여 네트워크 사이트를 만들려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성** 을 클릭합니다.

3.  **사이트** 탐색 단추를 클릭합니다.

4.  **새로 만들기** 를 클릭합니다.

5.  **네트워크 사이트** 페이지에서 **이름** 을 클릭한 다음 네트워크 사이트 이름을 입력합니다.

6.  **지역** 을 클릭한 다음 목록에서 지역을 클릭합니다.

7.  필요한 경우 **대역폭 정책** 을 클릭한 다음 목록에서 대역폭 정책을 클릭합니다.
    

    > [!NOTE]
    > 대역폭 정책은 사이트에 통화 허용 제어를 배포할 경우에만 필요합니다.



8.  필요한 경우 **위치 정책** 을 클릭한 다음 목록에서 위치 정책을 클릭합니다.
    

    > [!NOTE]
    > 위치 정책은 사이트에 E9-1-1을 배포할 경우에만 필요합니다.



9.  필요한 경우 **설명** 을 클릭한 다음 이 네트워크 사이트를 설명하는 추가 정보를 입력합니다.

10. **커밋** 을 클릭합니다.

11. 토폴로지에 대한 네트워크 사이트 만들기를 종료하려면 다른 사이트에 대한 설정을 사용하여 4-10단계를 반복합니다.

## 네트워크 사이트 수정

통화 허용 제어, E9-1-1 또는 미디어 바이패스에서 사용할 수 있는 네트워크 지역을 수정합니다.

## 네트워크 사이트를 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  Set-CsNetworkSite cmdlet을 실행하여 네트워크 사이트를 수정합니다.
    
        Set-CsNetworkSite -Identity <string>
    
    예를 들면 다음과 같습니다.
    
        Set-CsNetworkSite -Identity Albuquerque -NetworkRegionID NorthAmerica
    
    이 예에서는 "앨버커키"라는 사이트를 "북미" 네트워크 지역으로 이동했습니다. 통화 허용 제어, E9-1-1 또는 미디어 바이패스를 배포하기 위해 네트워크 사이트 구성을 수정하려면 각각 BWPolicyProfileID 또는 LocationPolicy 매개 변수와 함께 Set-CsNetworkSite cmdlet을 실행하여 네트워크 사이트 설정을 수정합니다.
    

    > [!NOTE]
    > 미디어 바이패스에는 BypassID 매개 변수가 있지만 자동으로 생성된 바이패스 ID를 재정의하지 않는 것이 좋습니다. 미디어 바이패스에 대한 네트워크 사이트를 구성하기 위해 추가 매개 변수를 지정할 필요는 없습니다.



3.  토폴로지에 대한 네트워크 사이트 수정을 종료하려면 다른 사이트에 대한 설정을 사용하여 2단계를 반복합니다.

## Lync Server 제어판을 사용하여 네트워크 사이트를 수정하려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성** 을 클릭합니다.

3.  **사이트** 탐색 단추를 클릭합니다.

4.  테이블에서 수정할 네트워크 사이트를 클릭합니다.

5.  **편집** 을 클릭한 다음 **자세한 정보 표시...** 를 클릭합니다.

6.  **사이트 편집** 페이지에서 이 네트워크 사이트의 설정 값을 적절하게 변경합니다.

7.  **커밋** 을 클릭합니다.

8.  네트워크 사이트 수정을 종료하려면 다른 사이트에 대한 설정을 사용하여 4-7단계를 반복합니다.

