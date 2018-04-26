---
title: Lync Online 도메인에 대한 페더레이션 지원 구성
TOCTitle: Lync Online 도메인에 대한 페더레이션 지원 구성
ms:assetid: 19d5d5be-cd7f-47b8-b6c5-651a3191def7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202166(v=OCS.15)
ms:contentKeyID: 49302958
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online 도메인에 대한 페더레이션 지원 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

Microsoft Lync Online 2010 고객과 페더레이션하려면 다음 단계를 완료해야 합니다.

  - Lync Online 2010 고객의 도메인(예: contoso.onmicrosoft.com)에 대한 지원을 구성합니다. 이 설명서의 [Lync Online 고객과의 페더레이션을 위한 필수 구성 요소](lync-server-2013-prerequisites-for-federating-with-a-lync-online-customer.md) 섹션에 지정된 것처럼 조직에 대한 페더레이션이 이미 사용하도록 설정된 상태여야 합니다. 페더레이션을 설정하려면 페더레이션된 도메인에서 액세스를 제어하기 위해 사용할 방법을 지정해야 합니다. 조직에 검색이 사용되도록 구성한 경우 필요에 따라 도메인을 조직의 허용 목록에 추가할 수 있습니다. 도메인 검색을 사용하도록 설정하지 않은 경우 Lync Online 고객의 도메인 이름을 허용 도메인 목록에 추가해야 합니다. Lync Server 제어판을 사용하거나 **New-CSAllowedDomain** cmdlet을 실행하여 도메인 이름을 추가할 수 있습니다. 도메인 검색을 사용하도록 설정하는 방법을 비롯하여 Lync Server 제어판을 사용하는 방법에 대한 자세한 내용은 작업 설명서에서 [Lync Server 2013에서 조직에 대한 SIP 페더레이션 공급자 관리](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)를 참조하십시오. **New-CSAllowedDomain** cmdlet을 사용하여 도메인을 추가하는 방법에 대한 자세한 내용은 작업 설명서에서 [New-CsAllowedDomain](new-csalloweddomain.md)을 참조하십시오.
    

    > [!NOTE]
    > Lync Online 고객은 여러 도메인을 가질 수 있습니다. 두 개 이상의 도메인과 페더레이션하려면 페더레이션을 지원하려는 개별 도메인에 대해 지원을 구성하고 Lync Online 고객 관리자가 페더레이션할 각 도메인에 대한 페더레이션을 설정해야 합니다.



  - 페더레이션하려는 Lync Online 2010 고객 도메인의 호스팅 공급자에 대한 지원을 구성합니다. 이 섹션의 절차에 따라 호스팅 공급자에 대한 지원을 구성합니다.
    

    > [!NOTE]
    > 이 단계는 페더레이션된 파트너의 위치에서 온-프레미스로 배포된 도메인과의 페더레이션이 아니라 Lync Online 고객의 도메인과 페더레이션하려는 경우에만 수행하면 됩니다.



## 호스팅 공급자에 대한 지원을 구성하려면

1.  프런트 엔드 서버에서 Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  **New-CsHostingProvider** cmdlet을 실행하여 호스팅 공급자를 만들고 구성합니다. 예를 들어 다음을 실행합니다.
    
        New-CsHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -VerificationLevel UseSourceVerification -Enabled $True -EnabledSharedAddressSpace $False -HostsOCSUsers $False -IsLocal $False
    
    위의 예는 다음 매개 변수를 설정합니다.
    
      - **Identity**는 만들고 있는 호스팅 공급자에 대한 고유 문자열 값 식별자를 지정합니다. 이 Identity로 기존 공급자가 이미 구성된 경우에는 명령이 실패합니다.
    
      - **ProxyFQDN**은 호스팅 공급자가 사용하는 프록시 서버의 FQDN(정규화된 도메인 이름)을 지정합니다. 이 값은 수정할 수 없습니다. 호스팅 공급자가 프록시 서버를 변경하는 경우 해당 공급자에 대한 항목을 삭제한 다음 다시 만들어야 합니다.
    
      - **VerificationLevel**은 호스팅 공급자가 보낸 메시지가 해당 공급자로부터 전송되었는지 확인하는 방법 또는 여부를 나타냅니다.
    
      - **Enabled**는 도메인과 호스팅 공급자 간의 네트워크 연결을 활성화할지 여부를 나타냅니다. 이 값이 **True**로 설정되어야 두 조직 간 메시지를 교환할 수 있습니다.
    
      - **EnabledSharedAddressSpace**는 호스팅 공급자가 공유 SIP 주소 공간(분할 도메인) 시나리오에서 사용 중인지 여부를 나타냅니다.
    
      - **HostsOCSUsers**는 호스팅 공급자가 Lync Server 계정을 호스팅하는 데 사용되는지 여부를 나타냅니다. **False**로 설정하면 공급자가 Microsoft Exchange 계정 등의 다른 계정 유형을 호스팅합니다.
    
      - **IsLocal**은 호스팅 공급자가 사용하는 프록시 서버가 Lync Server 토폴로지에 포함되는지 여부를 나타냅니다.
    
    이 cmdlet을 사용하는 방법에 대한 자세한 내용은 작업 설명서에서 [New-CsHostingProvider](new-cshostingprovider.md)를 참조하십시오.

