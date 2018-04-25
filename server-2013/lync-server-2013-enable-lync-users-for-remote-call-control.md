---
title: 'Lync Server 2013: Lync 사용자가 원격 통화 제어를 사용하도록 설정'
TOCTitle: Lync 사용자가 원격 통화 제어를 사용하도록 설정
ms:assetid: f39bc10d-034c-4875-a0b8-554e1109e7e6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615048(v=OCS.15)
ms:contentKeyID: 49305514
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync 사용자가 원격 통화 제어를 사용하도록 설정

 

_**마지막으로 수정된 항목:** 2012-09-21_

서버 기반의 인밴드 프로비전 정책을 사용하여 원격 통화 제어에 대해 Lync 사용자를 구성할 수 있습니다. 인밴드 프로비전 설정은 Lync Server 제어판 또는 Lync Server 관리 셸 명령줄 인터페이스를 사용하여 관리할 수 있습니다. 이러한 도구는 이전 버전의 그룹 정책 설정을 관리하는 데 사용된 WMI(Windows Management Instrumentation) 스냅인을 대체합니다.

사용자가 Lync에서 자신의 원격 통화 제어를 구성하도록 허용하려면 **회선 서버 URI** 및 **줄 URI** 값을 지정하지 않고 서버에서 사용자에 대한 원격 통화 제어 설정을 구성하면 됩니다. 올바른 **회선 서버 URI** 및 **줄 URI** 값을 사용자에게 전달하고 이러한 설정을 구성할 수 있는 지침을 제공해야 합니다. Lync Server에서 원격 통화 제어를 수동으로 구성하는 절차는 Microsoft Office 웹 사이트의 Lync 클라이언트 설명서에서 "전화 옵션 및 번호 설정"( [http://go.microsoft.com/fwlink/?linkid=210132\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=210132%26clcid=0x412))을 참조하십시오.

기존 Communications Server 2007 R2 또는 Communications Server 2007 배포가 있는 경우 Communicator 2007 R2 및 Communicator 2007 클라이언트는 수평적 마이그레이션 중에 그룹 정책을 계속 사용합니다. 그러나 정책 설정을 Lync 클라이언트에 전달하려면 일치하는 Lync Server 인밴드 프로비전 설정을 구성해야 합니다.


> [!NOTE]
> 사용자가 원격 통화 제어를 사용하도록 설정하려면 사용자에게 줄 URI와 회선 서버 URI가 둘 다 있어야 합니다. <A href="lync-server-2013-deployment-tasks-for-remote-call-control.md">Lync Server 2013의 원격 통화 제어에 대한 배포 작업</A>에 설명된 대로 게이트웨이에 필요한 구문을 이러한 설정에 사용해야 합니다.<BR>회선 서버 URI의 도메인이 고정 게이트웨이 경로를 구성할 때 MatchUri 매개 변수에 지정한 대상 도메인과 같은지 확인합니다.<BR>줄 URI는 사용자에게 할당된 전화 번호를 E.164 형식으로 지정합니다. 이 형식은 "TEL:" 접두사로 시작해야 합니다. 예를 들면 tel:+14255550150과 같습니다. 내선 번호를 구성하려면 tel:+14255550150;ext=111과 같이 형식을 지정하면 됩니다. 이전에 사용자의 줄 URI를 구성하고 값을 변경하지 않은 경우에는 사용자가 원격 통화 제어를 사용하도록 설정할 때 줄 URI를 지정하지 않아도 됩니다.



## 관리 셸을 사용하여 Lync 사용자가 원격 통화 제어를 사용하도록 설정하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원 또는 **Set-CsUser** cmdlet를 할당한 역할 기반 액세스 제어 역할로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  **Set-CsUser** cmdlet를 사용하여 기존 Lync 사용자에 대한 원격 통화 제어를 구성하려면 다음을 수행합니다.
    
        Set-CsUser -Identity <User ID> -EnterpriseVoiceEnabled $false -LineServerUri <SIP URI of the SIP/CSTA gateway> -LineUri <TEL URI of the user> -RemoteCallControlTelephonyEnabled $true
    
    예를 들면 다음과 같습니다.
    
        Set-CsUser -Identity "Katie Jordan" -EnterpriseVoiceEnabled $false -LineServerUri sip:rccgateway@contoso.net -LineUri tel:+14255550150 -RemoteCallControlTelephonyEnabled $true

## Lync Server 제어판을 사용하여 원격 통화 제어에 대해 사용자를 구성하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자** 를 클릭합니다.

4.  **사용자 검색** 상자에 원하는 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 첫부분을 입력하고 **찾기** 를 클릭합니다.

5.  표에서 수정할 사용자 계정을 클릭합니다.

6.  **편집** 메뉴에서 **수정** 을 클릭합니다.

7.  **전화 통신** 에서 다음 중 하나를 수행합니다.
    
      - 사용자가 Lync 2013에서 PBX(Private Branch Exchange) 전화를 제어하여 PC-PC 음성 통화 및 PC-전화 통화를 설정하도록 원격 통화 제어를 구성하려면 **원격 통화 제어** 를 클릭합니다. **줄 URI** 에 사용자의 전화 번호를 지정합니다. **회선 서버 URI** 에 SIP/CSTA 게이트웨이의 SIP URI를 지정합니다.
    
      - 원격 통화 제어를 사용하되, PC-PC 음성 통화를 사용하지 않도록 설정하고 사용자가 Lync 2013에서 PBX 전화를 제어하여 PC-전화 통화만 설정하도록 구성하려면 **원격 통화 제어만** 을 클릭합니다. **줄 URI** 에 사용자의 전화 번호를 지정합니다. **회선 서버 URI** 에 SIP/CSTA 게이트웨이의 SIP URI를 지정합니다.

8.  작업을 마치면 **커밋** 을 클릭합니다.

