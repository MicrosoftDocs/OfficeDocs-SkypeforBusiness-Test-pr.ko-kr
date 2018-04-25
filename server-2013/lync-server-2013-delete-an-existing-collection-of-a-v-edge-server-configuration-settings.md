---
title: 기존 A/V 에지 서버 구성 설정 모음 삭제
TOCTitle: 기존 A/V 에지 서버 구성 설정 모음 삭제
ms:assetid: 668d3613-e464-4b68-967a-cfff90b9ce4b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688077(v=OCS.15)
ms:contentKeyID: 49885790
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 A/V 에지 서버 구성 설정 모음 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

A/V 에지 서비스는 내부 사용자(조직 단위 네트워크에 로그온된 사용자)가 외부 사용자(조직 단위 네트워크에 로그온되지 않은 사용자)와 오디오 및 비디오를 공유할 수 있는 방법을 제공합니다. A/V 에지 서비스는 주로 사이트 범위 또는 서비스 범위에서 구성할 수 있는(즉, 개별 A/V 에지 서버에 대해 구성할 수 있는) 설정인 A/V 에지 구성 설정을 사용해서 관리됩니다.

Lync Server을 설치하면 A/V 에지 구성 설정의 전역 컬렉션이 생성됩니다. 이 전역 컬렉션은 삭제할 수 없습니다. 하지만 Lync Server 관리 셸 및 Remove-CsAVEdgeConfiguration cmdlet을 사용해서 전역 컬렉션을 "다시 설정"할 수는 있습니다. 즉, 전역 컬렉션의 모든 속성 값을 기본값으로 다시 설정할 수 있습니다. 예를 들어 MaxTokenLifetime 속성을 16시간으로 설정했으면, 해당 속성이 기본값인 8시간으로 다시 설정됩니다.

하지만 사이트 범위 또는 서비스 범위에서 만든 사용자 지정 설정 컬렉션은 Remove-CsAVEdgeConfiguration cmdlet을 사용하여 삭제할 수 있습니다. 사이트 설정을 삭제하면 해당 사이트의 A/V 에지 서버가 전역 설정에 의해 관리됩니다. 장치 범위 설정을 삭제할 경우 해당 서버가 사이트 설정(있는 경우)으로 관리되거나, 사이트 설정을 사용할 수 없으면 전역 설정으로 관리됩니다.

자세한 내용은 [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md) cmdlet의 도움말 항목을 참조하십시오.

## 전역 컬렉션 다시 설정

  - 다음 명령은 A/V 에지 구성 설정의 전역 컬렉션을 다시 설정합니다.
    
        Remove-CsAVEdgeConfiguration -Identity "global"

## 사이트 범위에서 컬렉션 제거

  - 이 명령은 Redmond 사이트에 적용된 A/V 에지 구성 설정을 제거합니다.
    
        Remove-CsAVEdgeConfiguration -Identity "site:Redmond"

## 서비스 범위에서 컬렉션 제거

  - 이 명령은 A/V 에지 서버 atl-edge-001.litwareinc.com에 적용된 설정을 제거합니다.
    
        Remove-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"

## 참고 항목

#### 작업

[A/V 에지 서버 구성 정보 반환](lync-server-2013-return-a-v-edge-server-configuration-information.md)  
[A/V 에지 서버 구성 설정 모음 만들기 또는 수정](lync-server-2013-create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)  

#### 기타 리소스

[Lync Server 2013의 A/V(오디오/비디오) 에지 서버](lync-server-2013-audio-video-a-v-edge-servers.md)  
[Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

