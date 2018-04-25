---
title: Lync Phone Edition에 대한 보안 설정 구성
TOCTitle: Lync Phone Edition에 대한 보안 설정 구성
ms:assetid: 6e7cec17-8a79-4428-9300-8821256c46cf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521014(v=OCS.15)
ms:contentKeyID: 49303976
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Phone Edition에 대한 보안 설정 구성

 

_**마지막으로 수정된 항목:** 2013-02-23_

SIP 보안 설정 및 전화 잠금 설정을 통해 Lync Phone Edition을 실행하는 장치의 보안을 향상시킬 수 있습니다.

## Lync Phone Edition에 대한 보안 설정을 구성하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **클라이언트**를 클릭하고 **장치 구성**을 클릭합니다.

4.  **장치 구성** 페이지의 장치 구성 목록에서 보안 설정을 변경할 구성을 두 번 클릭합니다.

5.  **장치 구성 편집**의 **SIP 보안**에서 SIP 보안 수준을 지정합니다. 권장되는 기본 수준은 **높음**입니다.

6.  **장치 구성 편집**의 **전화 잠금**에서 **장치 잠금 적용** 확인란(기본적으로 선택되어 있음)을 선택하거나 선택을 취소하고 최소 PIN 길이(기본값 6자)를 지정하고 시간 초과 기간(기본값 10분)을 지정합니다. 이러한 기본값을 사용하거나 PIN 길이를 늘리고, 또는 시간 초과 기간을 줄이는 것이 좋습니다.
    

    > [!NOTE]
    > 자세한 내용은 <A href="lync-server-2013-enforce-phone-locking.md">전화 잠금 적용</A>를 참조하십시오.



## Lync Server 관리 셸 Cmdlet을 사용하여 Lync Phone Edition 전화에 대한 보안 설정 구성

또한 Lync Server 관리 셸 및 **Get-CsUCPhoneConfiguration** cmdlet을 사용하여 보안 설정을 관리할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## SIP 보안 모드를 수정하려면

  - 이 명령은 UC 전화 설정의 전역 설정에 대해 SIPSecurityMode를 중간으로 설정합니다. SIP 보안은 낮음 또는 높음(기본값)으로 설정할 수도 있습니다.
    
        Set-CsUCPhoneConfiguration -Identity global -SIPSecurityMode "Medium"

## 최소 PIN 길이를 수정하려면

  - 이 예에서 모든 UC 전화 설정은 최소 PIN 길이로 7자리 숫자를 요구하도록 수정됩니다.
    
        Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration -MinPhonePinLength 7

자세한 내용은 [Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md)를 참조하십시오.

## 참고 항목

#### 개념

[Lync Server 2013 인증 관리](lync-server-2013-managing-lync-server-authentication.md)  

#### 기타 리소스

[Lync Server 2013에서 장치, 전화 및 클라이언트 응용 프로그램 관리](lync-server-2013-managing-devices-phones-and-client-applications.md)

