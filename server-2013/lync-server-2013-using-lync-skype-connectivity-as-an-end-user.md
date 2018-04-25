---
title: 'Lync Server 2013: 최종 사용자로서 Lync-Skype 연결 사용'
TOCTitle: 최종 사용자로서 Lync-Skype 연결 사용
ms:assetid: ad22f731-118c-4349-8790-b1a72941cbdd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn440175(v=OCS.15)
ms:contentKeyID: 59602779
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 최종 사용자로서 Lync Server 2013에서 Lync-Skype 연결 사용

 

_**마지막으로 수정된 항목:** 2014-12-05_

Lync-Skype 연결을 통해 Skype 사용자와 Lync 사용자는 서로를 대화 상대로 추가하고, 메신저 대화를 교환하고, 오디오 및 비디오 통화를 할 수 있습니다. Skype 사용자가 Lync 사용자를 추가하면 Skype 사용자는 Skype에서 Lync 사용자의 SIP(Session Initiation Protocol) URI(Uniform Resource Identifier)가 포함된 대화 상대를 만듭니다. 반대로 Lync 사용자가 Skype 대화 상대를 추가하는 경우에는 Lync 사용자가 Lync에서 Skype 사용자 이름이 아닌 Skype 사용자의 MSA(Microsoft 계정)가 포함된 대화 상대를 만듭니다.

**MSA란?** Skype 사용자가 Lync 대화 상대와 통신하려면 Microsoft 계정(이전 Windows Live ID)을 사용하여 Skype에 로그인해야 합니다. Microsoft 계정은 전자 메일 주소와 암호의 조합으로 구성되며, Microsoft OneDrive 저장 기술, Windows Phone, Microsoft Xbox LIVE 온라인 게임 서비스 및 Microsoft Outlook 메시징 및 공동 작업 클라이언트(및 이전 Microsoft Hotmail 웹 기반 전자 메일 서비스 또는 Windows Live Messenger) 등의 서비스에 로그인하는 데 사용할 수 있습니다. 전자 메일 주소 및 암호를 사용하여 이 서비스 또는 다른 서비스에 로그인했다면 이미 Microsoft 계정이 있는 것입니다. Microsoft 계정을 만드는 방법에 대한 자세한 내용은 Microsoft 계정 등록 페이지([http://go.microsoft.com/fwlink/p/?LinkId=306061](http://go.microsoft.com/fwlink/p/?linkid=306061))를 참조하세요. 다양한 응용 프로그램과 서비스에서 SSO(Single Sign-on)를 위해 기존 Skype 계정을 Microsoft 계정과 병합할 수 있습니다. 계정이 병합되면 Skype 사용자가 Lync 사용자에게 대화 상대 요청을 보낼 수 있습니다.


> [!IMPORTANT]
> Lync 및 Skype 사용자가 서로 완벽하게 통신하기 위해서는 다음 요구 사항이 충족되어야 합니다. 
> <UL>
> <LI>
> <P>Skype 사용자는 MSA(Microsoft 계정)를 사용하여 Skype 클라이언트에 로그인해야 합니다.</P>
> <LI>
> <P>Lync 관리자는 Lync 사용자를 위해 공용 메신저 연결을 설정해야 합니다.</P>
> <LI>
> <P>Skype 사용자가 Lync 대화 상대를 추가할 때 Lync라는 단어가 대화 상대 이름 아래에 나타나는지 확인합니다. 이것은 Lync URI를 찾았다는 의미입니다.</P>
> <LI>
> <P>Skype 사용자가 Lync 대화 상대를 추가했는데도 해당 Lync 도메인에 대해 어떤 검색 결과도 반환되지 않으면 PIC 프로비저닝 프로세스가 완료되지 않았거나 Lync 도메인이 설정되지 않았을 수 있습니다.</P>
> <LI>
> <P>Lync 및 Skype 사용자의 개인 정보 설정에 따라 각 사용자가 새 대화 상대를 수락할 때까지 메신저, 비디오, 현재 상태가 작동하지 않을 수 있습니다.</P></LI></UL>



**Skype 대화 상대를 Lync 2013에 추가하려면**

1.  Lync에서 **대화 상대 추가 \> 내 조직 외부의 대화 상대 추가**를 클릭합니다.

2.  사용 가능한 대화 상대 공급자 목록에서 아래와 같이 **Skype**를 선택합니다.
    
    ![Skype 연락처를 추가하는 방법을 보여 주는 Lync 클라이언트](images/Dn440175.ac4e2f21-c1d9-47d8-b99e-d49fe4eb36d7(OCS.15).jpg "Skype 연락처를 추가하는 방법을 보여 주는 Lync 클라이언트")

3.  **메신저 주소** 필드에 Skype 사용자의 MSA(Microsoft 계정)를 입력합니다.

4.  **대화 상대 그룹에 추가** 드롭다운 상자에서 사용자를 추가할 대화 상대 그룹을 선택합니다.

5.  **정보 공개 범위 설정** 드롭다운 상자에서 적절한 대화 상대 설정을 선택한 다음 **확인**을 클릭합니다.

6.  사용자가 Lync에서 대화 상대로 표시됩니다. 사용자 속성을 보려면 사용자를 선택하고 사용자 이름을 마우스 오른쪽 단추로 클릭한 다음 **대화 상대 카드 보기**를 클릭합니다. 아래와 같이 **통화**, **Lync 통화**를 차례로 클릭하여 새로 추가한 Skype 사용자와 음성 또는 비디오 통화를 설정할 수 있습니다.
    
    ![대화 상대와 Lync 통화를 시작하는 Lync 클라이언트](images/Dn440175.cd7cb21a-87f7-4bfa-b30c-980d4098d226(OCS.15).jpg "대화 상대와 Lync 통화를 시작하는 Lync 클라이언트")

대화 상대 지원에 대한 자세한 내용은 [Lync에서 대화 상대 추가](http://office.microsoft.com/ko-kr/office365-lync-online-help/add-a-contact-in-lync-ha102828922.aspx) 및 [Lync에서 외부 대화 상대 추가](http://office.microsoft.com/ko-kr/office365-lync-online-help/add-an-external-contact-in-lync-ha104038998.aspx?ctt=5%26origin=ha102828922)를 참고하세요.

Skype 사용자의 Microsoft 계정이 사용자 지정 도메인 이름(예: **bob@contoso.com**)인 경우 Lync 사용자는 다음 두 가지 방법으로 해당 Microsoft 계정을 Lync에 추가할 수 있습니다.

1.  **대화 상대 추가** 아이콘을 사용합니다. 또는,

2.  **대화 상대 또는 채팅방을 찾거나 전화를 겁니다** 필드를 사용합니다.

각 인스턴스에서 Lync 사용자는 Skype 사용자의 전자 메일 주소를 **사용자(도메인 이름)@msn.com** 형식으로 입력해야 합니다.


> [!IMPORTANT]
> <STRONG>@live.com, @hotmail.com 또는 @outlook.com</STRONG> 도메인 이름을 사용하는 Microsoft 계정에는 이 단계가 필요하지 않습니다. 지원되는 사용자 지정 도메인 이름에 대한 자세한 내용은 <A href="http://support.microsoft.com/kb/897567">지원되는 공용 메신저 도메인</A>을 참고하세요.



**사용자 지정 도메인 이름을 사용할 경우 Skype 대화 상대를 Lync에 추가하려면**

1.  Lync에서 **대화 상대 추가 \> 내 조직 외부의 대화 상대 추가**를 클릭합니다.

2.  사용 가능한 대화 상대 공급자 목록에서 아래와 같이 **Skype**를 선택합니다.
    
    ![Skype 연락처를 추가하는 방법을 보여 주는 Lync 클라이언트](images/Dn440175.ac4e2f21-c1d9-47d8-b99e-d49fe4eb36d7(OCS.15).jpg "Skype 연락처를 추가하는 방법을 보여 주는 Lync 클라이언트")

3.  **메신저 주소** 필드에 Skype 사용자의 MSA(Microsoft 계정)를 **사용자(도메인 이름)@msn.com** 형식으로 입력합니다. 따라서 사용자 bob@contoso.com의 경우 입력한 내용은 아래와 같이 **bob(contoso.com)@msn.com**이 됩니다.
    
    ![Lync 클라이언트 새 대화 상대 설정](images/Dn440175.422e69b5-2c0c-4260-858f-f10309af772f(OCS.15).jpg "Lync 클라이언트 새 대화 상대 설정")

4.  **대화 상대 그룹에 추가** 드롭다운 목록 상자에서 사용자를 추가할 대화 상대 그룹을 선택합니다.

5.  **정보 공개 범위 설정** 드롭다운 목록 상자에서 적절한 대화 상대 설정을 선택한 다음 **확인**을 클릭합니다.

6.  Lync 사용자는 Lync에서 **대화 상대 또는 채팅방을 찾거나 전화를 겁니다** 필드를 사용하여 **사용자(도메인 이름)@msn.com**과 비슷한 주소를 추가할 수도 있습니다. 따라서 bob@contoso.com Microsoft 계정의 경우 입력한 내용은 아래와 같이 **bob(contoso.com)@msn.com**이 됩니다.
    
    ![Lync 클라이언트의 대화 상대 검색](images/Dn440175.69787db8-f9b9-49e5-b197-b90b10393301(OCS.15).jpg "Lync 클라이언트의 대화 상대 검색")

7.  이 절차의 앞부분에 설명된 4-5단계에 따라 대화 상대 그룹에 대화 상대를 추가하고 적절한 정보 공개 범위를 선택합니다.

**Lync 대화 상대를 Skype에 추가하려면**

1.  Skype에 로그인합니다. Skype 사용자는 MSA(Microsoft 계정)를 사용하여 Skype 클라이언트에 로그인해야 합니다.
    
    ![Skype 클라이언트 로그인 페이지](images/Dn440175.b4fd7c5a-be35-4205-80c7-872863b7a91d(OCS.15).jpg "Skype 클라이언트 로그인 페이지")

2.  대화 상대 추가 아이콘을 선택합니다.

3.  Lync 사용자의 SIP URI를 입력합니다(예: bob@contoso.com).

4.  Skype의 검색 결과에서 일치하는 항목이 나타나면 Lync 사용자 이름 아래에서 **Lync**라는 단어를 찾습니다. 이 단어가 있으면 Skype에서 Lync 클라이언트의 SIP URI를 찾았다는 의미입니다. 이름을 클릭합니다.
    
    ![Lync 대화 상대를 보여 주는 Skype 클라이언트](images/Dn440175.4e690a72-1a54-4442-89cf-0fb45ac5f56a(OCS.15).jpg "Lync 대화 상대를 보여 주는 Skype 클라이언트")

5.  창의 오른쪽 위 모서리에서 대화 상대에 추가를 클릭합니다.

6.  새 대화 상대가 대화 상대 목록에 추가되지만 상대가 요청을 수락할 때까지 상태 아이콘 대신 물음표가 표시됩니다. 새 대화 상대가 요청을 수락하면 상대의 온라인 상태를 보고, 메신저 대화를 시작하고, 음성 및 비디오 통화를 할 수 있습니다.
    
    ![Lync 대화 상대와의 Skype 클라이언트 메신저 대화](images/Dn440175.86ca6f81-4db9-45ba-8511-1f7541aaf066(OCS.15).jpg "Lync 대화 상대와의 Skype 클라이언트 메신저 대화")
    

    > [!IMPORTANT]
    > Lync Server 관리자는 들어오는 요청을 허용하도록 Lync 사용자의 개인 정보 설정을 구성해야 합니다. 그렇지 않은 경우, Lync 사용자는 Skype 사용자로부터 대화 상대 요청을 받을 수 없습니다. Lync 사용자의 정책 설정 구성에 따라, Skype 사용자를 추가하라는 요청이 Lync 클라이언트의 <STRONG>새로 만들기</STRONG> 탭에 표시됩니다. Skype 사용자와 통신을 시작하려면 Lync 사용자가 Skype 사용자를 즐겨찾기 목록 또는 대화 상대 목록에 추가해야 합니다. 아래 이미지는 Lync 클라이언트에서 <STRONG>새로 만들기</STRONG> 탭의 위치를 나타냅니다.

    
    ![Lync 클라이언트 새 대화 상대 페이지](images/Dn440175.b1cf8570-1401-47d9-ab14-b04f0d7e8a7a(OCS.15).jpg "Lync 클라이언트 새 대화 상대 페이지")

Lync 사용자는 Skype 사용자가 보낸 요청이 표시되고 Lync 사용자가 요청을 검색할 수 있도록 Lync 알림을 구성해야 합니다. Lync 알림을 구성하려면 다음 절차를 완료하세요.

**Lync 알림을 구성하려면**

1.  Lync 클라이언트에서 **옵션** 아이콘을 클릭합니다.

2.  **알림**을 선택합니다.

3.  **일반 알림**에서 **다른 사람이 대화 상대 목록에 나를 추가할 때 알림**을 선택합니다.

4.  **Lync를 사용하지 않는 대화 상대**에서 **초대는 허용하고 기타 모든 통신은 차단**을 선택합니다.

5.  **확인**을 클릭하여 옵션 창을 닫습니다.

![Lync 클라이언트 옵션 대화 상자, 알림 페이지](images/Dn440175.b36ed67f-f394-4f66-b60a-b74793001bfc(OCS.15).jpg "Lync 클라이언트 옵션 대화 상자, 알림 페이지")

