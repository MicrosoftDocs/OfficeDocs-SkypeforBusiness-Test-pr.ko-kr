---
title: 하이브리드 배포에서 Windows PowerShell 사용
TOCTitle: 하이브리드 배포에서 Windows PowerShell 사용
ms:assetid: b19625d4-4b68-403c-a072-5296aa590556
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362835(v=OCS.15)
ms:contentKeyID: 56270290
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 하이브리드 배포에서 Windows PowerShell 사용

 

_**마지막으로 수정된 항목:** 2015-06-22_

하이브리드 배포에서 조직의 일부 사용자는 온-프레미스 버전의 Lync Server 2013에 있고 일부 사용자는 비즈니스용 Skype Online에 있습니다. Windows PowerShell의 단일 세션을 사용하여 온-프레미스 버전의 Lync Server와 비즈니스용 Skype Online 테넌트를 동시에 관리할 수 있습니다. 이렇게 하려면 다음 두 가지 중요한 사항을 이해해야 합니다.

1.  Lync Server와 비즈니스용 Skype Online에 동시에 연결하는 방법

2.  이러한 동시 연결에서 비즈니스용 Skype Online 설정을 참조하는 방법

Lync Server와 비즈니스용 Skype Online에 동시에 연결하기는 매우 쉽습니다. 일반적인 방식대로 Lync Server 관리 셸을 시작하거나 프런트 엔드 풀에 대한 원격 연결을 만들어 Lync Server를 연결합니다. 온-프레미스 버전의 Lync Server에 연결한 후에는 비즈니스용 Skype Online에만 연결하는 것과 동일한 방식으로 비즈니스용 Skype Online에 연결할 수 있습니다. 이렇게 연결하려면 먼저 Office 365 로그온 정보를 사용하여 Windows PowerShell 자격 증명 개체를 만들어야 합니다. Windows PowerShell 프롬프트에 다음을 입력한 후 Enter 키를 누릅니다.

    $credential = Get-Credential

Enter 키를 누르면 **Windows PowerShell 자격 증명** 대화 상자가 나타납니다.

![Windows PowerShell 로그인 자격 증명](images/Dn362795.0f04e0a1-c9d6-4341-a0bb-ef721c4815fd(OCS.15).png "Windows PowerShell 로그인 자격 증명")

**사용자 이름** 상자에 비즈니스용 Skype Online 이름을 입력합니다. **암호** 상자에는 비즈니스용 Skype Online 암호(암호는 마스킹되어 화면에 표시되지 않음)를 입력합니다. 예를 들어 사용자 이름이 kenmyer@litwareinc.com이고 암호가 p@ssw0rd\!인 경우 대화 상자는 다음과 같이 표시됩니다.

![Windows PowerShell 자격 증명 로그인](images/Dn362795.85977a0e-b14a-4aec-a45e-8548e9c9f691(OCS.15).png "Windows PowerShell 자격 증명 로그인")

자격 증명 개체를 만들려면 **확인**을 클릭합니다. 자격 증명 개체를 만든 후에는 다음 명령을 실행하여 비즈니스용 Skype Online에 연결할 수 있습니다.

    $session = New-CsOnlineSession -Credential $credential

화면에 나타난 그대로 명령을 입력해야 합니다. 비즈니스용 Skype Online 도메인 이름은 중요하지 않습니다. **New-CsOnlineSession** cmdlet을 통해 Office 365에 연결되고 제공된 자격 증명을 사용해 로그온할 수 있습니다. 연결 및 인증이 완료되면 적절한 URI로 자동 리디렉션됩니다.

연결에 성공하면 Windows PowerShell 콘솔에 다음과 비슷한 메시지가 나타납니다.

    VERBOSE: Determining domain to admin
    VERBOSE: AdminDomain = litwareinc.com
    VERBOSE: Discovering PowerShell endpoint URI
    VERBOSE: TargetUri = https://webdir0d.litwareinc.com/OcsPowerShellLiveId
    VERBOSE: Requesting authentication token
    VERBOSE: Success
    VERBOSE: Initializing remote session
    VERBOSE: Success
    Id Name       ComputerName    State        ConfigurationName     Availability -- ----       ------------    -----        -----------------     ------------
    2 Session2    litwarein...    Opened       Microsoft.PowerShell  Available

비즈니스용 Skype Online에 대한 연결을 올바르게 설정한 후에 다음과 비슷한 명령을 실행하여 해당 세션을 가져옵니다.

    Import-PSSession $session -AllowClobber


> [!NOTE]
> AllowClobber 매개 변수를 사용하여 일반 Lync Server cmdlet과 이름이 같은 cmdlet을 포함하여 모든 비즈니스용 Skype Online cmdlet을 가져왔는지 확인합니다. <A href="get-csmeetingconfiguration.md">Get-CsMeetingConfiguration</A>, <A href="new-csexumcontact.md">New-CsExUmContact</A>, <A href="remove-csvoicepolicy.md">Remove-CsVoicePolicy</A> 등을 비롯해 대부분의 비즈니스용 Skype Online cmdlet에는 온-프레미스에 해당하는 cmdlet이 있기 때문에 이러한 cmdlet의 수는 매우 많습니다. 쌍으로 연결된 cmdlet(예: Lync Server<STRONG>Get-CsMeetingConfiguration</STRONG> cmdlet과 비즈니스용 Skype Online<STRONG>Get-CsMeetingConfiguration</STRONG> cmdlet)은 동일합니다. 어떤 cmdlet을 사용하는지는 중요하지 않습니다. AllowClobber 매개 변수를 사용하는 유일한 이유는 화면에 경고 메시지가 나타나는 것을 방지하려는 것입니다.



이제 온-프레미스 버전의 Lync Server와 비즈니스용 Skype Online을 모두 관리할 수 있습니다. 이 시점에서 Lync Server 정책 및 설정과 비즈니스용 Skype Online 정책 및 설정을 구분하는 방법에 대한 의문이 생길 수도 있습니다. 예를 들어 전역 모임 구성 설정을 변경해야 할 수도 있습니다. 이를 수행하려면 다음 명령을 실행합니다.

    Set-CsMeetingConfiguration -Identity "global" -AdmitAnonymousUsersByDefault $False

이 명령은 전역 설정을 수정합니다. 하지만 어떤 전역 설정인지, 즉 Lync Server 온-프레미스인지 비즈니스용 Skype Online인지, 둘 다인지, 둘 다 아닌지 알 수 없습니다.

이러한 특수한 경우에서는 온-프레미스 설정이 수정됩니다. 이것을 어떻게 알 수 있을까요? 명령에 Tenant 매개 변수가 포함되지 않았기 때문입니다. Lync Server 온-프레미스와 비즈니스용 Skype Online에 동시에 연결되어 있는 경우, 별도로 지정하지 않는 한, 이 중 하나의 플랫폼에서 작동하는 cmdlet이 Lync Server를 대상으로 실행됩니다. 별도로 지정하는 유일한 방법은 명령을 실행할 때 Tenant 매개 변수를 포함하는 것입니다. 예를 들어 이 명령은 비즈니스용 Skype Online 테넌트에 대한 전역 설정을 테넌트 ID bf19b7db-6960-41e5-a139-2aa373474354로 업데이트합니다.

    Set-CsMeetingConfiguration -Identity "global" -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AdmitAnonymousUsersByDefault $False

Tenant 매개 변수가 핵심입니다. 다음 명령은 Lync Server 온-프레미스에 대한 전역 외부 액세스 정책을 반환합니다.

    Get-CsExternalAccessPolicy -Identity "global"

또한 다음 명령은 사용자의 비즈니스용 Skype Online 테넌트에 대한 전역 외부 액세스 정책을 반환합니다.

    Get-CsExternalAccessPolicy -Identity "global" -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

온-프레미스 cmdlet의 수는 700개가 넘습니다. 그러나 대부분의 cmdlet에는 Tenant 매개 변수가 없기 때문에 비즈니스용 Skype Online에서 사용할 수 없습니다. 또한 Tenant 매개 변수가 있는 cmdlet도 몇 개 있기는 하지만 아직 비즈니스용 Skype Online에서 사용할 수는 없습니다. 비즈니스용 Skype Online에서 사용할 수 있는 정확한 cmdlet 집합을 검색하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-Module

화면에 다음과 비슷한 정보가 나타납니다.

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A...}
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl...}

ModuleType 스크립트가 있는 모듈은 비즈니스용 Skype Online cmdlet을 포함하는 모듈입니다. 이러한 cmdlet 목록을 반환하려면 모듈 이름에 스크립트 모듈의 이름을 사용하여 **Get-Command** cmdlet을 실행합니다.

    Get-Command -Module tmp_5astd3uh.m5v

그러면 Windows PowerShell에 모든 비즈니스용 Skype Online cmdlet 목록이 표시됩니다.

**하이브리드 배포에서 연결 문제 해결**

경우에 따라 관리자가 Office 365 계정(예: administrator@litwareinc.onmicrosoft.com) 대신 온-프레미스 계정(예: administrator@litwareinc.net)을 사용하여 Office 365에 로그인할 때 문제가 발생할 수 있습니다. 디렉터리 동기화가 올바르게 작동할 경우 두 계정 중 하나를 사용하여 로그인할 수 있습니다. 이것이 바로 하이브리드 배포의 장점 중 하나입니다. 그러나 관리자가 자신의 온-프레미스 계정을 사용하여 로그온하지 못하는 상황이 발생합니다. 이 문제의 원인은 일반적으로 로그온 시도를 Office 365 대신 Lync Server의 온-프레미스 설치로 지정하는 자동 검색에 있습니다.

다행히 이 문제를 해결하는 쉬운 방법이 하나 있습니다. **New-CsOnlineSession** cmdlet을 사용하여 Office 365에 로그온할 경우 OverrideAdminDomain 매개 변수 뒤에 Office 365 도메인 이름이 오도록 만들면 됩니다. 예를 들어 administrator@litwareinc.net 계정을 사용하여 Office 365에 로그온하려면 OverrideAdminDomain 매개 변수를 포함하고 뒤에 litwareinc.onmicrosoft.com: 도메인 이름을 입력하세요.

    $session = New-CsOnlineSession -Credential $credential -OverrideAdminDomain "litwareinc.onmicrosoft.com"

해당 명령은 로그온 시도를 명확하게 Office 365 서버 및 litwareinc.onmicrosoft.com 도메인에 지정합니다.

