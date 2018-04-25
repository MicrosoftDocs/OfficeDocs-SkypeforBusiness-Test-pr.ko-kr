---
title: 명시적으로 지원되지 않거나 제한된 클라이언트에 대한 기본 작업 수정
TOCTitle: 명시적으로 지원되지 않거나 제한된 클라이언트에 대한 기본 작업 수정
ms:assetid: 548dd0f5-62fe-4c3f-8952-2b9fd4c5fff3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520994(v=OCS.15)
ms:contentKeyID: 49303656
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 명시적으로 지원되지 않거나 제한된 클라이언트에 대한 기본 작업 수정

 

_**마지막으로 수정된 항목:** 2013-02-23_

Lync Server 2013 환경에서 지원하려는 클라이언트 버전을 지정하는 것 외에도, 아직 버전 정책이 정의되지 않은 클라이언트에 대해 기본 동작을 지정할 수 있습니다. 이렇게 하면 Lync Server 환경에서 사용되는 클라이언트 버전을 제한할 수 있으므로 여러 클라이언트 버전 지원과 연관된 비용을 제어할 수 있습니다.

## 명시적으로 지원 또는 제한되지 않는 클라이언트에 대한 기본 동작을 수정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **클라이언트**를 클릭하고 **클라이언트 버전 구성**을 클릭합니다.

4.  **클라이언트 버전 구성** 페이지의 목록에서 **전역** 구성을 두 번 클릭합니다.

5.  **클라이언트 버전 구성 편집** 대화 상자에서 **버전 제어 사용** 확인란이 선택되어 있는지 확인하고 **기본 동작** 아래에서 다음 중 하나를 선택합니다.
    
      - **허용**   클라이언트 버전이 **클라이언트 버전 정책** 목록의 필터와 일치하지 않아도 클라이언트 로그온을 허용합니다.
    
      - **차단**   클라이언트 버전이 **클라이언트 버전 정책** 목록의 필터와 일치하지 않으면 클라이언트 로그온을 차단합니다.
    
      - **URL로 차단**   클라이언트 버전이 **클라이언트 버전 정책** 목록의 필터와 일치하지 않으면 클라이언트 로그온을 차단하고, 새 클라이언트를 다운로드할 수 있는 URL이 포함된 오류 메시지를 포함합니다.
    
      - **URL로 허용**   클라이언트 버전이 **클라이언트 버전 정책** 목록의 필터와 일치하지 않아도 클라이언트 로그온을 허용하고, 새 클라이언트를 다운로드할 수 있는 URL이 포함된 오류 메시지를 포함합니다.

6.  **URL로 차단**을 선택한 경우 오류 메시지에 포함할 클라이언트 다운로드 URL을 **URL** 상자에 입력합니다.

7.  **커밋**을 클릭합니다.

## 클라이언트 버전 제어를 사용하지 않도록 설정하려면

  - 버전 제어를 사용하지 않도록 설정하여 클라이언트 버전에 관계없이 모든 클라이언트의 로그온을 허용하려면 **버전 제어 사용** 확인란 선택을 취소하고 **커밋**을 클릭합니다.

## Lync Server PowerShell Cmdlet을 사용하여 기본 작업 수정

사용자가 클라이언트 버전 정책에 의해 명시적으로 지원되거나 제한되지 않는 클라이언트를 사용해서 로그인하려고 할 때 수행할 기본 작업은 Windows PowerShell 명령줄 인터페이스 및 **Set-CsClientVersionPolicy** cmdlet을 사용하여 관리할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 액세스 차단을 위한 기본 작업 구성

  - 다음 명령은 Redmond 사이트 차단을 위한 기본 작업을 설정합니다. 이 명령은 클라이언트 버전 구성 규칙이 없는 모든 클라이언트의 등록을 차단합니다.
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -DefaultAction Block

## 액세스 허용을 위한 기본 작업 구성

  - 이 예에서 Redmond 사이트에 대한 기본 작업은 허용으로 설정됩니다. 이 명령은 클라이언트 버전 구성 규칙이 없는 모든 클라이언트의 등록을 허용합니다.
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -DefaultAction Allow

자세한 내용은 [Set-CsClientVersionPolicy](set-csclientversionpolicy.md) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 장치, 전화 및 클라이언트 응용 프로그램 관리](lync-server-2013-managing-devices-phones-and-client-applications.md)

