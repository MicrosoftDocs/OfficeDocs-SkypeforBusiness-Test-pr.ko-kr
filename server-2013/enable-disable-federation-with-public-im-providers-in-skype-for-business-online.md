---
title: 공용 메신저 공급자와 페더레이션 설정/해제
TOCTitle: 공용 메신저 공급자와 페더레이션 설정/해제
ms:assetid: 8609682c-97d3-48e6-a243-d84c1f9c8419
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362809(v=OCS.15)
ms:contentKeyID: 56270274
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 공용 메신저 공급자와 페더레이션 설정/해제

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용자가 공용 메신저(메신저) 공급자의 계정이 있는 다른 사용자와 통신할 수 있도록 하려면 [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet을 사용하고 AllowPublicUsers 속성을 True($True)로 설정합니다.

    Set-CsTenantFederationConfiguration -AllowPublicUsers $True

그런 다음 [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) cmdlet을 사용해 통신을 허용할 공용 메신저 공급자를 지정해야 합니다.

공용 공급자와의 페더레이션을 해제하려면 AllowPublicUsers 속성을 다시 False($False)로 설정합니다.

    Set-CsTenantFederationConfiguration -AllowPublicUsers $False

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

