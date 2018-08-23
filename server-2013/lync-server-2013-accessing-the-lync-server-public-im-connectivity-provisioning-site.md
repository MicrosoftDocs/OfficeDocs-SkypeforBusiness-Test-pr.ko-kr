---
title: 'Lync Server 2013: Lync Server 공용 메신저 연결 프로비저닝 사이트에 액세스'
TOCTitle: Lync Server 공용 메신저 연결 프로비저닝 사이트에 액세스
ms:assetid: 77a08234-6bcf-4f59-b43b-ee5fc1926585
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn440174(v=OCS.15)
ms:contentKeyID: 59602776
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync Server 공용 메신저 연결 프로비저닝 사이트에 액세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync-Skype 연결을 위한 프로비저닝 프로세스가 이전 PIC 프로비저닝 방법과 비교해 달라졌습니다. 이 프로비저닝 프로세스는 완료하는 데 30일까지 걸릴 수 있습니다. 이 문서에 남아 있는 단계를 완료하기 전에 이 프로세스를 먼저 시작하는 것이 좋습니다. 계정에 대한 Lync-Skype 프로비저닝 프로세스가 완료되면 계정이 정품 인증되고 해당 사용자가 공용 메신저 연결을 사용할 수 있게 됩니다.

### Lync-Skype 연결을 프로비저닝하려면 다음 정보가 필요합니다.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ol>
<li><p>Microsoft 계약 번호</p></li>
<li><p>액세스 에지 서비스 FQDN(정규화된 도메인 이름)</p></li>
<li><p>SIP(Session Initiation Protocol) 도메인</p></li>
<li><p>추가 액세스 에지 서비스 FQDN</p></li>
<li><p>연락처 정보</p></li>
</ol></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Microsoft 계약 번호</p></li>
<li><p>액세스 에지 서비스 FQDN(정규화된 도메인 이름)</p></li>
<li><p>SIP(Session Initiation Protocol) 도메인</p></li>
<li><p>추가 액세스 에지 서비스 FQDN</p></li>
<li><p>연락처 정보</p></li>
</ol></td>
</tr>
</tbody>
</table>


### Lync-Skype 연결을 위해 프로비저닝 프로세스를 시작하려면

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ol>
<li><p>Microsoft Windows Live ID를 사용해 <strong>https://pic.lync.com</strong> 웹 사이트에 로그인합니다.</p></li>
<li><p>Microsoft 사용권 계약 유형을 선택합니다.</p></li>
<li><p>Lync Server의 제품 사용 권한을 읽고 동의한다는 사실을 확인하는 확인란을 선택합니다.</p></li>
<li><p><strong>프로비저닝 요청 시작</strong> 페이지에서 해당 링크를 클릭하여 프로비저닝 요청을 시작합니다.</p></li>
<li><p><strong>프로비저닝 정보 지정</strong> 페이지에서 <strong>액세스 에지 서비스 FQDN</strong>을 입력합니다(예: <strong>accessedge.contoso.com</strong>).</p></li>
<li><p>하나 이상의 SIP 도메인 이름을 입력한 다음 <strong>추가</strong>를 클릭합니다.</p>


> [!IMPORTANT]
> 프로비저닝 프로세스를 완료하기 위해서는 최소 하나의 액세스 에지 서버와 SIP 도메인이 필요합니다. SIP 도메인과 액세스 에지 서버는 활성 상태로 작동 중이어야 하며 네트워크에서 연결할 수 있어야 합니다.


</li>
<li><p><strong>공용 메신저 서비스 공급자</strong> 목록에서 <strong>Skype</strong>를 선택하고 <strong>다음</strong>을 클릭하여 대화 상대 정보를 추가한 다음 프로비저닝 요청을 제출합니다.</p></li>
</ol></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Microsoft Windows Live ID를 사용해 <strong>https://pic.lync.com</strong> 웹 사이트에 로그인합니다.</p></li>
<li><p>Microsoft 사용권 계약 유형을 선택합니다.</p></li>
<li><p>Lync Server의 제품 사용 권한을 읽고 동의한다는 사실을 확인하는 확인란을 선택합니다.</p></li>
<li><p><strong>프로비저닝 요청 시작</strong> 페이지에서 해당 링크를 클릭하여 프로비저닝 요청을 시작합니다.</p></li>
<li><p><strong>프로비저닝 정보 지정</strong> 페이지에서 <strong>액세스 에지 서비스 FQDN</strong>을 입력합니다(예: <strong>accessedge.contoso.com</strong>).</p></li>
<li><p>하나 이상의 SIP 도메인 이름을 입력한 다음 <strong>추가</strong>를 클릭합니다.</p>


> [!IMPORTANT]
> 프로비저닝 프로세스를 완료하기 위해서는 최소 하나의 액세스 에지 서버와 SIP 도메인이 필요합니다. SIP 도메인과 액세스 에지 서버는 활성 상태로 작동 중이어야 하며 네트워크에서 연결할 수 있어야 합니다.


</li>
<li><p><strong>공용 메신저 서비스 공급자</strong> 목록에서 <strong>Skype</strong>를 선택하고 <strong>다음</strong>을 클릭하여 대화 상대 정보를 추가한 다음 프로비저닝 요청을 제출합니다.</p></li>
</ol></td>
</tr>
</tbody>
</table>


프로비저닝 요청을 전송한 후에 계정이 정품 인증되고 사용자가 공용 메신저 연결을 사용할 수 있게 되기까지 최대 30일 정도 걸릴 수 있습니다.

## 페더레이션 및 PIC(공용 메신저 연결) 설정

프로비저닝 요청을 전송한 후에는 Lync-Skype 연결을 구성하는 데 필요한 Lync Server 환경과 관리 작업에 집중할 수 있습니다. 이 섹션에서는 Lync Server 관리자가 Lync Server를 배포하고 외부 액세스를 구성했다고 가정합니다. Lync Server에 대한 외부 액세스를 구성하는 방법에 대한 자세한 내용은 "외부 사용자 액세스 계획"( [http://go.microsoft.com/fwlink/p/?LinkID=273772](http://go.microsoft.com/fwlink/p/?linkid=273772)) 및 "외부 사용자 액세스 배포"( [http://go.microsoft.com/fwlink/p/?LinkID=27378](http://go.microsoft.com/fwlink/p/?linkid=27378))를 참고하세요.

Lync-Skype 연결을 위해 Lync Server 환경을 준비하려면 Lync Server 관리자가 다음 세 가지 작업을 완료해야 합니다.

## 1\. 페더레이션 및 PIC 구성

Skype 사용자가 조직의 Lync 사용자와 통신할 수 있도록 설정하려면 페더레이션이 필요합니다. PIC(공용 메신저 연결)는 페더레이션의 한 클래스로, Lync 사용자가 Skype 사용자와 통신할 수 있도록 구성해야 합니다. 페더레이션과 PIC는 아래와 같이 Lync Server 제어판을 통해 구성됩니다.


> [!IMPORTANT]
> PIC 페더레이션은 Live Communication Server 2005 SP1 또는 Office Communications Server 2007에서 더 이상 지원되지 않습니다. 지원되는 PIC 페더레이션의 플랫폼에는 Lync Server 2013, Lync Server 2010, Office Communications Server 2007 R2가 포함됩니다.



## 2\. 최소 하나의 정책이 페더레이션된 사용자 액세스를 지원하도록 구성

관리자는 Lync Server 제어판을 사용하여 Skype 사용자가 내부 Lync Server 사용자와 공동 작업할 수 있는지 여부를 제어하는 하나 이상의 외부 사용자 액세스 정책을 구성해야 합니다.

## 3\. Lync에 대해 Skype PIC 공급자 설정 구성

관리자는 Lync Server 관리 셸을 사용하여 Skype를 추가 PIC 공급자로 표시하도록 Lync 클라이언트 정책을 구성해야 합니다.


> [!NOTE]
> 공용 메신저 연결을 지원하기 위한 최소 하나의 정책(이 절차 앞에 나온 2단계)을 구성할 때까지 PIC(공용 메신저 연결) 서비스 공급자의 사용자는 조직의 메신저 대화 또는 회의에 참가할 수 없습니다.<BR>페더레이션 및 PIC를 구성하려면 "페더레이션 및 공용 IM 연결 사용 또는 사용 안 함"( <A href="http://go.microsoft.com/fwlink/p/?linkid=306063">http://go.microsoft.com/fwlink/p/?LinkId=306063</A>)를 참고하세요.<BR>페더레이션된 사용자 액세스를 지원하기 위한 최소 하나의 정책을 구성하려면 "공용 사용자 액세스를 제어하도록 정책 구성"( <A href="http://go.microsoft.com/fwlink/p/?linkid=306064">http://go.microsoft.com/fwlink/p/?LinkId=306064</A>)을 참고하세요.



1.  Lync Server 프런트 엔드 서버에서 Lync Server 관리 셸을 엽니다.

2.  다음 두 개의 명령을 실행합니다.
    
      - Remove-CsPublicProvider -Identity Messenger
    
      - New-CsPublicProvider -Identity Skype -ProxyFqdn federation.messenger.msn.com -IconUrl "https://images.edge.messenger.live.com/Messenger\_16x16.png" -VerificationLevel 2 -Enabled 1

3.  이제 Lync 클라이언트에서 Skype를 PIC 공급자로 선택하고 해당 Microsoft 계정을 지정하여 Skype 클라이언트를 추가할 수 있습니다. 또한 Microsoft 계정을 사용하여 병합하고 로그인한 Skype 사용자는 Lync 사용자에게 대화 상대 요청을 보낼 수 있습니다. Microsoft 계정에 대한 자세한 내용은 [Microsoft 계정이란?](https://support.skype.com/en/faq/fa12059/what-is-a-microsoft-account)을 참조하세요. Lync에 클라이언트를 추가하는 방법에 대한 자세한 내용은 [최종 사용자로서 Lync Server 2013에서 Lync-Skype 연결 사용](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md)을 참조하세요.

4.  호스팅된 공급자를 수정하는 방법에 대한 자세한 내용은 "호스팅된 SIP 페더레이션 공급자 만들기 또는 편집"( [http://go.microsoft.com/fwlink/p/?LinkId=306065](http://go.microsoft.com/fwlink/p/?linkid=306065))을 참고하세요.

이제 서버에서 수행해야 하는 관리 작업을 완료했습니다. 이렇게 하면 Lync-Skype 연결이 설정됩니다.

## 추가 리소스

[최종 사용자로서 Lync Server 2013에서 Lync-Skype 연결 사용](lync-server-2013-using-lync-skype-connectivity-as-an-end-user.md)

[Provisioning guide for Lync-Skype connectivity in Lync Server 2013](lync-server-2013-provisioning-guide-for-lync-skype-connectivity.md)

