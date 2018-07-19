---
title: Lync에서 사용자 사진이 표시되는 방식
TOCTitle: Lync에서 사용자 사진이 표시되는 방식
ms:assetid: b44a364d-a1d2-4d45-b27a-b5f77775e233
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn783119(v=OCS.15)
ms:contentKeyID: 62832553
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync에서 사용자 사진이 표시되는 방식

 

_**마지막으로 수정된 항목:** 2015-03-09_

**요약:** Lync 클라이언트에 표시되는 사용자 사진은 회의 또는 메신저 대화 등 사용 중인 Lync 기능에 따라 달라질 수 있습니다.

Lync 2010에서는 Lync 프로필에 다른 Lync 사용자에게 표시되는 사진을 포함할 수 있는 기능이 도입되었습니다. Lync 클라이언트에서 대화 상대의 사진을 표시할지 여부를 선택할 수도 있습니다. Lync 2013에서는 사용자를 위한 고해상도 사진이 지원됩니다. 이 항목에서는 Lync 클라이언트가 어떤 방식으로 사용자 사진을 가져와 표시하고, 어디에 이미지를 저장하고, 각 이미지 원본에 대한 제한 사항은 무엇이며, 여러 Lync 서비스에서 사용자 사진이 어떻게 다르게 사용되는지 설명합니다.

## 계획 고려 사항

사용자 사진 지원을 구현하기 위한 계획을 세울 때에는 다음 사항을 고려해야 합니다.

  - 고해상도 사용자 사진 지원을 위해서는 사용자의 사서함이 Exchange 2013에 있고, Lync 사용자 계정이 Lync 2013 풀에 있어야 합니다.

  - 고해상도 사용자 사진은 Lync Server 2013 및 Exchange 2013이 모두 사용되는 환경에서만 지원됩니다.

  - Exchange 2010에 사서함이 있는 사용자는 항상 사용자 사진의 원본으로 AD DS의 **thumbnailPhoto** 특성을 사용합니다.

  - AD DS의 **thumbnailPhoto** 특성으로 저장된 사용자 사진은 외부/페더레이션 대화 상대에게 표시되지 않습니다.

  - 사용자 대화 상대의 사진이 AD DS에 저장되어 있으면 사용되는 이미지 파일이 96×96픽셀 및 100KB 미만의 파일 크기로 제한됩니다.

  - Lync Server와 Exchange Server 간에 연결이 끊기면 AD DS에 있는 사용자의 저해상도 **thumbnailPhoto**가 내부 사용자에게만 표시됩니다.

  - Lync 2013 모임에서 현재 발표자가 비디오를 사용할 수 없는 경우 고해상도 사용자 사진이 표시됩니다. 또한 갤러리에서 축소판 그림 이미지 위로 마우스를 이동해도 고해상도 사진이 표시됩니다.

## Lync 2010의 사용자 사진

Lync 2010 클라이언트에서는 **기본 회사 사진**과 **웹 주소의 사진 표시** 옵션 중에서 선택해 프로필의 사진을 표시할 수 있습니다.

## 기본 회사 사진

**기본 회사 사진** 옵션을 선택하면 Lync가 Active Directory 도메인 서비스에서 사용자에 대해 표시된 사진을 가져옵니다. 사용된 이미지는 Active Directory 도메인 서비스에서 **thumbnailPhoto** 특성의 값으로 정의된 이미지입니다. 이는 Outlook에서 이미지를 표시하기 위해 Exchange에서 사용하는 파일과 동일합니다.

Active Directory 도메인 서비스의 이미지를 사용하기 위해 고려해야 할 사항은 다음과 같습니다.

  - 크기가 최대 96x96픽셀인 이미지만 지원됩니다. 이미지의 파일 크기는 100KB로 제한됩니다.

  - 기본적으로 사용자는 **thumbnailPhoto** 특성에 사용되는 이미지를 변경할 수 있지만, Lync 클라이언트를 통해 직접 변경하는 것은 불가능합니다. Active Directory 도메인 서비스에서 이 기능을 사용하지 않도록 설정할 수 있습니다.

  - Active Directory 도메인 서비스에 저장된 이미지는 조직 외부의 대화 상대가 페더레이션 대화 상대라 하더라도 이들에게 표시되지 않습니다.

  - 대규모 조직의 경우 많은 사용자 이미지를 저장하고 검색하면 Active Directory 도메인 서비스 데이터베이스 크기와 성능이 영향을 받을 수 있습니다.

  - 이미지 크기와 파일 크기가 제한되므로 해상도가 낮은 이미지만 사용할 수 있습니다.

## Active Directory 도메인 서비스에서 사용자가 사용자 사진을 관리하는 방법

사용자는 Lync 2010 클라이언트를 통해 Active Directory 도메인 서비스 프로필에 사용되는 이미지를 직접 변경할 수 없습니다. 다음과 같은 옵션이 제공될 경우 이 중 하나를 사용해 변경할 수 있습니다.

  - **SharePoint Server**   사용자는 SharePoint Server의 '내 사이트'에 사진을 업로드한 후 [SharePoint에서 프로필 동기화를 구성](http://go.microsoft.com/fwlink/p/?linkid=507466)하여 사진을 Active Directory 도메인 서비스의 **thumbnailPhoto** 특성과 동기화할 수 있습니다.

  - **공용으로 액세스할 수 있는 URL에 저장된 사진**   사용자는 사용하려는 이미지에 공용으로 액세스할 수 있는 URL을 지정하여 사용자 사진을 구성할 수 있습니다. 이미지는 암호 없이 공용으로 액세스할 수 있어야 합니다. 지정된 웹 주소에 저장된 이미지는 현재 상태 정보의 대화 상대 카드 범주를 통해 다른 사용자에게 전송됩니다. Lync 클라이언트에서 사용자 사진을 표시해야 하는 경우 지정된 웹 주소에서 이미지를 가져옵니다.

  - **Windows PowerShell용 Exchange 2010 cmdlet**   관리자는 Exchange 2010 관리 셸에서 [Import-RecipientDataProperty](http://go.microsoft.com/fwlink/p/?linkid=507468) cmdlet을 실행하여 **thumbnailPhoto** 특성을 관리할 수 있습니다. Exchange 2010 cmdlet을 사용해 이미지를 가져올 경우 파일 크기는 10KB로 제한됩니다.

  - **타사 도구**   사용자는 **thumbnailPhoto** 특성에 자신의 사진만 업로드할 수 있습니다.

## 웹 주소의 사진 표시

**웹 주소의 사진 표시** 옵션을 선택하면 Lync가 사용자가 입력한 주소에서 이미지를 가져와 Lync의 사용자 사진으로 표시합니다.

웹 주소의 이미지를 사용할 때 고려해야 할 사항은 다음과 같습니다.

  - 파일 크기 제한은 [New-CsClientPolicy](http://go.microsoft.com/fwlink/p/?linkid=507463) cmdlet으로 정의된 클라이언트 정책의 **MaxPhotoSizeKB** 특성에 의해 결정됩니다. 기본 크기 제한은 30KB이며, 최대값은 100KB입니다. 이미지의 해상도에 대해서는 제한이 없지만 크기 제한을 초과하는 이미지 파일을 사용하는 경우에는 이미지가 Lync 클라이언트로 다운로드되지 않습니다. 값을 0으로 설정하여 Lync에서 모든 사용자 사진이 사용되지 않도록 설정할 수 있습니다.

  - 웹 주소의 사용자 사진은 외부 페더레이션 대화 상대가 볼 수 있습니다.

## 클라이언트 정책 cmdlet을 사용해 사용자의 사진 관리

Lync Server 2010에서 클라이언트 정책 설정은 CsClientPolicy cmdlet을 사용해 구성됩니다. 구성된 정책 설정은 인밴드 프로비저닝을 통해 클라이언트로 전송됩니다. 사용자 사진 환경을 결정하는 CsClientPolicy cmdlet의 두 가지 매개 변수는 **DisplayPhoto** 및 **MaxPhotoSizeKB**입니다. **DisplayPhoto** 및 **MaxPhotoSizeKB**에 해당하는 인밴드 프로비저닝 매개 변수를 **PhotoUsage**라고 합니다. **PhotoUsage** 매개 변수의 값은 **endpointConfigurationprovisionGroup**을 통해 클라이언트로 전송됩니다. 자세한 내용은 [클라이언트 정책 및 설정 개요](http://go.microsoft.com/fwlink/?linkid=507470)를 참조하세요.

**DisplayPhoto** 매개 변수 값은 사용자의 사진 이미지 원본을 결정합니다. 지원되는 값은 다음 표에 포함되어 있습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>DisplayPhoto 매개 변수 값</th>
<th>이미지 원본</th>
<th>Lync 2010 클라이언트 설정</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NoPhoto</p></td>
<td><p>없음</p></td>
<td><p><strong>내 사진을 표시하지 않음</strong></p></td>
</tr>
<tr class="even">
<td><p>PhotoFromADOnly</p></td>
<td><p>Active Directory</p></td>
<td><p><strong>기본 회사 사진</strong></p></td>
</tr>
<tr class="odd">
<td><p>AllPhotos</p></td>
<td><p>웹 주소</p></td>
<td><p><strong>웹 주소의 사진 표시</strong></p></td>
</tr>
</tbody>
</table>


## Lync 2010 클라이언트가 사진을 가져오는 방법

Lync 2010에서 사용자 사진은 주소록 서비스에 의해 서버에서 관리됩니다. Lync 클라이언트는 먼저 서버에서 메일 그룹 확장 웹 서비스를 통해 표시되는 ABWQ(주소록 웹 쿼리 서비스)를 쿼리해 사용자 사진을 가져옵니다. 클라이언트는 이미지를 표시해야 할 때마다 다운로드해야 하는 번거로움을 없애기 위해 이미지 파일을 받은 후에 사용자의 캐시에 복사합니다. 쿼리에서 반환된 특성 값 또한 사용자의 캐시된 주소록 서비스 항목에 저장됩니다. 주소록 서비스는 캐시된 모든 이미지를 24시간에 한 번씩 삭제합니다. 따라서 새 사용자 이미지를 서버의 캐시에서 업데이트하는 데 최대 24시간이 걸릴 수 있습니다. [Update-CsAddressBook](https://docs.microsoft.com/en-us/powershell/module/skype/Update-CsAddressBook) cmdlet를 사용하여 캐시에 대한 업데이트를 강제로 실행할 수 있습니다.

현재 상태에 포함된 사용자 사진에도 Lync 클라이언트에서 최신 이미지가 있는지 확인하는 데 사용하는 연결된 해시 값이 있습니다. 현재 상태에 사용된 이미지 파일이 변경되면 클라이언트가 자동으로 알림을 받습니다.


> [!NOTE]
> GalContacts.db 데이터베이스에 사진이 저장되지 않기 때문에 사용자 사진 다운로드는 클라이언트 정책(<A href="http://go.microsoft.com/fwlink/p/?linkid=507508">Set-CsClientPolicy</A>)의 <STRONG>AddressBookAvailability</STRONG> 설정과 상관없이 진행됩니다.



ABWQ 서비스에 대한 쿼리에는 다음 특성이 포함됩니다.

  - **PhotoHash**   이진 사진 데이터의 해시 값으로, 현재 사진이 변경되었는지 여부를 확인하는 데 사용됩니다.

  - **PhotoRelPath**   서버에 저장된 이미지 파일에 대한 상대 경로입니다.

  - **PhotoSize**   바이트 단위의 이미지 파일 크기입니다.

  - **TimeStamp**   서버에서 이미지 파일을 마지막으로 다운로드해 클라이언트 캐시에 복사한 날짜 및 시간입니다.

다음으로 Lync 2010 클라이언트는 이미지 파일을 가져온 후에 쿼리에서 반환된 특성 값을 인밴드 프로비저닝에서 클라이언트가 받은 특성 값과 비교해 두 값이 다른지 확인합니다. 값이 다를 경우 클라이언트는 HTTP GET 요청을 사용해 로그인한 사용자의 이미지 파일을 검색합니다.

또한 클라이언트는 이미지 파일의 캐시된 버전을 만든 시간부터 24시간마다 서버를 확인해 서버의 **PhotoHash** 특성 값을 클라이언트의 값과 비교합니다. 두 값이 다르면 클라이언트에서 이미지 파일이 변경되었음을 인식합니다. 업데이트된 이미지 파일을 가져오기 위해 클라이언트는 다시 한 번 ABWQ 서비스를 쿼리하여 서버의 이미지 파일로 클라이언트 캐시의 이미지 파일을 업데이트합니다. 이 때 클라이언트 캐시에 있는 파일의 **TimeStamp**도 다시 설정됩니다.

다음은 ABWQ 서비스에 대한 쿼리의 응답 예제입니다.

    <Attribute>
              <Name>PhotoRelPath</Name>
              <Value>efa6096aed2746cb9ab2037f7dbdde9d.f2eeeb5946db54a7aa607ecd3ae09d
              95.photo</Value>
              <Values xmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" i:nil="true" />
    </Attribute>
    <Attribute>
              <Name>PhotoHash</Name>
              <Value>f2eeeb5946db54a7aa607ecd3ae09d95</Value>
              <Values xmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" i:nil="true" />
    </Attribute>
    <Attribute>
         <Name>PhotoSize</Name>
         <Value>4620</Value>
         <Valuesxmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays"
    i:nil="true" />
    </Attribute>

## Lync 2013의 사용자 사진

Lync 2013에는 사용자 사진을 위한 고해상도 이미지 지원이 도입되었습니다. 또한 Lync 2013에서 Exchange 2013의 사용자 사서함에 사용자 사진을 저장하는 기능이 지원되면서 Lync 2010의 이미지 해상도 및 크기 제한이 사라졌습니다. Lync 2013의 사용자 사진은 크기가 최대 648x648픽셀, 파일 크기가 최대 20MB까지 허용됩니다. Lync 2013의 고해상도 사진은 Exchange 2013의 사용자 사서함에 있어야 하며, Lync 2013 클라이언트를 통해서만 지원됩니다. 이와 같은 Exchange와의 통합은 Oauth라고 하는 2013 버전의 Lync, Exchange, SharePoint에 포함된 새로운 권한 부여 프레임워크를 활용합니다.

Exchange 2013가 배포에 사용되지 않은 경우 사용자 사진에 대한 지원은 Lync 2010에서와 동일합니다. 하지만 Lync 2013 클라이언트의 경우 사용할 사진을 선택할 수 있는 사용자 옵션이 다릅니다. Lync 2013 클라이언트에서는 사용자가 **내 사진 숨기기** 또는 **내 사진 표시**를 선택할 수 있습니다. **웹 사이트의 사진 표시** 옵션은 기본적으로 제공되지 않지만 클라이언트 정책을 할당해 설정할 수 있습니다.

## 내 사진 숨기기

사용자 사진에 대한 설정은 Lync 2013의 **옵션** 대화 상자에 있습니다. **내 사진 숨기기**를 선택하는 경우 Lync 클라이언트에서는 사용자의 사용자 사진이 표시되지 않지만 대화 상대 카드와 Lync 외부에는 여전히 사용자 사진이 표시됩니다.

## 내 사진 표시

**내 사진 표시** 옵션을 선택하면 사용자 사진이 Lync 클라이언트와 Lync 대화에 참여한 다른 사용자에게 표시됩니다. 여기에는 AD DS에 저장된 이미지가 사용됩니다.

## 웹 사이트의 사진 표시

**웹 사이트의 사진 표시** 옵션을 사용하도록 클라이언트 정책을 설정한 경우 Lync 2013에서 이 옵션을 사용할 수 있습니다. 클라이언트 버전은 15.0.4535.1002 이상 버전이어야 하며, [Lync 누적 업데이트: 2013년 11월](http://go.microsoft.com/fwlink/p/?linkid=509908)이 설치되어 있어야 합니다. 사용자는 로그아웃했다가 다시 로그인해야 클라이언트의 변경 내용을 볼 수 있습니다.

Lync Server 관리 셸에서 [Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy) 정책을 실행하여 **웹 사이트의 사진 표시** 설정을 사용하도록 클라이언트 정책을 설정할 수 있습니다. 다음 예제 cmdlet은 배포에 속한 모든 사용자를 위해 전역적으로 정책을 설정하는 방법을 보여 줍니다.

    $pe=New-CsClientPolicyEntry -Name EnablePresencePhotoOptions -Value True

    $po=Get-CsClientPolicy -Identity Global

    $po.PolicyEntry.Add($pe)

    Set-CsClientPolicy -Instance $po

사용자의 사서함에 이미지를 업로드하면 Exchange가 클라이언트 응용 프로그램에서 사용할 수 있는 더 낮은 해상도의 이미지를 자동으로 만듭니다. 사용자 사진은 AD DS에서도 업데이트됩니다.


> [!NOTE]
> AD DS에서 이미지 파일이 업데이트되면 48x48픽셀 이미지가 만들어지고 AD DS의 thumbnailPhoto에 사용됩니다. 기존 이미지는 모두 바뀝니다. 따라서 이전에 AD DS에 96x96 이미지를 추가했다면 새 48x48 이미지가 이 이미지를 덮어씁니다. Lync 2010 클라이언트가 AD DS에서 사용자 사진을 가져오기 때문에 이 클라이언트를 사용하는 환경에 사용자가 있는 경우에만 해당되는 내용입니다. 조직에서 Lync 2010 클라이언트를 사용하고 있는 경우에는 96x96픽셀 이미지를 가져와 AD DS에서 만든 이미지를 바꿀 수 있습니다.



## Lync 2013의 사용자 사진 지원

Lync 2013에서는 다음 표에 설명되어 있는 대로 사용자 사진에 세 가지 이미지 해상도가 지원됩니다. 사용되는 이미지는 Lync 사용자에게 할당된 클라이언트 정책 설정에 의해 결정됩니다. 자세한 내용은 이 항목의 "클라이언트 정책 cmdlet을 사용해 사용자의 사진 관리"를 참조하세요.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>이미지 해상도(픽셀)</th>
<th>Application</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>48 x 48</p></td>
<td><p>더 높은 해상도의 이미지를 선택하지 않은 경우에 사용됨</p></td>
</tr>
<tr class="even">
<td><p>96 x 96</p></td>
<td><p>Outlook Web App 및 Outlook 2013에서 사용됨</p></td>
</tr>
<tr class="odd">
<td><p>648 x 648</p></td>
<td><p>Lync 2013 데스크톱 클라이언트 및 Lync 2013 Web App에서 사용됨</p></td>
</tr>
</tbody>
</table>


Exchange 2013에서 사서함을 사용할 수 있는 사용자라면 누구나 Outlook Web Access 또는 Lync 2013 클라이언트 옵션을 통해 고해상도 사진을 포함한 다른 이미지를 업로드할 수 있습니다. 이미지에 권장되는 설정은 다음과 같습니다.

  - **이미지 해상도**   648x648픽셀

  - **색 농도**   24비트

  - **이미지 파일 크기**   최대 20MB

  - **파일 형식**   JPEG

크기가 648x648픽셀인 일반적인 24비트 JPEG 이미지의 경우 파일 크기가 240KB 정도이므로 사용자 사진 4장당 1MB의 저장 공간이 필요합니다.

