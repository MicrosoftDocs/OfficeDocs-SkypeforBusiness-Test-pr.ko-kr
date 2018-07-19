---
title: 통합 연락처 저장소를 사용하도록 Microsoft Lync Server 2013 구성
TOCTitle: 통합 연락처 저장소를 사용하도록 Microsoft Lync Server 2013 구성
ms:assetid: 6aa17ae3-764e-4986-a900-85a3cdb8c1fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688083(v=OCS.15)
ms:contentKeyID: 49885800
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 통합 연락처 저장소를 사용하도록 Microsoft Lync Server 2013 구성

 

_**마지막으로 수정된 항목:** 2014-02-07_

통합 연락처 저장소를 통해 사용자는 단일 연락처 목록을 유지 관리하고 Microsoft Lync 2013, Microsoft Outlook 2013 및 Microsoft Outlook Web App 2013 등 여러 응용 프로그램에서 해당 연락처를 사용할 수 있습니다. 사용자에 대해 통합 연락처 저장소를 사용하도록 설정해도 해당 사용자의 연락처는 Microsoft Lync Server 2013에 저장되지 않으며, SIP 프로토콜을 사용하여 검색되지 않습니다. 대신 이 사용자의 연락처는 Microsoft Exchange Server 2013에 저장되며 Exchange 웹 서비스를 사용하여 검색됩니다.


> [!NOTE]
> 기술적으로 연락처 정보는 사용자의 Exchange 2013 사서함에 있는 폴더 쌍에 저장됩니다. 연락처 자체는 최종 사용자에게 표시되는 Lync 연락처라는 이름의 폴더에 저장되고, 연락처에 대한 메타데이터는 최종 사용자에게 표시되지 않는 하위 폴더에 저장됩니다.



## 사용자에 대해 통합 연락처 저장소를 사용하도록 설정

Lync Server 2013 및 Exchange 2013 사이에 서버 간 인증을 이미 구성한 경우 통합 연락처 저장소가 이미 사용하도록 설정되어 있으며, 추가 서버 구성은 필요하지 않습니다. 하지만 사용자의 연락처를 통합 연락처 저장소로 이동하기 위해서는 추가 사용자 계정 구성이 필요합니다. 기본적으로 사용자 연락처는 통합 연락처 저장소가 아닌 Lync Server에 보관됩니다.

통합 연락처 저장소에 대한 액세스는 Lync Server 사용자 서비스 정책을 사용하여 관리됩니다. 사용자 서버 정책은 단일 속성(UcsAllowed)만 포함하며, 이 속성은 사용자의 연락처가 저장된 위치를 확인하는 데 사용됩니다. UcsAllowed가 True($True)로 설정된 사용자 서비스 정책에 의해 사용자가 관리될 경우 사용자의 연락처는 통합 연락처 저장소에 저장됩니다. UcsAllowed가 False($False)로 설정된 사용자 서비스 정책에 의해 사용자가 관리될 경우에는 사용자의 연락처가 Lync Server에 저장됩니다.

Lync Server 2013을 설치하면 단일 사용자 서비스 정책(전역 범위로 구성됨)도 함께 설치됩니다. 이 정책에서 UcsAllowed 값은 True로 설정됩니다. 즉, 기본적으로 사용자 연락처는 통합 연락처 저장소에 저장됩니다(이 저장소가 배포 및 구성된 것으로 간주). 모든 사용자 연락처를 통합 연락처 저장소로 마이그레이션하기 위해 수행해야 하는 작업은 없습니다.

모든 연락처를 통합 연락서 저장소로 마이그레이션하지 않으려면 글로벌 정책의 UcsAllowed 속성을 False로 설정하여 모든 사용자에 대해 통합 연락처 저장소가 사용되지 않도록 설정할 수 있습니다.

    Set-CsUserServicesPolicy -Identity global -UcsAllowed $False

글로벌 정책에서 통합 연락처 저장소를 사용하지 않도록 설정한 후에는 통합 연락처 저장소를 사용하도록 설정하는 사용자별 정책을 만들 수 있습니다. 이렇게 하면 일부 사용자의 연락처를 통합 연락처 저장소에 보관하면서 다른 사용자의 연락처는 Lync Server에 계속 보관할 수 있습니다. 사용자별 사용자 서비스 정책은 다음과 비슷한 명령을 사용하여 만들 수 있습니다.

    New-CsUserServicesPolicy -Identity "AllowUnifiedContactStore" -UcsAllowed $True

새 정책을 만든 후에는 통합 연락처 저장소에 액세스해야 하는 사용자에게 해당 정책을 지정해야 합니다. 사용자별 정책은 다음과 비슷한 명령을 사용하여 사용자에게 지정할 수 있습니다.

    Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName "AllowUnifiedContactStore"

정책을 지정한 후 Lync Server는 사용자의 연락처를 통합 연락처 저장소로 마이그레이션하는 작업을 시작합니다. 마이그레이션이 완료된 후에는 사용자의 연락처가 Lync Server가 아닌 Exchange에 저장됩니다. 마이그레이션이 완료되었을 때 사용자가 Lync 2013에 로그온하면 메시지 상자가 나타나고 프로세스를 종료하기 위해 Lync에서 로그오프하고 다시 로그온하라는 요청이 표시됩니다. 이 사용자별 정책이 지정되지 않은 사용자의 연락처는 통합 연락처 저장소로 마이그레이션되지 않습니다. 이러한 사용자는 글로벌 정책에 의해 관리되며 해당 글로벌 정책에서 통합 연락처 저장소가 사용되지 않도록 설정되었기 때문입니다.

사용자의 연락처가 통합 연락처 저장소에 성공적으로 마이그레이션되었는지 여부는 Lync Server 관리 셸 내에서 [Test-CsUnifiedContactStore](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsUnifiedContactStore) cmdlet을 실행하여 확인할 수 있습니다.

    Test-CsUnifiedContactStore -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com"

Test-CsUnifiedContactStore가 성공하면 sip:kenmyer@litwareinc.com 사용자의 연락처가 통합 연락처 저장소에 마이그레이션되었음을 의미합니다.

## 통합 연락처 저장소 롤백

통합 연락처 저장소에서 사용자의 연락처를 제거하려는 경우(예: 사용자를 다시 Microsoft Lync Server 2010에 지정해서 해당 사용자가 더 이상 통합 연락처 저장소를 사용할 수 없도록 설정하려는 경우) 두 가지 작업을 수행해야 합니다. 첫째, 사용자에게 통합 연락처 저장소에 연락처를 저장하지 못하도록 금지하는 새로운 사용자 서비스 정책을 지정해야 합니다(즉, UcsAllowed 속성이 $False로 설정된 정책). 이러한 정책이 없으면 다음과 비슷한 명령을 사용해서 정책을 만들 수 있습니다.

    New-CsUserServicesPolicy -Identity NoUnifiedContactStore -UcsAllowed $False

그런 후 다음과 비슷한 명령을 사용해서 이 새로운 사용자별 정책(NoUnifiedContactStore)을 지정할 수 있습니다.

    Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName NoUnifiedContactStore

위 명령은 새로운 정책을 사용자 Ken Myer에게 지정하고 Ken의 연락처가 통합 연락처 저장소로 마이그레이션되지 않도록 방지합니다.


> [!NOTE]
> 일부 경우에는 사용자의 현재 사용자 서비스 정책을 단순히 지정 해제함으로써 동일한 효과를 얻을 수 있습니다. 예를 들어 Ken Myer에게 통합 연락처 저장소를 사용할 수 있는 사용별 사용자 서비스 정책이 포함되고, 글로벌 정책에 의해 통합 연락처 저장소 사용이 금지된다고 가정해보십시오. 이 경우에는 Ken의 사용자별 서비스 정책을 지정 해제할 수 있습니다. 이렇게 하면 Ken이 자동으로 글로벌 정책에 의해 관리되므로 더 이상 통합 연락처 저장소에 액세스할 수 없게 됩니다.<BR>이전에 지정한 사용자별 정책을 지정 해제하려면 이전에 표시된 것과 동일한 명령을 사용하되, 이번에는 PolicyName 매개 변수를 null 값으로 설정합니다.<BR>Grant-CsUserServicesPolicy –Identity "Ken Myer" –PolicyName $Null



통합 연락처 저장소를 사용할 때는 "Ken의 연락처가 통합 연락처 저장소로 마이그레이션되지 않도록 방지"한다는 표현을 기억해야 합니다. 단순히 Ken에게 새로운 사용자 서비스 정책을 지정한다고 해서 이 사용자의 연락처가 통합 연락처 저장소에서 제거되는 것은 아닙니다. 사용자가 Lync Server 2013에 로그온하면 시스템이 해당 사용자의 사용자 서비스 정책을 검사해서 이 사용자의 연락처를 통합 연락처 저장소에 보관해야 하는지 여부를 확인합니다. 답변이 예인 경우(즉, UcsAllowed 속성이 $True로 설정된 경우)에는 해당 연락처가 통합 연락처 저장소로 마이그레이션됩니다(해당 연락처가 아직 통합 연락처 저장소에 없다고 가정). 답변이 아니요인 경우 Lync Server는 단순히 사용자의 연락처를 무시하고 다음 작업으로 이동합니다. 즉, UcsAllowed 속성의 값에 관계없이 Lync Server가 사용자의 연락처를 통합 연락처 저장소에서 자동으로 제거하지 않습니다.

따라서 사용자에게 새 사용자 서비스 정책을 지정한 후[Invoke-CsUcsRollback](https://docs.microsoft.com/en-us/powershell/module/skype/Invoke-CsUcsRollback) cmdlet을 실행해서 사용자의 연락처를 Exchange 2013에서 Lync Server 2013으로 다시 옮겨야 한다는 것을 의미합니다. 예를 들어 Ken Myer에게 새로운 사용자 서비스 정책을 지정한 후 다음 명령을 사용하여 이 사용자의 연락처를 통합 연락처 저장소에서 제거할 수 있습니다.

    Invoke-CsUcsRollback -Identity "Ken Myer"

사용자 서비스 정책을 변경했지만 Invoke-CsUcsRollback cmdlet을 실행하지 않으면 통합 연락처 저장소에서 Ken의 연락처가 제거되지 않습니다. Invoke-CsUcsRollback을 실행하지만 Ken Myer의 사용자 서비스 정책을 변경하지 않으면 어떻게 될까요? 이 경우에는 Ken의 연락처가 통합 연락처 저장소에서 일시적으로 제거됩니다. 여기서 중요한 것은 이러한 제거가 일시적으로 수행된다는 것입니다. Ken의 연락처가 통합 연락처 저장소에서 제거된 후 Lync Server 2013은 7일간 기다린 후 Ken에게 지정된 사용자 서비스 정책을 확인합니다. Ken에게 여전히 통합 연락처 저장소를 사용할 수 있는 정책이 지정되어 있으면 Ken의 연락처가 자동으로 통합 저장소로 자동으로 이동됩니다. 통합 연락처 저장소에서 연락처를 영구적으로 제거하기 위해서는 Invoke-CsUcsRollback cmdlet을 실행하는 것 외에도 사용자 서비스 정책을 변경해야 합니다.

마이그레이션에 영향을 줄 수 있는 변수는 매우 다양하므로 계정이 통합 연락처 저장소로 완전히 마이그레이션되기 전에는 시간이 얼마나 걸릴지 예상하기가 어렵습니다. 그러나 대개는 마이그레이션이 즉각적으로 실행되지는 않으며, 소수의 연락처를 마이그레이션하는 경우에도 이동이 완료되기 전에는 10분 이상 걸릴 수 있습니다.

