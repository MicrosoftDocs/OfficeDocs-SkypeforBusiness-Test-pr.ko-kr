---
title: 레거시 풀에서 모든 Exchange UM 연락처 개체 제거 확인
TOCTitle: 레거시 풀에서 모든 Exchange UM 연락처 개체 제거 확인
ms:assetid: 5a813169-0ed7-4f84-a242-ed2cd4ea5c43
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688068(v=OCS.15)
ms:contentKeyID: 49885779
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 레거시 풀에서 모든 Exchange UM 연락처 개체 제거 확인

 

_**마지막으로 수정된 항목:** 2012-09-26_

**OCSUmUtil** 도구 또는 **Get-CsExumContact** cmdlet을 사용하여 레거시 Office Communications Server 2007 R2 풀에서 Exchange UM 대화 상대 개체가 제거되었는지 확인합니다. **OCSUmUtil**은 다음 폴더에 있습니다.

%Program Files%\\Common Files\\ Lync Server 2013\\Support\\OcsUMUtil.exe

**OCSUmUtil**은 다음을 포함하는 사용자 계정으로부터 실행해야 합니다.

  - RTCUniversalServerAdmins 및 RTCUniversalUserAdmins 그룹의 구성원 자격(Exchange Server 통합 메시징 설정을 읽을 수 있는 권한 포함)

  - 지정된 OU(조직 구성 단위) 컨테이너에 대화 상대 개체를 만드는 도메인 권한

**Get-CsExumContact** cmdlet 사용에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 [Get-CsExUmContact](get-csexumcontact.md)를 참조하십시오.

