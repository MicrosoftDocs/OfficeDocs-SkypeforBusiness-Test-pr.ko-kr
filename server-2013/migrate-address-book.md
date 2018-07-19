---
title: 주소록 마이그레이션
TOCTitle: 주소록 마이그레이션
ms:assetid: ac7f0f39-4c6d-4702-8e25-93a73e3d800f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205160(v=OCS.15)
ms:contentKeyID: 49304699
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-09_

일반적으로 Lync Server 2010 주소록은 다른 토폴로지와 함께 마이그레이션됩니다. 하지만 Lync Server 2010 환경에서 다음과 같은 항목을 사용자 지정한 경우 일부 마이그레이션 후 단계를 수행해야 할 수 있습니다.

  - OU(조직 구성 단위)별로 주소록 항목을 그룹화하도록 **PartitionbyOU** WMI 속성 설정

  - 주소록 정규화 규칙을 사용자 지정

  - **UseNormalizationRules** 매개 변수의 기본값을 False로 변경

**그룹화된 주소록 항목**

각 OU에 대해 주소록을 만들기 위해 **PartitionbyOU** WMI 속성을 True로 설정한 경우 주소록 항목을 계속 그룹화하려면 사용자 및 대화 상대에 대해 **msRTCSIP-GroupingId** Active Directory 특성을 설정해야 합니다. 주소록 항목을 그룹화하여 주소록 검색 범위를 제한할 수도 있습니다. **msRTCSIP-GroupingId** 특성을 사용하려면 특성을 채우는 스크립트를 작성하여 함께 그룹화하려는 모든 사용자에 대해 동일한 값을 지정합니다. 예를 들어 OU의 모든 사용자에 대해 단일 값을 지정합니다.

**주소록 정규화 규칙**

Lync Server 2010 환경에서 주소록 정규화 규칙을 사용자 지정한 경우 사용자 지정된 규칙을 파일럿 풀에 마이그레이션해야 합니다. 주소록 정규화 규칙을 사용자 지정하지 않은 경우 주소록 서비스에 대해 마이그레이션할 항목이 없습니다. Lync Server 2013의 기본 정규화 규칙은 Lync Server 2010의 기본 규칙과 동일합니다. 사용자 지정된 정규화 규칙을 마이그레이션하려면 이 섹션 뒷부분에 나온 절차를 따르십시오.


> [!NOTE]
> 조직에서 원격 통화 제어를 사용하고 사용자가 주소록 정규화 규칙을 사용자 지정한 경우 원격 통화 제어를 사용하기 전에 이 항목의 절차를 수행해야 합니다. 이 절차를 수행하려면 RTCUniversalServerAdmins 그룹의 구성원이거나 이와 동등한 권한이 있어야 합니다.



**False로 설정된 UseNormalizationRules**

Lync Server 2013에서 정규화 규칙이 적용되게 하지 않고도 사용자가 Active Directory 도메인 서비스에 정의된 전화 번호를 사용할 수 있도록 **UseNormalizationRules**의 값을 False로 설정한 경우 **UseNormalizationRules** 및 **IgnoreGenericRules** 매개 변수를 True로 설정해야 합니다. 이러한 매개 변수를 True로 설정하려면 이 섹션 뒷부분에 나온 절차를 따르십시오.

## 사용자 지정된 주소록 정규화 규칙을 마이그레이션하려면

1.  주소록 공유 폴더의 루트에서 Company\_Phone\_Number\_Normalization\_Rules.txt 파일을 찾고 이를 Lync Server 2013 파일럿 풀에 있는 주소록 공유 폴더의 루트에 복사합니다.
    

    > [!NOTE]
    > ABS 웹 구성 요소 파일 디렉터리에 샘플 주소록 정규화 규칙이 설치되어 있습니다. 경로는 <STRONG>$설치 드라이브 문자:\Program Files\Microsoft Lync Server 2013\Web Components\Address Book Files\Files\ Sample_Company_Phone_Number_Normalization_Rules.txt</STRONG>입니다. 이 파일은 주소록 공유 폴더의 루트 디렉터리로 복사하여&nbsp; <STRONG>Company_Phone_Number_Normalization_Rules.txt</STRONG>로 이름을 바꿀 수 있습니다. 예를 들어 <STRONG>$serverX</STRONG>에 공유된 주소록의 경우 &nbsp;경로는 <STRONG>\\$serverX \LyncFileShare\2-WebServices-1\ABFiles</STRONG>와 유사합니다.



2.  메모장과 같은 텍스트 편집기를 사용하여 Company\_Phone\_Number\_Normalization\_Rules.txt 파일을 엽니다.

3.  특정 유형의 항목은 Lync Server 2013에서 올바르게 작동하지 않습니다. 파일에서 이 단계에 설명한 항목 유형을 조사하고, 필요에 따라 편집한 후 변경 내용을 파일럿 풀의 주소록 공유 폴더에 저장합니다.
    
    공백 또는 문장 부호가 포함된 문자열의 경우 정규화 규칙에 입력할 때 이러한 문자가 제거되기 때문에 이러한 문자열을 사용하면 정규화 규칙이 실패할 수 있습니다. 공백 또는 문장 부호가 필요한 문자열의 경우 문자열을 수정해야 합니다. 예를 들어 다음 문자열을 사용하면 정규화 규칙이 실패합니다.
    
        \s*\(\s*\d\d\d\s*\)\s*\-\s*\d\d\d\s*\-\s*\d\d\d\d
    
    다음 문자열을 사용하면 정규화 규칙이 실패하지 않습니다.
    
        \s*\(?\s*\d\d\d\s*\)?\s*\-?\s*\d\d\d\s*\-?\s*\d\d\d\d

## UseNormalizationRules 및 IgnoreGenericRules를 true로 설정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음 중 하나를 수행합니다.
    
      - 배포에 Lync Server 2013만 포함되어 있는 경우 전역 수준으로 다음 cmdlet을 실행하여 **UseNormalizationRules** 및 **IgnoreGenericRules**의 값을True로 변경합니다.
        
            Set-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true
    
      - 배포에 Lync Server 2013과 Lync Server 2010 또는 Office Communications Server 2007 R2가 함께 포함되어 있는 경우 다음 cmdlet을 실행하여 토폴로지의 각 Lync Server 2013 풀에 할당합니다.
        
            new-csaddressbookconfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true

3.  모든 풀에서 중앙 관리 저장소 복제가 수행될 때까지 기다립니다.

4.  배포의 전화 정규화 규칙 파일 "Company\_Phone\_Number\_Normalization\_Rules.txt"에 들어 있는 내용을 삭제하여 이 파일을 수정합니다. 이 파일은 각 Lync Server 2013 풀의 파일 공유에 있습니다. 이 파일이 없는 경우 "Company\_Phone\_Number\_Normalization\_Rules.txt"라는 이름의 비어 있는 파일을 만듭니다.

5.  모든 프런트 엔드 풀에서 새 파일을 읽을 때까지 몇 분 정도 기다립니다.

6.  배포의 각 Lync Server 2013 풀에 대해 다음 cmdlet을 실행합니다.
    
        Update-CsAddressBook

