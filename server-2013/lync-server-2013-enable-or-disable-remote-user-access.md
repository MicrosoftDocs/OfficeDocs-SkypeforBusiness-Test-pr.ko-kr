---
title: 'Lync Server 2013: 원격 사용자 액세스 사용 또는 사용 안 함'
TOCTitle: 원격 사용자 액세스 사용 또는 사용 안 함
ms:assetid: cd9d3ddc-4839-457a-86d9-b15413e74002
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182586(v=OCS.15)
ms:contentKeyID: 49305062
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함

 

_**마지막으로 수정된 항목:** 2013-02-23_

원격 사용자는 조직 내에 영구 Active Directory ID가 있는 조직 내의 사용자입니다. 원격 사용자는 흔히 조직의 네트워크에 연결되어 있지 않을 때 VPN(가상 사설망)을 사용하여 네트워크 외부에서 Lync Server 네트워크에 로그인합니다. 원격 사용자에는 자택이나 출장지에서 일하는 직원과 엔터프라이즈 자격 증명이 부여된 신뢰할 수 있는 공급업체 등의 기타 원격 직원이 포함됩니다. 원격 사용자에 대해 원격 사용자 액세스를 사용하도록 설정한 경우 지원되는 원격 사용자는 Lync Server를 사용하여 내부 사용자와 공동 작업을 수행하기 위해 인터넷을 통해 연결하며, VPN을 사용하여 연결할 필요가 없습니다.

원격 사용자 액세스를 지원하려면 원격 사용자 액세스를 사용하도록 설정해야 합니다. 원격 사용자 액세스를 사용하도록 설정하는 경우 전체 조직에 대해 원격 사용자 액세스를 사용하도록 설정해야 합니다. 나중에 페더레이션 도메인 사용자의 액세스를 일시적으로 또는 영구적으로 차단하려면 조직의 페더레이션을 사용하지 않도록 설정하면 됩니다. 이 섹션의 절차를 사용하여 조직에 대해 원격 사용자 액세스를 사용하거나 사용하지 않도록 설정하십시오.


> [!NOTE]
> 원격 사용자 액세스를 사용하도록 설정하면 액세스 에지 서비스를 실행 중인 서버가 원격 사용자와의 통신을 지원하도록 지정될 뿐이지만 원격 사용자는 원격 사용자 액세스 사용을 관리하기 위한 하나 이상의 정책도 구성될 때까지 조직의 메신저 대화나 회의에 참가할 수 없습니다. 한 정책 수준에서 적용되는 Lync Server 정책 설정은 다른 정책 수준에서 적용되는 설정을 재정의할 수 있습니다. Lync Server 정책 우선 순위에 따르면 사용자 정책(최대 영향력)이 사이트 정책을 재정의한 후 사이트 정책이 글로벌 정책(최소 영향력)을 재정의합니다. 즉, 정책 설정이 해당 정책의 영향을 받는 개체에 가까울수록 개체에 미치는 영향력도 커집니다. 원격 사용자 액세스를 사용하기 위해 정책을 구성하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-configure-policies-to-control-remote-user-access.md">Lync Server 2013에서 원격 사용자 액세스를 제어하도록 정책 구성</A>를 참조하십시오.



## 조직에 대해 원격 사용자 액세스를 사용하거나 사용하지 않도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **페더레이션 및 외부 액세스** 를 클릭하고 **액세스 에지 구성** 을 클릭합니다.

4.  **액세스 에지 구성** 페이지에서 **전역** 을 클릭하고 **편집** 을 클릭한 후에 **세부 정보 표시** 를 클릭합니다.

5.  **액세스 에지 구성 편집** 에서 다음 중 하나를 수행합니다.
    
      - 조직에 대해 원격 사용자 액세스를 사용하도록 설정하려면 **원격 사용자 액세스 사용** 확인란을 선택합니다.
    
      - 조직에 대해 원격 사용자 액세스를 사용하지 않도록 설정하려면 **원격 사용자 액세스 사용** 확인란을 선택 취소합니다.

6.  **커밋** 을 클릭합니다.

원격 사용자가 Lync Server를 실행하는 서버에 로그인할 수 있도록 하려면 원격 사용자 액세스를 지원하는 외부 액세스 정책을 하나 이상 구성해야 합니다. 자세한 내용은 배포 설명서 또는 작업 설명서에서 [Lync Server 2013에서 원격 사용자 액세스를 제어하도록 정책 구성](lync-server-2013-configure-policies-to-control-remote-user-access.md)를 참조하십시오.

## Windows PowerShell cmdlet을 사용하여 원격 사용자 액세스를 사용하거나 사용하지 않도록 설정

Windows PowerShell 및 Set-CsAccessEdgeConfiguration cmdlet을 사용하여 원격 사용자 액세스를 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 원격 사용자 액세스를 사용하도록 설정하려면

  - 원격 사용자 액세스를 사용하도록 설정하려면 **AllowOutsideUsers** 속성 값을 True($True)로 설정합니다.
    
        Set-CsAccessEdgeConfiguration -AllowOutsideUsers $True

## 원격 사용자 액세스를 사용하지 않도록 설정하려면

  - 원격 사용자 액세스를 사용하지 않도록 설정하려면 **AllowOutsideUsers** 속성 값을 False($False)로 설정합니다.
    
        Set-CsAccessEdgeConfiguration -AllowOutsideUsers $False

