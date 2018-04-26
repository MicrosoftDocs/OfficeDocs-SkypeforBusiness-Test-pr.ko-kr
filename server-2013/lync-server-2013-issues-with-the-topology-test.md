---
title: 토폴로지 테스트 문제
TOCTitle: 토폴로지 테스트 문제
ms:assetid: 821e8916-7b5d-4f64-8fb0-e5cc392ec1bb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205045(v=OCS.15)
ms:contentKeyID: 49304222
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 토폴로지 테스트 문제

 

_**마지막으로 수정된 항목:** 2012-09-21_

**Test-CsTopology** cmdlet과 마찬가지로 모범 사례 분석기를 사용하면 Lync Server 2013이 전역 수준에서 올바르게 작동하는지 확인할 수 있습니다. 기본적으로 cmdlet과 마찬가지로 모범 사례 분석기는 전체 Lync Server 2013 인프라를 검사하여 필요한 서비스가 실행되고 있는지, 그리고 이러한 서비스 및 Lync Server 2013을 설치할 때 만들어진 유니버설 보안 그룹에 대해 적절한 사용 권한이 설정되었는지 확인합니다.

Lync Server 전체의 유효성을 검사하는 것 외에도 **Test-CsTopology**를 통해 특정 서비스의 유효성을 검사할 수 있습니다. cmdlet을 사용해서 특정 서비스를 테스트하는 방법에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 [Test-CsTopology](test-cstopology.md)를 참조하십시오. 토폴로지 문제를 해결하는 데 도움이 필요하면 다음 정보를 참조하십시오.


> [!NOTE]
> 방화벽 설정과 권한을 포함하여 에지 서버 및 관련 경계 네트워크 설정의 구성에 따라 모범 사례 분석기가 에지 서버를 액세스하고 검색하지 못할 수 있습니다. 검색에 에지 서버를 포함하고 보고서에 에지 서버 액세스 문제가 표시되면 <STRONG>에지 서버</STRONG> 확인란의 선택을 취소하고 검색을 다시 실행해서 문제가 보고서에 표시되지 않도록 합니다.



## 토폴로지 문제 해결

토폴로지 테스트로 토폴로지 문제가 발견된 경우 이러한 문제는 토폴로지를 게시하거나 사용하도록 설정할 때 발생한 문제로 인한 것일 수 있습니다.

토폴로지를 변경할 때는 토폴로지를 게시하고 사용하도록 설정한 경우에만 변경 내용이 적용됩니다. 토폴로지를 변경하려면 토폴로지 작성기를 사용해야 합니다. 변경한 후에는 토폴로지 작성기를 사용하여 해당 변경 내용을 게시하고 사용하도록 설정할 수 있습니다.

변경 내용을 게시하면 새 정보(예: 새 사이트 또는 새 서버 역할)가 중앙 관리 저장소에 기록됩니다. 그러나 이러한 새 개체 또는 새로 수정한 개체가 토폴로지에 즉시 조인되는 것은 아닙니다. 개체는 사용자가 업데이트한 토폴로지를 사용하도록 설정할 때만 토폴로지에 참가합니다. 토폴로지 작성기에서 게시 옵션을 선택하면 변경 내용이 게시(중앙 관리 저장소에 기록)된 다음 새 토폴로지가 사용하도록 설정되는 두 가지 단계가 수행됩니다.

기본적으로 RTCUniversalServerAdmins 그룹의 구성원에게는 **Publish-CsTopology** cmdlet 및 **Enable-CsTopology** cmdlet을 실행할 수 있는 권한이 부여됩니다. 하지만 설정 권한이 위임되지 않은 경우 **Publish-CsTopology**를 실행하려면 도메인 관리자로 로그온해야 합니다. RTCUniversalServerAdmins에게 **Publish-CsTopology** cmdlet을 실제로 사용할 수 있는 권한을 부여하려면 Lync Server 서비스를 실행하는 컴퓨터가 포함된 모든 Active Directory 컨테이너에서 **Grant-CsSetupPermission** cmdlet을 실행해야 합니다. RTCUniversalServerAdmins에게 **Enable-CsTopology** cmdlet을 실행할 수 있는 권한을 부여하려면 Lync Server 서비스를 실행하는 컴퓨터가 포함된 모든 Active Directory 도메인 서비스 컨테이너에 대해 **Set-CsSetupPermission** cmdlet을 실행해야 합니다. 이러한 방식은 토폴로지 작성기를 사용하여 토폴로지를 사용하도록 설정하고 게시하는 데 적용됩니다. **Set-CsSetupPermission**을 사용하여 권한을 위임하지 않은 경우 도메인 관리자만 토폴로지 작성기를 통해 토폴로지를 사용하도록 설정하고 게시할 수 있습니다.

