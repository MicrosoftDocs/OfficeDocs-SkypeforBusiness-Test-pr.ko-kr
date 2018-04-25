---
title: 오디오 회의 공급자에 대한 정보 반환
TOCTitle: 오디오 회의 공급자에 대한 정보 반환
ms:assetid: df9c8fc0-8bb6-4416-a5cc-aa9b1601a688
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362848(v=OCS.15)
ms:contentKeyID: 56270304
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 오디오 회의 공급자에 대한 정보 반환

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용자에게 할당된 오디오 회의 공급자에 대한 정보를 반환하려면 [Get-CsUserAcp](get-csuseracp.md) cmdlet과 다음 구문을 사용합니다.

    Get-CsUserAcp -Identity "Ken Myer" | Select-Object -ExpandProperty AcpInfo

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

