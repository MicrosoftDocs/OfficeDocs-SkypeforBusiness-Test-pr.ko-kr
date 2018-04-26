---
title: hot-desk를 사용하거나 사용하지 않도록 설정
TOCTitle: hot-desk를 사용하거나 사용하지 않도록 설정
ms:assetid: 93a7fed6-f61a-4b41-9336-a8320afa87cf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994057(v=OCS.15)
ms:contentKeyID: 52056905
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# hot-desk를 사용하거나 사용하지 않도록 설정

 

_**마지막으로 수정된 항목:** 2013-02-20_

공통 영역 전화를 *hot-desk 전화*로 설정할 수 있습니다. 사용자는 hot-desk 전화를 통해 자신의 사용자 계정에 로그온할 수 있으며 로그온한 후에는 Lync Server 기능과 자신의 사용자 프로필 설정을 사용할 수 있습니다. hot-desk는 클라이언트 정책을 사용하여 관리되며, hot-desk를 사용하거나 사용하지 않도록 설정하려면 공통 영역 전화에서 사용하는 클라이언트 정책을 수정해야 합니다. 공통 영역 전화에 할당된 회의 정책을 확인하는 방법에 대한 자세한 내용은 [공통 영역 전화 정보 보기](lync-server-2013-view-common-area-phone-information.md)를 참조하십시오.

**New-CSClientPolicy** cmdlet 또는 **Set-CSClientPolicy** cmdlet의 EnableHotdesking 매개 변수를 사용하여 다음과 같이 전화에서 hot-desk를 사용하거나 사용하지 않도록 설정합니다. 이러한 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.의 원격 세션에서 실행합니다.


## hot-desk를 사용하도록 설정

  - 공통 영역 전화에 대해 hot-desk를 사용하도록 설정하려면 해당 전화나 전화 집합에 대해 할당된 클라이언트 정책을 수정해야 합니다.
    
    수정해야 하는 정책을 확인한 후에는 **Set-CsClientPolicy** cmdlet을 사용하여 EnableHotdesking 매개 변수를 True로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsClientPolicy -Identity "CommonAreaPhonePolicy" - EnableHotdesking $True

  - **New-CsClientPolicy** cmdlet을 사용하여 hot-desk를 사용하도록 설정하는 새 클라이언트 정책을 만들 수도 있습니다. 예를 들면 다음과 같습니다.
    
        New-CsClientPolicy -Identity "NewCommonAreaPhonePolicy" - EnableHotdesking $True


> [!IMPORTANT]
> 이 정책은 작성한 후에 해당하는 공통 영역 전화에 할당해야 합니다. 자세한 내용은 <A href="lync-server-2013-assign-policies-to-a-common-area-phone.md">공통 영역 전화에 정책 할당</A>을 참조하십시오.



## hot-desk를 사용하지 않도록 설정

  - 공통 영역 전화에 대해 hot-desk를 사용하지 않도록 설정하려면 **Set-CsClientPolicy** cmdlet의 EnableHotdesking 매개 변수를 기본값인 False로 다시 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsClientPolicy -Identity "CommonAreaPhonePolicy" - EnableHotdesking $False

자세한 내용은 [New-CsClientPolicy](new-csclientpolicy.md) cmdlet 및 [Set-CsClientPolicy](set-csclientpolicy.md) cmdlet의 도움말 항목을 참조하십시오.

