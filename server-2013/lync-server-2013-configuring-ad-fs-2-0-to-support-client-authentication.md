---
title: 클라이언트 인증을 지원하도록 AD FS 2.0 지원
TOCTitle: 클라이언트 인증을 지원하도록 AD FS 2.0 지원
ms:assetid: 4d93d400-ccaa-4da8-a71b-d05d7ba79d93
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn308565(v=OCS.15)
ms:contentKeyID: 56270231
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 클라이언트 인증을 지원하도록 AD FS 2.0 지원

 

_**마지막으로 수정된 항목:** 2013-07-03_

AD FS 2.0에서 스마트 카드를 이용한 인증을 지원하도록 구성할 수 있는 두 가지 인증 유형이 있습니다.

  - FBA(양식 기반 인증)

  - TLS(전송 계층 보안) 클라이언트 인증

양식 기반 인증을 사용하면 사용자가 자신의 이름/암호를 사용하거나 스마트 카드 및 PIN을 사용하여 인증할 수 있도록 하는 웹 페이지를 개발할 수 있습니다. 이 항목에서는 AD FS 2.0으로 TLS(전송 계층 보안) 클라이언트 인증을 구현하는 방법을 집중적으로 다룹니다. AD FS 2.0 인증 유형에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/p/?LinkId=313384](http://go.microsoft.com/fwlink/p/?linkid=313384)에서 AD FS 2.0: 로컬 인증 유형을 변경하는 방법(영어)을 참고하세요.


**클라이언트 인증을 지원하도록 AD FS 2.0을 구성하려면**

1.  도메인 관리자 계정을 사용하여 AD FS 2.0에 로그인합니다.

2.  Windows 탐색기를 시작합니다.

3.  C:\\inetpub\\adfs\\ls로 이동합니다.

4.  기존 web.config 파일의 백업 복사본을 만듭니다.

5.  메모장을 사용하여 기존 web.config 파일을 엽니다.

6.  메뉴 표시줄에서 **편집**을 선택한 후 **찾기**를 선택합니다.

7.  **\<localAuthenticationTypes\>**를 검색합니다.
    
    4개의 인증 유형이 한 줄에 하나씩 나열되어 있습니다.

8.  TLSClient 인증 유형이 포함되어 있는 줄을 섹션에 있는 목록 맨 위로 이동합니다.

9.  web.config 파일을 저장하고 닫습니다.

10. 상승된 권한을 사용하여 명령 프롬프트를 시작합니다.

11. 다음 명령을 실행하여 IIS를 다시 시작합니다.
    
        IISReset /Restart /NoForce

