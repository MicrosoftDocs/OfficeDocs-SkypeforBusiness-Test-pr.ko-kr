---
title: 'Lync Server 2013: 공용 사용자 액세스를 제어하도록 정책 구성'
TOCTitle: 공용 사용자 액세스를 제어하도록 정책 구성
ms:assetid: 090aea0f-ef0b-49da-9c80-02d9279f2fa6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520946(v=OCS.15)
ms:contentKeyID: 49302732
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 공용 사용자 액세스를 제어하도록 정책 구성

 

_**마지막으로 수정된 항목:** 2013-10-07_

공용 IM(인스턴트 메시징) 연결을 사용하면 조직 내 사용자가 IM을 통해 Windows Live의 인터넷 서비스 네트워크, Yahoo\! 및 AOL을 비롯한 공용 IM 서비스 공급자가 제공하는 IM 서비스 사용자와 통신할 수 있습니다. 하나 이상의 외부 사용자 액세스 정책을 구성하여 공용 사용자가 내부 Lync Server 사용자와 공동 작업을 수행할 수 있는지 여부를 제어할 수 있습니다. 공용 인스턴트 메시징 연결은 배포 및 사용자 구성을 사용하는 추가된 기능입니다. 이 기능은 공용 IM 공급자의 서비스 프로비저닝에 따라서도 달라집니다. 공용 공급자를 사용하도록 배포를 프로비저닝하는 방법에 대한 자세한 내용은 "Microsoft Lync Server, Office Communications Server 및 Live Communications Server용 공용 IM 연결 프로비저닝 가이드" 가이드( <http://go.microsoft.com/fwlink/?linkid=269821>)를 참조하십시오.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



Microsoft Lync Server 공용 IM 연결 프로비저닝 사이트에 액세스하려면 <http://go.microsoft.com/fwlink/?linkid=212638> 링크를 사용하십시오.

공용 사용자 액세스를 제어하려면 전역, 사이트 및 사용자 수준에서 정책을 구성할 수 있습니다. 구성할 수 있는 정책의 유형에 대한 자세한 내용은 배포 설명서 또는 계획 설명서에서 [Lync Server 2013에서 외부 사용자 액세스에 대한 지원 구성](lync-server-2013-configuring-support-for-external-user-access.md)을 참조하십시오. 한 정책 수준에서 적용되는 Lync Server 정책 설정은 다른 정책 수준에서 적용되는 설정을 재정의할 수 있습니다. Lync Server 정책 우선 순위에 따르면 사용자 정책(최대 영향력)이 사이트 정책을 재정의한 후 사이트 정책이 글로벌 정책(최소 영향력)을 재정의합니다. 즉, 정책 설정이 해당 정책의 영향을 받는 개체에 가까울수록 개체에 미치는 영향력도 커집니다.

IM 초대의 경우 응답 여부는 클라이언트 소프트웨어에 따라 다릅니다. 사용자가 구성한 규칙(사용자 클라이언트 **허용** 및 **차단** 목록의 설정)에 의해 명시적으로 차단되는 경우가 아니면 요청이 수락됩니다. 또한 사용자가 자신의 **허용** 목록에 없는 사용자에 대해 모든 IM을 차단하도록 선택한 경우 IM 초대가 차단될 수 있습니다.


> [!NOTE]
> 조직에 대해 페더레이션을 사용하도록 설정하지 않았더라도 공용 사용자 액세스를 제어하는 정책을 구성할 수 있습니다. 그러나 구성하는 정책은 조직에 대해 페더레이션을 사용하도록 설정하는 경우에만 적용됩니다. 페더레이션을 사용하도록 설정하는 방법에 대한 자세한 내용은 배포 설명서 또는 작업 설명서에서 <A href="lync-server-2013-enable-or-disable-remote-user-access.md">Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함</A>을 참조하십시오. 또한 공용 사용자 액세스를 제어하기 위한 사용자 정책을 지정하는 경우 해당 정책은 Lync Server에 대해 사용하도록 설정되었으며 해당 정책을 사용하도록 구성된 사용자에게만 적용됩니다. Lync Server에 로그인할 수 있는 공용 사용자를 지정하는 방법에 대한 자세한 내용은 배포 설명서 또는 작업 설명서에서 <A href="lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md">Lync Server 2013에서 Lync 사용이 가능한 사용자에게 외부 사용자 액세스 정책 할당</A>을 참조하십시오.



다음 절차에 따라 하나 이상의 공용 IM 공급자 사용자의 액세스를 지원하기 위한 정책을 구성합니다.

## 공용 사용자 액세스를 지원하기 위한 외부 액세스 정책을 구성하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **외부 사용자 액세스** 를 클릭하고 **외부 액세스 정책** 을 클릭합니다.

4.  **외부 액세스 정책** 페이지에서 다음 중 하나를 수행합니다.
    
      - 공용 사용자 액세스를 지원하기 위한 글로벌 정책을 구성하려면 글로벌 정책을 클릭하고 **편집** 을 클릭한 후에 **자세한 정보 표시** 를 클릭합니다.
    
      - 새 사이트 정책을 만들려면 **새로 만들기** 를 클릭하고 **사이트 정책** 을 클릭합니다. **사이트 선택** 의 목록에서 적절한 사이트를 클릭하고 **확인** 을 클릭합니다.
    
      - 새 사용자 정책을 만들려면 **새로 만들기** 를 클릭하고 **사용자 정책** 을 클릭합니다. **새 외부 액세스 정책** 의 **이름** 필드에서 사용자 정책이 다루는 내용을 나타내는 고유한 이름을 만듭니다(예: 공용 사용자에 대한 통신을 사용하도록 설정하는 사용자 정책의 경우 **EnablePublicUsers** ).
    
      - 기존 정책을 변경하려면 테이블에 나열되어 있는 적절한 정책을 클릭하고 **편집** , **세부 정보 표시** 를 차례로 클릭합니다.

5.  (선택 사항) 설명을 추가하거나 편집하려면 정책에 대한 정보를 **설명** 에 지정합니다.

6.  다음 중 하나를 수행합니다.
    
      - 정책에 대한 공용 사용자 액세스를 사용하도록 설정하려면 **공용 사용자와의 통신 사용** 확인란을 선택합니다.
    
      - 정책에 대한 공용 사용자 액세스를 사용하지 않도록 설정하려면 **공용 사용자와의 통신 사용** 확인란 선택을 취소합니다.

7.  **커밋** 을 클릭합니다.

공용 사용자 액세스를 사용하도록 설정하려면 조직에서 페더레이션 지원도 사용하도록 설정해야 합니다. 자세한 내용은 [Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성](lync-server-2013-configure-policies-to-control-federated-user-access.md)을 참조하십시오.

사용자 정책의 경우에는 공용 사용자와 공동 작업하도록 할 공용 사용자에게도 정책을 적용해야 합니다. 자세한 내용은 [사용자별 정책 할당](lync-server-2013-assigning-per-user-policies.md)을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013에서 공용 SIP 페더레이션 공급자 만들기 또는 편집](lync-server-2013-create-or-edit-public-sip-federated-providers.md)  

#### 기타 리소스

[Lync Server 2013에서 조직에 대한 SIP 페더레이션 공급자 관리](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)

