---
title: 크로스-프레미스 환경에서 Microsoft Lync Server 2013 구성
TOCTitle: 크로스-프레미스 환경에서 Microsoft Lync Server 2013 구성
ms:assetid: 700639ec-5264-4449-a8a6-d7386fad8719
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204990(v=OCS.15)
ms:contentKeyID: 49303989
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 크로스-프레미스 환경에서 Microsoft Lync Server 2013 구성

 

_**마지막으로 수정된 항목:** 2014-02-05_

프레미스 간 구성에서 일부 사용자는 Microsoft Lync Server 2013의 온-프레미스 설치에 있고 다른 사용자는 Lync Server의 Office 365 버전에 있습니다. 프레미스 간 환경에서 서버 간 인증을 구성하려면 먼저 Office 365 권한 부여 서버를 신뢰할 수 있도록 Lync Server 2013의 온-프레미스 설치를 구성해야 합니다. 이 프로세스의 초기 단계는 다음 Lync Server 관리 셸 스크립트를 실행하여 수행할 수 있습니다.

    $TenantID = (Get-CsTenant -Filter {DisplayName -eq "Fabrikam.com"}).TenantId
    
    $sts = Get-CsOAuthServer microsoft.sts -ErrorAction SilentlyContinue
            
       if ($sts -eq $null)
          {
             New-CsOAuthServer microsoft.sts -MetadataUrl "https://accounts.accesscontrol.windows.net/$TenantId/metadata/json/1"
          }
       else
          {
             if ($sts.MetadataUrl -ne  "https://accounts.accesscontrol.windows.net/$TenantId/metadata/json/1")
                {
                   Remove-CsOAuthServer microsoft.sts
                   New-CsOAuthServer microsoft.sts -MetadataUrl "https://accounts.accesscontrol.windows.net/$TenantId/metadata/json/1"
                }
            }
    
    $exch = Get-CsPartnerApplication microsoft.exchange -ErrorAction SilentlyContinue
            
    if ($exch -eq $null)
       {
          New-CsPartnerApplication -Identity microsoft.exchange -ApplicationIdentifier 00000002-0000-0ff1-ce00-000000000000 -ApplicationTrustLevel Full -UseOAuthServer
        }
    else
        {
           if ($exch.ApplicationIdentifier -ne "00000002-0000-0ff1-ce00-000000000000")
              {
                 Remove-CsPartnerApplication microsoft.exchange
                 New-CsPartnerApplication -Identity microsoft.exchange -ApplicationIdentifier 00000002-0000-0ff1-ce00-000000000000 -ApplicationTrustLevel Full -UseOAuthServer 
              }
           else
              {
                 Set-CsPartnerApplication -Identity microsoft.exchange -ApplicationTrustLevel Full -UseOAuthServer
              }
       }
    
    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000

테넌트의 영역 이름은 일반적으로 조직 이름과 다릅니다. 하지만 실제로 영역 이름은 거의 항상 테넌트 ID와 동일합니다. 이러한 이유로 인해 스크립트의 첫 번째 줄은 지정된 테넌트(이 예의 경우 fabrikam.com)에 대한 TenantId 속성의 값을 반환하고 해당 이름을 $TenantId 변수에 지정하는 데 사용됩니다.

    $TenantID = (Get-CsTenant -DisplayName "Fabrikam.com").TenantId

스크립트가 완료된 후에는 Lync Server 2013 및 권한 부여 서버 사이의 트러스트 관계와 Exchange 2013 및 권한 부여 서버 간의 보조 트러스트 관계를 구성해야 합니다. 이 작업은 Microsoft Online Services cmdlet을 사용해서만 수행할 수 있습니다.


> [!NOTE]
> Microsoft Online Services cmdlet을 설치하지 않은 경우 계속하기 전에 두 가지 작업을 수행해야 합니다. 우선 Microsoft Online Services 로그인 도우미의 64비트 버전을 다운로드하고 설치해야 합니다. 설치가 완료되면 Windows PowerShell에 대한 Microsoft Online Services 모듈의 64비트 버전을 다운로드하고 설치해야 합니다. Microsoft Online Services 모듈 설치 및 사용에 대한 자세한 정보는 Office 365 웹 사이트에서 찾을 수 있습니다. 이러한 지침에서는 Office 365 및 Active Directory 간의 단일 로그인 구성, 페더레이션 및 동기화 방법을 설명합니다.<BR>이러한 cmdlet을 설치하지 않았을 경우 Get-CsTenant cmdlet을 사용할 수 없어 스크립트가 실패합니다.



Office 365를 구성하고 Lync Server 2013 및 Exchange 2013에 대한 Office 365 서비스 계정을 만든 후에는 이러한 서비스 계정을 사용해서 자격 증명을 등록해야 합니다. 이렇게 하려면 먼저 .CER 파일로 저장된 X.509 Base64를 구해야 합니다. 이 인증서는 Office 365 서비스 계정에 적용됩니다.

X.509 인증서를 구했으면 Microsoft Online Services 모듈을 시작합니다(**시작**, **모든 프로그램**, **Microsoft Online Services**를 차례로 클릭한 후 **Windows PowerShell에 대한 Microsoft Online 서비스 모듈**을 차례로 클릭). 서비스 모듈이 열리면 다음을 입력하여 서비스 계정을 관리하는 데 사용할 수 있는 cmdlet이 포함된 Microsoft Online Windows PowerShell 모듈을 가져올 수 있습니다.

    Import-Module MSOnlineExtended

모듈을 가져왔으면 Office 365에 연결하기 위해 다음 명령을 입력하고 Enter 키를 누릅니다.

    Connect-MsolService

Enter를 누르면 자격 증명 대화 상자가 표시됩니다. 대화 상자에 Office 365 사용자 이름 및 암호를 입력한 후 확인을 클릭합니다.

Office 365에 연결되는 즉시 서비스 계정에 대한 정보를 반환하기 위해 다음 명령을 실행할 수 있습니다.

    Get-MsolServicePrincipal

모든 서비스 계정에 대해 이와 비슷한 정보를 얻으려면

    ExtensionData        : System.Runtime.Serialization.ExtensionDataObject
    AccountEnabled       : True
    Addresses            : {}
    AppPrincipalId       : 00000004-0000-0ff1-ce00-000000000000
    DisplayName          : Microsoft Lync Server
    ObjectId             : aada5fbd-c0ae-442a-8c0b-36fec40602e2
    ServicePrincipalName : LyncServer/litwareinc.com
    TrustedForDelegation : True

다음 단계에서는 X.509 인증서를 가져오고, 인코딩하고, 지정합니다. 인증서를 가져오고 암호화하려면 다음 Windows PowerShell 명령을 사용하고 가져오기 메서드를 호출할 때 .CER 파일에 대한 전체 파일 경로를 지정합니다.

    $certificate = New-Object System.Security.Cryptography.X509Certificates.X509Certificate
    $certificate.Import("C:\Certificates\Office365.cer")
    $binaryValue = $certificate.GetRawCertData()
    $credentialsValue = [System.Convert]::ToBase64String($binaryValue)

인증서를 가져오고 인코딩한 후에는 Office 365 서비스 계정에 인증서를 지정할 수 있습니다. 이를 위해서는 먼저 Get-MsolServicePrincipal을 사용해서 Lync Server 및 Microsoft Exchange 서비스 계정 모두에 대해 AppPrincipalId 속성의 값을 검색합니다. AppPrincipalId 속성의 값은 인증서에 지정 중인 서비스 계정을 식별하는 데 사용됩니다. 현재 Lync Server 2013에 대한 AppPrincipalId 속성 값을 사용해서 다음 명령을 사용하여 인증서를 Lync Server의 Office 365 버전에 인증서를 지정합니다(StartDate 및 EndDate 속성은 인증서의 유효성 검사 기간에 따라 달라져야 합니다.

    New-MsolServicePrincipalCredential -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -Type Asymmetric -Usage Verify -Value $credentialsValue -StartDate 6/1/2012 -EndDate 5/31/2013

그런 후 명령을 반복하되 이번에는 Exchange 2013에 대해 AppPrincipalId 속성 값을 사용합니다.

해당 인증서를 나중에 삭제해야 할 때는 먼저 인증서의KeyID를 검색하여 작업을 수행할 수 있습니다.

    Get-MsolServicePrincipalCredential -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000

이 명령은 다음과 비슷한 데이터를 반환합니다.

    Type      : Asymmetric
    Value     : 
    KeyId     : bc2795f3-2387-4543-a95d-f92c85c7a1b0
    StartDate : 6/1/2012 8:00:00 AM
    EndDate   : 5/31/2013 8:00:00 AM
    Usage     : Verify

그런 후 다음과 비슷한 명령을 사용하여 인증서를 삭제할 수 있습니다.

    Remove-MsolServicePrincipalCredential -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -KeyId bc2795f3-2387-4543-a95d-f92c85c7a1b0

인증서를 지정하는 것 외에도 Exchange 온라인 서비스 계정을 구성하고 Lync Server 2013의 온-프레미스 버전을 Office 365 서비스 계정으로 구성해야 합니다. 이 작업은 다음 두 가지 명령을 실행하여 수행할 수 있습니다.

    Set-MSOLServicePrincipal -AppPrincipalID 00000002-0000-0ff1-ce00-000000000000 -AccountEnabled $true
    
    $lyncSP = Get-MSOLServicePrincipal -AppPrincipalID 00000004-0000-0ff1-ce00-000000000000
    $lyncSP.ServicePrincipalNames.Add("00000004-0000-0ff1-ce00-000000000000/lync.contoso.com")
    Set-MSOLServicePrincipal -AppPrincipalID 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $lyncSP.ServicePrincipalNames

