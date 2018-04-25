---
title: 장치 업데이트 로그 파일 삭제
TOCTitle: 장치 업데이트 로그 파일 삭제
ms:assetid: 58d4097f-5bbf-4824-a04d-2a6555cd93c3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994039(v=OCS.15)
ms:contentKeyID: 52056863
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치 업데이트 로그 파일 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

장치 업데이트 웹 서비스에서는 광범위한 로그 파일 집합을 보관합니다. 이 집합에는 서비스 자체에서 생성하는 감사 로그와 클라이언트 장치에서 업로드되는 로그 파일이 모두 포함됩니다. 서버가 장치 업데이트 웹 서비스 서비스 로그로 가득 차지 않도록 하려면 특정 기간(일)이 경과한 로그 파일을 서버에서 지울 수 있습니다. 이 기간(일)은 조직의 클라이언트 장치 수와 업데이트 작업을 기반으로 하여 Lync Server 제어판 또는 Lync Server 관리 셸을 사용해 설정합니다.

## Lync Server 제어판을 사용하여 장치 업데이트 로그를 지우려면

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **장치 로그 구성**을 클릭합니다.

3.  **장치 로그 구성** 페이지에서 변경할 구성을 두 번 클릭합니다.

4.  **로그 설정 편집** 대화 상자의 **로그 파일을 유지할 기간(일)(1~365)**에서 일 수를 지정합니다.

5.  **커밋**을 클릭합니다. 그러면 지정한 일 수보다 오랫동안 서버에 보관되어 있었던 모든 파일이 삭제됩니다. 이 설정은 변경할 때까지 이 구성에 적용됩니다.

## Windows PowerShell cmdlet을 사용하여 장치 업데이트 로그 지우기

Windows PowerShell 및 **Clear-CsDeviceUpdateLog** cmdlet 사용하여 장치 업데이트 로그를 지울 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.



## 단일 서버에서 장치 업데이트 로그를 지우려면

  - 다음 명령은 웹 서버 atl-cs-001.litwareinc.com에서 장치 업데이트 로그를 지웁니다. DaysBack 매개 변수로 지정된 값인 10일보다 오래된 모든 로그 항목이 로그에서 제거됩니다.
    
        Clear-CsDeviceUpdateLog -Identity "service:WebServer:atl-cs-001.litwareinc.com" -DaysBack 10

## 모든 장치 업데이트 로그를 지우려면

  - 다음 명령은 조직에서 현재 사용 중인 모든 장치 업데이트 로그에서 오래된 항목(이 예에서는 10일보다 오래된 항목)을 제거합니다.
    
        Get-CsService -WebServer | Foreach-Object {Clear-CsDeviceUpdateLog -Identity $_.Identity -DaysBack 10}

자세한 내용은 [Clear-CsDeviceUpdateLog](clear-csdeviceupdatelog.md) cmdlet의 도움말 항목을 참조하십시오.

