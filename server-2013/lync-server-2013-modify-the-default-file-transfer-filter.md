---
title: 기본 파일 전송 필터 수정
TOCTitle: 기본 파일 전송 필터 수정
ms:assetid: 791774a2-0bb6-4b5b-aeb0-ff69abb170f4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521017(v=OCS.15)
ms:contentKeyID: 49304108
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기본 파일 전송 필터 수정

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server 2013에서는 Lync Server 2013 배포 내에서 다음과 같은 파일 관련 작업을 수행하는 동안 특정 파일 형식을 차단하는 전역 파일 전송 필터를 제공합니다.

  - IM(인스턴트 메시징) 대화 중 파일 전송 요청

  - Office Live Meeting 2007 클라이언트에서 참고 파일 기능을 사용하는 중의 파일 업로드 및 다운로드

  - 회의 중 멀티미디어 재생

차단하거나 허용할 파일 형식에 따라 Lync Server 제어판을 사용하여 전역 필터를 수정할 수 있습니다. 파일 전송 필터링에 대한 자세한 내용은 [Lync Server 2013에서 IM(메신저 대화)에 대한 파일 전송 및 URL 필터링 구성](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)을 참조하십시오.

## 기본 파일 전송 필터를 수정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **IM 및 현재 상태**를 클릭한 다음 **파일 필터**를 클릭합니다.

4.  **파일 필터** 페이지에서 **전역** 필터를 두 번 클릭합니다.

5.  **파일 필터 편집**에서 **파일 필터 사용** 확인란을 선택합니다.

6.  **파일 전송** 드롭다운 목록 상자에서 **모두 차단** 또는 **특정 파일 형식 차단**을 클릭합니다.

7.  **모두 차단**을 클릭한 경우 9단계로 건너뜁니다.

8.  **특정 파일 형식 차단**을 클릭한 경우 다음을 수행합니다.
    
    1.  **선택**을 클릭하여 차단할 파일 형식 확장명의 기본 목록을 수정합니다.
    
    2.  **파일 형식 선택**에서 **파일 형식 확장명** 아래의 범주에서 해당 확장명을 추가하거나 제거하여 차단하거나 허용할 파일 형식을 선택합니다.
    
    3.  차단할 파일 형식 확장명이 표시되지 않은 경우 **목록에 새 파일 형식 확장명 추가** 아래의 텍스트 상자에 확장명을 입력한 다음 **추가**를 클릭합니다.
    
    4.  **확인**을 클릭합니다.

9.  **커밋**을 클릭합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 IM(메신저 대화)에 대한 파일 전송 및 URL 필터링 구성](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)  
[특정 사이트에 대한 새 파일 전송 필터 만들기](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)  
[IM 대화에서 하이퍼링크를 처리할 새 URL 필터 만들기](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)  

#### 개념

[기본 URL 필터 수정](lync-server-2013-modify-the-default-url-filter.md)

