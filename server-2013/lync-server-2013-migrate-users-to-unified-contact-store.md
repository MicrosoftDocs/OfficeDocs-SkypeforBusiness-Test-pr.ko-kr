---
title: 'Lync Server 2013: 통합 연락처 저장소로 사용자 마이그레이션'
TOCTitle: 통합 연락처 저장소로 사용자 마이그레이션
ms:assetid: 215a8ec1-d63e-4fdf-b73d-75aeb9dddb43
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204737(v=OCS.15)
ms:contentKeyID: 49303037
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 통합 연락처 저장소로 사용자 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-15_

사용자가 다음을 수행하면 사용자의 연락처는 Exchange 2013 서버로 자동 마이그레이션됩니다.

  - UcsAllowed가 True로 설정된 사용자 서비스 정책을 할당한 경우

  - Exchange 2013 사서함이 프로비저닝되었으며 해당 사서함에 한 번 이상 로그인한 경우

  - Lync 2013 리치 클라이언트를 사용하여 로그인하는 경우

사용자가 Lync 2010 이하 버전의 클라이언트를 사용하여 로그인하거나 Exchange 2013 서버에 연결되어 있지 않으면 사용자 서비스 정책은 무시되며 사용자의 연락처는 Lync Server에 계속 남아 있습니다.

다음 방법 중 하나를 사용하여 사용자 연락처가 마이그레이션되었는지 확인할 수 있습니다.

  - 클라이언트 컴퓨터에서 다음 레지스트리 키를 확인합니다.
    
    HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\\\<SIP URL\>\\UCS
    
    사용자 연락처가 Exchange 2013에 저장되어 있으면 이 키는 값이 2165인 InUCSMode 값을 포함합니다.

  - **Test-CsUnifiedContactStore** cmdlet을 실행합니다. Lync Server 관리 셸 명령줄에 다음을 입력합니다.
    
        Test-CsUnifiedContactStore -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com"
    
    **Test-CsUnifiedContactStore**가 정상적으로 실행되면 사용자 연락처가 통합 연락처 저장소로 마이그레이션된 것입니다.

