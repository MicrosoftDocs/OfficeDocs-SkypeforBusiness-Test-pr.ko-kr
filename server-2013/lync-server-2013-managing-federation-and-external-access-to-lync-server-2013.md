---
title: 'Lync Server 2013: Lync Server 2013에 대한 외부 액세스 및 페더레이션 관리'
TOCTitle: Lync Server 2013에 대한 외부 액세스 및 페더레이션 관리
ms:assetid: 26f806c1-f284-4637-b06b-06270336c540
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520966(v=OCS.15)
ms:contentKeyID: 49303105
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 외부 액세스 및 페더레이션 관리

 

_**마지막으로 수정된 항목:** 2015-03-09_

에지 서버 또는 에지 풀을 배포하는 것은 외부 사용자를 지원하기 위한 첫 번째 단계입니다. 에지 서버를 배포하는 방법에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)를 참조하십시오.

Lync Server 2013의 내부 배포를 설치하고 구성하면 조직의 내부 사용자가 AD DS(Active Directory 도메인 서비스) SIP 계정을 가진 다른 내부 사용자와 공동 작업할 수 있습니다. 공동 작업에는 인스턴트 메시지 보내기/받기, 현재 상태 업데이트, 회의("모임"이라고도 함) 참가 등이 포함될 수 있습니다. 외부 사용자 액세스를 사용하도록 설정하고 구성하여 지원되는 외부 사용자가 내부 Lync Server 사용자와 공동 작업할 수 있는지 여부를 제어할 수 있습니다. 외부 사용자에는 배포의 원격 사용자, 페더레이션 사용자(지원되는 IM(인스턴트 메시징) 서비스 공급자의 사용자 포함), XMPP 페더레이션 및 전화 회의의 익명 참가자가 포함될 수 있습니다.

배포에 Lync Server 2013  에지 서버 또는 에지 풀 설치가 포함되는 경우에는 외부 사용자 액세스, 다른 SIP 페더레이션 도메인 구성원/SIP 페더레이션 공급자/XMPP 페더레이션 사용자와의 통신을 위한 옵션이 다수 추가되므로 가능한 통신 유형의 범위가 크게 확대됩니다. 에지 서버 또는 에지 풀 풀을 설정한 후에는 제공할 외부 사용자 액세스 유형을 사용하도록 설정하고 외부 액세스를 제어할 정책을 구성합니다. Lync Server 2013에서는 작업 요구 사항에 따라 Lync Server 제어판이나 Lync Server 관리 셸 중 하나 또는 둘 다를 사용하여 외부 사용자 액세스를 설정하고 구성합니다. 이러한 관리 도구에 대한 자세한 내용은 작업 설명서의 [Lync Server 2013 관리 도구](lync-server-2013-lync-server-administrative-tools.md), [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md) 및 [Lync Server 2013 관리 도구 설치](lync-server-2013-install-lync-server-administrative-tools.md)를 참조하십시오.


> [!IMPORTANT]
> 외부 사용자 액세스를 위한 구성 및 정책을 디자인할 때는 정책 우선 순위와 정책 적용 방법을 파악해야 합니다. 한 정책 수준에서 적용되는 Lync Server 정책 설정은 다른 정책 수준에서 적용되는 설정을 재정의할 수 있습니다. Lync Server 정책 우선 순위에 따르면 사용자 정책(최대 영향력)이 사이트 정책을 재정의한 후 사이트 정책이 글로벌 정책(최소 영향력)을 재정의합니다. 즉, 정책 설정이 해당 정책의 영향을 받는 개체에 가까울수록 개체에 미치는 영향력도 커집니다.



조직에서 외부 사용자 액세스를 이미 지원하도록 설정한 경우에도 기본적으로 원격 사용자 액세스, 페더레이션 사용자 액세스를 비롯한 외부 사용자 액세스를 지원하는 정책은 구성되지 않습니다. 외부 사용자 액세스 사용을 제어하려면 하나 이상의 정책을 구성하고 각 정책에 대해 지원되는 외부 사용자 액세스 유형을 지정해야 합니다. 여기에는 다음 외부 액세스 정책이 포함됩니다.

  - **글로벌 정책**   글로벌 정책은 에지 서버를 배포할 때 작성됩니다. 기본적으로 글로벌 정책에서는 외부 사용자 액세스 옵션이 사용하도록 설정되지 않습니다. 글로벌 수준에서 외부 사용자 액세스를 지원하려면 외부 사용자 액세스 옵션 유형을 하나 이상 지원하도록 글로벌 정책을 구성합니다. 글로벌 정책은 조직의 모든 사용자에게 적용되지만, 사이트 정책과 사용자 정책이 글로벌 정책을 다시 정의합니다. 삭제한 글로벌 정책은 제거되는 것이 아니라 기본 설정으로 다시 설정됩니다.

  - **사이트 정책**   하나 이상의 사이트 정책을 만들고 구성하여 특정 사이트에 대한 외부 사용자 액세스 지원을 제한할 수 있습니다. 사이트 정책의 구성은 사이트 정책에 포함되는 특정 사이트에 한해 글로벌 정책을 다시 정의합니다. 예를 들어 글로벌 정책에서 원격 사용자 액세스를 사용하도록 설정하는 경우 특정 사이트에 대해서는 원격 사용자 액세스를 사용하지 않도록 설정하는 사이트 정책을 지정할 수 있습니다. 기본적으로 사이트 정책은 해당 사이트의 모든 사용자에게 적용되지만, 사용자에게 사용자 정책을 지정하여 사이트 정책 설정을 다시 정의할 수 있습니다.

  - **사용자 정책**   하나 이상의 사용자 정책을 만들고 구성하여 특정 사용자에 대한 원격 사용자 액세스 지원을 제한할 수 있습니다. 사용자 정책의 구성은 사용자 정책이 지정된 특정 사용자에 한해 글로벌 정책 및 사이트 정책을 다시 정의합니다. 예를 들어 글로벌 정책 및 사이트 정책에서 원격 사용자 액세스를 사용하도록 설정하는 경우 원격 사용자 액세스를 사용하지 않도록 설정하는 사용자 정책을 지정한 다음 특정 사용자에게 해당 사용자 정책을 지정할 수 있습니다. 사용자 정책을 만드는 경우에는 한 명 이상의 사용자에게 정책을 적용해야 정책이 효력을 발휘합니다.

만들거나 편집해야 하는 구성 설정 및 정책을 확인하려면 다음 결정 사항을 참조하십시오.

**도메인 내부 및 외부 사용자가 인스턴트 메시징, 웹 회의 및 오디오/비디오를 사용하여 공동 작업을 하도록 허용할지 여부**

[Lync Server 2013에서 원격 사용자 액세스를 제어하도록 정책 구성](lync-server-2013-configure-policies-to-control-remote-user-access.md) 및 [Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) 항목에 설명된 대로 설정을 구성합니다.

**배포의 사용자가 호스트하는 회의에 익명 사용자가 참가하고 초대를 받도록 허용할지 여부**

[Lync Server 2013에서 익명 사용자 지원을 위한 회의 정책 할당](lync-server-2013-assign-conferencing-policies-to-support-anonymous-users.md), [회의 정책 만들기 또는 수정](lync-server-2013-create-or-modify-a-conferencing-policy.md) 및 [Lync Server 2013용 회의 정책 설정 참조](lync-server-2013-conferencing-policy-settings-reference.md) 항목에 설명된 대로 설정을 구성합니다.

**사용자가 SIP 페더레이션 도메인 대화 상대와 통신하도록 허용할지 여부**

[Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성](lync-server-2013-configure-policies-to-control-federated-user-access.md), [Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) 및 [Lync Server 2013에서 조직의 SIP 페더레이션된 도메인 관리](lync-server-2013-manage-sip-federated-domains-for-your-organization.md) 항목에 설명된 대로 설정을 구성합니다.

**SIP 페더레이션 도메인과의 통신을 사용하도록 설정한 경우 XMPP 페더레이션 파트너 대화 상대와의 통신을 사용하도록 설정할지 여부**

[Lync Server 2013에서 XMPP 페더레이션 사용자 액세스를 제어하도록 정책 구성](lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md) 및 [Lync Server 2013에서 XMPP 페더레이션 파트너 관리](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md) 항목에 설명된 대로 설정을 구성합니다.

**SIP 페더레이션 도메인과의 통신을 사용하도록 설정한 경우 SIP 페더레이션 자동 검색을 사용하도록 설정할지 여부**

[Lync Server 2013에서 페더레이션 파트너 검색을 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md) 항목에 설명된 대로 설정을 구성합니다.

**SIP 페더레이션 도메인과의 통신을 사용하도록 설정한 경우 보관을 사용하며 통신 내용이 보관될 수 있음을 알리는 고지 사항을 페더레이션 대화 상대에게 보내도록 설정할지 여부**

[Lync Server 2013에서 페더레이션 파트너에게 보관 고지 사항 보내기를 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md) 항목에 설명된 대로 설정을 구성합니다.

**사용자가 SIP 페더레이션 공급자와 통신하도록 허용하여 Windows Live Messenger, AOL, Yahoo\!와 같은 공용 공급자와의 통신을 사용하도록 설정할지 여부**

[Lync Server 2013에서 공용 사용자 액세스를 제어하도록 정책 구성](lync-server-2013-configure-policies-to-control-public-user-access.md) [Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) 및 [Lync Server 2013에서 공용 SIP 페더레이션 공급자 만들기 또는 편집](lync-server-2013-create-or-edit-public-sip-federated-providers.md) 항목에 설명된 대로 설정을 구성합니다.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



**사용자가 Microsoft Office 365, Microsoft Lync Online 및 Microsoft Lync Online 2010을 실행하는 호스트된 공급자인 SIP 페더레이션 공급자와 통신하도록 허용할지 여부**

[Lync Server 2013에서 공용 SIP 페더레이션 공급자 만들기 또는 편집](lync-server-2013-create-or-edit-public-sip-federated-providers.md), [Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) 및 [Lync Server 2013에서 호스팅된 SIP 페더레이션 공급자 만들기 또는 편집](lync-server-2013-create-or-edit-hosted-sip-federated-providers.md) 항목에 설명된 대로 설정을 구성합니다.

**배포가 분할(하이브리드라고도 함) 도메인, 즉 일부 사용자는 온-프레미스 배포에 홈 서버가 있고 나머지 사용자는 온라인 환경의 홈 서버로 구성되는 도메인으로 구성되어 있는지 여부**

[Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성](lync-server-2013-configure-policies-to-control-federated-user-access.md), [Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) 및 [Lync Server 2013에서 호스팅된 SIP 페더레이션 공급자 만들기 또는 편집](lync-server-2013-create-or-edit-hosted-sip-federated-providers.md) 항목에 설명된 대로 설정을 구성합니다.

원하는 경우에는 요구 사항이 나와 있는 아래 표를 참조할 수 있습니다.


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>페더레이션 및 외부 액세스의 탭(가로) 페더레이션 또는 외부 액세스 유형(세로)</th>
<th>외부 액세스 정책</th>
<th>액세스 에지 구성</th>
<th>SIP 페더레이션 도메인</th>
<th>SIP 페더레이션 공급자</th>
<th>XMPP 페더레이션 파트너</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>원격 사용자</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-remote-user-access.md">Lync Server 2013에서 원격 사용자 액세스를 제어하도록 정책 구성</a></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-remote-user-access.md">Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함</a></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>SIP 페더레이션 대화 상대</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성</a></p>
<p></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함</a></p>
<p><a href="lync-server-2013-enable-or-disable-discovery-of-federation-partners.md">Lync Server 2013에서 페더레이션 파트너 검색을 사용하거나 사용하지 않도록 설정</a></p>
<p><a href="lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md">Lync Server 2013에서 페더레이션 파트너에게 보관 고지 사항 보내기를 사용하거나 사용하지 않도록 설정</a></p></td>
<td><p><a href="lync-server-2013-manage-sip-federated-domains-for-your-organization.md">Lync Server 2013에서 조직의 SIP 페더레이션된 도메인 관리</a></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>XMPP 페더레이션 대화 상대</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성</a></p>
<p><a href="lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md">Lync Server 2013에서 XMPP 페더레이션 사용자 액세스를 제어하도록 정책 구성</a></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함</a></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p><a href="lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md">Lync Server 2013에서 XMPP 페더레이션 파트너 관리</a></p></td>
</tr>
<tr class="even">
<td><p>분할 도메인/하이브리드 사용자</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성</a></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함</a></p></td>
<td><p></p></td>
<td><p><a href="lync-server-2013-create-or-edit-hosted-sip-federated-providers.md">Lync Server 2013에서 호스팅된 SIP 페더레이션 공급자 만들기 또는 편집</a></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>공용 IM 서비스 대화 상대</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-public-user-access.md">Lync Server 2013에서 공용 사용자 액세스를 제어하도록 정책 구성</a></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함</a></p></td>
<td><p></p></td>
<td><p><a href="lync-server-2013-create-or-edit-public-sip-federated-providers.md">Lync Server 2013에서 공용 SIP 페더레이션 공급자 만들기 또는 편집</a></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>모임 및 회의에 대한 익명 사용자 액세스</p></td>
<td><p></p></td>
<td><p><a href="lync-server-2013-assign-conferencing-policies-to-support-anonymous-users.md">Lync Server 2013에서 익명 사용자 지원을 위한 회의 정책 할당</a></p>


> [!NOTE]
> 회의 정책 아래의 <A href="lync-server-2013-create-or-modify-a-conferencing-policy.md">회의 정책 만들기 또는 수정</A> 및 <A href="lync-server-2013-conferencing-policy-settings-reference.md">Lync Server 2013용 회의 정책 설정 참조</A> 구성 설정도 고려해야 합니다.


</td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


조직에서 외부 사용자 액세스를 지원하도록 설정하지 않은 경우에도 외부 사용자 액세스를 제어하는 데 사용할 정책을 포함하여 외부 사용자 액세스 설정을 구성할 수 있습니다. 그러나 구성한 정책 및 기타 설정은 조직에서 외부 사용자 액세스를 사용하도록 설정한 경우에만 적용됩니다. 외부 사용자 액세스가 해제되어 있거나 지원하는 외부 사용자 액세스 정책이 구성되어 있지 않은 경우에는 외부 사용자가 조직의 사용자와 통신할 수 없습니다.

에지 배포에서는 에지 지원을 구성한 방법에 따라 외부 사용자 유형(전화 회의를 만들고 참가자를 초대할 때 익명 참가자에게 보낸 암호 키와 전화 회의 ID로 인증된 익명 사용자 제외)을 인증하고 액세스를 제어합니다. 통신을 제어하기 위해 하나 이상의 정책을 구성하고 배포 내부 사용자와 외부 사용자가 서로 통신하는 방법을 정의하는 설정을 구성할 수 있습니다. 이러한 정책과 설정에는 외부 사용자 액세스에 대한 기본 글로벌 정책과 특정 사이트 또는 사용자에 대해 하나 이상의 외부 사용자 액세스 유형을 사용하도록 설정하기 위해 만들고 구성할 수 있는 사이트 및 사용자 정책이 포함됩니다.

## 이 단원의 내용

  - [Lync Server 2013에서 외부 액세스 정책 관리](lync-server-2013-manage-external-access-policy-for-your-organization.md)

  - [Lync Server 2013에서 조직에 대한 액세스 에지 구성 관리](lync-server-2013-manage-access-edge-configuration-for-your-organization.md)

  - [Lync Server 2013에서 조직의 SIP 페더레이션된 도메인 관리](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)

  - [Lync Server 2013에서 조직에 대한 SIP 페더레이션 공급자 관리](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)

  - [Lync Server 2013에서 XMPP 페더레이션 파트너 관리](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)

  - [Lync Online 고객에 대한 페더레이션 지원 구성](lync-server-2013-configuring-federation-support-for-a-lync-online-customer.md)

