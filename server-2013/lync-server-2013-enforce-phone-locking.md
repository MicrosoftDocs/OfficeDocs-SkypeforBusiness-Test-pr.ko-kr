---
title: 전화 잠금 적용
TOCTitle: 전화 잠금 적용
ms:assetid: 1f89298b-aea9-4952-93ca-0270b565792b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520963(v=OCS.15)
ms:contentKeyID: 49303017
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전화 잠금 적용

 

_**마지막으로 수정된 항목:** 2013-02-23_

보안상 Lync Phone Edition 장치를 잠글 수 있습니다. 전화 잠금을 적용하는 경우 구성된 기간이 지나면 Lync Phone Edition을 실행하는 장치가 잠깁니다. 전화가 잠겨 있으면 사용자는 전화를 걸 수는 있지만 일정/연락처 정보, 음성 사서함 또는 통화 기록에 액세스하거나 검색을 사용할 수는 없습니다. 전화 잠금을 해제하려면 PIN을 입력합니다.

전화 잠금을 적용하려면 Lync Server 제어판 또는 Lync Server PowerShell cmdlet을 사용하여 잠금을 사용하도록 설정하고 구성합니다. 전화 잠금은 전역적으로 적용할 수도 있고 잠금이 구성된 사이트 내에서만 적용할 수도 있습니다.

## 전화 잠금을 구성하고 적용하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  **클라이언트**를 클릭하고 **장치 구성**을 클릭합니다.

4.  **장치 구성** 탭의 장치 구성 목록에서 전화 잠금 설정을 변경할 구성을 두 번 클릭합니다.

5.  **장치 구성 편집** 대화 상자에서 **장치 잠금 적용** 확인란이 선택되어 있는지 확인합니다.

6.  **최소 PIN 길이**에서 잠금 해제 PIN에 포함해야 하는 최소 자릿수에 대한 기본값을 적용하거나 새 값을 지정합니다. PIN 길이의 범위는 4~15자리이며 기본값은 6자리입니다.

7.  **전화 잠금 시간 초과**에서 전화가 자동으로 잠길 때까지의 최소 시간에 대한 기본값을 적용하거나 새 값을 지정합니다. 시간 초과 범위는 0~60분이고 기본값은 10분입니다. HH:MM:SS 형식으로 값을 입력하십시오.

8.  **커밋**을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 전화 잠금 적용

Set-CsUCPhoneConfiguration cmdlet을 사용하여 전화 잠금을 적용할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 전화 잠금을 사용하도록 설정하려면

  - 다음 명령은 Redmond 사이트에 대한 전화 잠금을 사용하도록 설정합니다. 전화 잠금을 사용하지 않도록 설정하려면 EnforcePhoneLock 속성을 False($False)로 설정합니다.
    
        Set-CsUCPhoneConfiguration -Identity" site:Redmond" -EnforcePhoneLock $True

## 전화 잠금을 사용하도록 설정하고 전화 잠금 시간 초과를 수정하려면

  - 다음 명령은 전화 잠금을 사용하도록 설정하고 전화 잠금 제한 시간을 30분으로 설정합니다.
    
        Set-CsUCPhoneConfiguration -Identity" site:Redmond" -EnforcePhoneLock $True -PhoneLockTimeout "00:30:00"

## 조직 전체에서 전화 잠금을 사용하도록 설정하려면

  - 이 예에서는 조직에서 사용 중인 모든 UC 전화 구성 설정에서 전화 잠금이 사용하도록 설정됩니다.
    
        Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration  -EnforcePhoneLock $True

자세한 내용은 [Set-CsUCPhoneConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUCPhoneConfiguration) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 개념

[Lync Server 2013 인증 관리](lync-server-2013-managing-lync-server-authentication.md)  

#### 기타 리소스

[Lync Server 2013에서 장치, 전화 및 클라이언트 응용 프로그램 관리](lync-server-2013-managing-devices-phones-and-client-applications.md)

