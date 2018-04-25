---
title: 'Lync Server 2013: 모바일 기능 배포 확인'
TOCTitle: 모바일 기능 배포 확인
ms:assetid: 72f9b4d3-57b0-4705-9480-cfdca313a70c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690024(v=OCS.15)
ms:contentKeyID: 49304022
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 모바일 기능 배포 확인

 

_**마지막으로 수정된 항목:** 2013-02-12_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Lync Server Mobility Service 및 Lync Server 자동 검색 서비스를 배포한 후에는 테스트 트랜잭션을 실행하여 배포가 정상적으로 작동하는지 확인합니다. **Test-CsUcwaConference**를 실행하여 Lync 2013 모바일 클라이언트를 사용하는 두 사용자가 회의를 만들고 회의에 참가하여 의사를 교환하는 기능을 테스트할 수 있습니다. 이 테스트 트랜잭션을 사용하려면 두 명의 실제 또는 테스트 사용자와 해당 사용자의 전체 자격 증명이 필요합니다.

**Test-CsMcxP2PIM**을 사용하여 Lync 2010 Mobile을 사용하는 두 사용자 간의 인스턴트 메시지 보내기를 테스트합니다. **Test-CsUcwaConference**와 마찬가지로 두 명의 실제 사용자 또는 미리 정의된 테스트 사용자가 필요합니다.

## Lync 2013 모바일 클라이언트에 대해 회의를 테스트하려면

1.  Lync Server 관리 셸 및 Ocscore가 설치되어 있는 컴퓨터에 CsAdministrator 역할의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력합니다.
    
        Test-CsUcwaConference -TargetFqdn <FQDN of Front End pool> -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -OrganizerSipAddress sip:<SIP address of test user 1> -OrganizerCredential <test user 1 credentials> -ParticipantSipAddress sip:<SIP address of test user 2> -ParticipantCredential <test user 2 credentials> -v
    
    스크립트에서 자격 증명을 설정하여 테스트 cmdlet으로 전달할 수 있습니다. 예를 들면 다음과 같습니다.
    
        $passwd1 = ConvertTo-SecureString "Password01" -AsPlainText -Force
        $passwd2 = ConvertTo-SecureString "Password02" -AsPlainText -Force
        $testuser1 = New-Object Management.Automation.PSCredential("contoso\UserName1", $passwd1)
        $testuser2 = New-Object Management.Automation.PSCredential("contoso\UserName2", $passwd2)
        Test-CsUcwaConference -TargetFqdn pool01.contoso.com -Authentication Negotiate -OrganizerSipAddress sip:UserName1@contoso.com -OrganizerCredential $testuser1 -ParticipantSipAddress sip:UserName2@contoso.com -ParticipantCredential $testuser2 -v

## Lync 2010 Mobile에 대해 사용자 간 IM(인스턴트 메시징)을 테스트하려면

1.  Lync Server 관리 셸 및 Ocscore가 설치되어 있는 컴퓨터에 CsAdministrator 역할의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력합니다.
    
        Test-CsMcxP2PIM -TargetFqdn <FQDN of Front End pool> -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -SenderSipAddress sip:<SIP address of test user 1> -SenderCredential <test user 1 credentials> -ReceiverSipAddress sip:<SIP address of test user 2> -ReceiverCredential <test user 2 credentials> -v
    
    스크립트에서 자격 증명을 설정하여 테스트 cmdlet으로 전달할 수 있습니다. 예를 들면 다음과 같습니다.
    
        $passwd1 = ConvertTo-SecureString "Password01" -AsPlainText -Force
        $passwd2 = ConvertTo-SecureString "Password02" -AsPlainText -Force
        $tuc1 = New-Object Management.Automation.PSCredential("contoso\UserName1", $passwd1)
        $tuc2 = New-Object Management.Automation.PSCredential("contoso\UserName2", $passwd2)
        Test-CsMcxP2PIM -TargetFqdn pool01.contoso.com -Authentication Negotiate -SenderSipAddress sip:UserName1@contoso.com -SenderCredential $tuc1 -ReceiverSipAddress sip:UserName2@contoso.com -ReceiverCredential $tuc2 -v

## 참고 항목

#### 기타 리소스

[Test-CsMcxP2PIM](test-csmcxp2pim.md)  
[Test-CsUcwaConference](test-csucwaconference.md)

