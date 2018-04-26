---
title: 'Lync Server 2013: 아웃바운드 통화에 대한 음성 경로 구성'
TOCTitle: 아웃바운드 통화에 대한 음성 경로 구성
ms:assetid: 3c182cdd-7a4a-4a9d-bdac-4199f0abd947
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425890(v=OCS.15)
ms:contentKeyID: 49303371
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 아웃바운드 통화에 대한 음성 경로 구성

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server 2013 음성 경로는 대상 전화 번호를 하나 이상의 PSTN(공중 전화망) 게이트웨이 또는 SIP 트렁크 및 하나 이상의 PSTN 사용 레코드와 연결합니다.

**Lync Server 제어판을 사용하여 음성 경로를 보려면**

1.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

2.  **음성 라우팅**을 클릭합니다.

3.  **경로** 를 클릭합니다.

4.  음성 경로를 두 번 클릭하여 음성 경로 목록에서 추가 속성을 보거나 경로를 선택하고 **편집** 을 클릭한 후 **세부 정보 표시** 를 클릭합니다.
    

    > [!NOTE]
    > 한 번에 하나씩 단일 경로에 대한 자세한 정보만 볼 수 있습니다.



**Windows PowerShell을 사용하여 음성 경로를 보려면**

  - Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다. 음성 경로는 Windows PowerShell 및 **Get-CsVoiceRoute** cmdlet을 사용해서 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.
    
    모든 음성 경로에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsVoiceRoute
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity          : global
        Priority          : -1
        Description       :
        NumberPattern     : ^(\+1[0-9]{10})$
        PstnUsages        : {}
        PstnGatewayList   : {}
        Name              : global
        SuppressCallerId  :
        AlternateCallerId :


> [!NOTE]
> 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-voice-routes.md">Lync Server 2013의 음성 경로</A>을 참고하세요.



## 이 단원의 내용

  - [Lync Server 2013에서 음성 경로 만들기](lync-server-2013-create-a-voice-route.md)

  - [Lync Server 2013에서 음성 경로 수정](lync-server-2013-modify-a-voice-route.md)

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 음성 라우팅 관리](lync-server-2013-managing-voice-routing.md)

