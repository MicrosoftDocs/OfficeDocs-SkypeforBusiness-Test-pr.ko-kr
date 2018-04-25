---
title: 'Lync Server 2013: 스키마 복제 확인'
TOCTitle: 스키마 복제 확인
ms:assetid: ad01a7cf-aa79-4648-ba5a-a7a09172db36
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412822(v=OCS.15)
ms:contentKeyID: 49304703
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Active Directory 스키마 복제 확인

 

_**마지막으로 수정된 항목:** 2012-10-29_

포리스트 준비를 실행하기 전에 스키마 파티션이 복제되었는지 수동으로 확인합니다.

## 스키마 복제를 수동으로 확인하려면

1.  Enterprise Admins 그룹의 구성원으로 도메인 컨트롤러에 로그온합니다.

2.  **시작** , **관리 도구** 를 차례로 클릭한 다음 **ADSI 편집** 을 클릭하여 ADSI 편집을 엽니다.
    

    > [!TIP]
    > 또는 명령줄에서 <STRONG>adsiedit.msc</STRONG> 를 실행할 수도 있습니다.



3.  아직 선택되지 않은 경우 MMC(Microsoft Management Console) 트리에서 **ADSI 편집** 을 클릭합니다.

4.  **동작** 메뉴에서 **연결** 을 클릭합니다.

5.  **잘 알려진 명명 컨텍스트를 선택합니다** 아래에 있는 **연결 설정** 대화 상자에서 **스키마** 를 선택한 다음 **확인** 을 클릭합니다.

6.  스키마 컨테이너 아래에서 CN=ms-RTC-SIP-SchemaVersion을 검색합니다. 이 개체가 존재하고 **rangeUpper** 특성 값이 1150이며 **rangeLower** 특성 값이 13이면 스키마가 성공적으로 업데이트 및 복제된 것입니다. 반면 이 개체가 없거나 **rangeUpper** 및 **rangeLower** 특성 값이 지정된 값이 아닐 경우에는 스키마가 수정되지 않았거나 복제되지 않은 것입니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 Active Directory 스키마 준비 실행](lync-server-2013-running-schema-preparation.md)  

#### 개념

[Lync Server 2013에서 Active Directory 스키마 준비](lync-server-2013-preparing-the-active-directory-schema.md)

