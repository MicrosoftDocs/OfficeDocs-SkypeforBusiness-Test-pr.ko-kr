---
title: 회의 공급자 ID를 사용하는 cmdlet
TOCTitle: 회의 공급자 ID를 사용하는 cmdlet
ms:assetid: be5621b6-ec11-4b12-83ec-075af269ca6a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362841(v=OCS.15)
ms:contentKeyID: 56270294
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 회의 공급자 ID를 사용하는 cmdlet

 

_**마지막으로 수정된 항목:** 2015-06-22_

조직이 계약을 맺은 모든 오디오 회의 공급자에 대한 정보를 반환하려는 경우, 매개 변수 없이 [Get-CsAudioConferencingProvider](get-csaudioconferencingprovider.md) cmdlet만 호출하면 됩니다.

    Get-CsAudioConferencingProvider

반환된 데이터를 하나의 공급자(이 예제의 경우 Contoso Audio Services 공급자)로 제한하려면 Identity 매개 변수를 사용합니다.

    Get-CsAudioConferencingProvider -Identity "Contoso Audio Services"

오디오 회의 공급자 ID를 허용하는 비즈니스용 Skype Online cmdlet은 단 하나뿐입니다.

  - [Get-CsAudioConferencingProvider](get-csaudioconferencingprovider.md)

## 참고 항목

#### 개념

[ID, 범위, 테넌트](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)

