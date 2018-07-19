---
title: Lync Server 2013에서 통화 허용 제어 사용
TOCTitle: Lync Server 2013에서 통화 허용 제어 사용
ms:assetid: 80201105-18f7-4c02-9c71-8df5a952f6c7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398642(v=OCS.15)
ms:contentKeyID: 49304202
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 통화 허용 제어 사용

 

_**마지막으로 수정된 항목:** 2012-10-19_

통화 허용 제어 배포에 대한 네트워크 설정을 구성한 후 CAC를 사용하도록 설정하여 대역폭 정책을 적용해야 합니다.

자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - [Get-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkConfiguration)

  - [Set-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkConfiguration)

  - [Remove-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkConfiguration)

## 관리 셸을 사용하여 통화 허용 제어를 사용하도록 설정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  Set-CsNetworkConfiguration cmdlet을 실행하여 네트워크에서 CAC를 사용하도록 설정합니다. 예를 들어 다음을 실행합니다.
    
        Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck 1
    
    네트워크에서 CAC를 사용하지 않도록 설정하려면 다음을 실행합니다.
    
        Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck 0

## Lync Server 제어판을 사용하여 통화 허용 제어를 사용하도록 설정하려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭합니다.

3.  **전역** 탐색 단추를 클릭합니다.

4.  목록에서 **전역**을 클릭한 다음 **편집** 메뉴에서 **세부 정보 표시**를 선택합니다.

5.  **전역 설정 편집** 페이지에서 **통화 허용 제어 사용** 확인란을 선택합니다.
    

    > [!NOTE]
    > 배포 전체에서 통화 허용 제어를 사용하지 않도록 설정하려면 이 확인란을 선택 취소합니다.



6.  **커밋**을 클릭합니다.

