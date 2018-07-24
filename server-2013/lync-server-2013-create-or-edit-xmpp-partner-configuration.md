---
title: 'Lync Server 2013: XMPP 파트너 구성 만들기 또는 편집'
TOCTitle: XMPP 파트너 구성 만들기 또는 편집
ms:assetid: 362dbe5e-8ee9-4aba-8c26-5907312b4a60
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ552447(v=OCS.15)
ms:contentKeyID: 49303285
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 XMPP 파트너 구성 만들기 또는 편집

 

_**마지막으로 수정된 항목:** 2014-09-03_

Microsoft Lync Server 2013에서는 에지 서버의 XMPP(Extensible Messaging and Presence Protocol) 프록시와 프런트 엔드 서버 또는 프런트 엔드 풀의 XMPP 게이트웨이를 통합합니다. 다른 XMPP 배포로부터의 연결을 허용하려면 Lync Server 제어판에서 XMPP를 구성해야 합니다. XMPP 도메인별로 설정을 구성합니다. 새 파트너 연결을 만들려면 다음을 수행합니다.

## 새 페더레이션 파트너를 만들거나 기존 구성을 편집하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **페더레이션 및 외부 액세스** 를 클릭한 다음 **XMPP 페더레이션 파트너** 를 클릭합니다.

4.  새 구성을 만들려면 **새로 만들기** 를 클릭합니다.

5.  기존 구성을 편집하려면 구성을 선택하고 **편집** 을 클릭합니다.

6.  **XMPP 페더레이션 파트너** 에 대한 구성을 만들거나 편집하려면 다음 설정을 정의합니다.

7.  **기본 도메인**(필수). 기본 도메인은 XMPP 파트너의 기반이 되는 도메인입니다. 예를 들어 XMPP 파트너 도메인 이름으로 **fabrikam.com**을 입력할 수 있습니다. 이는 필수 항목입니다.

8.  **설명**. 설명은 이 특정 구성에 대한 참고 사항이거나 기타 식별 정보입니다. 이 항목은 선택 사항입니다.

9.  **추가 도메인**. 추가 도메인은 허용되는 XMPP 통신의 일부분으로 포함해야 하는 XMPP 파트너 도메인의 일부분인 도메인입니다. 예를 들어 기본 도메인이 **fabrikam.com**이면 XMPP를 통해 통신할 fabrikam.com 아래의 기타 모든 도메인을 나열합니다. 예를 들어 회사 XMPP 도메인에는 **corp.fabrikam.com** 및 **it.fabrikam.com**을 입력할 수 있고 fabrikam.com의 기본 XMPP 도메인 아래에는 IT XMPP 도메인을 입력할 수 있습니다.

10. **파트너 유형**. **파트너 유형**은 필수 설정이며, 드롭다운 메뉴에서 세 가지 선택 항목을 제공합니다. 다음 중 하나를 선택하여 추가할 수 있는 대화 상대를 설명 및 적용해야 합니다. 다음 중에서 선택할 수 있습니다.
    
      - **페더레이션**. **페더레이션** 파트너 유형은 Lync Server 또는 Office Communications Server 2007 R2 파트너 배포 간의 신뢰할 수 있는 연결입니다.
    
      - **확인된 공공 파트너**. **확인된 공공 파트너**는 공급자에 의해 확인된 배포 내의 대화 상대를 사용자의 대화 상대 목록에 추가할 수 있는 파트너입니다. Lync 사용자가 초대를 보내거나 Lync 사용자가 파트너 대화 상대의 초대를 수락할 수 있습니다.
    
      - **확인되지 않은 공공 파트너**. **확인되지 않은 공공 파트너** 관계는 두 배포 간에 확인 가능한 상태가 설정되어 있지 않음을 의미합니다. Lync 사용자가 Lync 사용자를 대화 상대 목록에 추가하려면 해당 대화 상대에 대해 확인되지 않은 대화 상대를 초대해야 합니다. 예를 들어 Google GTalk는 Lync Server와 관련하여 확인된 공공 파트너 XMPP 서비스가 아닙니다. 즉, GTalk 사용자는 Lync 사용자가 명시적으로 초대를 보내지 않으면 Lync 사용자를 대화 상대로 추가할 수 없습니다.

11. 스트림 협상 및 보안 방법 TLS(전송 계층 보안) 및 SASL(Software Authentication and Security Layer)에 대한 참고 사항
    
    XSF( **XMPP Standards Foundation**) 및 IETF( **Internet Engineering Task Force**)에서는 TLS 클라이언트 인증서, TLS 서버 인증서 및 SASL 메커니즘 사용/관리에 대한 규칙 및 표준 집합을 정의합니다. XMLL 스트림을 보호하려면 TLS 및 SASL을 사용해야 합니다. XMPP Standards 문서 **XEP-0178**에서 "PKIX 인증서를 사용하는 SASL EXTERNAL 메커니즘 사용을 위해 권장 프로토콜 흐름을 지정(특히 XMPP 서비스에서 TLS 협상을 필수로 지정하는 경우)"하는 작업은 PKI(공용 키 인프라)로 지칭됩니다.
    
    XMPP 요구 사항에 대한 자세한 내용은 XSF 문서 XEP-0178을 참조하십시오. 자세한 내용은 "XEP-0178: 인증서와 함께 SASL EXTERNAL을 사용하는 모범 사례"( <http://xmpp.org/extensions/xep-0178.html>)를 참조하십시오.
    
    IETF 문서 "XMPP(Extensible Messaging and Presence Protocol): 핵심", 섹션 5.0, STARTTLS 협상( <http://tools.ietf.org/html/rfc6120>)을 참조하십시오.
    
      - **TLS 협상**. TLS 협상 규칙을 정의합니다. XMPP 서비스에 대해 TLS를 필수, 선택 사항 또는 지원 안 됨으로 설정할 수 있습니다. "선택 사항"으로 설정하는 경우 협상 필수 항목 결정을 위해 요구 사항을 최대한 XMPP 서비스까지 그대로 둘 수 있습니다. 유효하지 않은 구성, 알려진 오류 구성 등 가능한 모든 설정과 SASL, TLS 및 다이얼백에 대한 자세한 내용을 보려면 [Lync Server 2013의 XMPP 페더레이션 파트너의 협상 설정](lync-server-2013-negotiation-settings-for-xmpp-federated-partners.md) 섹션을 참조하세요.
        
           **필수**. XMPP 서비스에 TLS 협상이 필요합니다.
        
           **선택 사항**. XMPP 서비스는 TLS가 협상 필수 항목임을 나타냅니다.
        
           **지원 안 됨**. XMPP 서비스가 TLS를 지원하지 않습니다.
    
      - **SASL 협상**. SASL 협상 규칙을 정의합니다. XMPP 서비스에 대해 SASL를 필수, 선택 사항 또는 지원 안 됨으로 설정할 수 있습니다. "선택 사항"으로 설정하는 경우 협상 필수 항목 결정을 위해 요구 사항을 최대한 파트너 XMPP 서비스까지 그대로 둘 수 있습니다.
        

        > [!WARNING]
        > SASL에는 TLS가 필요합니다. SASL을 사용하려면 TLS가 필수 또는 선택이어야 합니다. SASL을 필수 또는 선택으로 정의하는 모든 구성에서는 TLS를 지원해야 합니다. TLS를 필수 또는 옵션으로 설정하지 않은 상태에서 <STRONG>커밋</STRONG> 을 클릭하여 변경 내용을 저장하면 SASL에서 TLS를 지원해야 하며 변경 내용이 저장되지 않는다는 경고가 표시됩니다. 이 오류를 해결하려면 TLS를 <STRONG>필수</STRONG> 또는 <STRONG>선택</STRONG> 으로 설정합니다. SASL 사용이 선택 사항이며 TLS 협상을 지원할 수 없는 경우에는 SASL 협상을 <STRONG>지원되지 않음</STRONG> 으로 설정해야 합니다. XMPP 서비스에서 TLS 및 SASL에 대해 사용해야 하는 적절한 협상 스트림을 확인해야 하며, 그렇지 않으면 서비스가 중단됩니다.

        
           **필수**. XMPP 서비스에 SASL 협상이 필요합니다.
        
           **선택 사항**. XMPP 서비스는 SASL가 협상 필수 항목임을 나타냅니다.
        
           **지원 안 됨**. XMPP 서비스가 SASL를 지원하지 않습니다.
    
      - **전화 접속 회의 협상**. 전화 접속 회의 협상은 XSF의 **XEP-220 : 서버 전화 접속 회의**(<http://xmpp.org/extensions/xep-0220.html>) 문서에 정의되어 있습니다. 서버 전화 접속 회의 프로세스에서는 DNS(Domain Name System) 및 신뢰할 수 있는 서버를 사용하여 요청이 유효한 XMPP 파트너로부터 받은 것임을 확인합니다. 이를 위해 원본 서버는 생성된 전화 접속 회의 키를 사용하여 특정 유형의 메시지를 만들고 DNS에서 수신 서버를 조회합니다. 원본 서버는 XML 스트림의 키를 결과 DNS 조회(대개 수신 서버)로 보냅니다. 수신 서버는 XML 스트림을 통해 키를 받으면 원본 서버에 응답하지는 않으며 키를 알려진 신뢰할 수 있는 서버로 보냅니다. 신뢰할 수 있는 서버는 키가 유효한지 여부를 확인합니다. 키가 유효하지 않으면 수신 서버는 원본 서버에 응답하지 않습니다. 키가 유효하면 수신 서버는 ID와 키가 유효함을 원본 서버에 알리며, 그러면 대화를 시작할 수 있습니다.
        
        **전화 접속 회의 협상**의 유효한 두 상태는 다음과 같습니다.
        
           **참**. 원본 서버에서 요청을 받아야 하는 경우 XMPP 서버가 전화 접속 회의 협상을 사용하도록 구성됩니다.
        
           **거짓**. XMPP 서버가 전화 접속 회의 협상을 사용하도록 구성되지 않으며, 원본 서버에서 요청을 받아야 하는 경우 해당 요청은 무시됩니다.

