---
title: 전체 Lync Online 사용자에 대한 정보 반환
TOCTitle: 전체 Lync Online 사용자에 대한 정보 반환
ms:assetid: 0b59fadf-67e6-48ea-86f1-2efef500ebdf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362769(v=OCS.15)
ms:contentKeyID: 56270212
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전체 Lync Online 사용자에 대한 정보 반환

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online을 사용하도록 설정된 모든 사용자에 대한 정보를 반환하려면 매개 변수를 추가하지 않고 [Get-CsOnlineUser](get-csonlineuser.md) cmdlet을 호출합니다.

    Get-CsOnlineUser

임의로 선택된 단일 사용자에 대한 정보를 반환하려면(테스트 목적으로 이 계정을 사용하려는 경우 등) **Get-CsOnlineUser** cmdlet을 호출하고 ResultSize 매개 변수를 1로 설정합니다.

    Get-CsOnlineUser -ResultSize 1

이렇게 하면 조직의 사용자 수와 관계없이 **Get-CsOnlineUser** cmdlet이 한 명의 사용자에 대한 정보만 반환합니다. 다섯 명의 사용자에 대한 정보를 반환하려면 ResultSize 매개 변수의 값을 5로 설정합니다.

    Get-CsOnlineUser -ResultSize 5

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

