---
title: 'Lync Server 2013: Lync Online으로 사용자 이동'
TOCTitle: Lync Online으로 사용자 이동
ms:assetid: 6a523c86-2eac-4fa4-973a-4406872c9a7d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204969(v=OCS.15)
ms:contentKeyID: 49303921
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync Online으로 사용자 이동

 

_**마지막으로 수정된 항목:** 2014-05-29_

사용자를 Lync Online으로 마이그레이션하기 전에 이동할 계정과 연결된 사용자 데이터를 백업해야 합니다. 모든 사용자 데이터가 사용자 계정과 함께 이동하지는 않습니다. 자세한 내용은 [Lync Server 2013의 백업 및 복원 요구 사항: 데이터](lync-server-2013-backup-and-restoration-requirements-data.md)를 참고하세요.

## Lync Online으로 사용자 설정 마이그레이션

사용자 설정은 사용자 계정과 함께 이동됩니다. 그러나 일부 온-프레미스 설정은 사용자 계정과 함께 이동되지 않습니다.

## Lync Online으로 파일럿 사용자 이동

Lync Online으로 사용자를 이동하기 전에 소수의 파일럿 사용자를 이동하여 환경이 올바르게 구성되었는지를 확인할 수 있습니다. 그러면 추가 사용자 이동을 시도하기 전에 Lync 기능과 서비스가 예상대로 작동하는지 확인할 수 있습니다.

온-프레미스 사용자를 비즈니스용 Skype Online 테넌트로 이동하려면 Microsoft Office 365 테넌트에 대한 관리자 자격 증명을 사용하여 Lync Server 관리 셸에서 다음 cmdlet을 실행합니다. 이때 "username@contoso.com"은 이동하려는 사용자의 정보로 바꿉니다.

    $creds=Get-Credential

    Move-CsUser -Identity username@contoso.com -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>

**HostedMigrationOverrideUrl** 매개 변수에 대해 지정되는 URL의 형식은 호스트된 마이그레이션 서비스가 실행되고 있는 풀의 URL이어야 하며 *Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc* 와 같은 형식이어야 합니다.

사용 중인 Office 365 테넌트 계정에 대해 Lync Online 제어판의 URL을 통해 호스트된 마이그레이션 서비스의 URL을 확인할 수 있습니다.

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

## Lync Online으로 사용자 이동

[Get-CsUser](get-csuser.md) cmdlet을 –Filter 매개 변수와 함께 사용하여 사용자 계정에 RegistrarPool 같은 특정 속성이 지정된 사용자를 선택하면 여러 사용자를 이동할 수 있습니다. 그리고 나서 다음 예제에 나와 있는 대로 반환된 사용자를 [Move-CsUser](move-csuser.md) cmdlet에 전달할 수 있습니다.

    Get-CsUser -Filter {UserProperty -eq "UserPropertyValue"} | Move-CsUser -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>

다음 예제와 같이 -OU 매개 변수를 사용하여 지정된 OU의 모든 사용자를 검색할 수도 있습니다.

    Get-CsUser -OU "cn=hybridusers,cn=contoso.." | Move-CsUser -Target sipfed.online.lync.com -Credentials $creds -HostedMigrationOverrideUrl <URL>

## Lync Online 사용자 설정 및 기능 확인

다음 방법을 통해 사용자가 정상적으로 이동되었는지 확인할 수 있습니다.

  - Lync Online 제어판에서 사용자의 상태를 확인합니다. 온-프레미스 사용자와 온라인 사용자는 각각 다르게 표시됩니다.

  - 다음 cmdlet을 실행합니다.
    
        Get-CsUser -Identity

