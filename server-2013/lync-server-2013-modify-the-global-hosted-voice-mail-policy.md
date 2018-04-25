---
title: Lync Server 2013에서 전역 호스팅된 음성 메일 정책 수정
TOCTitle: Lync Server 2013에서 전역 호스팅된 음성 메일 정책 수정
ms:assetid: f059b3ce-a7d8-4ea9-b10b-0052222ec2ce
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412994(v=OCS.15)
ms:contentKeyID: 49305474
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 전역 호스팅된 음성 메일 정책 수정

 

_**마지막으로 수정된 항목:** 2012-09-24_

호스팅된 *전역* 음성 사서함 정책은 Lync Server 2013과 함께 설치됩니다. 요구 사항을 충족하도록 정책을 수정할 수 있지만 정책의 이름을 변경하거나 정책을 삭제할 수는 없습니다. 글로벌 정책을 수정하려면 Set-CsHostedVoicemailPolicy cmdlet을 사용하여 특정 배포에 적절한 값으로 매개 변수를 설정합니다.

[Set-CsHostedVoicemailPolicy](set-cshostedvoicemailpolicy.md) cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.

## 호스팅된 전역 음성 메일 정책을 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  Set-CsHostedVoicemailPolicy cmdlet를 실행하여 환경에 대한 전역 정책 매개 변수를 설정합니다. 예를 들어 다음을 실행합니다.
    
        Set-CsHostedVoicemailPolicy -Destination ExUM.fabrikam.com -Organization "corp1.litwareinc.com"
    
    이 명령은 정책의 Identity 매개 변수를 지정하지 않으므로 Windows PowerShell 명령줄 인터페이스는 호스팅된 전역 음성 메일 정책에서 다음 값을 설정합니다.
    
      - **Destination**은 호스팅된 Exchange UM 서비스의 FQDN(정규화된 도메인 이름)을 지정합니다. 이 매개 변수는 선택 사항이지만 호스팅된 음성 메일에 대해 사용자를 활성화하려는 경우 사용자에게 할당된 정책에 Destination 값이 없으면 활성화가 실패합니다.
    
      - **Organization**은 Lync Server 사용자가 홈으로 사용하는 Exchange 테넌트의 쉼표로 구분된 목록을 지정합니다. 각 테넌트는 호스팅된 Exchange UM 서비스에 있는 테넌트의 FQDN으로 지정해야 합니다.
    

    > [!NOTE]
    > 이전 cmdlet 예에서 "corp1.litwareinc.com" 값은 Organization 매개 변수에 이미 있을 수 있는 값을 대체합니다. 예를 들어 정책에 쉼표로 구분된 조직 목록이 이미 있는 경우 전체 목록이 대체됩니다. 전체 목록을 대체하지 않고 목록에 조직을 추가하려면 다음과 같은 명령을 실행합니다.

    
        $a = Get-CsHostedVoicemailPolicy
        $a.Organization += ",corp3.litwareinc.com"
        Set-CsHostedVoicemailPolicy -Organization $a.Organization

