---
title: Lync Windows 스토어 앱 배포
TOCTitle: Lync Windows 스토어 앱 배포
ms:assetid: 9e00aaf4-15f9-4356-9ed7-5a58a2bfa043
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ822971(v=OCS.15)
ms:contentKeyID: 52056903
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Windows 스토어 앱 배포

 

_**마지막으로 수정된 항목:** 2013-12-03_

사용자에게 Lync Windows 스토어 앱을 제공하기 전에 해당 배포가 [Lync Server 2013용 Lync Windows 스토어 앱 요구 사항](lync-server-2013-lync-windows-store-app-requirements.md)을 충족하는지 확인합니다. Lync Windows 스토어 앱을 지원하도록 Lync Server 2013을 구성하는 방법에 대한 자세한 내용은 NextHop 블로그 문서, "Lync Server 자동 검색 및 Lync Windows 스토어 앱(영문)"([http://go.microsoft.com/fwlink/?LinkId=271966](http://go.microsoft.com/fwlink/?linkid=271966))을 참고하세요. 서버 환경을 올바르게 구성한 후에는 Windows 스토어에서 "Lync"를 검색하여 Lync 앱을 다운로드할 것을 사용자에게 알려 줄 수 있습니다.

## Lync Windows 스토어 앱에 다단계 인증을 사용하도록 설정

Lync Server 2013용 누적 업데이트(2013년 6월)는 Lync Windows 스토어 앱 클라이언트에 대한 다단계 인증을 추가로 지원합니다. 외부 사용자가 Lync 모임에 로그인할 때 인증을 위해 사용자 이름과 암호 외에 스마트 카드나 PIN 같은 추가 인증 방법을 요구할 수 있습니다. 다단계 인증을 사용하려면 AD FS(Active Directory Federation Service) 페더레이션 서버를 배포하고 Lync Server 2013에서 수동 인증을 사용하도록 설정합니다. AD FS가 구성된 후에는 Lync 모임에 참가하려는 외부 사용자에게 사용자 이름 및 암호 질문과 함께 관리자가 구성한 추가 인증 방법이 포함된 AD FS 다단계 인증 웹 페이지가 표시됩니다.


> [!IMPORTANT]
> Lync Windows 스토어 앱에서 다단계 인증을 사용하도록 AD FS를 구성하려는 경우 고려해야 하는 중요 사항은 다음과 같습니다 
> <UL>
> <LI>
> <P>최소 Lync Server 2013용 누적 업데이트(2013년 6월)가 설치된 Lync Server 2013이 필요합니다. Lync 2013 데스크톱 클라이언트의 경우에는 Lync Server 2013용 누적 업데이트(2013년 6월)가 필요하지 않고 Lync 2013 클라이언트로 인증할 수 있기 때문에 수동 인증이 작동하고 있다고 표시될 수 있습니다. 그러나 Lync Windows 스토어 앱 클라이언트의 인증 절차가 완료되지 않고 알림이나 오류 메시지가 표시되지 않습니다.</P>
> <LI>
> <P>제공되는 유일한 인증 유형이 수동 인증이 되도록 서버를 구성해야 합니다.</P>
> <LI>
> <P>하드웨어 부하 분산 장치를 사용하는 경우 Lync Windows 스토어 앱 클라이언트의 모든 요청이 동일한 프런트 엔드 서버에서 처리되도록 부하 분산 장치에 쿠키 지속성을 사용하도록 설정합니다.</P>
> <LI>
> <P>Lync Server와 AD FS 서버 간에 신뢰 당사자 트러스트를 설정하는 경우 최대 Lync 모임 시간 동안 지속될 만큼 충분히 긴 토큰 수명을 할당합니다. 일반적으로 240분의 토큰 수명이면 충분합니다.</P></LI></UL>



**다단계 인증을 구성하려면**

1.  AD FS 페더레이션 서버 역할을 설치합니다. 자세한 내용은 Active Directory Federation Services 2.0 배포 가이드(<http://go.microsoft.com/fwlink/p/?linkid=267511>)를 참고하세요.

2.  AD FS용 인증서를 만듭니다. 자세한 내용은 Single Sign-On에 사용할 AD FS 계획 및 배포 항목([http://go.microsoft.com/fwlink/p/?LinkId=285376](http://go.microsoft.com/fwlink/p/?linkid=285376))에서 "페더레이션 서버 인증서" 섹션을 참고하세요.

3.  Windows PowerShell 명령줄 인터페이스에서 다음 명령을 실행합니다.
    
        add-pssnapin Microsoft.Adfs.powershell

4.  다음 명령을 실행하여 파트너 관계를 설정합니다.
    
        Add-ADFSRelyingPartyTrust -Name ContosoApp -MetadataURL https://lyncpool.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml

5.  다음과 같은 신뢰 당사자 규칙을 설정합니다.
    
        $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.contoso.com/authorization/claims/permit", Value = "true");'$IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.contoso.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
    
        Set-ADFSRelyingPartyTrust -TargetName ContosoApp -IssuanceAuthorizationRules $IssuanceAuthorizationRules -IssuanceTransformRules $IssuanceTransformRules
    
        Set-CsWebServiceConfiguration -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml

## 로그인을 방해하는 알려진 문제점

## Lync Windows 스토어 앱 실행 장치에서 시간 및 날짜가 정확하게 설정되지 않음

장치의 시간 설정은 서버의 시간 설정과 동기화되어야 합니다. 이 작업은 Microsoft Surface 장치 또는 Windows RT를 실행하는 다른 장치 등 도메인에 가입되어 있지 않은 장치인 경우 특히 중요합니다.시간 서버로부터 장치의 시간을 자동으로 설정하려면 장치의 관리자 권한 명령 프롬프트에서 다음 명령을 실행합니다.

    w32tm /resync

## Lync Windows 스토어 앱에서 Lync 서버 또는 서비스에 액세스할 수 없음

Windows 8에 물리적 장치로 등록되지 않은 4G LTE USB 모뎀 등의 네트워크 어댑터를 통해 Lync Windows 스토어 앱에서 Lync 서버 또는 서비스에 액세스할 수 없을 수 있습니다. 데스크톱 앱 및 브라우저에서 다른 서버 및 웹 사이트에 액세스할 수 있는 경우에도 Lync Windows 스토어 앱에서 이 문제가 발생할 수 있습니다.

## Lync Windows 스토어 앱이 Lync Server 2010 및 Office Communications Server 2007 R2 에지 서버를 사용하여 로그인할 수 없음

토폴로지가 Lync Server 2010 및 Office Communications Server 2007 R2 에지 서버로 구성된 경우 Lync Server 2010: 2013년 7월 누적 업데이트에서 제공하는 업데이트된 버전의 토폴로지 작성기를 실행해야 합니다. 이전 버전의 토폴로지 작성기는 Office Communications Server 2007 에지 서버에 필요한 매핑을 만들지 않기 때문에 Lync Windows 스토어 앱 클라이언트가 로그인할 수 없습니다. 다음과 같은 단계를 따라야 합니다.

1.  Lync Server 2010: 2013년 7월 누적 업데이트를 Lync Server 2010 풀 및 Lync Server 2010 디렉터에 설치합니다.

2.  다음을 실행하여 외부 SIP 진입점이 에지 서버 주소임을 나타내도록 Lync 자동 검색 구성을 업데이트합니다.
    
    1.  Lync Server 관리 셸을 엽니다.
    
    2.  다음 명령을 실행합니다.
        
            Set-CsAutodiscoverConfiguration -ExternalSipClientAccessFqdn <FQDN of server used for external client access> -ExternalSipClientAccessPort 443

## Lync Windows 스토어 앱이 인증서 이름 유효성 검사에 실패로 인해 로그인할 수 없음

최신 버전의 Lync Windows 스토어 앱을 실행하지 않는 Office 365 사용자의 경우 로그인 문제가 발생할 수 있습니다. 이 문제는 일반적으로 여러 도메인을 사용하는 경우에 발생합니다(예: SIP URI가 **userA@domainZ.com**이지만 에지 서버가 **sip.domainX.com**인 경우). 문제를 해결하려면 사용자가 최신 버전의 Lync Windows 스토어 앱 및 Windows 8.1을 설치해야 합니다.

## Lync Windows 스토어 앱 로그를 사용하여 문제 해결

장치에서 생성된 로그를 사용하여 문제를 해결할 수 있습니다. 로그는 다음 폴더에 저장됩니다.

%LocalAppData%\\Packages\\Microsoft.LyncMX\_8wekyb3d8bbwe\\LocalState\\Tracing

사용자로부터 로그를 받기 전에 로깅이 설정되어 있는지 확인한 다음 사용자에게 메모리에 저장되는 모든 정보가 하드 드라이브의 파일에도 저장되도록 로그를 저장해 달라고 요청합니다.

**로깅을 설정하려면**

1.  장치에서 Lync Windows 스토어 앱을 엽니다.

2.  화면 오른쪽에서 손가락을 살짝 밉니다. 마우스를 사용하는 경우에는 화면의 오른쪽 위 모서리를 가리키고 마우스 포인터를 화면 아래로 이동합니다.

3.  **설정**, **옵션**을 선택하고 **진단 로그**를 **설정**으로 설정합니다.

4.  이전에 **진단 로그**를 해제한 경우 Lync를 다시 시작해야 합니다. Lync를 다시 시작하려면 다음 중 하나를 실행합니다.
    
      - 장치를 다시 시작합니다.
    
      - Lync 작업을 종료하고 앱을 다시 시작합니다. 작업을 종료하려면 Windows 작업 관리자를 열고 **Lync**를 선택한 다음 **작업 끝내기**를 탭합니다. Lync가 목록에 나타나지 않으면 **자세히**를 탭하고 **백그라운드 프로세스** 아래에서 Lync를 찾습니다.

**로그를 저장하려면**

1.  장치에서 Lync Windows 스토어 앱을 엽니다.

2.  로그인합니다.

3.  화면 오른쪽에서 손가락을 살짝 밉니다. 마우스를 사용하는 경우에는 화면의 오른쪽 위 모서리를 가리키고 마우스 포인터를 화면 아래로 이동합니다.

4.  **설정**, **정보**, **로그 저장**을 차례로 선택합니다.

