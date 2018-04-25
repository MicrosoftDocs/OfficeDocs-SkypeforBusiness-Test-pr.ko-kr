---
title: 'Lync Server 2013: Lync-Skype 연결 사용'
TOCTitle: Lync-Skype 연결 사용
ms:assetid: 34c4db3e-582f-41fb-85c4-3438ae02f09f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn440170(v=OCS.15)
ms:contentKeyID: 59602769
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync-Skype 연결 사용

 

_**마지막으로 수정된 항목:** 2014-12-16_

프로비저닝 요청을 전송한 후에는 Lync-Skype 연결을 구성하는 데 필요한 Lync Server 환경과 관리 작업에 집중할 수 있습니다. 이 섹션에서는 Lync Server 관리자가 Lync Server를 배포하고 외부 액세스를 구성했다고 가정합니다. Lync Server에 대한 외부 액세스를 구성하는 방법에 대한 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md) 및 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)를 참고하세요.

Lync-Skype 연결을 위해 Lync Server 환경을 준비하려면 Lync Server 관리자가 다음 세 가지 작업을 완료해야 합니다.

## 1\. 페더레이션 및 PIC 구성

Skype 사용자가 조직의 Lync 사용자와 통신할 수 있도록 설정하려면 페더레이션이 필요합니다. PIC(공용 메신저 연결)는 페더레이션의 한 클래스로, Lync 사용자가 Skype 사용자와 통신할 수 있도록 구성해야 합니다. 페더레이션과 PIC는 아래와 같이 Lync Server 제어판을 통해 구성됩니다.

![PIC 표시](images/Dn440170.451b94e3-0b38-488c-835f-1f25690e8074(OCS.15).jpg "PIC 표시")


> [!IMPORTANT]
> PIC 페더레이션은 Live Communication Server 2005 SP1 또는 Office Communications Server 2007에서 더 이상 지원되지 않습니다. 지원되는 PIC 페더레이션의 플랫폼에는 Lync Server 2013, Lync Server 2010, Office Communications Server 2007 R2가 포함됩니다.



## 2\. 최소 하나의 정책이 페더레이션된 사용자 액세스를 지원하도록 구성

관리자는 Lync Server 제어판을 사용하여 Skype 사용자가 내부 Lync Server 사용자와 공동 작업할 수 있는지 여부를 제어하는 하나 이상의 외부 사용자 액세스 정책을 구성해야 합니다.

![정책](images/Dn440170.8fd46ad1-9749-422c-8c47-c16ac9032cdb(OCS.15).jpg "정책")

## 3\. Lync에 대해 Skype PIC 공급자 설정 구성

관리자는 Lync Server 관리 셸을 사용하여 Skype를 추가 PIC 공급자로 표시하도록 Lync 클라이언트 정책을 구성해야 합니다.


> [!NOTE]
> PIC(공용 메신저 연결) 서비스 공급자의 사용자는 공용 메신저 연결을 지원하는 정책(이 절차 앞에 나온 2단계)도 하나 이상 구성해야 조직의 메신저 대화나 오디오 또는 비디오 회의에 참가할 수 있습니다.



1.  페더레이션 및 PIC를 구성하려면 "페더레이션 및 공용 IM 연결 사용 또는 사용 안 함"( [http://go.microsoft.com/fwlink/p/?LinkId=306063](http://go.microsoft.com/fwlink/p/?linkid=306063))를 참고하세요.

2.  페더레이션된 사용자 액세스를 지원하기 위한 최소 하나의 정책을 구성하려면 "공용 사용자 액세스를 제어하도록 정책 구성"( [http://go.microsoft.com/fwlink/p/?LinkId=306064](http://go.microsoft.com/fwlink/p/?linkid=306064))을 참고하세요.

**Skype용으로 Skype 메신저 PIC 공급자를 편집 및 구성하는 방법**

1.  Lync Server 프런트 엔드 서버에서 Lync Server 관리 셸을 엽니다.

2.  다음 두 개의 명령을 실행합니다.
    
    `Remove-CsPublicProvider -Identity Messenger`
    
    `New-CsPublicProvider -Identity Skype -ProxyFqdn federation.messenger.msn.com -IconUrl "https://images.edge.messenger.live.com/Messenger_16x16.png" -VerificationLevel 2 -Enabled 1`

3.  이제 Lync 클라이언트에서 Skype를 PIC 공급자로 선택하고 해당 Microsoft 계정을 지정하여 Skype 클라이언트를 추가할 수 있습니다. 또한 Microsoft 계정을 사용하여 병합하고 로그인한 Skype 사용자는 Lync 사용자에게 대화 상대 요청을 보낼 수 있습니다. Microsoft 계정에 대한 자세한 내용은 [Microsoft 계정이란?](https://support.skype.com/en/faq/fa12059/what-is-a-microsoft-account)을 참조하세요. Lync에 클라이언트를 추가하는 방법에 대한 자세한 내용은 [최종 사용자로서 Lync Server 2013에서 Lync-Skype 연결 사용](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md)을 참조하세요.
    
    ![Skype 대화 상대 추가](images/Dn440170.df0e6ed9-2374-4dfa-a815-87281989487c(OCS.15).jpg "Skype 대화 상대 추가")

4.  호스팅된 공급자를 수정하는 방법에 대한 자세한 내용은 "호스팅된 SIP 페더레이션 공급자 만들기 또는 편집"( [http://go.microsoft.com/fwlink/p/?LinkId=306065](http://go.microsoft.com/fwlink/p/?linkid=306065))을 참고하세요.

이제 서버에서 수행해야 하는 관리 작업을 완료했습니다. 이렇게 하면 Lync-Skype 연결이 설정됩니다.

