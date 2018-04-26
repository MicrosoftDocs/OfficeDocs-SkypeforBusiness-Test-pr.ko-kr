---
title: 'Lync Server 2013: cmdlet을 사용하여 도메인 준비 되돌리기'
TOCTitle: cmdlet을 사용하여 도메인 준비 되돌리기
ms:assetid: 014dba5d-fcb3-44c9-9d63-ae0755276dac
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398071(v=OCS.15)
ms:contentKeyID: 49302612
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대해 cmdlet을 사용하여 도메인 준비 되돌리기

 

_**마지막으로 수정된 항목:** 2012-10-29_

**Disable-CsAdDomain** cmdlet을 사용하여 도메인 준비 단계를 반전합니다.

## cmdlet을 사용하여 도메인 준비를 반전하려면

1.  도메인의 서버에 Domain Admins 그룹 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Disable-CsAdDomain [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] 
        [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] 
    
    예를 들면 다음과 같습니다.
    
        Disable-CsAdDomain -Domain domain1.contoso.net -GlobalSettingsDomainController dc01.domain1.contoso.net -Force
    
    Force 매개 변수가 있으면 도메인에서 하나 이상의 프런트 엔드 서버 또는 A/V 회의 서버가 활성화된 경우에도 도메인 준비가 롤백됩니다. Force 매개 변수가 없으면 도메인에서 프런트 엔드 서버 또는 A/V 회의 서버가 활성화된 경우 도메인 준비 롤백이 종료됩니다.
    

    > [!NOTE]
    > GlobalSettingsDomainController 매개 변수를 통해 전역 설정이 저장되어 있는 위치를 나타낼 수 있습니다. 설정이 시스템 컨테이너에 저장되어 있는 경우(전역 설정이 구성 컨테이너로 마이그레이션되지 않은 업그레이드 배포에서 일반적임) Active Directory 포리스트의 루트에서 도메인 컨트롤러를 정의합니다. 전역 설정이 구성 컨테이너에 있는 경우(설정이 구성 컨테이너로 마이그레이션된 업그레이드 배포 또는 새 배포에서 일반적임) 포리스트에서 도메인 컨트롤러를 정의합니다. 이 매개 변수를 지정하지 않는 경우 cmdlet은 설정이 구성 컨테이너에 저장되는 것으로 가정하고 AD&nbsp;DS의 도메인 컨트롤러를 참조합니다.



## 참고 항목

#### 작업

[Lync Server 2013에 대한 도메인 준비 실행](lync-server-2013-running-domain-preparation.md)  

#### 기타 리소스

[Lync Server 2013에 대한 도메인 준비](lync-server-2013-preparing-domains.md)

