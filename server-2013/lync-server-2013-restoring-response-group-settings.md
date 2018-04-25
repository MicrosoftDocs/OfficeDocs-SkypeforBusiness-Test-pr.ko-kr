---
title: 응답 그룹 설정 복원
TOCTitle: 응답 그룹 설정 복원
ms:assetid: 4f8e1949-925d-4538-be1d-9ac7c06b2aca
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202174(v=OCS.15)
ms:contentKeyID: 52056850
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 응답 그룹 설정 복원

 

_**마지막으로 수정된 항목:** 2013-02-18_

응답 그룹 응용 프로그램을 배포했고 백 엔드 서버 또는 Standard Edition 서버를 복원해야 하는 경우 응답 그룹 구성 설정도 복원해야 합니다.

## 응답 그룹 구성 설정을 복원하려면

1.  명령줄에 다음을 입력합니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<pool FQDN>" -OverwriteOwner -FileName "<path and file name of the backed up file at $Backup>"
    
    예:
    
        Import-CsRgsConfiguration -Destination "service: ApplicationServer:pool01.contoso.com" -OverwriteOwner -FileName "C:\RgsConfiguration.zip"

