---
title: 'Lync Server 2013: 마이그레이션된 사용자 롤백'
TOCTitle: 마이그레이션된 사용자 롤백
ms:assetid: bfabaf0b-9a42-4057-b729-a7ab9eee8c72
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205224(v=OCS.15)
ms:contentKeyID: 49304895
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 마이그레이션된 사용자 롤백

 

_**마지막으로 수정된 항목:** 2012-10-07_

통합 연락처 저장소 기능을 롤백해야 한다면 사용자를 Exchange 2010 또는 Lync Server 2010으로 다시 이동하는 경우에만 연락처를 롤백하십시오. 롤백하려면 사용자에 대한 정책을 사용하지 않도록 설정한 후에 **Invoke-CsUcsRollback** cmdlet을 실행합니다. **Invoke-CsUcsRollback**을 실행하는 것만으로는 영구적인 롤백을 보장하기에 충분하지 않습니다. 정책을 사용하지 않도록 설정하지 않을 경우 통합 연락처 저장소 마이그레이션이 다시 시작되기 때문입니다. 예를 들어 Exchange 2013을 Exchange 2010으로 롤백하기 때문에 사용자를 롤백하고 사용자의 사서함을 Exchange 2013으로 이동할 경우 사용자 서비스 정책에 사용자가 통합 연락처 저장소를 사용할 수 있도록 설정되어 있다면 롤백 후 7일 후에 통합 연락처 저장소 마이그레이션이 다시 시작됩니다.


> [!IMPORTANT]
> <STRONG>Move-CsUser</STRONG> cmdlet은 다음 상황에서 사용자의 연락처 저장소를 Exchange 2013에서 Lync Server 2013으로 자동으로 롤백합니다. 
> <UL>
> <LI>
> <P>사용자가 Lync Server 2013에서 Lync Server 2010으로 이동되는 경우</P>
> <LI>
> <P>사용자가 비즈니스용 Skype Online에서 Lync Server 2013 온-프레미스로 이동되거나 그 반대로 이동되는 것과 같이 사용자가 프레미스 간 마이그레이션되는 경우</P></LI></UL>




> [!IMPORTANT]
> 백업 데이터베이스에서 통합 연락처 저장소 데이터를 가져올 경우 통합 연락처 저장소 모드가 내보내기와 가져오기 간에 변경되면 통합 연락처 저장소 데이터 및 사용자 데이터가 손상될 수 있습니다. 예를 들면 다음과 같습니다. 
> <UL>
> <LI>
> <P>사용자의 대화 상대를 Exchange 2013으로 마이그레이션하기 전에 대화 상대 목록을 내보내고 마이그레이션 후 같은 데이터를 가져오면 통합 연락처 저장소 데이터 및 대화 상대 목록이 손상됩니다.</P>
> <LI>
> <P>사용자를 Exchange 2013으로 마이그레이션한 후에 사용자 데이터를 내보내고 마이그레이션을 롤백한 다음 어떤 이유로 마이그레이션된 후의 데이터를 가져오면 통합 연락처 저장소 데이터 및 대화 상대 목록이 손상됩니다.</P></LI></UL>




> [!IMPORTANT]
> Exchange 사서함을 Exchange 2013에서 Exchange 2010으로 이동하기 전에 Exchange 관리자는 Lync Server 관리자가 먼저 Lync Server 사용자 대화 상대를 Exchange 2013에서 Lync Server로 롤백했는지 확인해야 합니다. 통합 연락처 저장소 대화 상대를 Lync Server로 롤백하려면 이 섹션의 뒷부분에 나오는 "통합 연락처 저장소 대화 상대를 Exchange 2013에서 Lync Server 2013으로 롤백하려면" 절차를 참조하십시오.



다음 절차에서는 사용자 대화 상대를 롤백하는 방법에 대해 설명합니다. **Move-CsUser** cmdlet을 사용하여 Lync Server 2013과 Lync Server 2010 간에 사용자를 이동하는 경우 이러한 단계를 건너뛰어도 됩니다. **Move-CsUser** cmdlet이 사용자를 Lync Server 2013에서 Lync Server 2010으로 이동할 때 통합 연락처 저장소를 자동으로 롤백하기 때문입니다. **Move-CsUser**는 통합 연락처 저장소 정책을 사용하지 않도록 설정하지 않기 때문에 사용자가 Lync Server 2013으로 이동된 후에 통합 연락처 저장소로의 마이그레이션이 다시 이루어집니다.

## 사용자 대화 상대를 Lync Server 2013에서 Lync Server 2010으로 롤백하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  사용자가 롤백 후 다시 마이그레이션되지 않도록, 롤백할 사용자의 통합 연락처 저장소를 사용하지 않도록 설정합니다. 이후에 사용자가 다시 마이그레이션되지 않도록 하려는 경우에만 이 단계를 수행합니다. 개별 사용자의 통합 연락처 저장소를 사용하지 않도록 설정하려면 명령줄에 다음을 입력합니다.
    
        Set-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $False
    
    예를 들면 다음과 같습니다.
    
        Set-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $False

3.  사용자를 Lync Server 2013에서 Lync Server 2010으로 이동하기 전에 Lync Server에서 지정된 사용자의 대화 상대 목록을 롤백합니다.
    

    > [!IMPORTANT]
    > 이 단계를 생략할 경우 대화 상대 목록이 손실됩니다.



4.  명령줄에 다음을 입력하여 지정된 사용자를 롤백합니다.
    
        Invoke-CsUcsRollback -Identity "<user display name>"
    
    예를 들면 다음과 같습니다.
    
        Invoke-CsUcsRollback -Identity "Ken Myer"
    

    > [!IMPORTANT]
    > -Force 옵션을 사용하여 강제로 롤백하는 것은 좋지 않습니다. 이 옵션을 사용할 경우 사용자의 대화 상대가 손실됩니다.



## 통합 연락처 저장소 대화 상대를 Exchange 2013에서 Lync Server 2013으로 롤백하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  사용자가 롤백 후 다시 마이그레이션되지 않도록, 롤백할 사용자의 통합 연락처 저장소를 사용하지 않도록 설정합니다. 개별 사용자의 통합 연락처 저장소를 사용하지 않도록 설정하려면 명령줄에 다음을 입력합니다.
    
        Set-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $False
    
    예를 들면 다음과 같습니다.
    
        Set-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $False

3.  명령줄에 다음을 입력하여 지정된 사용자를 롤백합니다.
    
        Invoke-CsUcsRollback -Identity "<user display name>"
    
    예를 들면 다음과 같습니다.
    
        Invoke-CsUcsRollback -Identity "Ken Myer"
    

    > [!IMPORTANT]
    > 먼저 Lync Server 사용자를 롤백한 후에 Exchange 2013 사서함을 이동해야 합니다. Exchange 관리자는 Lync Server 롤백이 완료될 때까지 Exchange를 롤백하지 못하도록 차단됩니다.-Force 옵션을사용하여 강제로 롤백하는 것은 좋지 않습니다. 이 옵션을 사용할 경우 사용자의 대화 상대가 손실됩니다.



4.  사용자가 Lync Server로 롤백되고 나면 Exchange 관리자가 해당 Exchange 사용자를 Exchange 2013에서 Exchange 2010으로 롤백할 수 있습니다.

