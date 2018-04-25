---
title: 보안 Cmdlet
TOCTitle: 보안 Cmdlet
ms:assetid: 9a6c654d-287d-434e-8d93-409f0d623f5a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398799(v=OCS.15)
ms:contentKeyID: 49304503
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보안 Cmdlet

 

_**마지막으로 수정된 항목:** 2012-10-09_

Microsoft Lync Server 2013에 포함된 보안 cmdlet은 주로 인증과 사용자 권한 및 권한을 관리하는 데 사용됩니다. 인증서 및 PIN(개인 식별 번호) 인증을 위한 cmdlet 등 인증 관리에 사용할 수 있는 다양한 cmdlet이 있습니다. 또한 여러 cmdlet을 통해 새 RBAC(역할 기반 액세스 제어) 기능을 사용하여 Lync Server의 관리 권한을 위임할 수 있습니다.

## 보안 Cmdlet

Lync Server 제어판에서 보안 설정에 적용되는 많은 관리 작업을 수행할 수 있습니다. 한 가지 주요 예외는 사용자 권한 cmdlet입니다. 그러나 모든 보안 관리 작업은 Lync Server 관리 셸에서 또는 스크립트 내에서 cmdlet을 사용하여 수행할 수 있습니다(특정 작업을 자동화할 수 있는 스크립트 사용). 다음은 보안 설정 관리에 직접적으로 관련된 cmdlet 목록입니다.

**[인증서 및 인증 Cmdlet](lync-server-2013-certificate-and-authentication-cmdlets.md)**

  -   
    [Get-CsCertificate](get-cscertificate.md)

  -   
    [Import-CsCertificate](import-cscertificate.md)

  -   
    [Remove-CsCertificate](remove-cscertificate.md)

  -   
    [Request-CsCertificate](request-cscertificate.md)

  -   
    [Set-CsCertificate](set-cscertificate.md)

  -   
    [Test-CsCertificateConfiguration](test-cscertificateconfiguration.md)

  -   
    [Get-CsClientCertificate](get-csclientcertificate.md)

  -   
    [Revoke-CsClientCertificate](revoke-csclientcertificate.md)

  -   
    [Lock-CsClientPin](lock-csclientpin.md)

  -   
    [Set-CsClientPin](set-csclientpin.md)

  -   
    [Unlock-CsClientPin](unlock-csclientpin.md)

  -   
    [Get-CsClientPinInfo](get-csclientpininfo.md)

  -   
    [New-CsKerberosAccount](new-cskerberosaccount.md)

  -   
    [Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)

  -   
    [New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)

  -   
    [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)

  -   
    [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

  -   
    [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)

  -   
    [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)

  -   
    [Get-CsPinPolicy](get-cspinpolicy.md)

  -   
    [Grant-CsPinPolicy](grant-cspinpolicy.md)

  -   
    [New-CsPinPolicy](new-cspinpolicy.md)

  -   
    [Remove-CsPinPolicy](remove-cspinpolicy.md)

  -   
    [Set-CsPinPolicy](set-cspinpolicy.md)

  -   
    [Get-CsProxyConfiguration](get-csproxyconfiguration.md)

  -   
    [New-CsProxyConfiguration](new-csproxyconfiguration.md)

  -   
    [Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)

  -   
    [Set-CsProxyConfiguration](set-csproxyconfiguration.md)

  -   
    [Get-CsSipDomain](get-cssipdomain.md)

  -   
    [New-CsSipDomain](new-cssipdomain.md)

  -   
    [Remove-CsSipDomain](remove-cssipdomain.md)

  -   
    [Set-CsSipDomain](set-cssipdomain.md)

**[사용자 권한 및 사용 권한 Cmdlet](lync-server-2013-user-rights-and-permissions-cmdlets.md)**

  -   
    [Get-CsAdminRole](get-csadminrole.md)

  -   
    [New-CsAdminRole](new-csadminrole.md)

  -   
    [Remove-CsAdminRole](remove-csadminrole.md)

  -   
    [Set-CsAdminRole](set-csadminrole.md)

  -   
    [Update-CsAdminRole](update-csadminrole.md)

  -   
    [Get-CsAdminRoleAssignment](get-csadminroleassignment.md)

  -   
    [Grant-CsOUPermission](grant-csoupermission.md)

  -   
    [Revoke-CsOUPermission](revoke-csoupermission.md)

  -   
    [Test-CsOUPermission](test-csoupermission.md)

  -   
    [Grant-CsSetupPermission](grant-cssetuppermission.md)

  -   
    [Revoke-CsSetupPermission](revoke-cssetuppermission.md)

  -   
    [Test-CsSetupPermission](test-cssetuppermission.md)

**[상호 운용성 Cmdlet](lync-server-2013-interoperability-cmdlets.md)**

  - [Get-CsOAuthConfiguration](get-csoauthconfiguration.md)

  - [Set-CsOAuthConfiguration](set-csoauthconfiguration.md)

  - [Get-CsOAuthServer](get-csoauthserver.md)

  - [New-CsOAuthServer](new-csoauthserver.md)

  - [Remove-CsOAuthServer](remove-csoauthserver.md)

  - [Set-CsOAuthServer](set-csoauthserver.md)

  - [Get-CsPartnerApplication](get-cspartnerapplication.md)

  - [New-CsPartnerApplication](new-cspartnerapplication.md)

  - [Remove-CsPartnerApplication](remove-cspartnerapplication.md)

  - [Set-CsPartnerApplication](set-cspartnerapplication.md)

## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412)

