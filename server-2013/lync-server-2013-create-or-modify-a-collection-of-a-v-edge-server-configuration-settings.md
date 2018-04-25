---
title: A/V 에지 서버 구성 설정 모음 만들기 또는 수정
TOCTitle: A/V 에지 서버 구성 설정 모음 만들기 또는 수정
ms:assetid: 43899518-59c6-4be4-8892-d6f6207bfaab
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688039(v=OCS.15)
ms:contentKeyID: 49885743
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# A/V 에지 서버 구성 설정 모음 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2012-11-01_

A/V 에지 서비스는 내부 사용자(조직 단위 네트워크에 로그온된 사용자)가 외부 사용자(조직 단위 네트워크에 로그온되지 않은 사용자)와 오디오 및 비디오를 공유할 수 있는 방법을 제공합니다. A/V 에지 서비스는 주로 사이트 범위 또는 서비스 범위에서 구성할 수 있는(즉, 개별 A/V 에지 서버에 대해 구성할 수 있는) 설정인 A/V 에지 구성 설정을 사용해서 관리됩니다.

Lync Server을 설치할 때는 A/V 에지 구성 설정의 전역 컬렉션이 만들어집니다. 이 외에도 Lync Server 관리 셸 및 New-CsAVEdgeConfiguration cmdlet을 사용해서 사이트 범위 또는 서비스 범위(즉, 개별 A/V 에지 서버를 위한 범위)에서 새 설정을 만들 수 있습니다. 새 설정을 만들 때는 다음을 고려해야 합니다.

  - 서비스 범위로(즉, 개별 서버에서) 구성된 설정은 다른 모든 것들보다 우선 적용됩니다.

  - 사이트 범위에서 구성된 설정은 전역 범위에서 구성된 설정보다 우선 적용되지만 서비스 범위 설정은 사이트 범위 설정보다 우선 적용됩니다.

  - 전역 범위의 설정은 개별 서버에 구성된 서비스 설정이 없는 경우 그리고 서버가 배치된 위치에 사이트 설정이 없는 경우에만 사용됩니다.

그런 후 Set-CsAVEdgeConfiguration cmdlet을 사용하여 모든 설정을 수정할 수 있습니다. 자세한 내용은 [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md) 및 [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md) cmdlet에 대한 도움말 항목을 참조하십시오.

## 사이트 범위에서 새로운 A/V 에지 구성 설정 만들기

  - 다음 명령은 Redmond 사이트에 대해 새로운 A/V 에지 구성 설정의 컬렉션을 만듭니다.
    
        New-CsAVEdgeConfiguration -Identity "site:Redmond"

## 사이트 범위에서 사용자 지정 A/V 에지 구성 설정 만들기

  - 추가 매개 변수가 포함되지 않았기 때문에 이러한 새 설정에는 A/V 에지 서비스에 대한 기본 값이 사용됩니다. 또는 추가 매개 변수 및 매개 변수 값을 추가하여 사용자 지정 컬렉션을 만들 수 있습니다. 예를 들어 이 명령은 MaxTokenLifetime 속성을 4시간으로 설정합니다(04시간 : 00분 : 00초).
    
        New-CsAVEdgeConfiguration -Identity "site:Redmond" -MaxTokenLifetime "04:00:00"

## 서비스범위에서 사용자 지정 A/V 에지 구성 설정 만들기

  - 이 명령은 A/V 에지 서버 atl-edge-001.litwareinc.com에 적용되는 비슷한 컬렉션을 만듭니다.
    
        New-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com" -MaxTokenLifetime "04:00:00"

## 기존 A/V 에지 구성 설정 수정

  - 이 예에서 Set-CsAVEdgeConfiguration cmdlet은 Redmond 사이트의 최대 토큰 수명을 12시간으로 변경하는 데 사용됩니다.
    
        Set-CsAVEdgeConfiguration -Identity "site:Redmond" -MaxTokenLifetime "12:00:00"

## 참고 항목

#### 작업

[A/V 에지 서버 구성 정보 반환](lync-server-2013-return-a-v-edge-server-configuration-information.md)  
[기존 A/V 에지 서버 구성 설정 모음 삭제](lync-server-2013-delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)  

#### 기타 리소스

[Lync Server 2013의 A/V(오디오/비디오) 에지 서버](lync-server-2013-audio-video-a-v-edge-servers.md)  
[New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)  
[Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

