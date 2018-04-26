---
title: Lync Phone Edition 구성 설정 정보 보기
TOCTitle: Lync Phone Edition 구성 설정 정보 보기
ms:assetid: 15f94478-651f-4063-9918-6a059f98df16
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687976(v=OCS.15)
ms:contentKeyID: 49885659
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Phone Edition 구성 설정 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Phone Edition을 실행 중인 장치에 대한 구성 정보를 확인할 수 있습니다. 정보는 컬렉션으로 구성됩니다. Lync Server를 설치하면 배포에서 Lync Phone Edition을 실행 중인 모든 장치에 적용되는 Lync Phone Edition 설정 컬렉션이 제공됩니다. 특정 사이트에 대해 새 설정 컬렉션을 만들 수도 있습니다. 사이트 설정은 전역 설정보다 우선합니다. 각 설정 컬렉션은 이름, 범위(전역/사이트), SIP 보안 설정, 로깅 수준, 음성 QoS(서비스 품질) 수준, 전화 잠금 설정 및 전화 잠금 세부 정보(잠금 해제 개인 ID 번호(PIN)의 최소 길이 및 전화가 자동으로 잠길 때까지의 시간)로 구성됩니다.

## Lync Phone Edition을 실행 중인 장치에 대한 구성 정보를 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **클라이언트**를 클릭하고 **장치 구성** 탐색 단추를 클릭합니다.

4.  **장치 구성** 페이지에서 정보를 보려는 설정 컬렉션을 클릭합니다. 기본 페이지에 이름, 범위, SIP 보안 설정, 음성 품질 수준 및 전화 잠금 설정이 나열됩니다. 로깅 수준 및 전화 잠금 세부 정보를 보려면 **편집** 메뉴를 클릭하고 **자세한 정보 표시**를 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 Lync Phone Edition 구성 정보를 보려면

Lync Server 관리 셸 및 **Get-CsUCPhoneConfiguration** cmdlet을 사용하여 Lync Phone Edition 구성 정보를 볼 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## Lync Phone Edition 구성 정보를 보려면

  - 모든 Lync Phone Edition 구성 설정에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsUCPhoneConfiguration
    
    이 명령은 다음과 같은 정보를 반환합니다.
    
        Identity             : Global
        CalendarPollInterval : 00:03:00
        EnforcePhoneLock     : True
        PhoneLockTimeout     : 00:10:00
        MinPhonePinLength    : 6
        SIPSecurityMode      : High
        VoiceDiffServTag     : 40
        Voice8021p           : 0
        LoggingLevel         : Off

자세한 내용은 [Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md)을 참조하십시오.

## 참고 항목

#### 작업

[Lync Phone Edition 구성 설정 모음 만들기 및 수정](lync-server-2013-create-or-modify-a-collection-of-lync-phone-edition-configuration-settings.md)  
[Lync Phone Edition 구성 설정의 기존 컬렉션 삭제](lync-server-2013-delete-an-existing-collection-of-lync-phone-edition-configuration-settings.md)  
[Lync Phone Edition에 대한 보안 설정 구성](lync-server-2013-configure-security-settings-for-lync-phone-edition.md)  
[전화 잠금 적용](lync-server-2013-enforce-phone-locking.md)

