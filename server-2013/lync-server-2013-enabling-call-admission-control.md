---
title: 통화 허용 제어 사용
TOCTitle: 통화 허용 제어 사용
ms:assetid: 015f5c8f-2f90-4b9e-8149-b33767e90582
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520942(v=OCS.15)
ms:contentKeyID: 49302613
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 통화 허용 제어 사용

 

_**마지막으로 수정된 항목:** 2012-11-01_

CAC(통화 허용 제어)는 사용 가능한 대역폭을 기반으로 오디오 및 비디오 전송에 제한을 둘 수 있는 지역, 사이트 및 서브넷의 네트워크입니다. CAC 네트워크를 구성한 후에는 대역폭 제한을 적용할 수 있도록 CAC를 설정해야 합니다. 이렇게 하려면 Lync Server 제어판을 사용하면 됩니다.

## Lync Server 제어판에서 CAC를 사용하도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭하고 **전역**을 클릭합니다.

4.  **전역** 페이지에서 **전역** 구성을 클릭합니다.
    

    > [!NOTE]
    > 각 Microsoft Lync Server 2013 배포에는 네트워크를 하나만 구성할 수 있으므로, 목록에 둘 이상의 네트워크 구성이 있는 경우는 없습니다. 전역 구성은 이름을 바꿀 수 없습니다.



5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

6.  **전역 설정 편집** 페이지에서 **통화 허용 제어 사용** 확인란을 선택하고 **커밋**을 클릭합니다.

**커밋**을 클릭하면 구성 테스트가 실행됩니다. **전역 설정 편집** 대화 상자가 닫히고 **전역** 페이지로 돌아갑니다. 네트워크 구성에서 오류나 불일치 사항이 검색되어 구성이 제대로 작동하지 않는 경우(예: 모든 지역이 지역 간 경로를 통해 다른 모든 지역에 연결되어 있지 않은 경우)에는 경고가 표시됩니다.

네트워크 구성을 변경하는 경우 전역 구성을 열고 **커밋**을 클릭하여 유효성 검사를 실행할 수 있습니다. 먼저 CAC를 사용하지 않도록 설정할 필요는 없으며, 확인란을 선택한 대로 두고 **커밋**을 클릭하면 됩니다. 구성을 변경하지 않아도 언제든지 이 검사를 수행할 수 있습니다.

## 참고 항목

#### 개념

[Lync Server 2013의 통화 허용 제어 서비스 개요](lync-server-2013-overview-of-call-admission-control.md)  

#### 기타 리소스

[Lync Server 2013의 통화 허용 제어 서비스 계획](lync-server-2013-planning-for-call-admission-control.md)  
[Lync Server 2013에서 통화 허용 제어 서비스 구성](lync-server-2013-configure-call-admission-control.md)  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)  
[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)

