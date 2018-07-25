---
title: 웹 회의 요구 사항
TOCTitle: 웹 회의 요구 사항
ms:assetid: 125f847c-58ab-450f-ae43-41219fd38477
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619171(v=OCS.15)
ms:contentKeyID: 49302868
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 웹 회의 요구 사항

 

_**마지막으로 수정된 항목:** 2013-01-30_

웹 회의를 사용하도록 설정한 경우에는 다음 사항을 계획해야 합니다.

   웹 회의 콘텐츠를 저장하는 데 사용되는 파일 저장소 액세스

   회의 중에 PowerPoint 파일을 공유하는 데 필요한 Office Web Apps 서버와의 통합

## 파일 저장소

Lync Server 2013 웹 회의 서비스는 모임 중에 공유되는 콘텐츠를 파일 저장소에 저장합니다. 배포의 일부분으로 Standard Edition 서버 또는 Enterprise Edition프런트 엔드 풀에 대해 파일 저장소로 사용할 파일 공유를 지정해야 합니다. 기존 파일 공유를 파일 저장소로 사용하거나 파일 공유가 위치할 파일 서버의 FQDN(정규화된 도메인 이름) 및 새 파일 공유의 폴더 이름을 지정하여 새 파일 공유를 지정할 수 있습니다. 자세한 내용은 토폴로지 작성기 - 프런트 엔드에 대해 파일 저장소 정의를 참조하십시오. 웹 회의 서비스는 콘텐츠를 파일 저장소에 저장하기 전에 암호화합니다.

Lync Server 2013에서는 파일 저장소에 대해 RAID(Redundant Array of Independent Disks), DFS(분산 파일 시스템)를 비롯한 DAS(직접 연결된 저장소) 또는 SAN(저장 영역 네트워크)에서 파일 공유를 사용할 수 있습니다. Lync Server 배포 마법사에서 파일 공유 위치를 정의하고 나면 Lync Server에서 파일 공유 내에 다음과 같은 폴더 구조를 만듭니다.

  - 1-ApplicationServer-1

  - 1-CentralMgmt-1

  - 1-WebServices-1
    
      - CollabContent
    
      - CollabMetadata
    
      - DataConf

그러면 웹 회의 서비스에서 PowerPoint 슬라이드, 화이트보드, 설문 조사, 첨부 파일 등의 콘텐츠를 WebServices 폴더에 있는 CollabContent 및 CollabMetadata 폴더에 저장합니다.

관리자는 RTC 그룹이 필요한 읽기 및 쓰기 권한을 가지도록 파일 공유에 대한 사용 권한을 설정해야 합니다.


> [!WARNING]
> 사용 권한과 관련한 오류가 발생하는 경우 토폴로지 작성기를 열고 기존 토폴로지를 다운로드해 다시 게시합니다. 토폴로지를 게시하면 파일 공유 사용 권한이 확인되고 필요한 경우 다시 설정됩니다.



다음 설정을 사용하여 모임에 대해 콘텐츠가 저장되는 방법을 관리할 수 있습니다.

  - [Set-CsConferencingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsConferencingConfiguration)에 있는 **ContentGracePeriod**는 모임 종료 후 웹 회의 콘텐츠가 서버에 남아 있는 기간을 설정합니다.

  - [Set-CsConferencingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsConferencingConfiguration)에 있는 **MaxContentStorageMb**는 단일 모임 중 콘텐츠 저장을 위해 허용되는 최대 파일 공간의 양을 설정합니다.

**MaxUploadFileSizeMb**는 Lync Web App의 파일 업로드 설정을 제한하지는 않습니다. Lync Web App의 파일 크기 업로드 제한은 약 30MB로 설정되며 IIS web.config 파일(/DataCollabWeb/Int\[Ext\]/Handler/web.config)을 통해 제어됩니다. Lync Web App에 대해 파일 크기 업로드 제한을 구성하려면 다음과 같이 web.config 파일에서 `maxRequestLength` 및 `maxAllowedContentLength`를 업데이트합니다.

    <system.web>
        <!-- 
            Since this handler is used to upload files to DMCU the request size (in kilobytes) 
            has to fit max allowed file size uploaded by Lync Web App client.
            The timeout has to reflect the min client bandwidth. Timeout of 600 secs 
            and 512 Kbits of *client* bandwidth would result into aproximately 30 Mbytes 
            for Lync Web App upload size limit.
        -->
          <httpRuntime maxRequestLength="500000" executionTimeout="600" />
    
    
    
                    <security>
                    <requestFiltering>
                               <requestLimits maxAllowedContentLength="524288000" />
                    </requestFiltering>
                    </security>

각 프런트 엔드 서버에 대해 web.config 파일을 업데이트해야 합니다.

## Office Web Apps 서버

이러한 새 기능을 사용하려면 관리자는 Office Web Apps 서버를 설치해야 하며 Lync Server 2013이 Office Web Apps 서버와 통신하도록 구성해야 합니다. 이 설명서에서는 Office Web Apps 서버와 함께 작동하도록 Lync Server 2013을 구성하는 방법에 대한 정보를 제공합니다. 그러나 Office Web Apps 서버 설치 방법에 대한 정보는 제공하지 않습니다. 설치 세부 정보는 Microsoft Office Web App 배포 웹 사이트(<http://go.microsoft.com/fwlink/?linkid=257525>)를 참조하십시오. 해당 가이드에 Office Web Apps 서버의 전체 필수 구성 요소 정보가 포함되어 있습니다. Office Web Apps 서버는 Lync Server, SQL Server 또는 기타 서버 응용 프로그램을 실행하고 있지 않은 독립 실행형 컴퓨터에 설치해야 합니다. 즉, 해당 컴퓨터에 어떤 버전의 Office도 설치되어 있어서는 안 됩니다. Office Web Apps 서버를 실행하는 데 사용되는 컴퓨터에는 .NET Framework 4.5 및 Windows PowerShell 3.0을 비롯한 특정 소프트웨어 집합도 설치되어 있어야 합니다. 이러한 요구 사항 및 인증서와 IIS(인터넷 정보 서비스)를 구성하는 방법에 대한 정보는 Microsoft Office Web App 배포 웹 사이트(<http://go.microsoft.com/fwlink/?linkid=257525>)에 자세하게 설명되어 있습니다.

## 참고 항목

#### 개념

[Lync Server 2013의 웹 회의 개요](lync-server-2013-web-conferencing-overview.md)  
[Lync Server 2013의 웹 회의를 위한 배포 검사 목록](lync-server-2013-deployment-checklist-for-web-conferencing.md)

