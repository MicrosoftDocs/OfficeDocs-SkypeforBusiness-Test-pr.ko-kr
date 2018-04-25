---
title: 허용 도메인 목록에서 도메인 제거
TOCTitle: 허용 도메인 목록에서 도메인 제거
ms:assetid: 04948582-363b-49bd-8305-166c4c1d0dd9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362766(v=OCS.15)
ms:contentKeyID: 56270208
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 허용 도메인 목록에서 도메인 제거

 

_**마지막으로 수정된 항목:** 2015-06-22_

허용 도메인 목록에서 도메인을 제거하려면 일련의 단계를 수행해야 합니다. 먼저 현재 목록에 있는 모든 도메인의 컬렉션을 검색하려면 다음과 비슷한 명령을 사용해야 합니다.

    $x = (Get-CsTenantFederationConfiguration).AllowedDomains

다음으로 이 명령을 실행하여 검색한 도메인을 검토합니다.

``` 
$x
```

제거할 도메인의 숫자 위치를 메모해 둡니다. 해당 도메인이 목록의 첫 번째 도메인인 경우 인덱스 값은 0입니다. 해당 도메인이 목록의 두 번째 도메인인 경우 인덱스 값은 1이고 나머지도 이와 마찬가지입니다.

인덱스 번호를 확인한 후에는 다음과 같은 명령을 사용하여 지정한 도메인을 제거할 수 있는데, 이 때 올바른 인덱스 번호를 사용해야 합니다. 다음 명령은 목록의 첫 번째 도메인(인덱스 번호 0)을 제거합니다.

    $x.AllowedDomain.RemoveAt(0)

마지막으로 [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet을 호출하여 변경 내용을 비즈니스용 Skype Online에 기록합니다.

    Set-CsTenantFederationConfiguration -AllowedDomains $x

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

