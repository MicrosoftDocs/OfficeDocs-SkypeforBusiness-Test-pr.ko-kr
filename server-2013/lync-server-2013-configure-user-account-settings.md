---
title: 'Lync Server 2013: 사용자 계정 설정 구성'
TOCTitle: 사용자 계정 설정 구성
ms:assetid: b7c74ecc-b924-4efc-8a56-3a5f94a9ef13
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412896(v=OCS.15)
ms:contentKeyID: 49304813
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자 계정 설정 구성

 

_**마지막으로 수정된 항목:** 2012-10-05_

전화 접속 사용자는 전화 번호나 내선 번호 및 PIN을 입력하여 인증된 사용자로 회의에 참가하며, 인증 시 Lync Server 사용자 계정에 지정된 전화 통신 **줄 URI** 가 필요합니다.

이 항목의 절차에서는 단일 사용자 계정에 대해 **줄 URI** 를 할당하는 방법에 대해 설명합니다. 여러 사용자 계정에 대해 **줄 URI** 를 할당해야 하는 경우 **Set-CsUser** cmdlet이 사용되는 스크립트를 만들 수 있습니다. 샘플 스크립트를 사용하여 **줄 URI** 를 여러 사용자 계정에 할당하는 방법에 대한 자세한 내용은 "여러 사용자에게 줄 URI 할당"( [http://go.microsoft.com/fwlink/?linkid=196945\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=196945%26clcid=0x412))을 참조하십시오.

## 사용자 계정 설정을 구성하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 **Cs-UserAdministrator** 또는 **CsAdministrator** 역할의 구성원으로 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자** 를 클릭합니다.

4.  검색 필드에 전화 접속 회의에 대해 구성할 사용자 이름을 입력하거나 **필터 추가** 를 클릭하여 검색 필드를 지정한 다음 **찾기** 를 클릭합니다.

5.  사용자 이름을 두 번 클릭하여 **Lync Server 사용자 편집** 대화 상자를 엽니다.

6.  **전화 통신** 의 **줄 URI** 필드에 정규화된 고유한 전화 번호를 입력합니다(예: tel:+14255550200).
    

    > [!NOTE]
    > <STRONG>줄 URI</STRONG> 는 <STRONG>전화 통신</STRONG> 이 <STRONG>PC 대 PC 전용</STRONG> , <STRONG>Enterprise Voice</STRONG> 또는 <STRONG>원격 통화 제어</STRONG> 또는 <STRONG>원격 통화 제어만</STRONG> 으로 설정된 경우에만 지정할 수 있습니다.



7.  **커밋** 을 클릭합니다.

