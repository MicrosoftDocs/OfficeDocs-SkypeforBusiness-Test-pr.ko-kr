---
title: Lync Server 2013에서 사용자 지정된 영구 채팅 서버 준수 어댑터로 XmlAdapter 교체
TOCTitle: Lync Server 2013에서 사용자 지정된 영구 채팅 서버 준수 어댑터로 XmlAdapter 교체
ms:assetid: 2cb70db2-663f-40a6-abcf-89ea7d4a8b65
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ680106(v=OCS.15)
ms:contentKeyID: 49885699
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자 지정된 영구 채팅 서버 준수 어댑터로 XmlAdapter 교체

 

_**마지막으로 수정된 항목:** 2012-11-01_

영구 채팅 서버와 함께 설치되는 XmlAdapter를 사용하는 대신 사용자 지정 어댑터를 작성할 수 있습니다. 이렇게 하려면 **IComplianceAdapter** 인터페이스를 구현하는 공용 클래스가 포함된 .NET Framework 어셈블리를 제공해야 합니다. 이 어셈블리는 영구 채팅 서버 풀에 포함된 각 서버의 영구 채팅 서버 설치 폴더에 저장해야 합니다. 준수 서버 중 하나가 어댑터에 준수 데이터를 제공할 수 있지만, 준수 서버가 여러 어댑터 인스턴스에 대해 중복 준수 데이터를 제공하지는 않습니다.

## IComplianceAdapter 인터페이스 구현

인터페이스는 Compliance.dll 어셈블리의 `Microsoft.Rtc.Internal.Chat.Server.Compliance` 네임스페이스에 정의됩니다. 이 인터페이스는 사용자 지정 어댑터가 구현해야 하는 두 개의 메서드를 정의합니다.

    void SetConfig(AdapterConfig config)

영구 채팅 준수 서버는 어댑터를 처음 로드할 때 이 메서드를 호출합니다. `AdapterConfig`에는 준수 어댑터와 관련된 영구 채팅 준수 구성이 포함됩니다.

    void Translate(ConversationCollection conversations)

영구 채팅 준수 서버는 변환할 새 데이터가 있으면 일정한 간격으로 이 메서드를 호출합니다. 이 시간 간격은 영구 채팅 준수 구성에 설정된 `RunInterval`과 동일합니다.

`ConversationCollection`에는 이 메서드를 마지막으로 호출한 시간 이후 수집된 대화 정보가 포함됩니다.

