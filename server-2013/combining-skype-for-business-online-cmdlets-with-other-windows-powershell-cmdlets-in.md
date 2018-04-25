---
title: Lync Online Cmdlet과 기타 Windows PowerShell Cmdlet 결합
TOCTitle: Lync Online Cmdlet과 기타 Windows PowerShell Cmdlet 결합
ms:assetid: 8bb8800a-f966-4570-8c8b-db87a91ad783
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362816(v=OCS.15)
ms:contentKeyID: 56270266
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online Cmdlet과 기타 Windows PowerShell Cmdlet 결합

 

_**마지막으로 수정된 항목:** 2015-06-22_

Windows PowerShell을 사용하여 비즈니스용 Skype Online에 연결하면 약 40개의 비즈니스용 Skype Online cmdlet을 사용할 수 있습니다. 그러나 비즈니스용 Skype Online을 관리할 때 이 40개의 cmdlet만 사용하도록 제한되지는 않습니다. 비즈니스용 Skype Online cmdlet 외에도 컴퓨터에 설치되는 다른 Windows PowerShell cmdlet을 사용할 수도 있습니다. Windows PowerShell 3.0을 설치하면 수백 개의 중요 Windows PowerShell cmdlet이 함께 설치됩니다. 명령을 통해 비즈니스용 Skype Online cmdlet과 컴퓨터에서 사용할 수 있는 다른 cmdlet을 조합하여 사용할 수 있습니다.

Windows PowerShell 3.0의 전체 과정이 이 문서의 범위를 벗어나기는 하지만 cmdlet을 조합하여 사용하면 좋은 이유를 보여 주는 몇 가지 예제가 여기에 나와 있습니다. 먼저, 인쇄 명령이 포함되어 있는 비즈니스용 Skype Online cmdlet은 없으며, Windows PowerShell 콘솔에서도 이러한 명령을 찾을 수 없습니다. 그렇다면 cmdlet을 사용하여 검색한 정보의 인쇄물을 어떻게 구할 수 있을까요? 한 가지 방법은 정보를 검색한 후에 해당 정보를 **Out-Printer** cmdlet으로 보내는 것입니다.

    Get-CsTenant | Out-Printer

추가 매개 변수가 포함되어 있지 않기 때문에 **the Out-Printer** cmdlet이 반환하는 모든 정보가 기본 프린터로 인쇄됩니다.

마찬가지로 파일에 데이터를 저장할 수 있는 매개 변수가 포함된 비즈니스용 Skype Online cmdlet은 없지만 다음 명령은 **Out-File** cmdlet을 사용하여 반환된 정보를 C:\\Logs\\Tenants.txt 텍스트 파일에 저장합니다.

    Get-Tenant | Out-File -FilePath "C:\Logs\Tenants.txt"

다음 명령은 **Select-Object** cmdlet을 사용하여 반환되어 화면에 표시되는 데이터를 제합니다. 이 예제에서 [Get-CsOnlineUser](get-csonlineuser.md) cmdlet은 모든 비즈니스용 Skype Online 사용자의 정보를 검색하며, 표시되는 데이터를 사용자의 Indentity 값과 보관 정책으로 제한하기 위해 **Select-Object** cmdlet을 사용합니다.

    Get-CsOnlineUser | Select-Object Identity, ArchivingPolicy

컴퓨터에서 사용할 수 있는 cmdlet의 수가 워낙 많기 때문에 어떤 cmdlet이 비즈니스용 Skype Online cmdlet인지 구분하기 어려울 수 있습니다. To return a list of the 비즈니스용 Skype Online cmdlet 목록(비즈니스용 Skype Online cmdlet만)을 반환하려면 먼저 모든 비즈니스용 Skype Online cmdlet을 포함하는 임시 Windows PowerShell 모듈의 이름을 결정해야 합니다. 이렇게 하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-Module

화면에 다음과 같은 정보가 나타납니다.

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A...}
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl...}

ModuleType Script가 있는 모듈은 비즈니스용 Skype Online cmdlet을 포함하는 모듈입니다. 해당 cmdlet 목록을 반환하려면 Script 모듈의 이름을 모듈 이름으로 사용하여 **Get-Command** cmdlet을 실행합니다.

    Get-Command -Module tmp_5astd3uh.m5v

ModuleType이 Script와 동일한 여러 개의 모듈이 있을 수 있습니다. 이 경우 다음 명령을 실행하여 어떤 모듈에 **Get-CsTenant** cmdlet이 포함되어 있는지 알아볼 수 있습니다.

    Get-Command Get-CsTenant

**Get-CsTenant** cmdlet에 대해 반환되는 모듈이 비즈니스용 Skype Online cmdlet을 포함하는 모듈입니다.

    CommandType     Name                                               ModuleName
    -----------     ----                                               ----------
    Function        Get-CsTenant                                       tmp_5astd3uh.m5v

## 참고 항목

#### 개념

[Windows PowerShell 및 Lync Online 소개](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

