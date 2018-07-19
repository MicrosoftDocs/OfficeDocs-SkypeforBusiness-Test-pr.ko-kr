---
title: 장치 업데이트 규칙 다시 설정
TOCTitle: 장치 업데이트 규칙 다시 설정
ms:assetid: d1f597e7-dffd-4756-af07-10613a5d8729
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994069(v=OCS.15)
ms:contentKeyID: 52056961
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치 업데이트 규칙 다시 설정

 

_**마지막으로 수정된 항목:** 2013-02-23_

테스트 장치에 대해 업데이트가 작동하는 방식을 변경하려면 장치 업데이트 규칙을 다시 설정합니다(규칙의 보류 중 상태가 제거되고 업데이트가 테스트 장치에서 제거됨).

Lync Server 제어판 또는 Windows PowerShell을 사용하여 장치 업데이트 규칙을 제거할 수 있습니다.


> [!NOTE]
> 이미 승인(제공)한 규칙을 제거하려면 해당 규칙을 복원합니다. 자세한 내용은 <A href="lync-server-2013-restore-a-device-update-rule.md">장치 업데이트 규칙 복원</A>을 참조하십시오.



## Lync Server 제어판을 사용하여 장치 업데이트 규칙을 다시 설정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **장치 업데이트** 탐색 단추를 클릭합니다.

4.  **장치 업데이트** 페이지에서 다음 중 하나를 수행합니다.
    
      - 규칙 하나를 다시 설정하려면 다시 설정할 규칙을 선택합니다.
    
      - 모든 규칙을 다시 설정하려면 **편집** 메뉴에서 **모두 선택**을 클릭합니다.
    
      - 단일 브랜드에 대한 모든 규칙을 다시 설정하려면 **브랜드** 열 메뉴를 사용합니다.

5.  **작업**을 클릭하고 **보류 중인 업데이트 취소**를 클릭합니다.
    

    > [!TIP]
    > 취소한 장치 업데이트 규칙을 다시 제공하지 않으려는 경우에는 규칙을 삭제할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-remove-a-device-update-rule.md">장치 업데이트 규칙 제거</A>를 참조하십시오.



## Windows PowerShell cmdlet을 사용하여 장치 업데이트 규칙 다시 설정

Windows PowerShell 및 **Reset-CsDeviceUpdateRule** cmdlet을 사용하여 장치 업데이트 규칙을 다시 설정할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.



## 서버에서 특정 장치 업데이트 규칙을 다시 설정하려면

  - 다음 명령은 WebServer:atl-cs-001.litwareinc.com 웹 서버에서 장치 업데이트 규칙 d5ce3c10-2588-420a-82ac-dc2d9b1222ff9를 다시 설정합니다.
    
        Reset-CsDeviceUpdateRule -Identity "service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9"

## 서버에서 모든 장치 업데이트 규칙을 다시 설정하려면

  - 이 명령은 atl-cs-001.litwareinc.com 웹 서버의 모든 장치 업데이트 규칙을 다시 설정합니다.
    
        Get-CsDeviceUpdateRule -Filter "service:WebServer:atl-cs-001.litwareinc.com*"  | Reset-CsDeviceUpdateRule

## 특정 브랜드가 지정된 모든 장치 업데이트 규칙을 다시 설정하려면

  - 이 예제에서는 Brand가 Microsoft인 조직 전체의 모든 장치 업데이트를 다시 설정합니다.
    
        Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "Microsoft"} | Reset-CsDeviceUpdateRule

자세한 내용은 [Reset-CsDeviceUpdateRule](https://docs.microsoft.com/en-us/powershell/module/skype/Reset-CsDeviceUpdateRule) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[장치 업데이트 규칙 승인](lync-server-2013-approve-a-device-update-rule.md)

