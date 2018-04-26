---
title: Outlook 사용 목록 업데이트
TOCTitle: Outlook 사용 목록 업데이트
ms:assetid: 5db120dc-52f9-4dde-acb9-3824ae245086
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ215438(v=OCS.15)
ms:contentKeyID: 49303775
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Outlook 사용 목록 업데이트

 

_**마지막으로 수정된 항목:** 2013-01-07_

Outlook용 추가 기능 관리 목록에 Microsoft Lync 2013용 온라인 모임 추가 기능을 포함하는 정책을 만들어서 해당 추가 기능을 항상 사용자에 대해 사용하도록 설정할 수 있습니다. 추가 기능 관리 목록 정책은 그룹 정책 관리 콘솔의 Office 관리 템플릿 파일에 포함되어 있습니다. 이 정책은 HKCU\\Software\\Policies\\Microsoft\\Office\\15.0\\Outlook15\\Resiliency\\AddinList 아래에 레지스트리 키를 만듭니다. 이 키에 ucaddin.dll에 대한 값을 추가한 다음 해당 정책이 항상 사용하도록 설정되고 사용자가 수동으로 비활성화할 수 없도록 ucaddin.dll 값을 구성할 수 있습니다.

## Outlook 추가 기능 목록에 ucaddin.dll을 추가하려면

  - HKCU\\Software\\Policies\\Microsoft\\Office\\15.0\\Outlook15\\Resiliency\\AddinList에 있는 AddinList 레지스트리 키에 다음 값을 추가합니다.
    
      - 레지스트리 유형 = REG\_SZ
    
      - 이름 = ucaddin.dll
    
      - 값 = 1(추가 기능이 항상 설정되고 최종 사용자가 관리할 수 없도록 지정)

