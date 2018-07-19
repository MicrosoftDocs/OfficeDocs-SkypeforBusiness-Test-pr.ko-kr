---
title: 체감 품질 구성 설정 삭제
TOCTitle: 체감 품질 구성 설정 삭제
ms:assetid: fd0c4c2f-3bfb-42cb-9b6a-f0f8d5aa9e81
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182613(v=OCS.15)
ms:contentKeyID: 49305637
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 체감 품질 구성 설정 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

QoE(체감 품질) 메트릭은 손실된 네트워크 패킷 수, 백그라운드 노이즈, "지터"(패킷 지연의 차이) 크기 등 조직의 오디오 및 비디오 통화 품질을 추적합니다. 이러한 메트릭은 통화 정보 기록과 같은 기타 데이터와 별도로 데이터베이스에 저장되므로 다른 데이터 기록에 관계 없이 QoE를 설정 및 해제할 수 있습니다.

Microsoft Lync Server 2013을 설치할 경우 단일 전역 QoE 구성 설정 모음이 만들어집니다. 관리자는 개별 사이트에 적용할 수 있는 사용자 지정 설정 컬렉션을 만들 수도 있습니다. 이러한 설정은 전역 범위 또는 사이트 범위에서 구성할 수 있습니다. 사이트 범위의 설정을 삭제할 경우 QoE는 전역 설정을 사용하여 해당 사이트에서 관리됩니다.

또한 전역 설정을 “삭제”할 수도 있습니다. 그러나 전역 설정을 사실상 삭제되지 않습니다. 대신에, 해당 모음에 있는 모든 속성이 기본값으로 다시 설정됩니다. 예를 들면 기본적으로 지우기는 QoE 구성 설정 모음에서 사용할 수 있습니다. 지우기를 사용할 수 없도록 전역 모음을 수정한다고 가정하겠습니다. 나중에 전역 설정을 삭제하면 모든 속성이 기본값으로 다시 설정됩니다. 따라서 이 경우에는 지우기를 다시 사용할 수 있게 됩니다.

Lync Server 제어판을 사용하거나 [Remove-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsQoEConfiguration) cmdlet을 사용하여 QoE 구성 설정을 제거할 수 있습니다.

## Lync Server 제어판을 사용하여 QoE 구성 설정을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **체감 품질 데이터**를 클릭합니다.

4.  **체감 품질 데이터** 페이지에서 원하는 정책을 클릭하고 **편집**을 클릭한 다음 **삭제**를 클릭합니다.

5.  **확인**을 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 QoE 구성 설정을 제거하려면

또한 Lync Server 관리 셸 및 **Remove-CsQoEConfiguration** cmdlet을 사용하여 QoE 구성 설정을 삭제할 수도 있습니다. Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 이 cmdlet을 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 지정된 QoE 구성 설정 모음을 제거하려면

  - 이 명령은 Redmond 사이트에 적용된 QoE 구성 설정을 제거합니다.
    
        Remove-CsQoEConfiguration -Identity "site:Redmond"

## 사이트 범위에 적용된 모든 QoE 구성 설정을 제거하려면

  - 이 명령은 사이트 범주에 적용된 모든 QoE 구성 설정을 제거합니다.
    
        Get-CsQoEConfiguration -Filter "site:*" | Remove-CsQoEConfiguration

## QoE 모니터링을 사용할 수 없는 경우 모든 QoE 구성 설정을 제거하려면

  - 이 명령은 QoE 모니터링을 사용할 수 없는 경우 모든 QoE 구성 설정을 제거합니다.
    
        Get-CsQoEConfiguration | Where-Object {$_.EnableQoE -eq $False} | Remove-CsQoEConfiguration

자세한 내용은 [Remove-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsQoEConfiguration)을 참조하십시오.

