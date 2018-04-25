---
title: 특정 사용자에 대한 특정 정보 반환
TOCTitle: 특정 사용자에 대한 특정 정보 반환
ms:assetid: bbee85bd-d8a7-4b28-90d7-45c43eee48f6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362838(v=OCS.15)
ms:contentKeyID: 56270292
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 특정 사용자에 대한 특정 정보 반환

 

_**마지막으로 수정된 항목:** 2015-06-22_

기본적으로 [Get-CsOnlineUser](get-csonlineuser.md) cmdlet은 각 비즈니스용 Skype Online 사용자 계정에 대한 많은 양의 정보를 반환합니다. 해당 정보의 하위 집합에만 관심이 있는 경우 반환된 데이터를 **Select-Object** cmdlet으로 파이프합니다. 예를 들어 다음 명령은 Ken Myer라는 사용자에 대한 모든 데이터를 반환한 후 **Select-Object** cmdle을 사용하여 화면에 표시되는 정보를 Ken의 Active Directory 도메인 서비스 표시 이름과 다이얼 플랜으로 제한합니다.

    Get-CsOnlineUser -Identity "Ken Myer" | Select-Object DisplayName, DialPlan

다음 명령은 모든 사용자의 표시 이름과 다이얼 플랜을 반환합니다.

    Get-CsOnlineUser | Select-Object DisplayName, DialPlan

비즈니스용 Skype Online 사용자 계정의 속성을 찾으려면 다음 명령을 사용합니다.

    Get-CsOnlineUser | Get-Member

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

