---
title: 'Lync Server 2013: 익명 사용자 액세스 사용 또는 사용 안 함'
TOCTitle: 익명 사용자 액세스 사용 또는 사용 안 함
ms:assetid: f10c19e6-b6f9-4d26-9923-0165f36e4af8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619192(v=OCS.15)
ms:contentKeyID: 49305483
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 익명 사용자 액세스 사용 또는 사용 안 함

 

_**마지막으로 수정된 항목:** 2013-02-23_

익명 사용자는 조직의 Active Directory 도메인 서비스 또는 지원되는 페더레이션된 도메인의 사용자 계정을 가지고 있지는 않지만 온-프레미스 회의에 원격으로 참가하라는 초대를 받은 사용자입니다. 모임에서 익명 참가를 허용하면 익명 사용자(모임 또는 회의 키를 통해서만 ID가 확인되는 사용자)가 모임에 참가할 수 있게 됩니다. 익명 참가를 허용하려면 조직에 대해 익명 참가 기능을 사용하도록 설정해야 합니다.

나중에 익명 사용자의 액세스를 일시적으로 또는 영구적으로 차단하려면 조직에 대해 익명 참가 기능을 사용하지 않도록 설정하면 됩니다. 이 섹션의 절차에 따라 조직에 대해 익명 사용자 액세스를 사용하거나 사용하지 않도록 설정합니다.


> [!NOTE]
> 조직에 대해 익명 사용자 액세스를 사용하도록 설정하면 액세스 에지 서비스를 실행하는 서버만 익명 사용자의 액세스를 지원하도록 지정됩니다. 즉, 회의 정책도 하나 이상 구성하여 한 명 이상의 사용자 또는 하나 이상의 사용자 그룹에 적용할 때까지는 익명 사용자가 조직의 모임에 참가할 수 없습니다. 익명 사용자를 모임에 초대할 수 있는 사용자는 익명 사용자를 지원하도록 구성된 회의 정책이 할당된 사용자뿐입니다. 초대 익명 사용자를 지원하도록 회의 정책을 구성하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-conferencing-policies.md">Lync Server 2013의 회의 정책</A>을 참조하십시오.



## 조직에 대해 익명 사용자 액세스를 사용하거나 사용하지 않도록 설정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **외부 사용자 액세스** 를 클릭하고 **액세스 에지 구성** 을 클릭합니다.

4.  **액세스 에지 구성** 페이지에서 **전역** 을 클릭하고 **편집** 을 클릭한 후에 **세부 정보 표시** 를 클릭합니다.

5.  **액세스 에지 구성 편집** 에서 다음 중 하나를 수행합니다.
    
      - 조직에 대해 익명 사용자 액세스를 사용하도록 설정하려면 **익명 사용자와의 통신 사용** 확인란을 선택합니다.
    
      - 조직에 대해 익명 사용자 액세스를 사용하지 않도록 설정하려면 **익명 사용자와의 통신 사용** 확인란 선택을 취소합니다.

6.  **커밋** 을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 익명 사용자 액세스를 사용하거나 사용하지 않도록 설정

Windows PowerShell 및 **Set-CsAccessEdgeConfiguration** cmdlet을 사용하여 익명 사용자 액세스를 관리할 수 있습니다. Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 이 cmdlet을 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 익명 사용자 액세스를 사용하려면

  - 익명 사용자 액세스를 사용하려면 **AllowAnonymousUsers** 속성의 값을 True($True)로 설정합니다.
    
        Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $True

## 익명 사용자 액세스를 사용하지 않으려면

  - 익명 사용자 액세스를 사용하지 않으려면 **AllowAnonymousUsers** 속성의 값을 False($False)로 설정합니다.
    
        Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $False

## 참고 항목

#### 개념

[Lync Server 2013용 회의 정책 설정 참조](lync-server-2013-conferencing-policy-settings-reference.md)

