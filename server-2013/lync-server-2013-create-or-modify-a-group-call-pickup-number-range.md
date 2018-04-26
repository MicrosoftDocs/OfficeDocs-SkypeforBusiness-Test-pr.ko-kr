---
title: 그룹 호출 받기 번호 범위 만들기 또는 수정
TOCTitle: 그룹 호출 받기 번호 범위 만들기 또는 수정
ms:assetid: 4b442b98-df6b-4e50-8254-b3be9cde21dd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945627(v=OCS.15)
ms:contentKeyID: 52056846
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 그룹 호출 받기 번호 범위 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-01-30_

다음 절차에 따라 통화 대기 번호 테이블에서 호출 받기 그룹 번호 범위를 만들거나 수정합니다.


> [!NOTE]
> 통화 대기 번호 테이블에서 그룹 호출 받기 번호 범위를 만들고 수정하고 제거하고 보려면 Lync Server 관리 셸을 사용해야 합니다. Lync Server 제어판에서는 그룹 호출 받기 번호 범위를 사용할 수 없습니다.




> [!IMPORTANT]
> 호출 받기 그룹 번호 범위에는 GroupPickup 유형을 할당해야 합니다. 사용자에게 할당된 그룹 번호의 유형이 GroupPickup이어야 사용자가 그룹 호출 받기를 사용할 수 있습니다.



호출 받기 그룹 번호 범위는 다음 규칙을 따라야 합니다.

  - 범위의 시작 번호는 범위의 마지막 번호보다 작거나 같아야 합니다.

  - 범위의 시작 번호 값 길이는 범위의 마지막 번호 길이와 같아야 합니다.

  - 번호 범위는 고유해야 합니다. 범위가 다른 범위와 겹쳐서는 안 됩니다.

  - 번호 범위가 \* 또는 \# 문자로 시작하는 경우 범위는 100보다 커야 합니다.

  - 유효한 값은 정규식 문자열(\[\\\*|\#\]?\[1-9\]\\d{0,7})|(\[1-9\]\\d{0,8})과 일치해야 합니다. 즉, 값은 \* 또는 \# 문자나 1~9 사이의 숫자로 시작하는 문자열이어야 하며, 첫 문자가 0일 수는 없습니다. 첫 문자가 \* 또는 \#인 경우 다음 문자는 숫자 1~9여야 합니다(0일 수 없음). 이후 문자는 숫자 0~9가 최대 7자까지 올 수 있습니다(예: "\#6000", "\*92000", "\*95551212" 및 "915551212"). 첫 문자가 \* 또는 \#이 아닌 경우 첫 문자는 숫자 1~9여야 하고(0일 수 없음) 그 뒤에는 숫자 0~9가 최대 8자까지 올 수 있습니다(예: "915551212", "41212", "300").

## 호출 받기 그룹 범위를 만들거나 수정하려면

1.  Lync Server 관리 셸이 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온하거나 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)에 설명된 대로 필요한 사용자 권한으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  호출 받기 그룹 번호의 새 범위를 만들려면 **New-CsCallParkOrbit**을 사용합니다. 기존의 호출 받기 번호 범위를 수정하려면 **Set-CsCallParkOrbit**을 사용합니다.
    
    명령줄에서 다음을 실행합니다.
    
        New-CsCallParkOrbit -Identity <name of call pickup group range> -NumberRangeStart <first number in range> -NumberRangeEnd <last number in range> -CallParkService <FQDN or service ID of the Application service that hosts the Call Park application> -Type GroupPickup
    
    예를 들면 다음과 같습니다.
    
        New-CsCallParkOrbit -Identity "Redmond call pickup" -NumberRangeStart 100 -NumberRangeEnd 199 -CallParkService redmond-applicationserver-1 -Type GroupPickup
    
    다음 예에서는 통화 대기 번호에서 호출 받기 그룹으로 번호 범위를 변경하는 방법을 보여 줍니다.
    
        Set-CsCallParkOrbit -Identity "Redmond call pickup" -Type GroupPickup
    

    > [!IMPORTANT]
    > 처음에 잘못된 유형을 지정했으며 그룹 범위를 아직 사용하지 않은 경우에만 이 cmdlet을 사용하여 번호 범위에 할당된 유형을 변경하십시오. 번호 범위가 이미 사용 중인 상태에서 번호 범위를 CallPark에서 GroupPickup으로 또는 그 반대로 변경하면 해당 번호 범위에 대해 통화 대기 또는 그룹 호출 받기가 작동하지 않습니다. 예를 들어 번호 범위를 CallPark에서 GroupPick으로 변경하면 더 이상 통화 대기 응용 프로그램에서 해당 파킹된 통화 번호 범위를 사용하여 통화를 대기시킬 수 없습니다.



## 참고 항목

#### 작업

[Lync Server 2013에서 통화 대기 파킹된 통화 번호 범위 삭제](lync-server-2013-delete-a-call-park-orbit-range.md)  

#### 기타 리소스

[New-CsCallParkOrbit](new-cscallparkorbit.md)  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)

