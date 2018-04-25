---
title: 주소록 관리용 Get-CsService
TOCTitle: 주소록 관리용 Get-CsService
ms:assetid: 373b717d-5efa-4c36-a899-a23a5bd922b4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429698(v=OCS.15)
ms:contentKeyID: 49303298
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 Get-CsService

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 Get-CsService cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsService"}

Get-CsService는 인프라에서 정의된 웹 서비스의 현재 구성을 검색하고 표시하는 데 유용합니다. 이 cmdlet은 풀의 FQDN(정규화된 도메인 이름) 및 WebServer 매개 변수를 정의하여 서버에서 제공하는 웹 기반 서비스(주소록 처리기 및 메일 그룹 확장 URK 포함)를 반환합니다.

예:

    Get-CsService -PoolFqdn "fe01.contoso.net" -WebServer

이 cmdlet이 반환하는 내용은 다음과 같습니다.

Identity : WebServer:pool01.contoso.net

FileStore : FileStore:dc01.contoso.net

UserServer : UserServer:pool01.contoso.net

PrimaryHttpPort : 80

PrimaryHttpsPort : 443

ExternalHttpPort : 8080

ExternalHttpsPort : 4443

PublishedPrimaryHttpPort : 80

PublishedPrimaryHttpsPort : 443

PublishedExternalHttpPort : 80

PublishedExternalHttpsPort : 443

ReachPrimaryPsomServerPort : 8060

ReachExternalPsomServerPort : 8061

AppSharingPortStart : 49152

AppSharingPortCount : 16383

LIServiceInternalUri : https://internalweb.contoso.net/locationinformation/liservice.svc

ABHandlerInternalUri : https://internalweb.contoso.net/abs/handler

ABHandlerExternalUri : https://csweb.contoso.com/abs/handler

DLExpansionInternalUri : https://internalweb.contoso.net/groupexpansion/service.svc

DLExpansionExternalUri : https://csweb.contoso.com/groupexpansion/service.svc

CAHandlerInternalUri : https://internalweb.contoso.net/CertProv/CertProvisioningService.svc

CAHandlerInternalAnonUri : http://internalweb.contoso.net/CertProv/CertProvisioningService.svc

CollabContentInternalUri : https://internalweb.contoso.net/CollabContent

CollabContentExternalUri : https://csweb.contoso.com/CollabContent

CAHandlerExternalUri : https://csweb.contoso.com/CertProv/CertProvisioningService.svc

DeviceUpdateDownloadInternalUri : https://internalweb.contoso.net/RequestHandler/ucdevice.upx

DeviceUpdateDownloadExternalUri : https://csweb.contoso.com/RequestHandlerExt/ucdevice.upx

DeviceUpdateStoreInternalUri : http://internalweb.contoso.net/RequestHandler/Files

DeviceUpdateStoreExternalUri : https://csweb.contoso.com/RequestHandlerExt/Files

RgsAgentServiceInternalUri : https://internalweb.contoso.net/RgsClients/AgentService.svc

RgsAgentServiceExternalUri : https://csweb.contoso.com/RgsClients/AgentService.svc

MeetExternalUri : https://csweb.contoso.com/Meet

DialinExternalUri : https://csweb.contoso.com/Dialin

CscpInternalUri : https://internalweb.contoso.net/Cscp

ReachExternalUri : https://csweb.contoso.com/Reach

ReachInternalUri : https://internalweb.contoso.net/Reach

WebTicketExternalUri : https://csweb.contoso.com/WebTicket/WebTicketService.svc

WebTicketInternalUri : https://internalweb.contoso.net/WebTicket/WebTicketService.svc

ExternalFqdn : csweb.contoso.com

InternalFqdn : internalweb.contoso.net

DependentServiceList : {Registrar:pool01.contoso.net, ConferencingServer:pool01.contoso.net}

ServiceId : 1-WebServices-1

SiteId : Site:Redmond

PoolFqdn : pool01.contoso.net

Version : 5

Role : WebServer

전체 명령에 대한 자세한 설명은 기본 PowerShell RTCCmdlets 참조에서 다음 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Get-CsService](get-csservice.md)

