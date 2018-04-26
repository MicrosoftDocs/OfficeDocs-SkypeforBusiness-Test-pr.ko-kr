---
title: 경계 네트워크 외부에 위치한 감시자 노드에 인증서 설치
TOCTitle: 경계 네트워크 외부에 위치한 감시자 노드에 인증서 설치
ms:assetid: 825c9c02-1951-4d7a-a25e-a313a85333f8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688113(v=OCS.15)
ms:contentKeyID: 49885846
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 경계 네트워크 외부에 위치한 감시자 노드에 인증서 설치

 

_**마지막으로 수정된 항목:** 2012-10-22_

경계 네트워크에서(예: Lync Server 에지 서버), 기업 외부에서(예: 외부 가상 트랜잭션 감시자 노드) 또는 Active Directory 도메인 서비스 트러스트 경계에서 실행되는 System Center Operations Manager 에이전트를 사용하려면 System Center Operations Manager 게이트웨이 서버를 구성해야 합니다. 이 서버 역할을 통해 루트 관리 서버와의 트러스트 관계가 없는 에이전트가 알림을 발생시킬 수 있습니다. 자세한 내용은 System Center Operations Manager TechNet 라이브러리에서 "Operations Manager 2007에서 게이트웨이 서버 관리"([http://go.microsoft.com/fwlink/?linkid=268703\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268703%26clcid=0x412))를 참조하십시오.

이러한 위치 중 하나에 에이전트를 배포할 경우 감시자 노드가 System Center Operations Manager에 알림을 보낼 수 있게 해주는 인증서도 요청 및 구성해야 합니다. 이 프로세스를 간소화하기 위해 Operations Manager 팀은 감시자 노드 컴퓨터에 올바른 유형의 인증서를 요청하고 설치할 수 있게 해주는 유틸리티 집합을 만들었습니다. 자세한 내용을 확인하고 이러한 유틸리티를 다운로드하려면 "인증서 생성 마법사를 통해 도메인에 가입되지 않은 에이전트에 대한 인증서를 손쉽게 얻기" 블로그 문서([http://go.microsoft.com/fwlink/?linkid=267421\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=267421%26clcid=0x412))를 참조하십시오.

