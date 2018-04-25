---
title: 'Lync Server 2013: 역방향 프록시에 대한 인증서 설정'
TOCTitle: 역방향 프록시에 대한 인증서 설정
ms:assetid: c03a08ec-a67b-4f11-b0d7-6677461beaaa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412938(v=OCS.15)
ms:contentKeyID: 49304908
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 역방향 프록시에 대한 인증서 설정

 

_**마지막으로 수정된 항목:** 2012-09-08_

각 역방향 프록시 서버에는 수신 서비스에서 사용할 웹 서버 인증서가 필요합니다. 웹 서버 인증서는 공용 CA(인증 기간)에서 발급되어야 합니다.

이러한 인증서 요구 사항에 대한 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-external-user-access.md)을 참조하십시오.

## 역방향 프록시에 대해 웹 서비스 인증서를 설정하려면

  - 웹 서비스 인증서 설정 등을 비롯한 역방향 프록시가 설정되어 있어야 합니다. 에지 서버를 배포하기 전 역방향 프록시를 설정하지 않은 경우 [Lync Server 2013에 대한 역방향 프록시 서버 설치](lync-server-2013-setting-up-reverse-proxy-servers.md)의 절차를 사용하여 요청을 만들고 웹 서비스 인증서를 설치한 다음 각각의 웹 게시 규칙을 만들고 인증서를 사용하도록 웹 게시 규칙을 구성합니다.

