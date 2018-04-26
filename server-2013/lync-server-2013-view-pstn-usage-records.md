---
title: 'Lync Server 2013: PSTN 사용 레코드 보기'
TOCTitle: PSTN 사용 레코드 보기
ms:assetid: 65025c78-c263-472c-9ff9-e170588f10b5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398458(v=OCS.15)
ms:contentKeyID: 49303854
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 PSTN 사용 레코드 보기

 

_**마지막으로 수정된 항목:** 2013-02-22_

PSTN(공중 전화망) 사용 레코드는 조직의 여러 사용자 또는 사용자 그룹이 수행할 수 있는 통화 클래스(내부, 시내, 시외 등)를 지정합니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 PSTN 사용 레코드](lync-server-2013-pstn-usage-records.md)를 참조하십시오.

## Lync Server 제어판을 사용하여 PSTN 사용 레코드를 보려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 CsVoiceAdministrator, CsServerAdministrator 또는 CsAdministrator 역할의 구성원으로 컴퓨터에 로그온합니다. 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)을 참조하세요.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **음성 라우팅** 을 클릭하고 **PSTN 사용** 을 클릭합니다.

4.  **PSTN 사용** 페이지에서 보려는 PSTN 사용 레코드를 강조 표시하고 **편집** 을 클릭한 후에 **세부 정보 표시** 를 클릭합니다.
    

    > [!NOTE]
    > 선택한 PSTN 사용 레코드의 읽기 전용 페이지에 연결된 경로 및 음성 정책이 표시됩니다.



## Windows PowerShell cmdlet을 사용하여 PSTN 사용 정보 보기

또한 Windows PowerShell 및 **Get-CsPstnUsage** cmdlet을 사용하여 PSTN 사용을 볼 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## Windows PowerShell cmdlet을 사용하여 PSTN 사용 정보를 보려면

  - 모든 PSTN 사용에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsPstnUsage
    
    이 명령은 다음과 비슷한 정보를 반환합니다.
    
        Identity : Global
        Usage    : {Internal, Local, Long Distance}

자세한 내용은 [Get-CsPstnUsage](get-cspstnusage.md)을 참고하세요.

## 참고 항목

#### 작업

[Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 만들기](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Lync Server 2013에서 음성 정책 수정 및 PSTN 사용 레코드 구성](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)

