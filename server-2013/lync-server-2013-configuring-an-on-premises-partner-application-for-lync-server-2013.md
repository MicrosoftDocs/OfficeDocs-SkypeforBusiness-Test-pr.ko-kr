---
title: Microsoft Lync Server 2013에 대한 온-프레미스 파트너 응용 프로그램 구성
TOCTitle: Microsoft Lync Server 2013에 대한 온-프레미스 파트너 응용 프로그램 구성
ms:assetid: 696f2b26-e5d0-42b5-9785-a26c2ce25bb7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204975(v=OCS.15)
ms:contentKeyID: 49303914
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Server 2013에 대한 온-프레미스 파트너 응용 프로그램 구성

 

_**마지막으로 수정된 항목:** 2013-02-04_

OAuthTokenIssuer 인증서를 지정한 후에는 Microsoft Lync Server 2013 파트너 응용 프로그램을 구성해야 합니다. (여기에서 설명할 절차에서는 Microsoft Exchange Server 2013 및 Microsoft SharePoint 모두 파트너 응용 프로그램으로 작동하도록 구성합니다.) 온-프레미스 파트너 응용 프로그램을 구성하려면 먼저 다음 Windows PowerShell 스크립트를 복사해서 코드를 메모장(또는 다른 텍스트 편집기)에 붙여 넣어야 합니다.

    if ((Get-CsPartnerApplication -ErrorAction SilentlyContinue) -ne $Null)
       {
           Remove-CsPartnerApplication app
       }
    
    $exch = Get-CsPartnerApplication microsoft.exchange -ErrorAction SilentlyContinue
            
    if ($exch -eq $null)
       {
          New-CsPartnerApplication -Identity microsoft.exchange -MetadataUrl https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 -ApplicationTrustLevel Full 
        }
    else
        {
           if ($exch.ApplicationIdentifier -ne "00000002-0000-0ff1-ce00-000000000000")
              {
                 Remove-CsPartnerApplication microsoft.exchange
    New-CsPartnerApplication -Identity microsoft.exchange -MetadataUrl https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 -ApplicationTrustLevel Full 
               }
            else
               {
                 Set-CsPartnerApplication -Identity microsoft.exchange -ApplicationTrustLevel Full 
               }
         }
    
    $shp = Get-CsPartnerApplication microsoft.sharepoint -ErrorAction SilentlyContinue
            
    if ($shp -eq $null)
       {
          New-CsPartnerApplication -Identity microsoft.sharepoint -MetadataUrl http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx -ApplicationTrustLevel Full 
        }
    else
        {
           if ($shp.ApplicationIdentifier -ne "00000003-0000-0ff1-ce00-000000000000")
              {
                 Remove-CsPartnerApplication microsoft.sharepoint
      
                 New-CsPartnerApplication -Identity microsoft.sharepoint -MetadataUrl http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx -ApplicationTrustLevel Full 
               }
            else
               {
                 Set-CsPartnerApplication -Identity microsoft.sharepoint -ApplicationTrustLevel Full 
                }
       }
    
    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000

코드를 복사한 후에는 파일 확장명으로 .PS1을 사용해서 스크립트를 저장합니다(예: C:\\Scripts\\ServerToServerAuth.ps1). 이 스크립트를 실행하기 전에 메타데이터 URL https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 및 http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx를 각각 Exchange 2013 및 SharePoint 서버에서 사용되는 메타데이터 URL로 바꿔야 합니다. 각 제품의 메타데이터 URL을 식별할 수 있는 방법에 대한 자세한 내용은 Exchange 2013 및 SharePoint에 대한 제품 설명서를 참조하십시오.

스크립트의 마지막 줄을 보면 다음 구문을 사용해서 Set-CsOAuthConfiguration cmdlet이 호출되었음을 알 수 있습니다.

    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000

Set-CsOAuthConfiguration을 호출할 때 Realm 매개 변수는 사용되지 않았기 때문에 이 영역은 조직의 FQDN(정규화된 도메인 이름)으로 자동으로 설정됩니다(예: litwareinc.com). 영역 이름이 조직 이름과 다른 경우에는 다음과 같이 영역 이름을 포함해야 합니다.

    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000 -Realm "contoso.com"

이러한 항목을 변경할 때는 Lync Server 2013 관리 셸 내에서 스크립트 파일을 실행하여 스크립트를 실행하고, Exchange 2013 및 SharePoint를 모두 파트너 응용 프로그램으로 구성할 수 있습니다. 예:

    C:\Scripts\ServerToServerAuth.ps1

이 스크립트는 Exchange 2013 및 SharePoint Server가 모두 설치되지 않았어도 실행할 수 있습니다. SharePoint Server가 설치되지 않았어도 SharePoint Server를 파트너 응용 프로그램으로 구성해도 아무 문제가 발생하지 않습니다.

이 스크립트를 실행할 때는 다음과 비슷한 오류 메시지가 표시될 수 있습니다.

    New-CsPartnerApplication : Cannot bind parameter 'MetadataUrl' to the target. Exception setting "MetadataUrl": "The metadata document could not be downloaded from the URL in the MetadataUrl parameter or downloaded data is not a valid metadata document."

이 오류 메시지는 일반적으로 두 가지 의미를 갖습니다. 1) 스크립트에 지정된 URL 중 하나가 올바르지 않습니다(즉, 메타데이터 URL 중 하나가 실제 메타데이터 URL이 아님). 2) 메타데이터 URL 중 하나에 연결할 수 없습니다. 이 경우에는 URL이 올바르고 액세스할 수 있는지 확인한 후 스크립트를 다시 실행합니다.

Lync Server 2013에 대한 파트너 응용 프로그램을 만든 후에는 Exchange 2013에 대한 파트너 응용 프로그램으로 Lync Server를 구성해야 합니다. Exchange 2013에 대한 파트너 응용 프로그램은 Configure-EnterprisePartnerApplication.1 스크립트를 실행하여 구성할 수 있습니다. 필요한 작업은 Lync Server에 대한 메타데이터 URL을 지정하고 Lync Server를 새로운 파트너 응용 프로그램으로 표시하는 것입니다.

Lync Server를 Exchange에 대한 파트너 응용 프로그램으로 구성하려면 Exchange 관리 셸을 열고 다음과 비슷한 명령을 실행합니다.

    "c:\Program Files\Microsoft\Exchange Server\V15\Scripts\Configure-EnterprisePartnerApplication.ps1" -AuthMetadataUrl "https://lync.contoso.com/metadata/json/1" -ApplicationType "Lync"

