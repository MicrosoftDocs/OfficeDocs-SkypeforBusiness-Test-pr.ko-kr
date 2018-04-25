---
title: 사용자에게 오디오 회의 공급자 할당
TOCTitle: 사용자에게 오디오 회의 공급자 할당
ms:assetid: 60db6896-9c5c-4d64-ab7e-10d91748587c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362791(v=OCS.15)
ms:contentKeyID: 56270239
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자에게 오디오 회의 공급자 할당

 

_**마지막으로 수정된 항목:** 2015-06-22_

[Set-CsUserAcp](set-csuseracp.md) cmdlet에서는 사용자에게 오디오 회의 공급자를 할당할 수 있습니다.

    Set-CsUserAcp -Identity "Ken Myer" -TollNumber "12065551219" -TollFreeNumbers "18005550712" -ParticipantPasscode "p@ssw0rd" -Domain "sip.contoso.com" -Name "Contoso ACP"

지정된 공급자와 계약을 맺지 않은 경우 이러한 할당은 의미가 없습니다.

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

