---
title: 장치 업데이트 구성 설정 모음 삭제
TOCTitle: 장치 업데이트 구성 설정 모음 삭제
ms:assetid: 1a649136-34a9-42a7-a5b3-a78bbfe93f36
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994019(v=OCS.15)
ms:contentKeyID: 52056796
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치 업데이트 구성 설정 모음 삭제

 

_**마지막으로 수정된 항목:** 2013-02-20_

Windows PowerShell 및 **Remove-CsdeviceUpdateConfiguration** cmdlet을 사용하여 장치 업데이트 구성 설정을 삭제할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.


## 장치 업데이트 구성 설정의 특정 컬렉션을 제거하려면

  - 다음 명령은 Redmond 사이트에 적용된 장치 업데이트 구성 설정을 삭제합니다.
    
        Remove-CsDeviceUpdateConfiguration -Identity "site:Redmond"

## 사이트 범위에 적용된 모든 장치 업데이트 구성 설정을 제거하려면

  - 다음 명령은 사이트 범위에 적용된 모든 장치 업데이트 구성 설정을 삭제합니다.
    
        Get-CsDeviceUpdateConfiguration -Filter "site:*" | Remove-CsDeviceUpdateConfiguration

## LogCleanUpInterval 속성의 값에 따라 장치 업데이트 구성 설정을 제거하려면

  - 다음 명령은 로그 정리 간격이 10일(10.00:00:00)보다 긴 모든 장치 업데이트 구성 설정을 삭제합니다.
    
        Get-CsDeviceUpdateConfiguration | Where-Object {$_.LogCleanUpInterval -gt "10.00:00:00" | Remove-CsDeviceUpdateConfiguration

자세한 내용은 [Remove-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsDeviceUpdateConfiguration) cmdlet의 도움말 항목을 참조하십시오.

