---
title: 이동성 정책 만들기 또는 수정
TOCTitle: 이동성 정책 만들기 또는 수정
ms:assetid: fc2dfea0-2215-440d-9f4b-7c985da29211
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721946(v=OCS.15)
ms:contentKeyID: 49886069
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 이동성 정책 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-02-23_

모바일 사용자가 IM(인스턴트 메시징), 현재 상태 및 연락처 등 Lync 기능용으로 지원되는 모바일 장치를 사용할 수 있도록 모바일 정책을 만들거나 수정할 수 있습니다. Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸에서 모바일 정책을 만들거나 수정할 수 있습니다.

## Lync Server 제어판에서 모바일 정책을 만들려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **모바일 정책** 탐색 단추를 클릭합니다.

4.  **모바일 정책** 페이지에서 **새로 만들기**를 클릭하고 다음 중 하나를 수행합니다.
    
    1.  사이트 모바일 정책을 만들려면 **사이트 정책**을 클릭하고 사이트 하나를 클릭한 다음 **확인**을 클릭하고 기본 설정을 검토한 후 원할 경우 설정을 변경합니다.
    
    2.  사용자 모바일 정책을 만들려면 **사용자 정책**을 클릭하고 이름 하나를 입력한 다음 기본 설정을 검토한 후 원할 경우 설정을 변경합니다.

5.  **커밋**을 클릭합니다.

## Lync Server 제어판에서 모바일 정책을 수정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **모바일 정책** 탐색 단추를 클릭합니다.

4.  **모바일 정책** 페이지에서 기존 모바일 정책 중 하나를 클릭합니다.

5.  **편집** 메뉴에서 **자세한 정보 표시**를 클릭합니다.

6.  설정을 편집합니다.

7.  **커밋**을 클릭합니다.

## Windows PowerShell Cmdlet을 사용하여 외부 액세스 정책 제거

Windows PowerShell 및 **New-CsMobilityPolicy** cmdlet을 사용하여 사이트 범위나 사용자별 범위에서 모바일 정책을 만들 수도 있습니다. 또한 **Set-CsMobilityPolicy** cmdlet을 사용하여 글로벌 정책 등 기존 정책 중 하나를 수정할 수 있습니다. 이러한 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션(원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.)에서 실행할 수 있습니다.

## 사이트 범위에서 모바일 정책 만들기

  - 이 명령은 Redmond 사이트에 대한 새로운 모바일 정책을 만듭니다.
    
        New-CsMobilityPolicy -Identity "site:Redmond"
    
    이전 명령에 매개 변수(필수 Identity 매개 변수 이외)가 지정되지 않았으므로 정책에서 모든 속성에 대해 기본값을 사용합니다.

## 사용자별 범위에서 모바일 정책 만들기

  - 사용자별 범위에서 모바일 정책을 만들려면 정책에 대한 고유 ID를 지정합니다.
    
        New-CsMobilityPolicy -Identity "RedmondMobilityPolicy"

## 모바일 정책을 만들 때 단일 속성 값 변경

  - 다양한 속성 값을 사용하는 정책을 만들려면 해당 매개 변수 및 매개 변수 값을 포함합니다. 예를 들면 이 명령은 회사번호로 전화 기능을 사용하지 않도록 설정하는 모바일 정책을 만듭니다.:
    
        New-CsMobilityPolicy -Identity "site:Redmond" -EnableOutsideVoice $False

## 모바일 정책을 만들 때 여러 속성 값 변경

  - 여러 매개 변수를 포함하여 여러 속성 값을 수정할 수 있습니다. 예를 들면 이 명령은 모바일 및 회사번호로 전화 기능을 둘 다 사용하지 않도록 설정하는 정책을 만듭니다.
    
        New-CsMobilityPolicy "site:Redmond" -EnableMobility $False -EnableOutsideVoice $False

자세한 내용은 [New-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMobilityPolicy) 및 [Set-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMobilityPolicy) cmdlet 관련 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013에서 모바일 정책 구성](lync-server-2013-configuring-mobility-policy.md)

