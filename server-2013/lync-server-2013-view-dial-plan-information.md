---
title: Lync Server 2013에서 다이얼 플랜 정보 보기
TOCTitle: Lync Server 2013에서 다이얼 플랜 정보 보기
ms:assetid: 25ed0112-a8a7-418a-8c2c-580081be692a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687997(v=OCS.15)
ms:contentKeyID: 49885687
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 다이얼 플랜 정보 보기

 

_**마지막으로 수정된 항목:** 2012-11-01_

기존 다이얼 플랜에 대한 정보를 보려면 다음 절차의 단계를 수행합니다. 새 다이얼 플랜을 만들려면 [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)를 참조하십시오.

## Lync Server 제어판에서 다이얼 플랜에 대한 정보를 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅**을 클릭한 다음 **다이얼 플랜**을 클릭합니다.

4.  **다이얼 플랜** 페이지에서 다이얼 플랜 이름을 두 번 클릭합니다.
    

    > [!NOTE]
    > 한 번에 한 다이얼 플랜에 대한 정보만 볼 수 있습니다.



## Windows PowerShell cmdlet을 사용하여 다이얼 플랜 확인

  - Windows PowerShell 명령줄 인터페이스 및 **Get-CsDialPlan** cmdlet을 사용하여 다이얼 플랜을 확인할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.
    
    모든 다이얼 플랜에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsDialPlan
    
    이 명령은 다음과 같은 정보를 반환합니다.
    
        Identity                 : Global
        Description              :
        DialinConferencingRegion :
        NormalizationRules       : {Description=;
                                   Pattern=^(\d+)$;Translation=$1;Name=
                                   KeepAll;IsInternalExtension=False}
        CountryCode              :
        State                    :
        City                     :
        ExternalAccessPrefix     :
        SimpleName               : DefaultProfile
        OptimizeDeviceDialing    : False

## 참고 항목

#### 작업

[Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)  
[Lync Server 2013에서 다이얼 플랜 수정](lync-server-2013-modify-a-dial-plan.md)

