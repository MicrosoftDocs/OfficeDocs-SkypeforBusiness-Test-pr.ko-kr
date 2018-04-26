---
title: A/V 에지 서버 구성 정보 반환
TOCTitle: A/V 에지 서버 구성 정보 반환
ms:assetid: b041f5a4-2387-4075-846c-ec4f99640903
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721850(v=OCS.15)
ms:contentKeyID: 49885928
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# A/V 에지 서버 구성 정보 반환

 

_**마지막으로 수정된 항목:** 2012-11-01_

A/V 에지 서버를 사용하면 내부 사용자(조직 네트워크에 로그온한 사용자)가 외부 사용자(조직 네트워크에 로그온하지 않은 사용자)와 오디오 및 비디오를 공유할 수 있습니다. A/V 에지 서비스는 주로 A/V 에지 구성 설정을 사용하여 관리됩니다. A/V 에지 구성 설정은 사이트 범위 또는 서비스 범위(즉 개별 A/V 에지 서버)에 대해 구성할 수 있습니다.

조직에서 사용 중인 A/V 에지 서버에 대한 정보를 반환하려면 Lync Server 관리 셸과 Get-CsAVEdgeConfiguration cmdlet을 사용해야 합니다. 자세한 내용은 [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md) cmdlet에 대한 도움말 항목을 참조하십시오.

Get-CsAVEdgeConfiguration cmdlet에서 반환되는 정보는 다음과 유사합니다.

    Identity              : Global
    MaxTokenLifetime      : 08:00:00
    MaxBandwidthPerUserKb : 10000
    MaxBandwidthPerPortKb : 3000

## 모든 A/V 에지 구성 설정에 대한 정보 반환

  - 다음 명령은 조직에서 현재 사용 중인 모든 A/V 에지 구성 설정에 대한 정보를 반환합니다.
    
        Get-CsAVEdgeConfiguration

## 사이트 범위의 A/V 에지 구성 설정에 대한 정보 반환

  - A/V 에지 구성 설정의 특정 컬렉션에 대한 정보를 반환하려면 Get-CsAVEdgeConfiguration cmdlet을 실행할 때 컬렉션의 ID를 지정합니다. 예를 들어 다음 명령은 Redmond 사이트에 적용되는 설정에 대한 정보만 반환합니다.
    
        Get-CsAVEdgeConfiguration -Identity "site:Redmond"

## 서비스 범위의 A/V 에지 구성 설정에 대한 정보 반환

  - 또한 다음 명령은 특정 A/V 에지 서버에 적용되는 설정에 대한 정보만 반환합니다.
    
        Get-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"

## 참고 항목

#### 작업

[A/V 에지 서버 구성 설정 모음 만들기 또는 수정](lync-server-2013-create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)  
[기존 A/V 에지 서버 구성 설정 모음 삭제](lync-server-2013-delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)  

#### 기타 리소스

[Lync Server 2013의 A/V(오디오/비디오) 에지 서버](lync-server-2013-audio-video-a-v-edge-servers.md)

