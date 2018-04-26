---
title: 'Lync Server 2013: 도메인 준비 실행'
TOCTitle: 도메인 준비 실행
ms:assetid: 95dab800-1f2c-4506-b36c-99986643b149
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398761(v=OCS.15)
ms:contentKeyID: 49304440
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 도메인 준비 실행

 

_**마지막으로 수정된 항목:** 2013-04-16_

설치 프로그램 또는 Lync Server 관리 셸 cmdlet을 사용하여 도메인을 준비할 수 있습니다. 도메인을 준비하는 cmdlet은 **Enable-CsAdDomain**입니다.

도메인 준비는 Lync Server 2013에 대해 Active Directory 도메인 서비스를 준비하는 마지막 단계입니다.

## 설치 프로그램을 사용하여 도메인을 준비하려면

1.  도메인의 서버에 Domain Admins 그룹 구성원으로 로그온합니다.

2.  Lync Server 2013 설치 폴더 또는 미디어에서 Setup.exe를 실행하여 Lync Server 배포 마법사를 시작합니다.

3.  **Active Directory 준비** 를 클릭한 다음 배포 상태가 확인될 때까지 기다립니다.

4.  **5단계: 현재 도메인 준비** 에서 **실행** 을 클릭합니다.

5.  **도메인 준비** 페이지에서 **다음** 을 클릭합니다.

6.  **명령 실행** 페이지에서 **작업 상태: 완료됨** 을 찾은 다음 **로그 보기** 를 클릭합니다.

7.  **동작** 열 아래에 있는 **도메인 준비** 를 확장하고 각 작업 끝에 있는 **\<성공\>** 실행 결과를 찾아서 도메인 준비가 성공적으로 완료되었는지 확인한 다음 로그를 닫고 **마침** 을 클릭합니다.

8.  Active Directory 복제가 포리스트 루트 도메인 컨트롤러의 Active Directory 사이트 및 서비스 스냅인에 나열된 모든 도메인 컨트롤러로 복제를 완료하거나 적용할 때까지 기다립니다.

## cmdlet을 사용하여 도메인을 준비하려면

1.  도메인의 서버에 Domain Admins 그룹 구성원으로 로그온합니다.

2.  Lync Server 핵심 구성 요소를 다음과 같이 설치합니다.
    
    1.  Lync Server 2013 설치 폴더 또는 미디어에서 Setup.exe를 실행하여 Lync Server 배포 마법사를 시작합니다.
    
    2.  Microsoft Visual C++ 재배포 가능 파일을 설치하라는 메시지가 표시되면 **예** 를 클릭합니다.
    
    3.  Lync Server 2013 설치 대화 상자에 Lync Server 파일을 설치할 위치를 지정하라는 메시지가 표시됩니다. 기본 위치를 선택하거나 **찾아보기** 를 클릭하여 원하는 위치를 선택한 후에 **설치** 를 클릭합니다.
    
    4.  사용권 계약 페이지에서 **동의함** 을 선택한 다음 **확인** 을 클릭합니다. Lync Server 2013 핵심 구성 요소가 설치됩니다.

3.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

4.  다음을 실행합니다.
    
        Enable-CsAdDomain [-Domain <DomainFQDN>] 
    
    예를 들면 다음과 같습니다.
    
        Enable-CsAdDomain -Domain domain1.contoso.net 
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.

5.  다음을 실행하여 도메인 준비가 성공적으로 완료되었는지 확인합니다.
    
        Get-CsAdDomain [-Domain <Domain FQDN>] [-DomainController <Domain controller FQDN>] [-GlobalCatalog <Global catalog server FQDN>] [-GlobalSettingsDomainController <Domain controller FQDN where global settings are stored>] 
    
    예를 들면 다음과 같습니다.
    
        Get-CsAdDomain -Domain domain1.contoso.net -GlobalSettingsDomainController dc01.domain1.contoso.com
    

    > [!NOTE]
    > GlobalSettingsDomainController 매개 변수를 통해 전역 설정이 저장되어 있는 위치를 나타낼 수 있습니다. 설정이 시스템 컨테이너에 저장되어 있는 경우(전역 설정이 구성 컨테이너로 마이그레이션되지 않은 업그레이드 배포에서 일반적임) Active Directory 포리스트의 루트에서 도메인 컨트롤러를 정의합니다. 전역 설정이 구성 컨테이너에 있는 경우(설정이 구성 컨테이너로 마이그레이션된 업그레이드 배포 또는 새 배포에서 일반적임) 포리스트에서 도메인 컨트롤러를 정의합니다. 이 매개 변수를 지정하지 않는 경우 cmdlet은 설정이 구성 컨테이너에 저장되는 것으로 가정하고 AD DS의 도메인 컨트롤러를 참조합니다.

    
    **Domain** 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.
    
    이 cmdlet은 도메인 준비가 성공적이면 **LC\_DOMAINSETTINGS\_STATE\_READY** 값을 반환합니다.

## 참고 항목

#### 작업

[Lync Server 2013에 대해 cmdlet을 사용하여 도메인 준비 되돌리기](lync-server-2013-using-cmdlets-to-reverse-domain-preparation.md)  

#### 기타 리소스

[Lync Server 2013에 대한 도메인 준비](lync-server-2013-preparing-domains.md)

