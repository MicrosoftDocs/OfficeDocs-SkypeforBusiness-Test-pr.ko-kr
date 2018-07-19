---
title: 장치와 연결되지 않은 장치 업데이트 파일 제거
TOCTitle: 장치와 연결되지 않은 장치 업데이트 파일 제거
ms:assetid: ecebbf73-b456-4990-a91d-308b84d39404
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994084(v=OCS.15)
ms:contentKeyID: 52056988
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치와 연결되지 않은 장치 업데이트 파일 제거

 

_**마지막으로 수정된 항목:** 2013-02-20_

시스템에 새 장치 업데이트를 업로드할 때마다 해당 장치 업데이트 규칙이 만들어집니다. 기본적으로 새 장치 업데이트 규칙은 보류 중 상태에 할당됩니다. 따라서 테스트 장치에서는 규칙을 다운로드 및 설치할 수 있지만 프로덕션 장치에서는 이러한 작업을 수행할 수 없으므로, 사용자에게 업데이트를 제공하기 전에 업데이트를 테스트할 수 있습니다. 테스트 결과에 따라 업데이트를 수락하고 배포하거나 거부하고 삭제할 수 있습니다. 업데이트를 거부하면 장치 업데이트 규칙에서 장치 업데이트의 연결이 해제됩니다.


장치와 더 이상 연결되어 있지 않은 장치 업데이트 파일은 Windows PowerShell 및 **Clear-CsDeviceUpdateFile** cmdlet을 통해 제거할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.




  - 예를 들어 다음 명령은 웹 서버 atl-cs-001.litwareinc.com에서 장치와 더 이상 연결되어 있지 않은 모든 장치 업데이트 규칙을 제거합니다.
    
        Clear-CsDeviceUpdateFile -Identity "service:WebServer:atl-cs-001.litwareinc.com"

자세한 내용은 [Clear-CsDeviceUpdateFile](https://docs.microsoft.com/en-us/powershell/module/skype/Clear-CsDeviceUpdateFile) cmdlet의 도움말 항목을 참조하십시오.

