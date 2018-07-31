---
title: 'Lync Server 2013: Lync 페더레이션 설정'
TOCTitle: Lync 페더레이션 설정
ms:assetid: 374ddc43-26f9-499d-be68-a5158adfa49c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204800(v=OCS.15)
ms:contentKeyID: 49303299
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync 페더레이션 설정

 

_**마지막으로 수정된 항목:** 2015-03-09_

이미 에지 서버를 하나 이상 배포한 경우에는 페더레이션 시나리오 기능을 간단하게 추가할 수 있습니다. 에지 서버를 설정하지 않았다면 먼저 설정해야 합니다. 자세한 내용은 계획 설명서의 [Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md) 및 배포 설명서의 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)를 참고하세요.


> [!NOTE]
> XMPP 페더레이션, Lync 페더레이션 또는 공용 메신저 연결 조합을 설정하려는 경우 해당 항목을 동시에 또는 한 번에 하나씩 배포할 수 있습니다. 토폴로지 작성기 및 Lync Server 관리 셸을 통해 옵션을 구성하는 경우에는 페더레이션 유형 1~3개에 대한 옵션을 구성한 후 에지 서버에서 배포 마법사를 실행하면 수행해야 하는 단계 수를 줄일 수 있습니다.



## 토폴로지 작성기 및 배포 마법사에서 Lync 페더레이션 설정

1.  프런트 엔드 서버에서 토폴로지 작성기를 엽니다. 에지 풀을 확장한 다음 에지 서버 또는 에지 서버 풀을 마우스 오른쪽 단추로 클릭합니다. 속성 편집을 선택합니다.

2.  속성 편집의 일반에서 이 에지 풀에 페더레이션 사용(포트 5061)을 선택합니다. 확인을 클릭합니다.

3.  작업을 클릭하고 토폴로지, 게시를 차례로 선택합니다. 토폴로지를 게시하라는 메시지가 표시되면 다음을 클릭합니다. 게시가 완료되면 마침을 클릭합니다.

4.  에지 서버에서 Lync Server 배포 마법사를 엽니다. Lync Server 시스템 설치 또는 업데이트를 클릭하고, Lync Server 구성 요소 설치 또는 제거를 클릭합니다. 다시 실행을 클릭합니다.

5.  Lync Server 구성 요소 설치에서 다음을 클릭합니다. 요약 화면에는 실행되는 작업이 표시됩니다. 배포가 완료되면 로그 보기를 클릭하여 사용 가능한 로그 파일을 확인합니다. 그런 후에 마침을 클릭하여 배포를 완료합니다.
    

    > [!IMPORTANT]
    > 이 옵션을 선택할 수 있지만 페더레이션을 위해서는 조직의 에지 풀 또는 에지 서버 하나만 외부에 게시할 수 있습니다. 공용 메신저 사용자를 포함하여 페더레이션 사용자의 모든 액세스는 같은 에지 풀 또는 단일 에지 서버를 통해 전송됩니다. 예를 들어 배포에 각각 뉴욕과 런던에 배포된 에지 풀 또는 단일 에지 서버가 포함된 경우 뉴욕 에지 풀 또는 단일 에지 서버에 대한 페더레이션 지원을 사용하도록 설정하면 페더레이션 사용자에 대한 신호 트래픽이 뉴욕 에지 풀 또는 단일 에지 서버를 통해 전송됩니다. 이는 런던 페더레이션 사용자를 호출하는 런던 내부 사용자가 A/V 트래픽에 대해 런던 풀 또는 에지 서버를 사용하기는 하지만 런던 사용자와의 통신에도 해당합니다.



## 파트너와의 페더레이션 구성

1.  다른 Microsoft Lync Server 2013, Lync Server 2010, Office Communications Server 2007 R2 또는 Office Communicator 2007과의 페더레이션을 올바르게 설정하려면 다음 표에서 페더레이션 유형을 선택한 후에 DNS SRV 레코드와 DNS 호스트(A, IPv6의 경우 AAAA)를 정의하고 페더레이션 유형에 적합한 정책을 구성합니다.
    
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>페더레이션 유형</th>
    <th>DNS 레코드</th>
    <th>정책 정의</th>
    <th>참고</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>검색된 파트너 도메인</p></td>
    <td><p>_sipfederationtls._tcp.&lt;외부 도메인 이름&gt; 형식으로 SRV 레코드를 구성합니다. 여기서 SRV 레코드의 포트 값은 TCP 5061이고 <strong>이 서비스를 제공하는 호스트</strong> 는 sip. &lt;외부 도메인 이름&gt;( 액세스 에지 서비스의 FQDN)으로 정의됩니다. SRV 레코드를 만드는 방법에 대한 자세한 내용은 <a href="lync-server-2013-configure-dns-for-edge-support.md">Lync Server 2013에서 에지 지원에 대한 DNS 구성</a>을 참고하세요.</p></td>
    <td><ul>
    <li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함</a></p></li>
    <li><p><a href="lync-server-2013-enable-or-disable-discovery-of-federation-partners.md">Lync Server 2013에서 페더레이션 파트너 검색을 사용하거나 사용하지 않도록 설정</a></p></li>
    </ul></td>
    <td><p>이전 버전에서는 이러한 페더레이션 유형의 명칭이 <strong>개방형 확장 페더레이션</strong>이었습니다. 이러한 페더레이션 유형을 사용하는 경우에는 SRV 레코드를 만들어야 하며, 그러면 다른 파트너가 페더레이션을 검색할 수 있습니다.</p></td>
    </tr>
    <tr class="even">
    <td><p>허용 파트너 도메인</p></td>
    <td><p>_sipfederationtls._tcp.&lt;외부 도메인 이름&gt; 형식으로 SRV 레코드를 구성합니다. 여기서 SRV 레코드의 포트 값은 TCP 5061이고 <strong>이 서비스를 제공하는 호스트</strong> 는 sip. &lt;외부 도메인 이름&gt;( 액세스 에지 서비스의 FQDN)으로 정의됩니다. SRV 레코드를 만드는 방법에 대한 자세한 내용은 <a href="lync-server-2013-configure-dns-for-edge-support.md">Lync Server 2013에서 에지 지원에 대한 DNS 구성</a>을 참고하세요.</p></td>
    <td><ul>
    <li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함</a></p></li>
    </ul></td>
    <td><p>이전 버전에서는 이러한 페더레이션 유형의 명칭이 <strong>확장 페더레이션</strong>이었습니다. 이러한 페더레이션 유형을 사용하는 경우에는 필요에 따라 SRV 레코드를 만들면 되며, 그러면 다른 파트너가 페더레이션을 검색할 수 있습니다. 이 경우 해당 페더레이션이 <strong>개방형 확장 페더레이션</strong> 또는 <strong>검색된 파트너 도메인</strong>이 됩니다.</p></td>
    </tr>
    <tr class="odd">
    <td><p>허용 파트너 서버</p></td>
    <td><p>SIP 도메인 이름 및 파트너 에지 서버 FQDN을 정책에서 페더레이션 파트너로 구성합니다.</p></td>
    <td><ul>
    <li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함</a></p></li>
    <li><p><a href="lync-server-2013-configure-support-for-allowed-external-domains.md">Lync Server 2013에서 허용되는 외부 도메인 지원 구성</a></p></li>
    <li><p><a href="lync-server-2013-configure-support-for-blocked-external-domains.md">Lync Server 2013에서 차단된 외부 도메인 지원 구성</a></p></li>
    </ul></td>
    <td><p>이 페더레이션 유형은 일대일 관계의 정의이며, 다른 페더레이션 파트너 검색을 허용하지 않습니다. 각 페더레이션 파트너는 명시적으로 구성됩니다. 이전 버전에서는 이러한 유형을 <strong>직접 페더레이션</strong>이라고 했습니다.</p></td>
    </tr>
    <tr class="even">
    <td><p>호스트 파트너 및 공용 메신저 공급자</p></td>
    <td><p>이러한 페더레이션 유형에 대해서는 특정 DNS 요구 사항이 정의되지 않습니다.</p></td>
    <td><ul>
    <li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함</a></p></li>
    <li><p><a href="lync-server-2013-create-or-edit-public-sip-federated-providers.md">Lync Server 2013에서 공용 SIP 페더레이션 공급자 만들기 또는 편집</a></p></li>
    <li><p><a href="lync-server-2013-create-or-edit-hosted-sip-federated-providers.md">Lync Server 2013에서 호스팅된 SIP 페더레이션 공급자 만들기 또는 편집</a></p></li>
    </ul></td>
    <td><p>이 페더레이션 유형은 사용자에 대해 구성할 서비스 및 호스트 공급자를 정의합니다. 일반적인 사용 방식으로는 Windows Live Messenger, Yahoo!, AOL 등의 공용 메신저 공급자 및 Lync Online, Office 365 등의 호스트 공급자에 대한 구성이 포함됩니다.</p>
    

    > [!IMPORTANT]
    > <UL>
    > <LI>
    > <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
    > <LI>
    > <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
    > <LI>
    > <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>


    </td>
    </tr>
    </tbody>
    </table>


2.  필요한 DNS 호스트(A, IPv6의 경우 AAAA) 및 DNS SRV 레코드를 정의하고 구성합니다.

3.  Lync Server 제어판을 사용하거나 Lync Server 관리 셸 및 적절한 cmdlet을 사용하여 정책을 정의하고 구성합니다. Lync Server 관리 셸 cmdlet에 대한 자세한 내용은 [Lync Server 2013의 페더레이션 및 외부 액세스 Cmdlet](https://docs.microsoft.com/en-us/powershell/module/skype/)을 참고하세요.
    

    > [!NOTE]
    > LRS(Lync Room System)에는 페더레이션된 Lync 파트너의 이끌이가 보낸 모임에 대한 참가 단추가 표시되지 않습니다. 모임 참가 링크가 LRS에 표시되도록 하려면 전송하는 조직에서 다음 cmdlet을 사용하여 TNEF를 사용하도록 설정해야 합니다.<BR><BR><CODE>New-RemoteDomain -DomainName Contoso.com -Name Contoso</CODE><BR><CODE>Set-RemoteDomain -Identity Contoso -TNEFEnabled $true</CODE><BR>이것은 LRS에만 해당되는 것이 아닙니다. Outlook과 Lync에서도 이 경우 MAPI 속성이 전송되지 않으므로 참가 링크가 표시되지 않지만, Outlook의 경우에는 사용자가 모임 초대를 열고 모임 URL을 클릭할 수 있습니다. TNEFEnabled가 True로 설정된 경우 Exchange 2013에서 OnlineMeetingExternalLink를 포함한 MAPI 속성이 스트리핑되지 않아 참가 단추가 미리 알림에 표시됩니다.



## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 SIP, XMPP 페더레이션 및 공용 IM 계획](lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md)  
[Lync Server 2013에 대한 외부 액세스 및 페더레이션 관리](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md)

