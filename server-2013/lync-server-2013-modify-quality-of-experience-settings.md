---
title: 체감 품질 설정 수정
TOCTitle: 체감 품질 설정 수정
ms:assetid: a6b41de2-1466-4240-8a70-14ce6f0f3ddc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182563(v=OCS.15)
ms:contentKeyID: 49304625
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 체감 품질 설정 수정

 

_**마지막으로 수정된 항목:** 2013-02-23_

QoE(체감 품질) 데이터는 기본적으로 60일 후에 삭제됩니다. **체감 품질 데이터** 페이지의 설정을 사용하여 데이터를 60일 이상 보존하거나 60일보다 짧게 보존할 수 있습니다. QoE를 사용하지 않도록 설정한 경우 QoE를 사용하도록 설정하기 전에 캡처한 데이터도 삭제됩니다.


> [!NOTE]
> CDR(통화 정보 기록) 및 QoE의 데이터 보존 일수는 동일하게 구성해야 합니다. 모니터링 보고서 홈 페이지에 제공되는 CDR(통화 정보 보고서)의 각 통화에는 CDR 및 QoE 정보가 포함됩니다. CDR 및 QoE의 삭제 기간이 다를 경우 일부 통화에는 CDR 데이터만 포함되고 또 다른 일부 통화에는 QoE 데이터만 포함될 수 있습니다.



다음 절차는 QoE 데이터에 대한 삭제 설정을 구성하는 방법을 설명합니다.

## Lync Server 제어판을 사용하여 QoE 데이터 보존 기간을 지정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **모니터링 및 보관**을 클릭하고 **체감 품질 데이터**를 클릭합니다.

4.  **체감 품질 데이터** 페이지의 테이블에서 적합한 사이트를 클릭하고 **편집**, **자세한 정보 표시**를 차례로 클릭합니다.

5.  삭제를 설정하려면 **QoE 삭제 사용**을 선택합니다.

6.  **최대 기간(일) 동안 QoE 유지**에서 QoE 데이터를 보존할 최대 일수를 선택합니다.

7.  **커밋**을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 QoE 보존을 지정하려면

Windows PowerShell 및 **Set-CsQoEConfiguration** cmdlet을 사용하여 QoE 보존 설정을 만들 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 특정 위치에 대한 QoE 보존을 지정하려면

  - 이 명령은 Redmond 사이트에 대해 QoE 데이터 삭제를 사용하도록 설정하고 20일 동안 QoE 데이터를 유지하도록 구성합니다.
    
        Set-CsQoeConfiguration -Identity "site:Redmond" -EnablePurging -KeepQoEDataForDays 20

## 여러 위치에 대한 QoE 보존을 지정하려면

  - 이 명령은 조직에서 사용 중인 모든 QoE 구성 설정에 대해 QoE 보존을 구성합니다.
    
        Get-CsQoEConfiguration | Set-CsQoEConfiguration-EnablePurging -KeepQoEDataForDays 20 

자세한 내용은 [Set-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsQoEConfiguration) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 모니터링 배포](lync-server-2013-deploying-monitoring.md)

