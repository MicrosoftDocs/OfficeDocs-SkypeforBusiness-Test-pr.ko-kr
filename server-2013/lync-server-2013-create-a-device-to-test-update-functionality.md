---
title: 업데이트 기능 테스트를 위한 장치 만들기
TOCTitle: 업데이트 기능 테스트를 위한 장치 만들기
ms:assetid: ce509fd1-17b3-4b78-b269-fe5d06fe2e1d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182587(v=OCS.15)
ms:contentKeyID: 49305071
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 업데이트 기능 테스트를 위한 장치 만들기

 

_**마지막으로 수정된 항목:** 2013-02-23_

테스트 장치를 **테스트 장치** 페이지에 추가한 다음 이 장치를 사용하여 프로덕션 장치에 업데이트를 배포하기 전에 새 업데이트의 기능을 확인할 수 있습니다. 장치는 전역으로 테스트하거나(Lync Server 환경 전체에서) 단일 사이트에서 테스트할 수 있습니다. MAC(미디어 액세스 제어) 주소 또는 일련 번호로 테스트 장치를 식별합니다. 장치를 추가하면 Lync Server 제어판의 **테스트 장치** 페이지에 있는 목록에 해당 장치가 나타납니다.

## 테스트 장치를 추가하려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 표시줄에서 **클라이언트**, **테스트 장치**를 차례로 클릭합니다.

3.  **새로 만들기**를 클릭한 다음 **전역 테스트 장치**나 **사이트 테스트 장치**를 클릭합니다.

4.  다음 중 하나를 수행합니다.
    
      - **전역 테스트 장치**를 클릭한 경우 다음 단계로 건너뜁니다.
    
      - **사이트 테스트 장치**를 클릭한 경우에는 사용 가능한 사이트 목록에서 사이트를 선택하고 **확인**을 클릭합니다.

5.  **새 테스트 장치**의 **장치 이름**에 장치의 이름을 입력합니다.

6.  **식별자 유형**에서 **MAC 주소**나 **일련 번호**를 클릭합니다.

7.  **고유 식별자** 상자에 장치의 일련 번호나 MAC 주소를 입력합니다.

8.  **커밋**을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 테스트 장치 만들기

Windows PowerShell 및 New-CsTestDevice cmdlet을 사용하여 테스트 장치를 만들 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

이 cmdlet을 사용하여 테스트 장치를 만들려면 다음 두 작업을 수행해야 합니다.

  - MACAddress 또는 SerialNumber 중 하나를 IdentifierType으로 지정해야 합니다.

  - 장치 ID를 지정할 때 범위를 포함해야 합니다. 전역 범위에서 새 장치를 만들려면 다음과 유사한 구문을 사용합니다.
    
        -Identity "global/WindowsPhone"
    
    사이트 범위에서 테스트 장치를 만들려면 다음과 같은 구문을 사용합니다.
    
        -Identity "site:Redmond/WindowsPhone"

## MAC 주소를 사용하여 테스트 장치를 만들려면

  - 다음 명령을 실행하면 MAC 주소를 IdentifierType으로 사용하여 전역 범위에서 테스트 장치를 만들 수 있습니다.
    
        New-CsTestDevice -Identity "global/WindowsPhone" -IdentifierType "MACAddress" -Identifier "01:02:03:04:05:06"

## 일련 번호를 사용하여 테스트 장치를 만들려면

  - 다음 명령을 실행하면 일련 번호를 IdentifierType으로 사용하여 사이트 범위(레드몬드 사이트)에서 새 테스트 장치를 만들 수 있습니다.
    
        New-CsTestDevice -Identity "site:Redmond/WindowsPhone" -IdentifierType "SerialNumber" -Identifier "01ABC5419JKR55T"

자세한 내용은 [New-CsTestDevice](new-cstestdevice.md) cmdlet에 대한 도움말 항목을 참조하십시오.

