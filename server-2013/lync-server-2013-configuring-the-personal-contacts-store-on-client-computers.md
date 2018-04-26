---
title: 클라이언트 컴퓨터에서 개인 연락처 저장소 구성
TOCTitle: 클라이언트 컴퓨터에서 개인 연락처 저장소 구성
ms:assetid: ec69a6cb-07f2-4057-9544-55035f83eeae
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721922(v=OCS.15)
ms:contentKeyID: 49886044
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 클라이언트 컴퓨터에서 개인 연락처 저장소 구성

 

_**마지막으로 수정된 항목:** 2014-02-05_

Microsoft Lync Server 2013과 Microsoft Exchange Server 2013을 통합하려는 경우 Microsoft Lync 2010을 실행하는 모든 클라이언트 컴퓨터에 개인 연락처 저장소를 구성하는 것이 좋습니다. 특히 Exchange를 개인 연락처 저장소로 사용하도록 Lync를 구성해야 하며 이와 동시에 사용자가 해당 결정을 재정의할 수 없도록 해야 합니다. 각 클라이언트 컴퓨터에서 레지스트리 값을 만들고 구성하여 이 작업을 수행할 수 있습니다.

Lync 2013을 실행하는 컴퓨터에는 이 작업을 수행할 필요가 없습니다.

단일 컴퓨터에서 이 값을 구성하려면 다음 절차를 수행합니다.

1.  클라이언트 컴퓨터에서 **시작**을 클릭한 다음 **실행**을 클릭합니다.

2.  **실행** 대화 상자에서 regedit를 입력하고 Enter 키를 누릅니다.

3.  레지스트리 편집기에서 **HKEY\_LOCAL\_MACHINE**, **Software**,**Policies**, **Microsoft**, **Communicator**를 차례로 확장합니다.

4.  **Communicator**를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **DWORD(32비트) 값**을 클릭합니다.

5.  새 값을 만들었으면 **PersonalContactStoreOverride**를 입력하고 Enter 키를 눌러 값의 이름을 변경합니다.

6.  PersonalContactStoreOverride의 값이 0으로 설정되었는지 확인하고 레지스트리 편집기를 닫습니다.

여러 컴퓨터에 이와 동일한 변경 내용을 적용해야 하는 경우에는 사용자 지정 그룹 정책 개체를 만들면 됩니다. 그룹 정책 설명서([http://go.microsoft.com/fwlink/?linkid=268543\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268543%26clcid=0x412))를 참고하세요.

