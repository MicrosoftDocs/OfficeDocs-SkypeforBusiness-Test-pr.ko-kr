---
title: 네트워크 서브넷 삭제
TOCTitle: 네트워크 서브넷 삭제
ms:assetid: c1850f38-40a3-48c9-b6f1-f181c5e63b6b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721873(v=OCS.15)
ms:contentKeyID: 49885964
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 서브넷 삭제

 

_**마지막으로 수정된 항목:** 2013-02-21_

다음 절차를 사용하여 서브넷을 삭제할 수 있습니다. Lync Server 제어판에서 네트워크 서브넷을 만들거나, 수정하거나, 삭제할 수 있습니다. 네트워크 서브넷을 만들고 수정하는 방법에 대한 자세한 내용은 [네트워크 서브넷 만들기 또는 수정](lync-server-2013-create-or-modify-network-subnets.md)을 참조하십시오.

CAC(통화 허용 제어)를 구현하는 대부분의 Microsoft Lync Server 2013 배포에는 일반적으로 많은 서브넷이 있습니다. 따라서 Lync Server 관리 셸에서 서브넷을 구성하는 것이 가장 효율적인 경우가 많습니다. 여기서 Windows PowerShell cmdlet **Import-CSV**와 함께 **New-CsNetworkSubnet**을 호출할 수 있습니다. 두 cmdlet을 함께 사용하면 CSV(쉼표로 구분된 값) 파일에서 서브넷 설정을 읽어와서 여러 개의 서브넷을 동시에 만들 수 있습니다. .csv 파일에서 서브넷을 만드는 방법의 예제는 [New-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSubnet)을 참조하십시오.

## 네트워크 서브넷을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **서브넷**을 클릭합니다.

4.  **서브넷** 페이지에서 삭제할 서브넷을 클릭합니다.
    

    > [!NOTE]
    > 한 번에 둘 이상의 서브넷을 삭제할 수 있습니다. 이렇게 하려면 Ctrl 키를 누른 상태에서 여러 서브넷을 선택합니다. 또는 모든 서브넷을 선택하려면 <STRONG>편집</STRONG> 메뉴에서 <STRONG>모두 선택</STRONG>을 클릭합니다.



5.  **편집** 메뉴에서 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.

## 참고 항목

#### 작업

[네트워크 서브넷 만들기 또는 수정](lync-server-2013-create-or-modify-network-subnets.md)

