---
title: 'Lync Server 2013: 페더레이션 파트너에게 보관 고지 사항 보내기를 사용하거나 사용하지 않도록 설정'
TOCTitle: 페더레이션 파트너에게 보관 고지 사항 보내기를 사용하거나 사용하지 않도록 설정
ms:assetid: c8e9a2fa-9dc1-4e4d-919f-56ece8004864
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182584(v=OCS.15)
ms:contentKeyID: 49305016
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 페더레이션 파트너에게 보관 고지 사항 보내기를 사용하거나 사용하지 않도록 설정

 

_**마지막으로 수정된 항목:** 2013-02-23_

에지 서버를 배포하고 조직에 대해 페더레이션을 사용하도록 설정할 때 보관 고지 사항을 페더레이션 파트너에게 자동으로 보낼지 여부를 지정해야 합니다. 외부 통신을 보관할 경우에는 보관 고지 사항을 보낼 수 있도록 설정해야 합니다 해당 구성을 변경하려면 이 항목의 절차를 사용합니다.


> [!NOTE]
> 다음 절차에서는 이미 조직에 대해 페더레이션이 사용하도록 설정되어 있다고 가정합니다. 페더레이션을 사용하도록 설정하는 방법에 대한 자세한 내용은 배포 설명서 또는 작업 설명서에서 <A href="lync-server-2013-enable-or-disable-remote-user-access.md">Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함</A> 섹션을 참조하십시오.



## 페더레이션 파트너에게 보관 고지 사항 보내기를 사용하거나 사용하지 않도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **외부 사용자 액세스** 를 클릭한 다음 **액세스 에지 구성** 을 클릭합니다.

4.  **액세스 에지 구성** 탭에서 **전역** , **편집** , **자세한 정보 표시** 를 차례로 클릭합니다.

5.  **액세스 에지 구성 편집** 의 **페더레이션 사용자와의 통신 사용** 에서 **페더레이션 파트너에게 보관 고지 사항 보내기** 확인란을 선택하거나 선택 취소하여 보관 고지 사항을 자동으로 보내거나 보내지 않도록 설정할 수 있습니다.

6.  **커밋** 을 클릭합니다.

페더레이션 사용자가 Lync Server 2013 배포 내의 사용자와 공동 작업을 수행할 수 있도록 하려면 페더레이션 사용자 액세스를 지원하기 위한 외부 액세스 정책도 하나 이상 구성해야 합니다. 자세한 내용은 배포 설명서 또는 작업 설명서의 [Lync Server 2013에서 XMPP 페더레이션 파트너 관리](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md) 섹션을 참조하십시오. 특정 페더레이션 도메인의 액세스 제어에 대한 자세한 내용은 배포 설명서 또는 작업 설명서의 [Lync Server 2013에서 허용되는 외부 도메인 지원 구성](lync-server-2013-configure-support-for-allowed-external-domains.md) 섹션을 참조하십시오.

## Windows PowerShell cmdlet을 사용하여 보관 고지 사항을 사용하거나 사용하지 않도록 설정

보관 고지 사항의 사용은 Windows PowerShell 및 Set-CsAccessEdgeConfiguration cmdlet을 사용하여 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 원격 세션의 Windows PowerShell에서 실행할 수 있습니다.원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 보관 고지 사항을 사용하도록 설정하려면

  - 보관 고지 사항을 사용하도록 설정하려면 **EnableArchivingDisclaimer** 속성 값을 True($True)로 설정합니다.
    
        Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $True

## 보관 고지 사항을 사용하지 않도록 설정하려면

  - 보관 고지 사항을 사용하지 않도록 설정하려면 **EnableArchivingDisclaimer** 속성 값을 False($False)로 설정합니다.
    
        Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $False

