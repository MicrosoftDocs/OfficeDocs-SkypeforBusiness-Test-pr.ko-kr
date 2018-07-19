---
title: 위치 정책 정보 보기
TOCTitle: 위치 정책 정보 보기
ms:assetid: 14e41bcb-ea0a-49c2-99b3-1f61fc34416d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520954(v=OCS.15)
ms:contentKeyID: 49302903
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 위치 정책 정보 보기

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server 2013에서는 위치 정책을 사용하여 E9-1-1(고급 9-1-1) 기능 및 사용자 또는 대화 상대의 위치 설정과 관련된 설정을 적용할 수 있습니다. 위치 정책은 사용자가 E9-1-1을 사용하도록 설정되어 있는지 여부를 확인하고, 설정된 경우 긴급 통화에 대한 동작을 결정합니다. 예를 들어 위치 정책을 사용하여 긴급 통화 번호(예: 한국의 경우 119), 회사 보안 부서에 자동으로 알림을 제공할지 여부 및 통화를 라우팅할 방법을 정의할 수 있습니다.

위치 정책은 Lync Server 2013 제어판의 **네트워크 구성** 그룹에서 구성할 수 있습니다. Lync Server 제어판에서는 위치 정책을 보거나, 만들거나, 수정하거나, 삭제할 수 있습니다. 다음 절차에 따라 위치 정책에 대한 정보를 확인합니다. 위치 정책을 만들거나 수정하는 방법에 대한 자세한 내용은 [위치 정책 만들기 또는 수정](lync-server-2013-creating-or-modifying-a-location-policy.md)을 참조하십시오.

## 위치 정책에 대한 정보를 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭한 다음 **위치 정책**을 클릭합니다.

4.  **위치 정책** 페이지에서 수정할 위치 정책을 선택합니다.

5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.
    

    > [!NOTE]
    > 한 번에 한 위치 정책에 대한 정보만 볼 수 있습니다.



글로벌이라는 단일 정책은 기본적으로 존재하며, 삭제하거나 이름을 바꿀 수 없습니다. 그러나 글로벌 정책을 수정할 수는 있습니다. 이 정책은 사이트 정책 또는 사용자별 정책을 만들지 않은 경우 모든 사용자 및 대화 상대에 적용됩니다. 사용자별 정책은 특정 사용자에게 적용해야 합니다.

## 참고 항목

#### 작업

[위치 정책 만들기 또는 수정](lync-server-2013-creating-or-modifying-a-location-policy.md)  
[Lync Server 2013에서 위치 정책 만들기](lync-server-2013-create-location-policies.md)  
[Lync Server 2013에서 네트워크 사이트 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-site.md)  

#### 기타 리소스

[New-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsLocationPolicy)  
[Set-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsLocationPolicy)  
[Remove-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsLocationPolicy)  
[Get-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsLocationPolicy)

