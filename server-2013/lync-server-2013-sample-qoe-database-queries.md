---
title: 'Lync Server 2013: 샘플 QoE 데이터베이스 쿼리'
TOCTitle: 샘플 QoE 데이터베이스 쿼리
ms:assetid: 04e6bdd3-bbd1-47ca-8114-94a3db6beeeb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398100(v=OCS.15)
ms:contentKeyID: 49302666
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 샘플 QoE 데이터베이스 쿼리

 

_**마지막으로 수정된 항목:** 2012-10-17_

이 섹션에는 QoE(체감 품질) 데이터베이스에 대한 샘플 쿼리가 포함됩니다.

다음 예제를 사용하여 모든 오디오 스트림에 대한 지터 및 패킷 손실 평균을 가져옵니다.

    select avg(cast(JitterInterArrival as bigint)) as JitterAvg, avg(PacketLossRate) as PacketLossRateAvg from AudioStream

다음 예제를 사용하여 Meeting Console을 사용한 총 회의 수를 찾습니다.

    select avg(ConversationalMOS)
    from SessionView s
    inner join MediaLineView m
    on s.ConferenceDateTime = m.ConferenceDateTime
       and s.SessionSeq = m.SessionSeq
       and m.MediaLineLabel = 0 -- audio media line
       and s.CallerUserAgentType = 4 -- Lync
       and s.CalleeUserAgentType = 4 -- Lync

다음 예제를 사용하여 캡처 장치별 ConversstionalMOS, SendingMOS 및 ListendingMOS를 가져옵니다.

    select t.DeviceName as Device, count(*) as SampleNum, avg(ConversationalMOS) as ConversationalMOS, avg(SendListenMOS) SendingMOS, avg(RecvListenMOS) as ListendingMOS
    from
    (
       select m.CallerCaptureDev as DeviceName, m.ConferenceDateTime, m.SessionSeq, a.StreamID, m.ConversationalMOS,a.SendListenMOS, a.RecvListenMOS
       from MediaLineView m
       inner join AudioStream a
       on m.ConferenceDateTime = a.ConferenceDateTime
          and m.SessionSeq = a.SessionSeq
          and m.MediaLineLabel = 0
    
       union
    
       select m.CalleeCaptureDev as DeviceName, m.ConferenceDateTime, m.SessionSeq, a.StreamID, m.ConversationalMOS,a.SendListenMOS, a.RecvListenMOS
       from MediaLineView m
       inner join AudioStream a
       on m.ConferenceDateTime = a.ConferenceDateTime
          and m.SessionSeq = a.SessionSeq
          and m.MediaLineLabel = 0
    
    )as t
    group by t.DeviceName
    order by SampleNum desc

