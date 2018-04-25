---
title: 잘못된 Windows PowerShell 버전으로 인해 발생한 Import-Module 오류
TOCTitle: 잘못된 Windows PowerShell 버전으로 인해 발생한 Import-Module 오류
ms:assetid: 6c209f41-2b97-4dda-b0b7-e5b582d3e6b6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362802(v=OCS.15)
ms:contentKeyID: 56270252
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 잘못된 Windows PowerShell 버전으로 인해 발생한 Import-Module 오류

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online 커넥터 모듈은 Windows PowerShell 3.0에서만 실행할 수 있습니다. 이전 버전의 Windows PowerShell에서 모듈을 가져오려는 경우, 가져오기 프로세스는 실패하며 다음과 유사한 오류 메시지가 나타납니다.

    Import-Module : 로드된 PowerShell의 버전이 '2.0'입니다. 'D:\Program Files\Common Files\Microsoft Lync Server 2013\Modules\LyncOnlineConnector\LyncOnlineConnector.psd1' 모듈을 실행하려면 최소한 PowerShell 버전 '3.0'이(가) 필요합니다. PowerShell 설치를 확인한 다음 다시 시도하십시오.

이 문제를 해결하는 유일한 방법은 Windows PowerShell 3.0을 설치하는 것입니다. Microsoft 다운로드 센터(<http://www.microsoft.com/en-us/download/details.aspx?id=29939>)에서 다운로드할 수 있습니다.

## 참고 항목

#### 개념

[Lync Online의 연결 문제 진단 및 해결](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

