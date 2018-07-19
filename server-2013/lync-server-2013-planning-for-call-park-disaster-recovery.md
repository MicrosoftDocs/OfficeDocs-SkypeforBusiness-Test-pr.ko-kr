---
title: 'Lync Server 2013: 통화 대기 재해 복구 계획'
TOCTitle: 통화 대기 재해 복구 계획
ms:assetid: f7cf3958-177b-4340-a864-35a6f44d6d88
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205395(v=OCS.15)
ms:contentKeyID: 49305573
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 대기 재해 복구 계획

 

_**마지막으로 수정된 항목:** 2012-10-30_

이 섹션에서는 통화 대기 응용 프로그램의 재해 복구를 준비하는 방법과 재해 복구 프로세스 시 고려 사항에 대해 설명합니다.

## 통화 대기 재해 복구 준비

재해 복구 절차를 준비하고 수행할 때 다음 사항에 유의하십시오.

  - 용량 계획을 수행할 때 재해 복구를 계획합니다. 재해 복구 용량의 경우 연결된 풀의 각 풀은 두 풀 모두의 통화 대기 서비스 작업량을 처리할 수 있어야 합니다. 통화 대기 용량 계획에 대한 자세한 내용은 [Lync Server 2013의 통화 대기에 대한 용량 계획](lync-server-2013-capacity-planning-for-call-park.md)을 참조하십시오.

  - 재해 복구 중에 장애 조치(failover) 프로세스의 일부로서 백업 풀로 리디렉션된 사용자는 백업 풀에서 실행 중인 통화 대기 서비스를 사용합니다. 따라서 재해 복구 시 통화 대기를 지원하려면 기본 풀과 백업 풀 모두에서 통화 대기 응용 프로그램을 배포하고 사용하도록 설정해야 합니다.

  - 각 풀에는 해당 풀에 있는 사용자에 대해 통화 대기에 사용할 유효한 파킹된 통화 번호 범위가 있어야 합니다.

  - 통화 대기에 대해 업로드된 사용자 지정 대기 음악의 개별 백업 복사본을 항상 보관하십시오. 이러한 파일은 풀로 업로드된 파일이 손상되거나 변경되거나 삭제되는 경우 Lync Server 2013 재해 복구 프로세스의 일부로서 백업되지 않습니다.

## 통화 대기 재해 복구 고려 사항

풀당 통화 대기 응용 프로그램 구성 설정 집합 하나와 사용자 지정된 대기 음악 오디오 파일 하나만 정의할 수 있습니다. 이러한 설정에는 시간 제한 임계값, 대기 음악, 최대 호출 받기 시도 횟수 및 시간 제한 URI가 포함됩니다. 이러한 구성 설정을 보려면 **Get-CsCpsConfiguration** cmdlet을 실행합니다. **Get-CsCpsConfiguration** cmdlet에 대한 자세한 내용은 [Get-CsCpsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCpsConfiguration)을 참조하십시오.

재해 복구 중에는 통화 대기에서 백업 풀에 있는 통화 대기 응용 프로그램을 사용하므로 기본 풀의 설정이 백업되지 않습니다. 기본 풀을 복구할 수 없으며 새 풀을 배포하여 기본 풀을 대체할 경우 기본 풀의 설정이 손실되므로 새 풀에서 통화 대기 설정과 사용자 지정된 대기 음악 오디오 파일을 다시 구성해야 합니다.

FQDN(정규화된 도메인 이름)이 다른 새 풀을 배포하여 기본 풀을 대체할 경우 기본 풀과 연결된 모든 통화 대기 파킹된 통화 번호 범위를 새 풀의 FQDN에 다시 할당해야 합니다. 파킹된 통화 번호 범위를 새 풀에 다시 할당하려면 Lync Server 제어판 또는 **Set-CsCallParkOrbit** cmdlet을 사용할 수 있습니다. **Set-CsCallParkOrbit** cmdlet에 대한 자세한 내용은 [Set-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCallParkOrbit)를 참조하십시오.

