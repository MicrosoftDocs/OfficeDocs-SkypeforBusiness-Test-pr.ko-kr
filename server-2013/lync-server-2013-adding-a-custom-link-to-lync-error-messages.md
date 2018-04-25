---
title: 'Lync Server 2013: Lync 오류 메시지에 사용자 지정 링크 추가'
TOCTitle: Lync 오류 메시지에 사용자 지정 링크 추가
ms:assetid: de756088-fcc3-4e47-bde8-4fa4cc852fd1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398979(v=OCS.15)
ms:contentKeyID: 52056975
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync 오류 메시지에 사용자 지정 링크 추가

 

_**마지막으로 수정된 항목:** 2013-02-20_

문제 해결이나 지원 센터 정보에 링크를 추가하여 Lync 2013 오류 메시지를 사용자 지정할 수 있습니다. 이렇게 하려면 CustomLinkInErrorMessages 매개 변수와 함께 **New-CSClientPolicy** 또는 **Set-CSClientPolicy** Lync Server 관리 셸 cmdlet을 사용합니다. 사용자 지정 링크 텍스트는 "관리자의 지원 항목을 보려면 여기를 클릭하십시오."이며, 사용자 지정할 수 없습니다.

예를 들어 다음 명령은 모든 Lync 2013 오류 메시지의 각주 영역에 사용자 지정 링크를 표시하며 링크 대상을 http://contoso.com/help/LyncHelpDesk.aspx로 설정합니다.

    New-CsClientPolicy -Identity LyncErrorLink -CustomLinkInErrorMessages "http://contoso/help/LyncHelpDesk.aspx"

**Grant-CSClientPolicy**를 사용하여 새로운 이 정책을 사용자에게 할당합니다. 자세한 내용은 Lync Server 관리 셸 설명서에서 **New-CSClientPolicy** 및 **Grant-CSClientPolicy**를 참조하세요.

