---
title: 서버 역할 및 서비스 Cmdlet
TOCTitle: 서버 역할 및 서비스 Cmdlet
ms:assetid: ff3561de-043e-4071-88f7-8de3cded52f6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg415683(v=OCS.15)
ms:contentKeyID: 49305649
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 서버 역할 및 서비스 Cmdlet

 

_**마지막으로 수정된 항목:** 2013-07-29_

대부분의 Microsoft Lync Server 2013 구성 요소는 서버 역할 또는 서비스로 실행되며, Lync Server 2013에는 이러한 서버 역할 및 서비스를 관리할 수 있도록 여러 cmdlet이 제공됩니다.

## 서버 역할 및 서비스 Cmdlet

서버 및 서비스 역할에 적용되는 대부분의 관리 작업은 Lync Server 제어판에서 수행할 수 있습니다(일부 관리 작업은 제외). 예를 들어, Lync Server 제어판을 사용하여 보관 서버 설정 및 주소록 서버 설정을 관리할 수 있습니다. 단, 이러한 모든 작업은 Lync Server 관리 셸이나 스크립트 내에서 cmdlet을 사용하여 수행할 수 있습니다. 스크립트를 사용하면 특정 작업을 자동화할 수 있습니다. 다음은 서버 역할 및 서비스 관리와 직접 관련된 cmdlet 목록입니다.

**[주소록 서버 Cmdlet](lync-server-2013-address-book-server-cmdlets.md)**

  -   
    [Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)

  -   
    [New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)

  -   
    [Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)

  -   
    [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

<!-- end list -->

  -   
    [Update-CsAddressBook](update-csaddressbook.md)

  -   
    [Debug-CsAddressBookReplication](debug-csaddressbookreplication.md)

<!-- end list -->

  -   
    [Test-CsAddressBookService](test-csaddressbookservice.md)

  -   
    [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

**[보관 및 모니터링 Cmdlet](lync-server-2013-archiving-and-monitoring-cmdlets.md)**

  -   
    [Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)

  -   
    [New-CsArchivingConfiguration](new-csarchivingconfiguration.md)

  -   
    [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)

  -   
    [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)

  -   
    [Export-CsArchivingData](export-csarchivingdata.md)

  -   
    [Invoke-CsArchivingDatabasePurge](invoke-csarchivingdatabasepurge.md)

  -   
    [Get-CsArchivingPolicy](get-csarchivingpolicy.md)

  -   
    [Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)

  -   
    [New-CsArchivingPolicy](new-csarchivingpolicy.md)

  -   
    [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)

  -   
    [Set-CsArchivingPolicy](set-csarchivingpolicy.md)

  -   
    [Set-CsArchivingServer](set-csarchivingserver.md)

  -   
    [Get-CsCdrConfiguration](get-cscdrconfiguration.md)

  -   
    [New-CsCdrConfiguration](new-cscdrconfiguration.md)

  -   
    [Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)

  -   
    [Set-CsCdrConfiguration](set-cscdrconfiguration.md)

  -   
    [Set-CsMonitoringServer](set-csmonitoringserver.md)

  -   
    [Get-CsQoEConfiguration](get-csqoeconfiguration.md)

  -   
    [New-CsQoEConfiguration](new-csqoeconfiguration.md)

  -   
    [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)

  -   
    [Set-CsQoEConfiguration](set-csqoeconfiguration.md)

[Invoke-CsCdrDatabasePurge](invoke-cscdrdatabasepurge.md)

  -   
    [Export-CsArchivingData](export-csarchivingdata.md)

  -   
    [Invoke-CsQoEDatabasePurge](invoke-csqoedatabasepurge.md)

  -   
    [Get-CsReportingConfiguration](get-csreportingconfiguration.md)

  -   
    [New-CsReportingConfiguration](new-csreportingconfiguration.md)

  -   
    [Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)

  -   
    [Set-CsReportingConfiguration](set-csreportingconfiguration.md)

  -   
    [Get-CsTestUserCredential](get-cstestusercredential.md)

  -   
    [Remove-CsTestUserCredential](remove-cstestusercredential.md)

  -   
    [Set-CsTestUserCredential](set-cstestusercredential.md)

  -   
    [Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)

  -   
    [New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)

  -   
    [Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)

  -   
    [Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)

  -   
    [Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

  -   
    [New-CsExtendedTest](new-csextendedtest.md)

**[데이터베이스 및 관리 서버 Cmdlet](lync-server-2013-database-and-management-server-cmdlets.md)**

  -   
    [Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)

  -   
    [Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)

  -   
    [Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

  -   
    [Install-CsDatabase](install-csdatabase.md)

  -   
    [Test-CsDatabase](test-csdatabase.md)

  -   
    [Uninstall-CsDatabase](uninstall-csdatabase.md)

  - [Invoke-CsDatabaseFailover](invoke-csdatabasefailover.md)

  - [Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)

  - [Install-CsMirrorDatabase](install-csmirrordatabase.md)

  - [Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md)

  -   
    [Get-CsUserDatabaseState](get-csuserdatabasestate.md)

  -   
    [Set-CsUserDatabaseState](set-csuserdatabasestate.md)

  -   
    [Update-CsUserDatabase](update-csuserdatabase.md)

  -   
    [Move-CsManagementServer](move-csmanagementserver.md)

  -   
    [Set-CsManagementServer](set-csmanagementserver.md)

  - [Invoke-CsManagementServerFailover](invoke-csmanagementserverfailover.md)

**[에지 서버 Cmdlet](lync-server-2013-edge-server-cmdlets.md)**

  -   
    [Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)

  -   
    [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

  -   
    [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)

  -   
    [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)

  -   
    [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

  -   
    [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

  -   
    [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)

  -   
    [Set-CsEdgeServer](set-csedgeserver.md)

**[기타 서버 역할 Cmdlet](lync-server-2013-other-server-role-cmdlets.md)**

  -   
    [Set-CsConferenceServer](set-csconferenceserver.md)

  -   
    [Set-CsUserServer](set-csuserserver.md)

**[등록자 및 디렉터 Cmdlet](lync-server-2013-registrar-and-director-cmdlets.md)**

  -   
    [Set-CsDirector](set-csdirector.md)

  -   
    [Reset-CsPoolRegistrarState](reset-cspoolregistrarstate.md)

  -   
    [Set-CsRegistrar](set-csregistrar.md)

  -   
    [Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md)

  -   
    [New-CsRegistrarConfiguration](new-csregistrarconfiguration.md)

  -   
    [Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)

  -   
    [Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)

  -   
    [Test-CsRegistration](test-csregistration.md)

**[서비스 Cmdlet](lync-server-2013-services-cmdlets.md)**

  -   
    [Get-CsService](get-csservice.md)

  -   
    [Get-CsWindowsService](get-cswindowsservice.md)

  -   
    [Start-CsWindowsService](start-cswindowsservice.md)

  -   
    [Stop-CsWindowsService](stop-cswindowsservice.md)

**[서버 역할 및 서비스 문제 해결 Cmdlet](lync-server-2013-troubleshooting-server-roles-and-services-cmdlets.md)**

  -   
    [Get-CsAudioTestServiceApplication](get-csaudiotestserviceapplication.md)

  -   
    [Set-CsAudioTestServiceApplication](set-csaudiotestserviceapplication.md)

  -   
    [Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)

  -   
    [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)

  -   
    [Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)

  -   
    [Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)

  -   
    [Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)

  -   
    [New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)

  -   
    [Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)

  -   
    [Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

  -   
    [New-CsDiagnosticsFilter](new-csdiagnosticsfilter.md)

  -   
    [Get-CsDiagnosticHeaderConfiguration](get-csdiagnosticheaderconfiguration.md)

  -   
    [New-CsDiagnosticHeaderConfiguration](new-csdiagnosticheaderconfiguration.md)

  -   
    [Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)

  -   
    [Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)

**[웹 서버 및 서비스 Cmdlet](lync-server-2013-web-server-and-services-cmdlets.md)**

  -   
    [New-CsSimpleUrl](new-cssimpleurl.md)

  -   
    [Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)

  -   
    [New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)

  -   
    [Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)

  -   
    [Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

  -   
    [New-CsSimpleUrlEntry](new-cssimpleurlentry.md)

  -   
    [Set-CsWebServer](set-cswebserver.md)

  -   
    [Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)

  -   
    [New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)

  -   
    [Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)

  -   
    [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

  -   
    [New-CsWebTrustedCACertificate](new-cswebtrustedcacertificate.md)

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

  - [Test-CsWebApp](test-cswebapp.md)

  - [Test-CsWebAppAnonymous](test-cswebappanonymous.md)

## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412)

