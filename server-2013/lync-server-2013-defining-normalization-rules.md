---
title: 'Lync Server 2013: 정규화 규칙 정의'
TOCTitle: 정규화 규칙 정의
ms:assetid: ed31d56c-00b5-4f72-bd9f-beb4100d441f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399071(v=OCS.15)
ms:contentKeyID: 49305435
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 정규화 규칙 정의

 

_**마지막으로 수정된 항목:** 2014-04-22_

Lync Server 2013 정규화 규칙은 .NET Framework 정규식을 사용하여 전화를 거는 번호를 E.164 형식으로 변환합니다. 다시 말해서, 정규화 규칙은 사용자가 거는 전화 번호를 Lync Server 내부에서 사용되는 형식으로 변환합니다. 각 다이얼 플랜에는 하나 이상의 정규화 규칙을 할당해야 합니다.

정규화 규칙에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 다이얼 플랜 및 정규화 규칙](lync-server-2013-dial-plans-and-normalization-rules.md)을 참조하십시오.

정규식을 작성하는 방법에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=140927\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=140927%26clcid=0x412)에서 ".NET Framework 정규식"을 참조하십시오.

다음 방법 중 하나를 사용하여 정규화 규칙을 정의하거나 편집할 수 있습니다.

  - **정규화 규칙 작성** 도구를 사용하여 시작 숫자, 길이, 제거할 숫자 및 추가할 숫자에 대한 값을 지정한 다음 Lync Server 제어판에서 일치하는 해당 패턴 및 변환 규칙을 생성하도록 할 수 있습니다.

  - 수동으로 정규식을 작성하여 일치 패턴 및 변환 규칙을 정의합니다.

## 이 단원의 내용

  - [Lync Server 2013에서 정규화 규칙 작성을 사용하여 정규화 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule.md)

  - [Lync Server 2013에서 수동으로 정규화 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-normalization-rule-manually.md)

## 참고 항목

#### 작업

[Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)  
[Lync Server 2013에서 다이얼 플랜 수정](lync-server-2013-modify-a-dial-plan.md)

