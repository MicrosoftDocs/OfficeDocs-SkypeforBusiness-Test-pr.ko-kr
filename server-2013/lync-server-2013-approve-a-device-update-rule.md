---
title: 장치 업데이트 규칙 승인
TOCTitle: 장치 업데이트 규칙 승인
ms:assetid: 9dbb1c9a-be0f-4e13-9234-05501ab43ac5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994053(v=OCS.15)
ms:contentKeyID: 52056908
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치 업데이트 규칙 승인

 

_**마지막으로 수정된 항목:** 2013-02-23_

장치 업데이트 규칙을 가져오고 나면 테스트 장치에 해당 규칙이 설치됩니다. 테스트가 정상적으로 완료되어 조직에 업데이트를 제공하려는 경우에는 Lync Server 제어판 또는 Windows PowerShell을 사용하여 규칙을 승인합니다.

## Lync Server 제어판을 사용하여 장치 업데이트 규칙을 승인하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  **장치 업데이트** 페이지에서 다음 중 하나를 수행합니다.
    
      - 규칙 하나를 승인하려면 해당 규칙을 선택합니다.
    
      - 모든 규칙을 승인하려면 **편집**, **모두 선택**을 차례로 클릭합니다.

4.  **작업**, **승인**을 차례로 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 장치 업데이트 규칙 승인

Windows PowerShell 및 **Approve-CsDeviceUpdateRule** cmdlet을 사용하여 장치 업데이트 규칙을 승인할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.



## 단일 장치 업데이트 규칙을 승인하려면

  - 다음 명령은 WebServer:atl-cs-001.litwareinc.com 웹 서버에서 찾은 장치 업데이트 규칙 d5ce3c10-2588-420a-82ac-dc2d9b1222ff9를 승인합니다.
    
        Approve-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9

## 여러 장치 업데이트 규칙을 승인하려면

  - 이 명령은 Microsoft 브랜드 장치에 대한 모든 장치 업데이트 규칙을 승인합니다.
    
        Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "Microsoft"} | Approve-CsDeviceUpdateRule

자세한 내용은 [Approve-CsDeviceUpdateRule](https://docs.microsoft.com/en-us/powershell/module/skype/Approve-CsDeviceUpdateRule) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[장치 업데이트 규칙 가져오기](lync-server-2013-import-device-update-rules.md)  
[장치 업데이트 규칙 복원](lync-server-2013-restore-a-device-update-rule.md)

