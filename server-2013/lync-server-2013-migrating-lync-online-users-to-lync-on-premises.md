---
title: Lync Online 사용자를 Lync 온-프레미스로 마이그레이션
TOCTitle: Lync Online 사용자를 Lync 온-프레미스로 마이그레이션
ms:assetid: 0e29605b-db2d-4cbf-b6a9-15db6b9fdabc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn689115(v=OCS.15)
ms:contentKeyID: 62247349
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online 사용자를 Lync 온-프레미스로 마이그레이션

 

_**마지막으로 수정된 항목:** 2015-03-09_


> [!IMPORTANT]
> 다음 단계는 Lync 온-프레미스를 배포하기 전에 원래 Lync Online에서 Lync를 사용할 수 있는 사용자 계정을 마이그레이션할 경우에만 필요합니다. 원래 Lync 온-프레미스를 사용할 수 있는 사용자를 이동한 후에 나중에 Lync Online으로 이동하려면 <A href="lync-server-2013-administering-users-in-a-hybrid-deployment.md">하이브리드 Lync Server 2013 배포에서 사용자 관리</A>를 참고하세요.<BR>또한 이동 중인 모든 사용자에게는 온-프레미스 Active Directory에 계정이 있어야 합니다.



## Lync Online에서 원래 사용할 수 있는 사용자 계정을 Lync 온-프레미스로 마이그레이션

1.  먼저 조직이 하이브리드에 맞게 구성되어 있는지 확인합니다.
    
      - Windows Azure Active Directory 동기화 도구를 설치합니다. 자세한 내용은 <http://social.technet.microsoft.com/wiki/contents/articles/19098.howto-install-the-windows-azure-active-directory-sync-tool.aspx>를 참고하세요.
    
      - 사용자가 Lync Online용 Single Sign-On을 사용할 수 있도록 설정하려면 ADFS(Active Directory Federation Services)(<http://social.technet.microsoft.com/wiki/contents/articles/1011.active-directory-federation-services-ad-fs-overview.aspx>)를 설치합니다.
    
      - 온-프레미스 배포의 Lync Server 관리 셸에 다음 cmdlet을 입력해 Lync Online의 호스팅 공급자를 만듭니다.
        
            Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting -EnablePartnerDiscovery $true
        
            New-CSHostingProvider -Identity LyncOnline -Name LyncOnlin -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root

2.  온-프레미스 에지 서버에 다음 표에서와 같이 Lync Online에 대한 연결을 설정하는 인증서 체인이 있는지 확인합니다. 이 체인은 [https://corp.sts.microsoft.com/Onboard/ADFS\_Onboarding\_Pack/corp\_sts\_certs.zip](https://corp.sts.microsoft.com/onboard/adfs_onboarding_pack/corp_sts_certs.zip)에서 다운로드할 수 있습니다.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>인증서</th>
    <th>인증서 저장소</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Baltimore CyberTrust Root</p></td>
    <td><p>신뢰할 수 있는 루트 CA</p></td>
    </tr>
    <tr class="even">
    <td><p>Microsoft Internet Authority(새 CA 인증서)</p></td>
    <td><p>중간 CA</p></td>
    </tr>
    <tr class="odd">
    <td><p>MSIT Machine Auth CA2(새로 발급되는 CA2)</p></td>
    <td><p>중간 CA</p></td>
    </tr>
    </tbody>
    </table>


3.  온-프레미스 Active Directory에서 Lync 온-프레미스에 대해 영향을 받는 사용자 계정을 사용하도록 설정합니다. 다음 cmdlet을 입력해 각 사용자에 대해 이와 같이 할 수 있습니다.
    
        Enable-CsUser
        -Identity "username" 
        -SipAddress "sip: username@contoso.com"
        -HostingProviderProxyFqdn "sipfed.online.lync.com"
    
    또는 파일에서 사용자 이름을 읽고 Enable-CsUser cmdlet에 대한 입력으로 이를 제공하는 스크립트를 만들 수 있습니다.
    
        Enable-CsUser
        -Identity $Identity 
        -SipAddress $SipAddress 
        -HostingProviderProxyFqdn "sipfed.online.lync.com"

4.  DirSync를 실행해 Lync Online 사용자와 업데이트된 Lync 온-프레미스 사용자를 동기화합니다.

5.  모든 SIP 트래픽이 Lync 온-프레미스로 전달되도록 일부 DNS 레코드를 업데이트합니다.
    
      - 온-프레미스 역방향 프록시 서버의 FQDN을 가리키도록 **lyncdiscover.contoso.com** A 레코드를 업데이트합니다.
    
      - 공용 IP 또는 Lync 온-프레미스의 액세스 에지 서비스 VIP 주소로 확인하도록***\_sip*.\_tls.contoso.com** SRV 레코드를 업데이트합니다.
    
      - 공용 IP 또는 Lync 온-프레미스의 액세스 에지 서비스 VIP 주소로 확인하도록 ***\_sipfederationtls*.\_tcp.contoso.com** SRV 레코드를 업데이트합니다.
    
      - 조직에서 분할 DNS를 사용할 경우 내부 DNS 영역을 통해 이름을 확인하는 사용자를 프런트 엔드 풀로 보내야 합니다.

6.  `Get-CsUser` cmdlet을 입력해 이동 중인 사용자에 대한 일부 속성을 확인합니다. HostingProviderProxyFQDN이 `"sipfed.online.lync.com"`으로 설정되어 있고 SIP 주소가 올바르게 설정되었는지 확인해야 합니다.

7.  Lync Online 사용자를 Lync 온-프레미스로 이동합니다.
    
    단일 사용자를 이동하려면 다음을 입력합니다.
    
        $cred = Get-Credential
    
        Move-CsUser -Identity <username>@contoso.com -Target "<fe-pool>.contoso.com" -Credential $cred -HostedMigrationOverrideURL <URL>
    
    **Get-CsUSer** cmdlet과 함께 –Filter 매개 변수를 사용하여 특정 속성이 있는 사용자를 선택하면 여러 사용자를 이동할 수 있습니다. 예를 들어 {Hosting Provider –eq "sipfed.online.lync.om"}을 필터링해 모든 Lync Online 사용자를 선택할 수 있습니다. 그런 다음에 아래와 같이 반환된 사용자를 **Move-CsUSer** cmdlet에 전달하면 됩니다.
    
        Get-CsUser -Filter {Hosting Provider -eq "sipfed.online.lync.com"} | Move-CsUser -Target "<fe-pool>.contoso.com" -Credential $creds -HostedMigrationOverrideURL <URL>
    
    **HostedMigrationOverrideUrl** 매개 변수에 대해 지정되는 URL의 형식은 호스트된 마이그레이션 서비스가 실행되고 있는 풀의 URL이어야 하며 *Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc*와 같은 형식이어야 합니다.
    
    사용 중인 Office 365 테넌트 계정에 대해 Lync Online 제어판의 URL을 통해 호스트된 마이그레이션 서비스의 URL을 확인할 수 있습니다.
    
    ## Office 365 테넌트에 대해 호스트된 마이그레이션 서비스 URL을 확인하려면
    
    1.  Office 365 테넌트에 관리자로 로그인합니다.
    
    2.  **Lync 관리 센터**를 엽니다.
    
    3.  **Lync 관리 센터**가 표시되면 주소 표시줄에서 URL을 **lync.com**까지 선택하고 복사합니다. URL의 형태는 다음과 유사합니다.
        
        `https://webdir0a.online.lync.com/lscp/?language=en-US&tenantID=`
    
    4.  URL의 **webdir**을 **admin**으로 바꾸면 다음과 같이 표시됩니다.
        
        `https://admin0a.online.lync.com`
    
    5.  **/HostedMigration/hostedmigrationservice.svc** 문자열을 URL에 추가합니다.
        
        그러면 URL이 **HostedMigrationOverrideUrl**의 값에 해당하며 다음과 같이 표시됩니다.
        
        `https://admin0a.online.lync.com/HostedMigration/hostedmigrationservice.svc`
    

    > [!NOTE]
    > rtcxds 데이터베이스의 트랜잭션 로그 파일에 대한 기본 최대 크기는 16GB입니다. 한 번에 많은 사용자를 이동할 때 특히 미러링이 설정되어 있으면 이 정도로는 충분하지 않을 수 있습니다. 이 문제를 해결하기 위해서 파일 크기를 늘리거나 로그 파일을 정기적으로 백업하는 방법이 있습니다. 자세한 내용은 <A class=uri href="http://support.microsoft.com/kb/2756725">http://support.microsoft.com/kb/2756725</A>를 참고하세요.



8.  이 단계는 선택 사항입니다. Exchange 2013 Online과 통합해야 할 경우 추가 호스팅 공급자를 사용해야 합니다. 자세한 내용은 [Exchange Online과 온-프레미스 Lync Server 2013 통합 구성](lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md)을 참고하세요.

9.  이제 사용자가 이동됩니다. 다음 표에 나와 있는 특성에 대해 사용자에게 올바른 값이 있는지 확인하려면 이 cmdlet을 입력합니다.
    
        Get-CsUser | fl DisplayName,HostingProvider,SipAddress,Enabled
    
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Active Directory 특성</th>
    <th>특성 이름</th>
    <th>Lync Online 사용자에 대한 올바른 값</th>
    <th>Lync 온-프레미스 사용자에 대한 올바른 값</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>msRTCSIP-DeploymentLocator</p></td>
    <td><p>HostingProvider</p></td>
    <td><p>sipfed.online.lync.com</p></td>
    <td><p>SRV:</p></td>
    </tr>
    <tr class="even">
    <td><p>msRTCSIP-PrimaryUserAddress</p></td>
    <td><p>SIPAddress</p></td>
    <td><p>sip:userName@contoso.com</p></td>
    <td><p>sip:userName@contoso.com</p></td>
    </tr>
    <tr class="odd">
    <td><p>sRTCSIP-UserEnabled</p></td>
    <td><p>Enabled</p></td>
    <td><p>True</p></td>
    <td><p>True</p></td>
    </tr>
    </tbody>
    </table>


10. 이동된 각 사용자는 Lync에서 로그아웃했다가 다시 로그인해야 합니다. 로그인할 때에는 대화 상대 목록을 확인하고 필요할 경우 대화 상대를 추가해야 합니다.
    
    예약된 모임은 Lync Online에서 Lync 온-프레미스로 마이그레이션되지 않습니다. 이동된 후에 사용자가 이러한 모임을 다시 예약해야 합니다.
    
    DNS 레코드가 업데이트되고 모든 사용자가 온-프레미스에 연결되면 HostingProvider 특성이 Lync 사용자를 SRV 레코드를 사용하도록 안내하거나 온라인 공급자 "sipfed.online.lync.com"으로 보냅니다.

