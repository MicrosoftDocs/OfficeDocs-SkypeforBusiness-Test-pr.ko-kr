---
title: Lync Server 2013의 발신 번호 표시
TOCTitle: Lync Server 2013의 발신 번호 표시
ms:assetid: cf6c6af5-3418-411e-a50b-7a9cf8e100d4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721892(v=OCS.15)
ms:contentKeyID: 49885992
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 발신 번호 표시

 

_**마지막으로 수정된 항목:** 2012-09-21_

Lync Server 2010을 사용하여 전화받은 대상(즉, 수신 전화 번호)은 E.164 형식에서 *트렁크 피어*(즉, 관련 게이트웨이, PBX(Private Branch Exchange) 또는 SIP 트렁크)에서 필요한 지역 전화 번호 형식으로 변환될 수 있습니다. 그러려면 트렁크 피어로 라우팅되기 전에 요청 URI를 변환하는 변환 규칙을 하나 이상 정의해야 합니다.


> [!IMPORTANT]
> Enterprise Voice 트렁크 구성과 하나 이상의 변환 규칙을 연결하는 기능은 트렁크 피어에서 변환 규칙을 구성하는 <EM>대체 방안</EM>으로 사용하기 위해 고안되었습니다. 트렁크 피어에 대한 변환 규칙을 구성한 경우 변환 규칙을 Enterprise Voice 트렁크 구성과 연결하지 마십시오. 두 규칙이 충돌할 수 있습니다.



다음 방법 중 하나를 사용하여 변환 규칙을 만들거나 수정할 수 있습니다.

  - **변환 규칙 작성** 도구를 사용하여 시작 자릿수, 길이, 제거할 자릿수, 추가할 자릿수 등의 값을 지정하면 Lync Server 제어판 에서 해당하는 일치 패턴 및 변환 규칙을 자동으로 생성합니다.

  - 수동으로 정규식을 작성하여 일치 패턴 및 변환 규칙을 정의합니다.


> [!NOTE]
> 정규식을 작성하는 방법에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=140927%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=140927&amp;clcid=0x412</A>에서 ".NET Framework 정규식"을 참조하십시오.



## 이 단원의 내용

  - [변환 규칙 작성 도구를 사용하여 변환 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-translation-rule-by-using-the-build-a-translation-rule-tool.md)

  - [수동으로 변환 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-translation-rule-manually.md)

## 참고 항목

#### 개념

[Lync Server 2013의 발신자 번호 표시](lync-server-2013-caller-id-presentation.md)

