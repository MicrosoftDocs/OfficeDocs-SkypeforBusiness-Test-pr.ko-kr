---
title: Request-CsCertificate
TOCTitle: Request-CsCertificate
ms:assetid: 24e8ba6f-6023-4c03-a594-5b40784fd16a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425723(v=OCS.15)
ms:contentKeyID: 49303074
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Request-CsCertificate

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 실행 서버 및 서버 역할에 사용할 인증서를 요청하는 방법을 제공합니다. 또한 기존 인증서 요청의 상태를 확인하고, 필요한 경우 이러한 요청 중 한 개나 모두를 취소하는 방법을 제공합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Request-CsCertificate -New <SwitchParameter> -Type <CertType[]> [-AllSipDomain <SwitchParameter>] [-CA <String>] [-CaAccount <String>] [-CaPassword <String>] [-City <String>] [-ClientEKU <$true | $false>] [-ComputerFqdn <Fqdn>] [-Country <String>] [-DomainName <String>] [-FriendlyName <String>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-KeyAlg <RSA | ECDH_P256 | ECDH_P384 | ECDH_P521>] [-KeySize <Int32>] [-Organization <String>] [-OU <String>] [-Output <String>] [-PrivateKeyExportable <$true | $false>] [-State <String>] [-Template <String>] <COMMON PARAMETERS>

    Request-CsCertificate -List <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    Request-CsCertificate -Retrieve <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    Request-CsCertificate -Clear <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 CA atl-ca-001.litwareinc.com\\myca에 연결하여 새 WebServicesExternal 인증서를 요청하는 새 인증서 요청을 만듭니다.

    Request-CsCertificate -New -Type WebServicesExternal -CA "atl-ca-001.litwareinc.com\myca"

## 예제 2

예제 2에서는 **Request-CsCertificate** cmdlet을 사용하여 수행된 보류 중인 모든 인증서 요청을 표시합니다.

    Request-CsCertificate -List

## 예제 3

예제 3에서는 Output 매개 변수를 사용하여 오프라인 인증서 요청을 만듭니다.

    Request-CsCertificate -New -Type WebServicesExternal -Output C:\Certificates\WebServicesExternal.cer

## 예제 4

예제 4는 Request-CsCertificate cmdlet 사용 방법에 대한 보다 구체적이고 현실적인 예입니다. 이 예제에서는 Lync Server Standard Edition에서 사용할 인증서를 요청합니다.

    Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -ComputerFqdn "atl-cs-001.litwareinc.com" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Standard Edition Certficate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-cs-001.litwareinc.com,atl-ext.litwareinc.com"

## 예제 5

예제 5에서는 Lync Server Enterprise Edition에서 사용할 풀 인증서를 요청합니다.

    Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -ComputerFqdn "atl-cs-001.litwareinc.com" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Enterprise Edition Pool Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "pool1.litwareinc.com,pool1int.litwareinc.com,pool1ext.litwareinc.com"

## 예제 6

예제 6에서는 내부 에지 서버에 대한 인증서를 요청하는 방법을 보여 줍니다.

    Request-CsCertificate -New -Type Internal -ComputerFqdn "atl-edge-001" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Internal Edge Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-edge-001.litwareinc.com, ap.litwareinc.com"

## 예제 7

예제 7은 예제 6에 표시된 명령의 변형입니다. 그러나 이 경우에는 외부 에지 서버에 대해 요청합니다.

    Request-CsCertificate -New -Type AccessEdgeExternal,DataEdgeExternal,AudioVideoAuthentication -ComputerFqdn "atl-edge-001" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "External Edge Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-edge-001.litwareinc.com,ap.litwareinc.com,dp.litwareinc.com,atl-edge-001"

## 자세한 정보

Lync Server에서는 서버 및 서버 역할의 ID를 확인하는 방법으로 인증서를 사용합니다. 예를 들어 에지 서버는 인증서를 사용하여 현재 통신 중인 컴퓨터가 실제 프런트 엔드 서버인지 확인하며, 그 반대의 경우도 마찬가지입니다. Lync Server를 완전히 구현하려면 해당 인증서를 해당 서버 역할에 할당해야 합니다.

Lync Server에서 사용할 인증서를 요청하는 한 가지 방법은 **Request-CsCertificate** cmdlet을 호출하는 것입니다. Lync Server에서 사용할 인증서를 요청하기 위해 다른 표준 Windows 도구를 사용할 수도 있지만 **Request-CsCertificate** cmdlet을 사용할 경우 cmdlet이 CA(인증 기관)에 연결하기 전에 토폴로지를 분석한다는 이점이 있습니다. 이 분석을 기준으로 **Request-CsCertificate** cmdlet은 적절한 주체 이름 및 주체 대체 이름 필드가 포함된 인증서를 자동으로 요청합니다.

또한 **Request-CsCertificate** cmdlet은 특별히 Lync Server에서 사용할 인증서를 요청하도록 설계되었습니다. 이 cmdlet은 모든 용도에 사용되는 인증서 관리 도구가 아닙니다.

새 인증서 요청 외에도 이 cmdlet을 사용하여 보류 중인 인증서 요청을 검토할 수 있습니다. 단, **Request-CsCertificate** cmdlet을 사용하여 요청이 수행된 경우에만 해당합니다. **Request-CsCertificate** cmdlet을 사용하여 요청이 수행된 경우 이 cmdlet을 사용하여 보류 중인 인증서 요청을 삭제할 수도 있습니다.

취소한 요청이 있는 경우 인증서 요청을 검색하려고 하면 오류 메시지가 나타날 수 있습니다. **Request-CsCertificate** cmdlet은 현재 Issued, Denied 및 Pending 유형의 요청만 지원합니다. 취소한 인증서로 인해 문제가 발생한 경우 다음과 유사한 명령을 사용하여 취소한 요청을 삭제합니다(여기서 224는 취소한 인증서 요청의 RequestID).

Request-CsCertificate –Clear –RequestID 224

그런 다음에는 인증서 요청을 검색할 수 있어야 합니다.

이 cmdlet을 실행할 수 있는 사용자: **Request-CsCertificate** cmdlet을 로컬로 실행하려면 로컬 관리자이고 지정된 인증 기관에 대한 권한이 있어야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Request-CsCertificate"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Clear</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 <strong>Request-CsCertificate</strong> cmdlet을 사용하여 수행된 보류 중인 인증서 요청을 삭제합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>List</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 <strong>Request-CsCertificate</strong> cmdlet을 사용하여 수행된 보류 중인 인증서 요청을 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>New</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 새 인증서를 요청하도록 지정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Retrieve</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 <strong>Request-CsCertificate</strong> cmdlet을 사용하여 수행된 보류 중인 인증서 요청을 검색하며, 작업을 완료하고 요청한 인증서를 가져오려고 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>요청되는 인증서 유형입니다. 인증서 유형은 다음을 포함하지만 이러한 유형으로만 제한되지는 않습니다.</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>iPhoneAPNService</p>
<p>iPadAPNService</p>
<p>MPNService</p>
<p>PICWebService(Microsoft Lync Online 2010에만 해당)</p>
<p>ProvisionService(Microsoft Lync Online 2010에만 해당)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>예를 들어 -Type Default 구문은 새 Default 인증서를 요청합니다.</p>
<p>다음과 같이 인증서 유형을 쉼표로 구분하여 단일 명령에 여러 유형을 지정할 수 있습니다.</p>
<p>-Type Internal,External,Default</p></td>
</tr>
<tr class="even">
<td><p><em>AllSipDomain</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 모든 SIP 도메인이 인증서의 주체 대체 이름 필드에 자동으로 추가됩니다. 이 매개 변수가 없으면 기본적으로 주 SIP 도메인만 추가됩니다. 하지만 DomainName 매개 변수를 사용하여 추가 도메인을 지정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CA</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>CA를 가리키는 FQDN(정규화된 도메인 이름)입니다(예: -CA &quot;atl-ca-001.litwareinc.com\myca&quot;). 알려진 CA 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음을 입력하고 Enter 키를 누릅니다.</p>
<p>certutil</p>
<p>Certutil에서 반환된 Config 속성은 CA의 위치를 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CaAccount</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 인증서를 요청하는 사용자의 계정 이름으로, 도메인_이름\사용자_이름 형식을 사용합니다(예: -CaAccount &quot;litwareinc\kenmyer&quot;). 이 매개 변수를 지정하지 않으면 <strong>Request-CsCertificate</strong> cmdlet은 새 인증서를 요청할 때 로그온한 사용자의 자격 증명을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CaPassword</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 인증서를 요청하는 사용자(CaAccount 매개 변수를 사용하여 지정됨)의 암호입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>City</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서가 배포될 구/군/시입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientEKU</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>클라이언트 인증에 인증서를 사용하려는 경우 이 매개 변수를 True로 설정합니다. 사용자가 AOL 계정을 가진 사람과 메신저 대화를 교환할 수 있도록 하려면 이 유형의 인증이 필요합니다. 매개 변수 이름의 EKU 부분은 확장 키 사용을 수용하기에 너무 짧습니다. 확장 키 사용 필드에 인증서의 유효한 사용이 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ComputerFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>인증서를 요청할 컴퓨터의 FQDN입니다. 이 매개 변수가 있으면 <strong>Request-CsCertificate</strong> cmdlet이 지정한 컴퓨터를 찾기 위해 강제로 중앙 관리 저장소에 연결합니다. 인증서를 요청할 때는 풀 인증서를 요청하는 경우에도 항상 컴퓨터 이름을 사용해야 합니다. <strong>Request-CsCertificate</strong> cmdlet은 이 cmdlet을 사용하여 가져온 인증서의 Subject Name에 풀 이름을 자동으로 추가합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Country</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서를 배포할 국가/지역입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서의 주체 대체 이름 필드에 추가해야 하는 정규화된 도메인 이름의 쉼표로 구분된 목록입니다. 예를 들면 다음과 같습니다.</p>
<p>-DomainName &quot;atl-cs-001.litwareinc.com, atl-cs-002.litwareinc.com,atl-cs-003.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>FriendlyName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서를 쉽게 식별할 수 있도록 하는 사용자 할당 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN입니다. 사용자 도메인의 계정으로 컴퓨터에서 <strong>Request-CsCertificate</strong> cmdlet을 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장된 도메인 컨트롤러의 FQDN입니다. 전역 설정이 Active Directory 도메인 서비스의 시스템 컨테이너에 저장된 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장되어 있는 경우 모든 도메인 컨트롤러를 사용할 수 있으며 이 매개 변수를 생략해도 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>KeyAlg</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.X509Certificates.KeyAlgorithmIdentifier</p></td>
<td><p>새 인증서의 공개 키와 개인 키를 생성할 때 사용할 암호화 알고리즘 유형을 나타냅니다. 유효한 키 알고리즘은 다음과 같습니다.</p>
<p>RSA</p>
<p>ECDH_P256</p>
<p>ECDH_P384</p>
<p>ECDH_P521</p></td>
</tr>
<tr class="odd">
<td><p><em>KeySize</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>인증서에서 사용하는 개인 키의 크기(비트)를 나타냅니다. 키 크기가 클수록 안전하지만 해독하는 데 처리 오버헤드가 많이 발생합니다.</p>
<p>유효한 키 크기는 1024, 2048 및 4096입니다(예: -KeySize 2048).</p></td>
</tr>
<tr class="even">
<td><p><em>Organization</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 인증서를 요청하는 조직의 이름입니다(예: -Organization &quot;Litwareinc&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 인증서가 할당될 컴퓨터의 Active Directory 조직 구성 단위입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Output</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서 파일의 경로입니다. 오프라인 인증서 요청을 만들려면 Output 매개 변수를 사용하여 인증서 요청에 대한 파일 경로를 지정합니다(예: -Output C:\Certificates\NewCertificate.pfx). 그러면 처리를 위해 인증 기관에 전자 메일로 보낼 수 있는 인증서 요청 파일이 생성됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrivateKeyExportable</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>인증서의 개인 키를 내보낼 수 있도록 설정하려면 이 매개 변수를 True로 설정합니다. 개인 키를 내보낼 수 있는 경우 여러 컴퓨터에 인증서를 복사하여 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet을 실행할 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다(예: -Report &quot;C:\Logs\Certificates.html&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>RequestId</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>인증서 요청에 연결된 ID 번호입니다. RequestID 매개 변수를 통해 개별 인증서를 표시, 검색 또는 지울 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>State</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서가 배포될 시/도(미국의 주)입니다(예: -State WA).</p></td>
</tr>
<tr class="odd">
<td><p><em>Template</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>새 인증서를 생성할 때 사용할 인증서 템플릿을 나타냅니다(예: -Template &quot;WebServer&quot;). 요청한 템플릿이 CA에 설치되어 있어야 합니다. 입력한 값은 템플릿 표시 이름이 아니라 템플릿 이름이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Request-CsCertificate** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Request-CsCertificate** cmdlet은 Microsoft.Rtc.Management.Deployment.CertificateReference 개체의 인스턴스를 관리합니다.

## 참고 항목

#### 기타 리소스

[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)

