---
title: 네트워크 사이트 링크 구성
TOCTitle: 네트워크 사이트 링크 구성
ms:assetid: 7e9147ae-e727-46c8-8c1a-6c13201f09be
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521023(v=OCS.15)
ms:contentKeyID: 49304174
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 사이트 링크 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

CAC(통화 허용 제어) 구성 내에서 직접 연결된 사이트 간의 대역폭 제한을 정의하는 네트워크 사이트 간 정책을 만들 수 있습니다. 네트워크 사이트에서 직접 링크를 공유하는 경우 이 두 사이트 간에 오디오 및 비디오 연결에 대한 대역폭 제한이 정의될 수 있습니다. Lync Server 제어판을 사용해서는 네트워크 사이트 정책을 구성할 수 없으며, 네트워크 사이트 정책은 Lync Server 관리 셸에서 cmdlet을 사용해서만 구성할 수 있습니다. Lync Server 관리 셸에서 네트워크 사이트 링크(네트워크 사이트 간 정책이라고도 함)를 만들고 수정하고 제거할 수 있습니다.

## 네트워크 사이트 링크를 만들려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령 프롬프트에서 다음 명령을 입력하여 구성에 대해 올바른 값으로 대체합니다.
    
        New-CsNetworkInterSitePolicy -Identity Reno_Portland -NetworkSiteID1 Reno -NetworkSiteID2 Portland -BWPolicyProfileID LowBWLimits
    
    이 예제에서는 Reno와 Portland 네트워크 사이트 간 대역폭 제한을 설정하는 Reno\_Portland라는 새 네트워크 사이트 링크를 만듭니다. 네트워크 사이트 및 대역폭 정책 프로필은 이 명령을 실행하기 전에 이미 있어야 합니다.

자세한 매개 변수 설명은 Lync Server 관리 셸 설명서의 [New-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterSitePolicy)를 참조하십시오. 네트워크 사이트 링크에 적용할 수 있는 대역폭 정책 프로필 목록을 검색하려면 **Get-CsNetworkBandwidthPolicyProfile** cmdlet을 호출합니다. 자세한 내용은 Lync Server 관리 셸 설명서의 [Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)을 참조하십시오.

## 네트워크 사이트 링크를 수정하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  **Set-CsNetworkInterSitePolicy** cmdlet을 사용하여 해당 네트워크 사이트 링크의 속성을 수정합니다. 연결된 사이트 중 하나(또는 둘 다)를 수정할 수 있으며 링크와 연결된 대역폭 정책 프로필을 수정할 수 있습니다. 다음은 Reno\_Portland라는 사이트 링크의 대역폭 정책 프로필을 수정하는 예제입니다.
    
        Set-CsNetworkInterSitePolicy -Identity Reno_Portland -BWPolicyProfileID HighBWLimits

자세한 매개 변수 설명은 Lync Server 관리 셸 설명서의 [Set-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterSitePolicy)를 참조하십시오.

## 네트워크 사이트 링크를 삭제하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  **Remove-CsNetworkInterSitePolicy** cmdlet을 사용하여 네트워크 사이트 링크를 제거합니다. 다음 예제에서는 Reno\_Portland 네트워크 사이트 링크를 삭제합니다.
    
        Remove-CsNetworkInterSitePolicy -Identity Reno_Portland

자세한 매개 변수 설명은 Lync Server 관리 셸 설명서의 [Remove-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterSitePolicy)를 참조하십시오.

## 참고 항목

#### 개념

[통화 허용 제어 Cmdlet](lync-server-2013-call-admission-control-cmdlets.md)  

#### 기타 리소스

[New-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterSitePolicy)  
[Set-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterSitePolicy)  
[Remove-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterSitePolicy)  
[Get-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterSitePolicy)  
[Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)

