---
title: 'Lync Server 2013: 통화 대기에 대한 정규화 규칙 확인'
TOCTitle: 통화 대기에 대한 정규화 규칙 확인
ms:assetid: deaa170f-041e-45cb-8eab-f02931ab541e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398981(v=OCS.15)
ms:contentKeyID: 49305263
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 통화 대기에 대한 정규화 규칙 확인

 

_**마지막으로 수정된 항목:** 2012-09-11_

통화 대기 파킹된 통화 번호는 정규화할 수 없습니다. 다이얼 플랜을 확인하여 파킹된 통화 번호가 정규화되지 않았는지 확인하십시오. 파킹된 통화 번호가 정규화되지 않도록 제한하기 위해 추가 정규화 규칙을 만들어야 할 경우 [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)의 절차를 수행하여 새 정규화 규칙을 정의합니다. 이 경우 **일치시킬 패턴** 에서 파킹된 통화 번호 범위를 식별하며, **변환 패턴** 은 **$1**입니다. 예를 들어 통화 대기 파킹된 통화 번호 범위가 7000 ? 7999일 경우 **일치시킬 패턴** 은 **^(7\\d{3})$**이고 **변환 패턴** 은 **$1**입니다.


> [!IMPORTANT]
> 다이얼 플랜의 기본 정규화 규칙에 <STRONG>^(\d*)</STRONG>가 포함되지 않았는지 확인합니다. 그렇지 않으면 통화 대기 정규화 규칙이 실행되지 않습니다.



## 참고 항목

#### 작업

[Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)

