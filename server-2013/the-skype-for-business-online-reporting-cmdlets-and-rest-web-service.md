---
title: 'Lync Online: Lync Online 보고 cmdlet 및 REST 웹 서비스'
TOCTitle: Lync Online 보고 cmdlet 및 REST 웹 서비스
ms:assetid: cadd73a7-c08a-4102-b73a-ccb3ad4987bf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362845(v=OCS.15)
ms:contentKeyID: 56270303
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online 보고 cmdlet 및 REST 웹 서비스

 

_**마지막으로 수정된 항목:** 2015-06-22_

보고 기능과 함께 비즈니스용 Skype Online은 해당 보고서를 생성하는 데 도움을 주는 것은 물론 관리자가 사용자 지정된 보고 데이터를 반환하기 위해 사용할 수 있는 5개의 Windows PowerShell cmdlet에 대한 액세스를 제공합니다. 또한 비즈니스용 Skype Online에는 개발자가 사용자 지정된 보고 정보를 검색하는 데 사용할 수 있는 REST(Representational State Transfer)도 포함되어 있습니다.

관리자가 사용할 수 있는 보고 cmdlet은 다음과 같습니다.

  - Get-CsActiveUserReport는 활성 사용자(비즈니스용 Skype Online에 로그온하고 최소 하나의 회의나 피어-투-피어 통신 세션에 참가한 사용자)의 수에 대한 정보를 제공합니다.

  - Get-CsAVConferenceTimeReport는 사용자가 오디오/비디오 회의에서 소비한 시간(분)에 대한 정보를 제공합니다.

  - Get-CsConferenceReport는 사용자가 참석한 회의의 수와 유형에 대한 정보를 제공합니다.

  - Get-CsP2PAVTimeReport는 사용자가 오디오 및/또는 비디오를 포함한 피어-투-피어 세션에서 소비한 시간(분)에 대한 정보를 제공합니다.

  - Get-CsP2PSessionReport는 사용자가 참가한 피어-투-피어 세션의 수와 유형에 대한 정보를 제공합니다.

대부분의 관리자는 Office 365 관리 센터에 제공되는 보고서를 사용해야 합니다. 이러한 보고서는 자동으로 생성되며 데이터를 그래픽으로 표현하므로 cmdlet에서 반환하는 원래의 숫자 값보다 쉽게 해석할 수 있습니다. 그러나 Windows PowerShell에 익숙한 관리자들은 보고 cmdlet을 사용하여 Lync Online 보고서에서 바로 사용할 수 없는 데이터를 반환할 수 있습니다. 예를 들어 보고 cmdlet은 세션 시간(각 세션이 지속된 시간(분))에 대한 정보를 반환하지만 Lync Online 보고서를 사용할 경우에는 개별 세션 시간을 확인할 수 없습니다. 마찬가지로 일 단위 보기에서 Lync Online 보고서는 지난 14일 동안에만 해당하는 정보만 표시하며, 다른 날짜(예: 4개월 전의 날짜)의 일일 합계를 검토하려면 보고 cmdlet을 사용해야 합니다.

관리자는 Microsoft Excel의 OData 데이터 쿼리 기능을 사용하여 사용자 지정 Office 365 보고서를 만드는 방법을 설명하는 [Excel을 사용하여 Office 365 보고 데이터 검색](http://msdn.microsoft.com/en-us/library/dn781442.aspx) 문서도 참조할 수 있습니다. 사용자 지정 보고서에서는 Office 365 보고 서비스에서 어떤 데이터가 얼마나 많이 반환되는지 제어할 수 있습니다. 사용자 지정 보고서에서는 또한 데이터를 어떻게 정렬하고 그룹화해야 하는지 지정하고 Office 365 관리 센터에 표시되지 않는 정보에 액세스할 수 있습니다.

개발 경험이 있는 관리자는 REST 웹 서비스를 사용하여 비즈니스용 Skype Online 관리 센터에 표시되지 않는 정보를 가져올 수 있습니다. REST 서비스는 각 기술이 클라이언트와 서버 간에 XML 데이터를 전송하는 방법을 제공한다는 점에서 SOAP 서비스와 비슷합니다. 그러나 REST 서비스는 SOAP 서비스보다 적어도 두 가지 면에서 더 뛰어납니다. 먼저 REST는 ATOM 배포 형식이라는 표준화된 형식을 사용하여 XML 데이터 전송을 수행하지만 SOAP은 데이터를 전송할 때 비표준 형식을 사용합니다. 또한 REST는 GET 및 POST 외에 HTTP 동사를 차단하는 네트워크에서 데이터를 전송할 수 있습니다.

## 참고 항목

#### 개념

[Lync Online 보고](https://technet.microsoft.com/ko-kr/library/dn362827\(v=ocs.15\))  

#### 기타 리소스

[Office 365 보고 웹 서비스](http://msdn.microsoft.com/en-us/library/office/jj984325.aspx)  
[Office 365 보고 웹 서비스에 대한 자세한 정보](http://msdn.microsoft.com/en-us/library/office/jj984321.aspx)  
[Exchange Online 보고 Cmdlet](http://technet.microsoft.com/en-us/library/jj200780\(v=exchg.150\).aspx)  
[Excel을 사용하여 Office 365 보고 데이터 검색](http://msdn.microsoft.com/en-us/library/dn781442.aspx)

