---
title: Lync Server 2013에서 클라이언트 부트스트랩 정책 구성
TOCTitle: Lync Server 2013에서 클라이언트 부트스트랩 정책 구성
ms:assetid: 45042eca-b845-4207-b12f-b8b7f5d44bdf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425941(v=OCS.15)
ms:contentKeyID: 49303486
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 클라이언트 부트스트랩 정책 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

GPMC(그룹 정책 관리 콘솔) 및 그룹 정책 개체 편집기는 그룹 정책을 관리하는 데 사용하는 도구입니다. Office 그룹 정책 관리 템플릿에는 Lync 2013.admx(ADMX) 및 .adml(ADML) 관리 템플릿이 포함되어 있습니다. 이러한 템플릿에는 도메인의 그룹 정책 개체에 대해 구성하는 레지스트리 기반 설정이 들어 있습니다. ADML 파일은 ADMX 파일에 대한 언어별 보완 파일입니다. 각 ADMX 및 ADML 파일에는 단일 Office 응용 프로그램에 대한 정책 설정이 포함됩니다.

Lync 2013에는 사용자가 서버에 처음 로그인하기 전에 구성하도록 고려해야 하는 몇 가지 클라이언트 부트스트랩 정책이 있습니다. 예를 들어 로그인이 완료될 때까지 클라이언트가 사용할 기본 서버 및 보안 모드를 고려해야 합니다. 그룹 정책을 사용하면 사용자가 로그인하고 서버에서 인밴드 프로비전 설정을 수신하기 전에 사용자의 컴퓨터 레지스트리에 이러한 설정을 구성할 수 있습니다. 다음 표에서는 Lync 2013에서 사용할 수 있는 그룹 정책 설정을 보여줍니다.

### Lync 2013에 대한 그룹 정책 설정

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>그룹 정책 설정</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>서버 지정<br />
(ConfigurationMode)</p></td>
<td><p>Lync 2013에서 로그인 중 사용할 전송 및 서버를 식별할 방법을 지정합니다. 이 설정 내에서 다음을 지정할 수 있습니다.</p>
<ul>
<li><p>ServerAddressExternal: 외부 방화벽 외부에서 연결할 때 클라이언트 및 페더레이션 연락처가 사용하는 서버 이름 또는 IP 주소를 지정합니다.</p></li>
<li><p>ServerAddressInternal: 조직의 방화벽 내에서 클라이언트가 연결할 때 사용되는 서버 이름 또는 IP 주소를 지정합니다.</p></li>
<li><p>전송: TCP(Transmission Control Protocol) 또는 TLS(전송 계층 보안)를 지정합니다.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>지원되는 추가 서버 버전<br />
(ConfiguredServerCheckValues)</p></td>
<td><p>기본적으로 지원되는 서버 버전 외에 Lync Server 2013에서 로그인할 서버 버전 이름 목록을 세미콜론으로 구분하여 지정합니다.</p></td>
</tr>
<tr class="odd">
<td><p>로그인 오류 로그의 자동 업로드 해제(DisableAutomaticSendTracing)</p></td>
<td><p>로그인 오류 로그 분석을 위해 Lync Server에 자동으로 업로드합니다. 로그인이 성공한 경우 로그가 자동으로 업로드되지 않습니다. 이 정책을 구성하지 않으면 다음과 같은 상황이 발생합니다.</p>
<dl>
<dt><span></span></dt>
<dd><p>Lync Online 사용자의 경우: 로그인 오류 로그가 자동으로 업로드됩니다.</p>
</dd>
<dt><span></span></dt>
<dd><p>Lync 온-프레미스 사용자의 경우: 업로드 전에 확인 대화 상자가 사용자에게 표시됩니다.</p>
</dd>
</dl>
<p>이 설정을 해제한 경우 Lync 온-프레미스 및 Lync Online 사용자 모두에 대해 로그인 로그가 Lync Server에 자동으로 업로드됩니다. 이 설정을 사용하도록 지정하면 로그인 로그가 자동으로 업로드되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p>SIP 연결에 대한 HTTP 대체 해제<br />
(DisableHttpConnect)</p></td>
<td><p>TLS 또는 TCP를 사용할 수 없는 경우 Lync Server가 HTTP를 사용하여 서버에 연결을 시도하지 못하도록 방지합니다. 기본적으로 Lync는 먼저 TLS 또는 TCP를 사용하여 서버에 연결을 시도하고 이러한 전송 방법이 모두 실패하면 Lync가 HTTP를 사용하여 연결을 시도합니다. 대체 HTTP 연결 시도를 사용하지 않도록 설정하려면 이 정책을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>로그온 자격 증명 필요<br />
(DisableNTCredentials)</p></td>
<td><p>사용자는 SIP 서버에 로그인할 때 자동으로 Windows 자격 증명을 사용하는 대신 Lync에 대한 로그온 자격 증명을 제공해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p>서버 버전 검사 사용 안 함<br />
(DisableServerCheck)</p></td>
<td><p>이 정책을 1로 설정하면 로그인하기 전에 Lync가 서버 이름 및 버전을 검사하지 않도록 방지합니다. 기본적으로 Lync는 로그인 전에 이러한 검사를 수행합니다.</p></td>
</tr>
<tr class="odd">
<td><p>BITS를 사용하여 주소록 서비스 파일을 다운로드하도록 설정<br />
(EnableBitsForGalDownload)</p></td>
<td><p>Lync에서 BITS(Background Intelligent Transfer Service)를 사용하여 주소록 서비스 파일을 다운로드할 수 있도록 합니다.</p></td>
</tr>
<tr class="even">
<td><p>SIP 보안 모드 구성<br />
(EnableSIPHighSecurityMode)</p></td>
<td><p>Lync에서 인스턴트 메시지를 보다 안전하게 보내고 받을 수 있도록 설정합니다. 이 정책은 Windows .NET 또는 Microsoft Exchange Server 서비스에는 적용되지 않습니다.</p>
<p>이 정책 설정을 구성하지 않으면 Lync에서 아무 전송이나 사용할 수 있습니다. 그러나 TLS를 사용하지 않으며 서버에서 사용자를 인증하는 경우에는 Lync에서 NTLM 또는 Kerberos 인증을 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p>전역 주소록 다운로드 초기 지연<br />
(GalDownloadInitialDelay)</p></td>
<td><p>GAL(전역 주소록) 다운로드가 시작되기 전의 기간을 지정합니다. 기본값은 60분이며, 서버가 0~60분 사이의 임의 기간 동안 GAL 파일 다운로드를 지연시킵니다.</p></td>
</tr>
<tr class="even">
<td><p>사용자가 Microsoft Lync를 실행하지 못하도록 방지<br />
(PreventRun)</p></td>
<td><p>사용자가 Lync를 실행하지 못하도록 합니다. 컴퓨터 구성 및 사용자 구성 모두에서 이 정책 설정을 구성할 수 있지만 컴퓨터 구성의 정책 설정이 우선합니다.</p></td>
</tr>
<tr class="odd">
<td><p>사용자 암호 저장 허용<br />
(SavePassword)</p></td>
<td><p>Lync에서 암호를 저장할 수 있도록 합니다.</p></td>
</tr>
<tr class="even">
<td><p>SIP 압축 모드 구성<br />
(SipCompression)</p></td>
<td><p>SIP 압축을 사용할 경우를 지정합니다. 기본적으로 SIP 압축은 어댑터 속도를 기반으로 설정됩니다. 이 정책을 설정하면 로그인 시간이 늘어날 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p>신뢰할 수 있는 도메인 목록<br />
(TrustModelData)</p></td>
<td><p>고객 SIP 도메인의 접두사와 일치하지 않는 신뢰할 수 있는 도메인을 나열합니다.</p></td>
</tr>
</tbody>
</table>


서버에 구성된 정책은 사용자가 구성한 그룹 정책 설정 또는 클라이언트 옵션보다 우선적으로 적용됩니다. 다음 표에는 설정이 충돌하는 경우의 적용되는 순서가 요약되어 있습니다.

### 그룹 정책 우선 순위

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>우선 순위</th>
<th>설정 위치 또는 방법</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Lync Server 2013 인밴드 프로비전</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\15.0\Lync</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Lync 2013의 Lync - 옵션 대화 상자</p></td>
</tr>
</tbody>
</table>


## Lync 2013 관리 템플릿 파일을 사용하여 그룹 정책 설정을 정의하려면

1.  모든 언어 중립적인 ADMX 파일을 포함하기 위한 루트 수준 폴더를 만듭니다. 예를 들어 도메인 컨트롤러의 다음 위치에 중앙 저장소를 위한 루트 폴더를 만듭니다.
    
    `%systemroot%\sysvol\domain\policies\PolicyDefinitions`
    

    > [!NOTE]
    > 이 절차에서는 도메인에서 여러 컴퓨터를 관리한다고 가정합니다. 이 경우 기본 도메인 컨트롤러의 Sysvol 폴더에 있는 중앙 저장소에 템플릿을 저장합니다. 이렇게 하면 도메인 관리 템플릿에 대한 복제된 중앙 저장소 위치를 제공합니다.



2.  사용할 각 언어에 대한 하위 폴더를 만듭니다. 이러한 하위 폴더는 언어별 ADML 리소스 파일을 포함합니다. 예를 들어 미국 영어(EN-US)에 대한 하위 폴더는 다음 위치에 만듭니다.
    
    `%systemroot%\sysvol\domain\policies\PolicyDefinitions\EN-US`

ADMX 파일에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=75124\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=75124%26clcid=0x412)에서 그룹 정책 ADMX 파일 관리 단계별 가이드를 참조하십시오.

