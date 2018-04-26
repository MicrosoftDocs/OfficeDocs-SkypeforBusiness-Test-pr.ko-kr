---
title: Lync Online 테넌트에 대한 정보 가져오기
TOCTitle: Lync Online 테넌트에 대한 정보 가져오기
ms:assetid: 06467515-9114-45bb-8d09-26a915c3fc4d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362768(v=OCS.15)
ms:contentKeyID: 56270211
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online 테넌트에 대한 정보 가져오기

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online 테넌트에 대한 정보를 반환하려면 매개 변수를 추가하지 않고 [Get-CsTenant](get-cstenant.md) cmdlet을 호출합니다.

    Get-CsTenant

테넌트 이름과 ID(TenantID 매개 변수 값은 [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) 및 [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) 등의 cmdlet을 실행할 때 필요함)만 반환하려면 다음 명령을 사용합니다.

    Get-CsTenant | Select-Object Name, TenantID

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

