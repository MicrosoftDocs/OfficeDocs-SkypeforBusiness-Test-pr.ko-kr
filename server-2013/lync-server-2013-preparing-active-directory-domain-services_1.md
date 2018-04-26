---
title: 'Lync Server 2013:  Active Directory 도메인 서비스 준비'
TOCTitle: Active Directory 도메인 서비스 준비
ms:assetid: 7b0d9aa4-f1ab-4578-b22f-b802b6ed1530
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398607(v=OCS.15)
ms:contentKeyID: 49304132
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Active Directory 도메인 서비스 준비

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013에서는 Lync Server 배포 마법사를 사용하여 Active Directory 도메인 서비스를 준비하거나 Lync Server 관리 셸 cmdlet을 직접 사용할 수 있습니다. 또한 이 항목의 뒷 부분에 설명된 대로 도메인 컨트롤러에서 ldifde.exe 명령줄 도구를 직접 사용할 수 있습니다.

Lync Server 배포 마법사는 각 Active Directory 준비 작업을 안내합니다. 배포 마법사에서는 Lync Server 관리 셸 cmdlet을 실행합니다. 이 도구는 단일 도메인 및 단일 포리스트 토폴로지 또는 이와 유사한 토폴로지 환경에 유용합니다.


> [!IMPORTANT]
> Lync Server은 도메인 컨트롤러가 일부 운영 체제의 32비트 버전을 실행하는 도메인 또는 포리스트에 배포할 수 있습니다(자세한 내용은 <A href="lync-server-2013-active-directory-infrastructure-requirements.md">Lync Server 2013에 대한 Active Directory 인프라 요구 사항</A> 참조). 하지만 배포 마법사 및 지원 파일이 64비트 전용이므로 이러한 환경에서는 Lync Server 배포 마법사를 사용해서 스키마, 포리스트 및 도메인 준비를 실행할 수 없습니다. 대신 ldifde.exe 및 연결된 .ldf 파일을 32비트 도메인 컨트롤러에서 사용하여 스키마, 포리스트 및 도메인을 준비할 수 있습니다. 이 항목의 뒷 부분에 있는 "Cmdlet 및 Ldifde.exe 사용" 섹션을 참조하십시오.



Lync Server 관리 셸 cmdlet을 사용하여 원격으로 작업을 실행하거나 보다 복잡한 환경에 대한 작업을 실행할 수 있습니다.

## Active Directory 준비를 위한 필수 구성 요소

Active Directory 준비 단계는 Windows Server 2012, Windows Server 2012 R2 또는 Windows Server 2008 R2 SP1(64비트)을 실행하는 컴퓨터에서 실행해야 합니다. Active Directory 준비를 위해서는 Lync Server 관리 셸 및 OCSCore가 필요합니다.

Active Directory 준비 작업을 실행하려면 다음 구성 요소가 필요합니다.

  - Lync Server 핵심 구성 요소(OCScore.msi)
    

    > [!NOTE]
    > Lync Server 관리 셸을 사용하여 Active Directory를 준비하려면 먼저 Lync Server 배포 마법사를 실행하여 핵심 구성 요소를 설치해야 합니다.



  - Microsoft .NET Framework 4.5
    

    > [!NOTE]
    > Windows Server 2012 및 Windows Server 2012 R2의 경우 서버 관리자를 사용해서 .NET Framework 4.5를 설치하고 활성화합니다. 자세한 내용은 Microsoft .NET Framework 4.5( <A href="lync-server-2013-additional-software-requirements.md">Lync Server 2013에 대한 추가 소프트웨어 요구 사항</A>)를 참고하세요. Windows Server&nbsp;2008&nbsp;R2의 경우 Microsoft 웹 사이트에서 <A href="http://www.microsoft.com/en-us/download/details.aspx?id=30653">.Net Framework 4.5</A>를 다운로드하고 설치합니다.



  - RSAT(원격 서버 관리 도구)
    

    > [!NOTE]
    > 도메인 컨트롤러 대신 구성원 서버에서 Active Directory 준비 단계를 실행하려면 몇 가지 RSAT 도구가 필요합니다. 서버 관리자의 AD DS 및 AD LDS 도구 노드에서 Windows PowerShell용 Active Directory 모듈과 AD DS 스냅인 및 명령줄 도구를 설치합니다.



  - Microsoft Visual C++ 11 재배포 가능 패키지
    

    > [!NOTE]
    > 설치 시 이 필수 구성 요소를 설치할지 묻는 메시지가 나타납니다(컴퓨터에 이미 설치되지 않은 경우). 이 패키지는 자동으로 제공되므로 별도로 구입할 필요가 없습니다.



  - Windows PowerShell 3.0(64비트)
    
    Windows Server 2012 및 Windows Server 2012 R2의 경우 Windows PowerShell 3.0은 Lync Server 2013 설치에 포함되어 있습니다. Windows Server 2008 R2의 경우에는 Windows PowerShell 3.0 설치 또는 업그레이드가 필요합니다. 자세한 내용은 [Lync Server 2013용 Windows PowerShell 3.0 설치](lync-server-2013-installing-windows-powershell-3-0.md)를 참고하세요.

## 관리자 권한 및 역할

다음 표에서는 Active Directory 준비 작업에 필요한 관리자 권한 및 역할을 보여 줍니다.

### Active Directory 준비에 필요한 사용자 권한

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>절차</th>
<th>권한 또는 역할</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>스키마 준비</p></td>
<td><p>Schema Admins 그룹의 구성원(포리스트 루트 도메인) 및 관리자 권한(스키마 마스터)</p></td>
</tr>
<tr class="even">
<td><p>포리스트 준비</p></td>
<td><p>Enterprise Admins 그룹의 구성원(포리스트)</p></td>
</tr>
<tr class="odd">
<td><p>도메인 준비</p></td>
<td><p>Enterprise Admins 또는 Domain Admins 그룹의 구성원(지정된 도메인)</p></td>
</tr>
</tbody>
</table>


## Active Directory 준비 Cmdlet

다음 표에는 AD DS를 준비하는 데 사용되는 Lync Server 관리 셸 cmdlet과 Microsoft Office Communications Server 2007 R2에서 AD DS를 준비하는 데 사용되는 LcsCmd 명령이 비교되어 있습니다.

### cmdlet과 LcsCmd 비교

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>LcsCmd</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Install-CsAdServerSchema</p></td>
<td><p>Lcscmd /forest /action:SchemaPrep /SchemaType:Server</p></td>
</tr>
<tr class="even">
<td><p>Get-CsAdServerSchema</p></td>
<td><p>Lcscmd /forest /action:CheckSchemaPrepState</p></td>
</tr>
<tr class="odd">
<td><p>Enable-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:ForestPrep</p></td>
</tr>
<tr class="even">
<td><p>Disable-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:ForestUnprep</p></td>
</tr>
<tr class="odd">
<td><p>Get-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:CheckForestPrepState</p></td>
</tr>
<tr class="even">
<td><p>Enable-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action:DomainPrep</p></td>
</tr>
<tr class="odd">
<td><p>Disable-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action: DomainUnprep</p></td>
</tr>
<tr class="even">
<td><p>Get-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action:CheckDomainPrepState</p></td>
</tr>
</tbody>
</table>


## 잠긴 Active Directory 요구 사항

조직에서 권한 상속이 비활성화되어 있거나 인증된 사용자 권한을 비활성화해야 하는 경우 도메인 준비 작업 중에 추가 단계를 수행해야 합니다. 자세한 내용은 [Lync Server 2013에서 잠긴 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md)를 참조하십시오.

## 사용자 지정 컨테이너 권한

조직에서 세 가지 기본 제공 컨테이너(사용자, 컴퓨터 및 도메인 컨트롤러) 대신 사용자 지정 컨테이너를 사용하는 경우 Authenticated Users 그룹에 대해 사용자 지정 컨테이너에 대한 읽기 권한을 부여해야 합니다. 도메인 준비를 위해서는 컨테이너에 대한 읽기 액세스 권한이 필요합니다. 자세한 내용은 [Lync Server 2013에 대한 도메인 준비](lync-server-2013-preparing-domains.md)을 참조하십시오.

## Cmdlet 및 Ldifde.exe 사용

Lync Server 배포 마법사의 **스키마 준비** 단계와 **Install-CsAdServerSchema** cmdlet은 64비트 운영 체제를 실행하는 도메인 컨트롤러에서 Active Directory 스키마를 확장합니다. 32비트 운영 체제를 실행하는 도메인 컨트롤러에서 Active Directory 스키마를 확장해야 하는 경우 구성원 서버에서 원격으로 **Install-CsAdServerSchema** cmdlet을 실행할 수 있습니다(권장 방법). 그러나 도메인 컨트롤러에서 스키마 준비를 직접 실행해야 하는 경우에는 Ldifde.exe 도구를 사용하여 스키마 파일을 가져올 수 있습니다. Ldifde.exe 도구는 대부분의 Windows 운영 체제 버전에 포함되어 있습니다.

Ldifde.exe를 사용하여 스키마 파일을 가져오는 경우 이전 버전에서 마이그레이션 중인지 또는 새로 설치하는 중인지에 관계없이 네 개 파일을 모두 가져와야 합니다. 가져와야 하는 파일의 순서는 다음과 같습니다.

1.  ExternalSchema.ldf

2.  ServerSchema.ldf

3.  BackCompatSchema.ldf

4.  VersionSchema.ldf


> [!NOTE]
> 이 네 개의 .ldf 파일은 설치 미디어 또는 다운로드의 \Support\Schema 디렉터리에 있습니다.



Ldifde.exe를 사용하여 스키마 마스터인 도메인 컨트롤러에서 스키마 파일 네 개를 가져오려면 다음 형식을 사용합니다.

    ldifde -i -v -k -s <DCName> -f <Schema filename> -c DC=X <defaultNamingContext> -j logFilePath -b <administrator account> <logon domain> <password>

예를 들면 다음과 같습니다.

    ldifde -i -v -k -s DC1 -f ServerSchema.ldf -c DC=X "DC=contoso,DC=com" -j C:\BatchImportLogFile -b Administrator contoso password


> [!NOTE]
> b 매개 변수는 다른 사용자로 로그인한 경우에만 사용합니다. 필요한 사용자 권한에 대한 자세한 내용은 이 항목의 앞부분에 있는 "관리자 권한 및 역할" 섹션을 참조하십시오.



Ldifde.exe를 사용하여 스키마 마스터가 아닌 도메인 컨트롤러에서 스키마 파일 네 개를 가져오려면 다음 형식을 사용합니다.

    ldifde -i -v -k -s <SchemaMasterFQDN> -f <Schema filename> -c DC=X <rootDomainNamingContext> -j logFilePath -b <administrator account> <domain> <password>

Ldifde를 사용하는 방법에 대한 자세한 내용은 Microsoft 기술 자료 문서 237677, "LDIFDE를 사용하여 Active Directory로 디렉터리 개체 가져오기 및 내보내기"( [http://go.microsoft.com/fwlink/?linkid=132204\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=132204%26clcid=0x412))를 참조하십시오.

## 이 섹션의 내용

  - [Lync Server 2013에서 Active Directory 스키마 준비](lync-server-2013-preparing-the-active-directory-schema.md)

  - [Lync Server 2013에 대한 포리스트 준비](lync-server-2013-preparing-the-forest.md)

  - [Lync Server 2013에 대한 도메인 준비](lync-server-2013-preparing-domains.md)

