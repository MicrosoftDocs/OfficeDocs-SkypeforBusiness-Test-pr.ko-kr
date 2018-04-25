---
title: 현재 상태 사용자 지정 개인 정보 모드 구성
TOCTitle: 현재 상태 사용자 지정 개인 정보 모드 구성
ms:assetid: e7a6b873-486d-4dfb-a967-c48f61f237f3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399028(v=OCS.15)
ms:contentKeyID: 49305364
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 현재 상태 사용자 지정 개인 정보 모드 구성

 

_**마지막으로 수정된 항목:** 2014-12-08_

현재 상태 사용자 지정 개인 정보 보호 모드를 통해 사용자는 현재 상태 정보를 제한하여 Lync 2013 대화 상대 목록에 나열된 대화 상대에게만 현재 상태 정보를 표시할 수 있습니다. **New-CsPrivacyConfiguration** 및 **Set-CsPrivacyConfiguration** cmdlet에는 이 옵션을 제어하는 EnablePrivacyMode 매개 변수가 있습니다. EnablePrivacyMode가 True로 설정된 경우 Lync 2013 상태 옵션에 대화 상대로 현재 상태 정보를 제한하는 옵션이 제공됩니다. EnablePrivacyMode가 False로 설정된 경우에는 사용자가 자신의 현재 상태 정보를 항상 모든 사람이 볼 수 있도록 선택하거나 관리자가 개인 정보 보호 모드에 대해 이후에 변경한 내용을 준수하도록 선택할 수 있습니다.


> [!IMPORTANT]
> 이전 버전(Microsoft Office Communicator 2007 R2 또는 Microsoft Office Communicator 2007)에는 Lync 2013 및 Lync 2010 개인 정보 보호 설정이 적용되지 않습니다. 이전 버전의 Office Communicator에 로그인할 수 있는 경우 보기 권한이 없는 사용자가 Lync 2013 사용자의 상태, 대화 상대 정보나 사진 등을 볼 수 있습니다. 또한 이 사용자가 나중에 이전 버전의 Communicator에 로그인하면 Lync 2013 사용자의 개인 정보 보호 설정이 재설정됩니다.<BR>이러한 이유로 마이그레이션 시나리오에서 현재 상태 사용자 지정 개인 정보 보호 모드를 사용하도록 설정하기 전에 다음을 수행해야 합니다. 
> <UL>
> <LI>
> <P>모든 사용자가 Lync 2013을 설치했는지 확인합니다.</P>
> <LI>
> <P>이전 버전의 Communicator에서 로그인을 수행하지 못하도록 클라이언트 버전 정책 규칙을 정의합니다.</P></LI></UL>



## 현재 상태 사용자 지정 개인 정보 보호 모드를 사용하도록 설정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음 명령을 실행합니다.
    
        Get-CsPrivacyConfiguration | Set-CsPrivacyConfiguration -EnablePrivacyMode $True
    
    이 명령은 조직에서 현재 사용되고 있는 모든 개인 정보 보호 구성 설정에 대해 개인 정보 보호 모드를 사용하도록 설정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)  
[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

