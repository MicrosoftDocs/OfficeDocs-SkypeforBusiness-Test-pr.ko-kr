---
title: Lync Server 2013에서 대역폭 정책 프로필 만들기
TOCTitle: Lync Server 2013에서 대역폭 정책 프로필 만들기
ms:assetid: a71881ef-b04a-465e-9abb-0577bfd182f3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412785(v=OCS.15)
ms:contentKeyID: 49304632
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 대역폭 정책 프로필 만들기

 

_**마지막으로 수정된 항목:** 2012-10-19_

*대역폭 정책*은 실시간 오디오 및 비디오 형식의 대역폭 사용량에 대한 제한을 정의하며, 통화 허용 제어에 대한 여러 네트워크 사이트에 적용할 수 있는 *대역폭 정책 프로필*에 적용됩니다.

CAC 배포에서 설정해야 하는 대역폭 제한에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 정의](lync-server-2013-defining-your-requirements-for-call-admission-control.md)을 참조하십시오.

대역폭 정책 및 정책 프로필을 사용하는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - [New-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkBandwidthPolicyProfile)

  - [Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)

  - [Set-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkBandwidthPolicyProfile)

  - [Remove-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkBandwidthPolicyProfile)

다음 절차에서 만들어진 예 정책은 전체 오디오 트래픽, 개별 오디오 세션, 전체 비디오 트래픽 및 개별 비디오 세션에 대한 제한을 설정합니다. 예를 들어 5Mb\_Link 대역폭 정책 프로필에서는 다음과 같은 제한이 설정됩니다.

  - 오디오 제한: 2,000kbps

  - 오디오 세션 제한: 200kbps

  - 비디오 제한: 1,400kbps

  - 비디오 세션 제한: 700kbps


> [!NOTE]  
> 최소 오디오 세션 제한 값은 40kbps이며, 최소 비디오 세션 제한 값은 100kbps입니다.



## 관리 셸을 사용하여 대역폭 정책 프로필을 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  만들려는 각 대역폭 정책 프로필에 대해 New-CsNetworkBandwidthPolicyProfile cmdlet을 실행합니다. 예를 들어 다음을 실행합니다.
    
    ```
            New-CsNetworkBandwidthPolicyProfile -Identity 5Mb_Link -Description "BW profile for 5Mb links" -AudioBWLimit 2000 -AudioBWSessionLimit 200 -VideoBWLimit 1400  -VideoBWSessionLimit 700
    ```
    ```
        New-CsNetworkBandwidthPolicyProfile -Identity 10Mb_Link -Description "BW profile for 10Mb links" -AudioBWLimit 4000 -AudioBWSessionLimit 200 -VideoBWLimit 2800 -VideoBWSessionLimit 700
    ```
    ```
        New-CsNetworkBandwidthPolicyProfile -Identity 50Mb_Link -Description "BW profile for 50Mb links" -AudioBWLimit 20000 -AudioBWSessionLimit 200 -VideoBWLimit 14000 -VideoBWSessionLimit 700
    ```
    ```
        New-CsNetworkBandwidthPolicyProfile -Identity 25Mb_Link -Description "BW profile for 25Mb links" -AudioBWLimit 10000 -AudioBWSessionLimit 200 -VideoBWLimit 7000 -VideoBWSessionLimit 700
    ```
    
## Lync Server 제어판을 사용하여 대역폭 정책 프로필을 만들려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 모음에서 **네트워크 구성**을 클릭합니다.

3.  **정책 프로필** 탐색 단추를 클릭합니다.

4.  **새로 만들기**를 클릭합니다.

5.  **새 프로필 정책** 페이지에서 **이름**을 클릭한 후 대역폭 정책 프로필에 대한 이름을 입력합니다.

6.  **오디오 제한**을 클릭하고 결합된 모든 오디오 세션에 허용할 최대 kbps를 입력합니다.

7.  **오디오 세션 제한**을 클릭하고 각 개별 오디오 세션에 허용할 최대 kbps를 입력합니다.

8.  **비디오 제한**을 클릭하고 결합된 모든 비디오 세션에 허용할 최대 kbps를 입력합니다.

9.  **비디오 세션 제한**을 클릭하고 각 개별 비디오 세션에 허용할 최대 kbps를 입력합니다.

10. 경우에 따라 **설명**을 클릭하고 이 대역폭 정책 프로필을 설명하는 추가 정보를 입력합니다.

11. **커밋**을 클릭합니다.

12. 토폴로지에 대한 대역폭 정책 프로필 만들기를 종료하려면 다른 대역폭 정책 프로필에 대한 설정을 사용하여 4-11단계를 반복합니다.

