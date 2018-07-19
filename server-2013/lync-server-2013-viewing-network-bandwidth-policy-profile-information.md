---
title: 네트워크 대역폭 정책 프로필 정보 보기
TOCTitle: 네트워크 대역폭 정책 프로필 정보 보기
ms:assetid: eed453fc-04e9-4971-959c-6fad54bf1c96
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721931(v=OCS.15)
ms:contentKeyID: 49886050
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 대역폭 정책 프로필 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

대역폭 정책은 CAC(통화 허용 제어 서비스)의 일부로 특정 형식에 대한 대역폭 제한을 정의하는 데 사용됩니다. Microsoft Lync Server 2013에서는 오디오 및 비디오 형식에만 대역폭 제한이 할당될 수 있습니다. 전체 대역폭 제한 및 세션 제한을 설정할 수 있습니다. Lync Server 제어판을 사용하여 이러한 정책에 대해 컨테이너 프로필을 만들거나 수정 또는 삭제할 수 있습니다. 각 대역폭 정책 프로필은 하나 이상의 네트워크 사이트에 연결할 수 있습니다. 대역폭 정책 프로필을 만들거나 수정하려면 [대역폭 정책 프로필 만들기 또는 수정](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md)을 참조하십시오.

## 대역폭 정책 프로필을 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **대역폭 정책**을 클릭합니다.

4.  **대역폭 정책** 페이지에서 수정할 대역폭 정책 프로필을 클릭합니다.

5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

## Lync Server PowerShell Cmdlet을 사용하여 네트워크 대역폭 정책 프로필 정보 보기

네트워크 대역폭 프로필은 Lync Server PowerShell 및 Get-CsNetworkBandwidthPolicyProfile cmdlet을 사용하여 볼 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션(원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.)에서 실행할 수 있습니다.

## 네트워크 대역폭 정책 프로필 정보 보기

  - 네트워크 대역폭 정책 프로필에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsNetworkBandwidthPolicyProfile
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity          : RedmondBandwidthPolicy
        BWPolicy          : {BWLimit=200;BWSessionLimit=200;
                            BWPolicyModality=Audio, 
                            BWLimit=1400;BWSessionLimit=500;
                            BWPolicyModality=Video}
        BWPolicyProfileID : RedmondBandwidthPolicy
        Description       :

자세한 내용은 [Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile) cmdlet 관련 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[대역폭 정책 프로필 만들기 또는 수정](lync-server-2013-creating-or-modifying-bandwidth-policy-profiles.md)  
[네트워크 대역폭 정책 프로필 삭제](lync-server-2013-deleting-network-bandwidth-policy-profiles.md)  

#### 기타 리소스

[Lync Server 2013에서 통화 허용 제어 서비스 구성](lync-server-2013-configure-call-admission-control.md)

