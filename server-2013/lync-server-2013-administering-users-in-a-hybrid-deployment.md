---
title: 'Lync Server 2013: 하이브리드 배포에서 사용자 관리'
TOCTitle: 하이브리드 배포에서 사용자 관리
ms:assetid: 6924ed7b-30a9-4be7-b952-90655625f2c8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204967(v=OCS.15)
ms:contentKeyID: 49303912
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 하이브리드 Lync Server 2013 배포에서 사용자 관리 

_**마지막으로 수정된 항목:** 2014-05-29_

Microsoft Office 365 온라인 포털에서 제공되는 사용자 관리 기능을 통해 Lync Online으로 마이그레이션된 사용자에 대한 사용자 설정 및 정책을 관리할 수 있습니다. 관리 작업을 수행하려면 테넌트 관리자 계정을 사용하여 로그인해야 합니다.

## 사용자를 다시 온-프레미스로 이동


> [!IMPORTANT]
> 이 섹션은 사용자를 만들어 Lync 온-프레미스를 사용할 수 있도록 설정했다가 온-프레미스 배포에서 Lync Online으로 이동한 경우에만 적용됩니다. Lync Online에서 만들고 온-프레미스 배포에서 Lync를 사용할 수 있도록 설정하지 않은 사용자를 이동하려면 <A href="lync-server-2013-moving-users-from-lync-online-to-lync-on-premises.md">Lync Server 2013에서 Lync Online과 Lync 온-프레미스 간 사용자 이동</A>을 참고하세요.


  - 사용자를 Lync Online에서 다시 Lync 온-프레미스로 이동하려면 다음 cmdlet을 실행합니다.
    
    ``` 
        $cred=Get-Credential
    ```
    ```    
        Move-CsUser -Identity username@contoso.com -Target localpool.contoso.com -Credential $cred -HostedMigrationOverrideUrl <URL>
    ```

**HostedMigrationOverrideUrl** 매개 변수에 대해 지정되는 URL의 형식은 호스트된 마이그레이션 서비스가 실행되고 있는 풀의 URL이어야 하며 다음과 같은 형식이어야 합니다.

*Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc* . 사용 중인 Office 365 테넌트 계정에 대해 Lync Online 제어판의 URL을 통해 호스트된 마이그레이션 서비스의 URL을 확인할 수 있습니다.

**Office 365 테넌트에 대해 호스트된 마이그레이션 서비스 URL을 확인하려면**

1.  Office 365 테넌트에 관리자로 로그인합니다.

2.  **Lync 관리 센터** 를 엽니다.

3.  **Lync 관리 센터** 가 표시되면 주소 표시줄에서 URL을 **lync.com**까지 선택하고 복사합니다. URL의 형태는 다음과 유사합니다.
    
    `https://webdir0a.online.lync.com/lscp/?language=en-US&tenantID=`

4.  URL의 **webdir**을 **admin**으로 바꾸면 다음과 같이 표시됩니다.
    
    `https://admin0a.online.lync.com`

5.  **/HostedMigration/hostedmigrationservice.svc** 문자열을 URL에 추가합니다.
    
    그러면 URL이 **HostedMigrationOverrideUrl**의 값에 해당하며 다음과 같이 표시됩니다.
    
    `https://admin0a.online.lync.com/HostedMigration/hostedmigrationservice.svc`

