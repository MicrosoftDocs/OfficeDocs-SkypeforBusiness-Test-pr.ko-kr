---
title: Microsoft Lync Server 2013에서 고해상도 사진 사용 구성
TOCTitle: Microsoft Lync Server 2013에서 고해상도 사진 사용 구성
ms:assetid: 995da78a-dc44-45a3-908d-16fe36cfa0d9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688150(v=OCS.15)
ms:contentKeyID: 49885886
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Server 2013에서 고해상도 사진 사용 구성

 

_**마지막으로 수정된 항목:** 2014-02-05_

Microsoft Lync Server 2010에서는 사용자가 연락처의 사진을 보고 자신의 사진을 다른 사용자에게 표시할 수 있었습니다. 일반적으로 이러한 사진은 Active Directory에서 사용자의 thumbnailPhoto 특성의 일부로 저장되었으며, 이로 인해 사진의 크기와 해상도에 상당한 제한이 있었습니다. thumbnailPhoto 특성은 최대 48 x 48픽셀 크기의 사진을 포함할 수 있기 때문입니다.

이제 Microsoft Lync Server 2013에서는 사진을 사용자의 Microsoft Exchange Server 2013 사서함에 저장할 수 있어 최대 648 x 648픽셀 크기의 사진을 사용할 수 있습니다. 이뿐만 아니라 Exchange 2013에서는 필요에 따라 다른 제품에 사용하도록 이러한 사진의 크기를 자동으로 조정할 수 있습니다. 일반적으로 이 자동 조정 기능을 통해 세 가지 사진 크기 및 해상도를 사용할 수 있습니다.

  - 48 x 48픽셀: Active Directory thumbnailPhoto 특성에 사용되는 크기입니다. 사진을 Exchange 2013에 업로드하면 Exchange에서 48 x 48픽셀 버전의 사진을 자동으로 만들어 사용자의 thumbnailPhoto 특성을 업데이트합니다. 그러나 그 반대의 경우는 성립하지 않습니다. 즉, Active Directory에서 thumbnailPhoto 특성을 수동으로 업데이트하는 경우 사용자의 Exchange 2013 사서함에 있는 사진이 자동으로 업데이트되지 않습니다.

  - 96 x 96픽셀: Microsoft Outlook 2013 Web App, Microsoft Outlook 2013, Microsoft Lync Web App 및 Lync 2013에서 사용하도록 제공됩니다.

  - 648 x 648픽셀: Lync 2013 및 Microsoft Lync Web App에서 사용하도록 제공됩니다.


> [!NOTE]
> 리소스가 충분한 경우 모든 Office 2013 응용 프로그램에서 최대의 해상도와 최적의 화질을 제공하는 648x648 사진을 업로드하는 것이 좋습니다. 크기가 648 x 648이고 비트 수준이 24인 각 JPEG 사진의 파일 크기는 약 240KB입니다. 즉, 4명의 사용자 사진마다 약 1MB가 필요합니다.



Outlook 2013 Web App을 실행하는 사용자는 Exchange 웹 서비스를 사용하여 액세스되는 고해상도 사진을 업로드할 수 있습니다. 이 경우 사용자는 자신의 사진만 업데이트할 수 있지만 관리자는 Exchange 관리 셸 및 다음과 같은 일련의 Windows PowerShell 명령을 사용하여 모든 사용자의 사진을 업데이트할 수 있습니다.

    $photo = ([Byte[]] $(Get-Content -Path "C:\Photos\Kenmyer.jpg" -Encoding Byte -ReadCount 0))
    Set-UserPhoto -Identity "Ken Myer" -PictureData $photo -Confirm:$False
    Set-UserPhoto -Identity "Ken Myer" -Save -Confirm:$False

위의 예에서 첫 번째 명령은 Get-Content cmdlet을 사용하여 C:\\Photos\\Kenmyer.jpg 파일의 내용을 읽고 해당 데이터를 $photo라는 변수에 저장합니다. 두 번째 명령에서는 Exchange cmdlet인 Set-UserPhoto를 사용하여 사진을 업로드하고 이 사진을 Ken Myer의 사용자 계정에 연결합니다.


> [!NOTE]
> 이 예에서는 사용자 계정 ID로 Ken Myer의 Active Directory 표시 이름이 사용되었습니다. 또한 사용자의 SMTP 주소 또는 사용자 계정 이름 등의 다른 식별자를 사용하여 사용자 계정을 참조할 수도 있습니다. 자세한 내용은 Set-UserPhoto cmdlet에 대한 설명서(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=268536%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=268536&amp;clcid=0x412</A>)를 참고하세요.



사진을 업로드한다고 해서 해당 사진이 Ken Myer의 사용자 계정에 할당되는 것은 아닙니다. 사진을 업로드하면 단지 Outlook Web App 옵션 페이지에 해당 사진의 미리 보기가 표시됩니다. 실제로 사진을 사용자 계정에 할당하려면 사용자가 옵션 페이지에서 **저장**을 클릭하거나 관리자가 위 예에 있는 세 번째 명령을 실행해야 합니다. 세 번째 명령은 다음과 같이 Save 매개 변수를 사용하여 사진을 Ken Myer의 사용자 계정에 할당합니다.

    Set-UserPhoto -Identity "Ken Myer" -Save -Confirm:$False

새 사진이 사용자 계정에 할당되었는지 확인하기 위해 Ken Myer는 Lync 2013에 로그온하여 **옵션**을 선택한 후 **내 사진**을 선택하면 됩니다. 그러면 새로 업로드된 사진이 Ken의 개인 사진으로 표시됩니다. 또한 관리자의 경우 Internet Explorer를 시작하고 다음과 유사한 URL로 이동하여 모든 사용자의 사진을 확인할 수 있습니다.

    https://atl-mail-001.litwareinc.com/ews/Exchange.asmx/s/GetUserPhoto?email=kenmyer@litwareinc.com&size=HR648x648

관리자는 Internet Explorer를 사용하여 사진을 볼 수 있지만 사용자는 Lync 2013에서 자신의 사진을 볼 수 없는 경우 이는 일반적으로 Exchange 웹 서비스 또는 Exchange 자동 검색 서비스에 연결 문제가 있음을 나타냅니다.

또한 이 사진을 Lync 2013에서 사용할 수 있도록 하는 데 추가 구성이 필요 없습니다. 단, 사진을 업로드하고 Set-UserPhoto cmdlet을 실행한 후에 바로 사용할 수 있습니다.

