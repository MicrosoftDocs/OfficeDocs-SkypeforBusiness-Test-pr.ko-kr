---
title: 장치 업데이트 규칙에 대한 정보 보기
TOCTitle: 장치 업데이트 규칙에 대한 정보 보기
ms:assetid: d6677ca4-024b-4816-8511-8d7630788107
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994077(v=OCS.15)
ms:contentKeyID: 52056966
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 장치 업데이트 규칙에 대한 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

업데이트가 적용되는 장치의 유형/모델/브랜드, 업데이트의 버전/유형 및 업데이트 로캘/풀을 비롯하여 이미 가져온 장치 업데이트 규칙에 대한 세부 정보를 확인합니다. 승인 보류 중인 규칙, 배포(승인)된 규칙, 회수(복원)된 규칙 및 사용하지 않으려는(다시 설정된) 규칙 등 가져온 모든 장치 업데이트 규칙에 대한 정보를 확인할 수 있습니다. Lync Server 제어판 또는 Windows PowerShell에서 이 정보에 액세스합니다.


> [!NOTE]
> 규칙 가져오기/승인/다시 설정/복원/제거 방법에 대한 자세한 내용은 <A href="lync-server-2013-device-update-rules.md">Lync Server 2013의 장치 업데이트 규칙</A>에 나와 있는 항목을 참조하십시오.



## Lync Server 제어판을 사용하여 장치 업데이트 규칙을 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **장치 업데이트** 탐색 단추를 클릭합니다. 가져온 규칙은 **장치 업데이트** 페이지에 표시됩니다.

## Windows PowerShell cmdlet을 사용하여 장치 업데이트 규칙 보기

Windows PowerShell 및 **Get-CsDeviceUpdateRule** cmdlet을 사용하여 모든 장치 업데이트 규칙에 대한 자세한 정보를 볼 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.



## 모든 장치 업데이트 규칙을 보려면

  - 다음 명령은 조직에서 사용하도록 구성된 모든 장치 업데이트 규칙에 대한 정보를 반환합니다.
    
        Get-CsDeviceUpdateRule
    
    이 명령은 각 장치 업데이트 규칙에 대해 다음과 같은 정보를 반환합니다.
    
        Identity        : Service:WebServer:pool0.vdomain.com/2de8cbf6-9441-4f61-b755-1e4bef1effde
        Id              : 2de8cbf6-9441-4f61-b755-1e4bef1effde
        DeviceType      : UCPhone
        Brand           : Microsoft
        Model           : CPE
        Revision        : A
        Locale          : ENU
        UpdateType      : CPE
        ApprovedVersion :
        RestoreVersion  :
        PendingVersion  : 4.0.7577.4066

## 특정 웹 서버의 모든 장치 업데이트 규칙을 보려면

  - 특정 컴퓨터의 장치 업데이트 규칙을 보려면 Filter 매개 변수 뒤에 서버 ID 및 와일드카드 문자(\*)를 차례로 붙여서 사용합니다. 예를 들면 다음과 같습니다.
    
        Get-CsDeviceUpdateRule -Filter "service:WebServer:atl-cs-001.litwareinc.com*"

자세한 내용은 [Get-CsDeviceUpdateRule](get-csdeviceupdaterule.md) cmdlet의 도움말 항목을 참조하십시오.

