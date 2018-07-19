---
title: Lync Phone Edition 구성 설정 모음 만들기 및 수정
TOCTitle: Lync Phone Edition 구성 설정 모음 만들기 및 수정
ms:assetid: 6cf714af-8f57-4a71-89ad-0a776302b2ba
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688086(v=OCS.15)
ms:contentKeyID: 49885799
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Phone Edition 구성 설정 모음 만들기 및 수정

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server를 설치하면 Lync Phone Edition 설정에 대한 전역 컬렉션이 설정됩니다. 이러한 설정은 사용자의 배포에서 Lync Phone Edition을 실행하는 모든 장치에 적용됩니다. 이러한 설정은 언제라도 변경할 수 있습니다. 또한 이제는 특정 사이트의 장치에 적용되는 새로운 설정 컬렉션을 설정할 수도 있습니다. 사이트 설정은 전역 설정보다 우선 적용됩니다.

구성 설정은 컬렉션 이름, 범위(전역 또는 사이트), SIP 보안 설정, 로깅 수준, 음성 QoS(서비스 품질), 전화 잠금 설정, 전화 잠금 세부 정보(즉, a) PIN(개인 식별 번호) 잠금 해제를 유지해야 하는 시간 및 b) 자동으로 잠기기 전에 유지되어야 하는 전화 유휴 시간)로 구성됩니다.

## Lync Phone Edition 구성 설정의 컬렉션을 만들거나 기존 컬렉션의 설정을 편집하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **클라이언트**를 클릭하고 **장치 구성** 탐색 단추를 클릭합니다.

4.  **장치 구성** 페이지에서 다음 중 하나를 수행합니다.
    
      - Lync Phone Edition 구성 설정의 새 컬렉션을 만들려면 **새로 만들기**를 클릭하고, 사이트를 선택하고, **확인**을 클릭하고, 기본 설정을 검토하고, 필요에 따라 항목을 변경합니다.
    
      - 기존 컬렉션에서 설정을 편집하려면 컬렉션을 클릭하고, **편집** 메뉴를 클릭하고, **세부 정보 표시**를 클릭한 후 항목을 변경합니다.
        

        > [!TIP]
        > 전역 컬렉션에 대한 기본 설정 사용으로 돌아가려면 전역 컬렉션을 클릭하고, <STRONG>편집</STRONG> 메뉴를 클릭하고, <STRONG>삭제</STRONG>를 클릭한 후 <STRONG>확인</STRONG>을 클릭합니다. 그래도 전역 컬렉션이 삭제되지는 않으며 설정만 기본값으로 다시 설정됩니다.



5.  **커밋**을 클릭합니다.

## Lync Server 관리 셸 cmdlet을 사용하여 새 Lync Phone Edition 구성 설정을 만들려면

또한 Lync Server 관리 셸 및 **New-CsUCPhoneConfiguration** cmdlet을 사용하여 Lync Phone Edition 구성 설정을 만들 수 있습니다(사이트 범위에서만). 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 기본값을 사용해서 새 Lync Phone Edition 구성 설정을 만들려면

  - 이 명령은 Redmond 사이트에 대한 새로운 UC 전화 구성 설정 집합을 만듭니다.
    
        New-CsUCPhoneConfiguration -Identity "site:Redmond"
    
    이전 명령에서 매개 변수(필수 Identity 매개 변수 제외)가 지정되지 않았기 때문에 구성 설정의 새 컬렉션에는 모든 속성에 대해 기본값이 사용됩니다.

## 새 Lync Phone Edition 구성 설정을 만들 때 단일 속성 값을 변경하려면

  - 다른 속성 값을 사용하는 설정을 만들려면 적합한 매개 변수 및 매개 변수 값만 포함합니다. 예를 들어 기본적으로 전화 잠금이 필요한 UC 전화 구성 설정의 컬렉션을 만들려면 다음과 비슷한 명령을 사용합니다.
    
        New-CsUCPhoneConfiguration -Identity "site:Redmond" -EnforcePhoneLock $True

## 새 Lync Phone Edition 구성 설정을 만들 때 여러 속성 값을 변경하려면

  - 여러 매개 변수를 포함하여 여러 속성 값을 수정할 수 있습니다. 예를 들어 이 명령은 전화 잠금을 강제 적용하고 최소 PIN 길이도 8자리 숫자로 설정합니다.
    
        New-CsUCPhoneConfiguration -Identity "site:Redmond" -EnforcePhoneLock $True -MinPhonePinLength 8

자세한 내용은 [New-CsUCPhoneConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsUCPhoneConfiguration)를 참조하십시오.

## 참고 항목

#### 작업

[Lync Phone Edition 구성 설정의 기존 컬렉션 삭제](lync-server-2013-delete-an-existing-collection-of-lync-phone-edition-configuration-settings.md)  
[Lync Phone Edition에 대한 보안 설정 구성](lync-server-2013-configure-security-settings-for-lync-phone-edition.md)  
[전화 잠금 적용](lync-server-2013-enforce-phone-locking.md)

