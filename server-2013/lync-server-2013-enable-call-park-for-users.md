---
title: 'Lync Server 2013: 사용자에 대해 통화 대기를 사용하도록 설정'
TOCTitle: 사용자에 대해 통화 대기를 사용하도록 설정
ms:assetid: 9430763f-3394-467c-9c6d-426bf761604e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398753(v=OCS.15)
ms:contentKeyID: 49304411
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자에 대해 통화 대기를 사용하도록 설정

 

_**마지막으로 수정된 항목:** 2012-09-11_

사용자는 음성 정책에서 통화 대기를 사용할 수 있도록 설정된 경우에만 통화를 대기시키거나 대기 중인 통화를 재개할 수 있습니다.


> [!NOTE]
> 기본적으로 모든 사용자가 통화 대기를 사용할 수 없도록 설정되어 있습니다.



전역 범위에서 또는 사이트나 사용자 범위에서 통화 대기를 사용할 수 있도록 설정할 수 있습니다. 사용자 범위는 사이트 범위보다 우선하고 사이트 범위는 전역 범위보다 우선합니다. 음성 정책이 여러 개인 경우 전역 정책만이 아니라 모든 정책을 검토하여 통화 대기를 사용할 수 있도록 설정합니다.

## Lync Server 제어판을 사용하여 사용자가 통화 대기를 사용할 수 있도록 설정하려면

1.  **RTCUniversalServerAdmins** 그룹의 구성원이나 **CsVoiceAdministrator** , **CsServerAdministrator** 또는 **CsAdministrator** 관리 역할의 구성원으로 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅** 을 클릭합니다.

4.  **음성 정책** 탭을 클릭합니다.

5.  기존 음성 정책을 두 번 클릭하여 **음성 정책 편집** 대화 상자를 엽니다.

6.  **전화 걸기 기능** 에서 **통화 대기 사용** 을 선택합니다.

7.  **확인** 을 클릭하여 음성 정책을 저장합니다.

## cmdlet을 사용하여 사용자가 통화 대기를 사용할 수 있도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 관리 역할의 구성원으로 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Set-CsVoicePolicy -Identity <VoicePolicy> -EnableCallPark $true
    
    예를 들어 기본 전역 음성 정책에 대해 통화 대기를 사용하도록 설정합니다.
    
        Set-CsVoicePolicy -EnableCallPark $true

## 참고 항목

#### 작업

[Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 만들기](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)

