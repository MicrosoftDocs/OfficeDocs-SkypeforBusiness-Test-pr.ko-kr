---
title: 장치 업데이트 규칙 가져오기
TOCTitle: 장치 업데이트 규칙 가져오기
ms:assetid: 919e9c87-912b-4bc9-92e7-5998fc2e0bf0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994056(v=OCS.15)
ms:contentKeyID: 52056904
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치 업데이트 규칙 가져오기

 

_**마지막으로 수정된 항목:** 2013-02-23_

장치 업데이트 규칙은 Windows PowerShell 및 **Import-CsDeviceUpdate** cmdlet을 통해서만 가져올 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.




## 단일 웹 서버로 장치 업데이트 규칙을 가져오려면

  - 다음 명령은 장치 업데이트 규칙을 웹 서버 atl-cs-001.litwareinc.com으로 가져옵니다.
    
        Import-CsDeviceUpdate -Identity "service:WebServer:atl-cs-001.litwareinc.com" -FileName C:\Updates\UCUpdates.cab

## 모든 웹 서버로 장치 업데이트 규칙을 가져오려면

  - 이 예제에서는 조직에 배포된 모든 웹 서버로 장치 업데이트 규칙을 가져옵니다. 이 명령이 작동하려면 \\\\atl-fs-001.litwareinc.com\\Updates 폴더가 모든 웹 서버에서 공유되며 사용 가능해야 합니다.
    
        Get-CsService -WebServer | ForEach-Object {Import-CsDeviceUpdate -Identity $_.Identity -FileName \\atl-fs-001.litwareinc.com\Updates\UCUpdates.cab}

자세한 내용은 [Import-CsDeviceUpdate](import-csdeviceupdate.md) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[장치 업데이트 규칙에 대한 정보 보기](lync-server-2013-view-information-about-device-update-rules.md)  
[장치 업데이트 규칙 승인](lync-server-2013-approve-a-device-update-rule.md)

