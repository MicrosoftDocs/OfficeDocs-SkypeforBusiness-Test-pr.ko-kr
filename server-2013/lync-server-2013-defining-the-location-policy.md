﻿---
title: 'Lync Server 2013: 위치 정책 정의'
TOCTitle: 위치 정책 정의
ms:assetid: da3cca7f-f6e5-4b6f-90a1-2008e3dd1ebd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398962(v=OCS.15)
ms:contentKeyID: 49305226
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 위치 정책 정의

 

_**마지막으로 수정된 항목:** 2012-10-29_

각 위치 정책에는 다음 정보가 포함됩니다.

  - **긴급 서비스 사용**  
    이 값이 **예**인 경우 클라이언트가 E9-1-1을 사용하도록 설정됩니다. 클라이언트 등록 시 위치 정보 서비스에서 위치를 가져와서 위치 정보를 긴급 전화의 일부로 포함합니다.

<!-- end list -->

  - **위치 필요**  
    이 설정은 **긴급 서비스 사용**이 **예**로 설정된 경우에만 사용됩니다.
    
    **위치 필요** 설정을 구성하여 클라이언트 동작을 정의할 수 있습니다. 이 값을 **아니요**로 지정하면 사용자에게 위치를 입력하라는 메시지가 표시되지 않습니다. 반면 **예**로 지정하면 사용자에게 위치를 입력하라는 해제 가능한 메시지가 표시됩니다. 이 값을 **고지 사항**으로 지정하면 사용자에게 위치를 입력하라는 메시지가 표시되며, 메시지를 해제할 때도 고지 사항이 표시됩니다. 어느 옵션을 선택해도 사용자는 클라이언트를 계속 사용할 수 있습니다.
    

    > [!NOTE]
    > E9-1-1을 사용하도록 설정되기 전에 사용자가 위치를 수동으로 입력한 경우에는 고지 사항 텍스트가 표시되지 않습니다. 고지 사항을 이미 본 사용자에게는 고지 사항 텍스트에 대한 업데이트가 표시되지 않습니다.



<!-- end list -->

  - **향상된 긴급 서비스 고지 사항**  
    이 설정은 위치를 입력하라는 메시지를 해제하는 사용자에게 표시되는 고지 사항을 지정합니다. Lync Server 2013에서는 위치 정책을 사용하여 여러 로캘이나 사용자 집합에 대해 서로 다른 고지 사항을 설정할 수 있습니다.
    

    > [!NOTE]
    > 이 위치 정책 설정은 Lync Server 2010과 다릅니다. Lync Server 2010에서는 <STRONG>Set-CsEnhancedEmergencyServiceDisclaimer</STRONG> cmdlet을 사용하여 전체 조직에 대한 전역 고지 사항을 설정했습니다. 전역 고지 사항이 이미 있는 경우 위치 정책에 해당 고지 사항을 지정해야 합니다. 즉, Lync Server 2013에서는 위치 정책에 지정된 고지 사항만 사용합니다.



<!-- end list -->

  - **긴급 전화 문자열**  
    이 전화 문자열(선행 “+”를 제외하며 Lync 사용자의 다이얼 플랜에서 수행된 정규화 포함)은 통화가 긴급 전화임을 나타냅니다. **긴급 전화 문자열**은 클라이언트가 통화와 함께 위치 및 회신 전화 정보를 포함하도록 합니다.
    

    > [!NOTE]
    > 조직에서 외부 회선 접두어를 사용하지 않는 경우 Lync 풀 서버에서 아웃바운딩 라우팅으로 호출을 보내기 전에 "+"를 911 문자열에 추가하는 해당 다이얼 플랜 정규화 규칙을 만들 필요가 없습니다. "+"가 위치 정책의 결과로서 Lync에 의해 자동으로 추가됩니다. 하지만 해당 위치에서 외부 액세스 접두어를 사용하는 경우에는 적용 가능한 다이얼 플랜 정책에 정규화 규칙을 추가하여 외부 액세스 접두어를 제거하고 "+"를 추가하도록 해야 합니다. 예를 들어, 위치에서 외부 액세스 접두어로 9를 사용하며 사용자가 9_911을 입력하여 긴급 전화를 거는 경우 클라이언트에서는 발신자의 위치 프로필의 라우트를 통해 전화 건 번호를 평가하기 전에 해당 다이얼 플랜 정책을 사용하여 이 전화 문자열을 +911로 정규화합니다.



<!-- end list -->

  - **긴급 전화 문자열 마스크**  
    지정된 **긴급 전화 문자열**로 변환되는 세미콜론으로 구분된 전화 문자열 목록입니다. 예를 들어, 대부분 유럽 지역에서 긴급 서비스 번호로 사용되는 112를 추가할 수 있습니다. 유럽에서 방문하는 Lync 사용자가 911이 미국의 긴급 번호라는 사실을 모르고 112로 전화를 걸어도 긴급 서비스에 연결됩니다. 긴급 전화 문자열과 마찬가지로, 각 번호 앞에 "+"를 포함하지 않으며 외부 회선 액세스 코드를 사용하는 경우 사용자의 다이얼 플랜 정책에 액세스 코드 숫자를 제거하는 정규화 규칙이 있어야 합니다.

<!-- end list -->

  - **PSTN 사용**  
    SIP 트렁크, PSTN 게이트웨이 또는 ELIN 게이트웨이 긴급 전화가 연결될 위치를 결정하는 라우팅 경로를 포함하는 PSTN 사용 이름입니다.
    

    > [!NOTE]
    > 위치 정책에 하나의 사용만 할당할 수 있습니다. 이 PSTN 사용은 사용자의 음성 정책에 할당된 PSTN 사용을 재정의하지만, 긴급 전화 문자열이나 긴급 전화 문자열 마스크 중 하나로 건 통화에만 적용됩니다.



<!-- end list -->

  - **알림 URI**  
    긴급 전화가 걸려올 때 IM(인스턴트 메시징) 알림을 수신할 보안 담당자의 SIP URI를 하나 이상 지정합니다. 메일 그룹이 지원됩니다.

<!-- end list -->

  - **전화 회의 URI**  
    긴급 전화가 걸려올 때 회의를 열어야 하는 DID(자동 착신) 번호(일반적으로 보안 데스크 번호)를 지정합니다.

<!-- end list -->

  - **전화 회의 모드**  
    회의 URI가 단방향 또는 양방향 통신을 사용하여 긴급 전화에 참가하는지 여부를 지정합니다.

<!-- end list -->

  - **위치 새로 고침 간격(Location Refresh Interval)**  
    클라이언트가 위치 정보 서비스에 위치 업데이트를 요청하는 간격(시간)을 지정합니다. 설정 가능한 값은 1~12이며 기본값은 4입니다.

