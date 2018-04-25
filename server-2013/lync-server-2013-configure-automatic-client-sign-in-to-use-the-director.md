---
title: 'Lync Server 2013: 디렉터를 사용하도록 자동 클라이언트 로그인 구성'
TOCTitle: 디렉터를 사용하도록 자동 클라이언트 로그인 구성
ms:assetid: 85369ffc-53ae-43be-8a23-84a094faecff
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398678(v=OCS.15)
ms:contentKeyID: 49304258
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 디렉터를 사용하도록 자동 클라이언트 로그인 구성

 

_**마지막으로 수정된 항목:** 2012-09-08_

Lync Server 2013, 디렉터 또는 디렉터 풀을 배포할 때는 모범 사례로 자동 클라이언트 로그인을 사용하는 것이 좋습니다. 자동 클라이언트 로그인을 사용하도록 DNS 서버를 구성하는 방법에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 자동 클라이언트 로그인에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-automatic-client-sign-in.md)을 참조하십시오.

이미 자동 클라이언트 로그인을 배포한 경우 이를 디렉터에서 구성하려면 다음 섹션을 참조하십시오.

## 단일 디렉터 인스턴스

이미 자동 클라이언트 로그인을 배포했고 자동 클라이언트 로그인이 프런트 엔드 서버 또는 프런트 엔드 풀을 가리키고 있는 경우 디렉터를 가리키도록 DNS SRV 레코드를 변경해야 합니다.

## 디렉터 풀

이미 자동 클라이언트 로그인을 배포했고 자동 클라이언트 로그인이 프런트 엔드 서버 또는 프런트 엔드 풀을 가리키고 있는 경우 디렉터 풀을 가리키도록 DNS SRV 레코드를 변경해야 합니다.

