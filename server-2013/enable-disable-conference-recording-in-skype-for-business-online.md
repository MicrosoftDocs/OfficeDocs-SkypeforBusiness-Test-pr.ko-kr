---
title: 회의 기록 설정/해제
TOCTitle: 회의 기록 설정/해제
ms:assetid: f6c5afab-081c-495c-97f7-135dcc2f6085
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362857(v=OCS.15)
ms:contentKeyID: 56270316
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 기록 설정/해제

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용자에게 온라인 회의를 기록하는 기능을 제공하지 않으려면 [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) cmdlet을 사용하고 AllowConferenceRecording 매개 변수의 값을 False($False)로 설정합니다.

    Set-CsMeetingConfiguration -AllowConferenceRecording $False

온라인 회의를 기록하는 기능을 복원하려면 AllowConferenceRecording 매개 변수의 값을 True($True)로 설정합니다.

    Set-CsMeetingConfiguration -AllowConferenceRecording $True

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

