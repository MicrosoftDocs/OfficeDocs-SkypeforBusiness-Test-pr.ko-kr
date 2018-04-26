---
title: 필수 및 선택적 매개 변수
TOCTitle: 필수 및 선택적 매개 변수
ms:assetid: e766362f-e2e9-4598-a595-fdf5eedd9ad6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362851(v=OCS.15)
ms:contentKeyID: 56270312
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 필수 및 선택적 매개 변수

 

_**마지막으로 수정된 항목:** 2015-06-22_

Windows PowerShell 매개 변수는 필수 또는 선택 중 하나의 범주에 속합니다. *필수 매개 변수*는 명령을 실행할 때 포함해야 하는 매개 변수입니다. 예를 들어 [Remove-CsUserAcp](remove-csuseracp.md) cmdlet은 이전에 사용자에게 할당한 오디오 회의 공급자의 할당을 해제하는 데 사용됩니다. **the Remove-CsUserAcp** cmdlet을 실행할 경우 Identity 매개 변수를 포함해야 합니다. 해당 매개 변수는 오디오 회의 공급자를 제거해야 하는 사용자를 cmdlet에 알려 줍니다. 매개 변수 없이 이 명령을 실행하면 아무런 효과가 없습니다.

    Remove-CsUserAcp

이와 같은 경우에 cmdlet은 어떤 사용자의 오디오 회의 공급자를 제거해야 하는지 전혀 알지 못합니다. 대신 사용자의 ID를 지정해야 합니다.

    Remove-CsUserAcp -Identity "Ken Myer"

일반적으로 Windows PowerShell에서는 명령을 실행할 때 필수 매개 변수가 누락되면 메시지를 표시합니다. 예를 들어 다음을 입력한 뒤 Enter 키를 누릅니다.

    Remove-CsUserAcp

이 경우 Windows PowerShell에서는 이러한 불완전한 명령을 실행하지 않습니다. 대신 누락된 필수 매개 변수를 묻는 메시지를 표시합니다.

    cmdlet Remove-CsUserAcp(명령 파이프라인 위치 1)
    다음 매개 변수에 대한 값을 제공하십시오.
    ID:

올바른 Identity 매개 변수를 입력하고 Enter 키를 누르면 Windows PowerShell에서 **Remove-CsUserAcp** cmdlet을 실행하여 오디오 회의 공급자를 제거합니다. 명령을 실행하지 않기로 결정한 경우에는 Ctrl-C를 눌러 명령을 종료합니다.

이는 완벽한 시스템이 아니며 Windows PowerShell에서 항상 필요한 매개 변수 집합을 묻는 메시지를 표시하지 않을 수도 있습니다. 예를 들어, 일부 cmdlet은 매개 변수 A 또는 매개 변수 B(두 매개 변수가 동시에 필요하지는 않음)를 필수로 사용하도록 구성됩니다. Windows PowerShell에서 매개 변수 A 및 B를 모두 묻는 메시지를 표시할 수 있지만 같은 명령에서 매개 변수 A 및 매개 변수 B를 함께 사용할 수 없기 때문에 명령이 실패합니다. 이와 같은 이유로 Windows PowerShell에서 필요한 정보를 물을 때까지 기다리지 않고 명령을 실행하기 전에 필수 매개 변수를 모두 포함하는 것이 가장 좋습니다.

매개 변수 값의 서식을 지정하는 방법 역시 경우에 따라 직관적이지 못할 수 있습니다. 예를 들어 공백이 들어 있는 매개 변수 값을 포함하는 경우 해당 값을 큰따옴표로 묶어야 합니다.

    -Identity "Ken Myer"

그러나 큰따옴표는 매개 변수와 매개 변수 값을 실행할 명령의 일부로 입력할 경우에만 사용해야 합니다. **Remove-CsUserAcp** cmdlet을 실행했지만 실수로 Identity 매개 변수를 제외한 경우 Windows PowerShell에서 사용자 ID를 묻는 메시지를 표시합니다.

    cmdlet Remove-CsUserAcp(명령 파이프라인 위치 1)
    다음 매개 변수에 대한 값을 제공하십시오.
    ID:

따라서 Identity 매개 변수인 Ken Myer를 큰따옴표로 묶어 입력했습니다.

    cmdlet Remove-CsUserAcp(명령 파이프라인 위치 1)
    다음 매개 변수에 대한 값을 제공하십시오.
    ID: "Ken Myer"

이렇게 하면 명령이 실패하고 다음 오류 메시지가 표시됩니다.

    Remove-CsUserAcp : ID ""Ken Myer""에 대한 관리 개체가 없습니다.

이 경우 ID가 "Ken Myer"인 사용자를 검색합니다. 이때 큰따옴표가 Identity 매개 변수의 일부로 포함합니다. 매개 변수 값을 입력하라는 메시지가 나타나면 큰따옴표를 포함하지 않고 입력합니다.

    cmdlet Remove-CsUserAcp(명령 파이프라인 위치 1)
    다음 매개 변수에 대한 값을 제공하십시오.
    ID: Ken Myer

그에 비해 *선택적 매개 변수*는 이름 그대로 cmdlet을 실행하기 위해 매개 변수를 입력할 필요는 없습니다. 예를 들어 Remove-CsUserAcp에는 선택적 매개 변수 Name이 있습니다. Name 매개 변수가 명령에 포함되어 있으면 지정된 오디오 회의 공급자만 제거됩니다. 다음 명령은 이름이 Fabrikam ACP인 오디오 회의 공급자를 제거하지만 Ken Myer에게 할당된 다른 오디오 회의 공급자는 제거하지 않습니다.

    Remove-CsUserAcp -Identity "Ken Myer" -Name "Fabrikam ACP"

이 선택적 매개 변수를 제외해도 명령이 여전히 실행됩니다. 그러나 이 경우 Remove-CsUserAcp는 Ken Myer에게 할당된 모든 오디오 회의 공급자를 삭제합니다.

    Remove-CsUserAcp -Identity "Ken Myer"

## 참고 항목

#### 개념

[Windows PowerShell 및 Lync Online 소개](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

