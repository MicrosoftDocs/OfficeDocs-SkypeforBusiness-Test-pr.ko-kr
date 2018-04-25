---
title: 'Lync Server 2013: Kerberos 인증에 대한 기능 준비 상태 테스트 및 보고'
TOCTitle: Kerberos 인증에 대한 기능 준비 상태 테스트 및 보고
ms:assetid: d52c39e5-747d-4f29-88aa-30fd6f26b99c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398925(v=OCS.15)
ms:contentKeyID: 49305145
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Kerberos 인증에 대한 기능 준비 상태 테스트 및 보고

 

_**마지막으로 수정된 항목:** 2012-01-16_

이 절차를 성공적으로 완료하려면 RTCUniversalServerAdmins 그룹의 구성원인 사용자로 로그온해야 합니다.

**Test-CsKerberosAccountAssignment**  Windows PowerShell cmdlet를 사용하여 Kerberos 인증을 위한 사이트 할당 기능 준비를 테스트하고 보고할 수 있습니다. 이 명령은 필수 Identity 매개 변수에서 지정된 사이트를 쿼리합니다. 선택적 Report 매개 변수는 cmdlet가 HTML 보고서를 명령이 실행되는 컴퓨터의 C:\\Logs에 작성하도록 합니다. 선택적 Verbose 매개 변수는 작업 정보를 화면에 보고합니다.

## 사이트에 대한 Kerberos 인증을 위해 기능 준비를 테스트 및 보고하려면

1.  Lync Server 2013을 실행하는 도메인의 컴퓨터나 관리 도구가 설치된 컴퓨터에 RTCUniversalServerAdmins 그룹의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음 명령을 실행합니다.
    
        Test-CsKerberosAccountAssignment -Identity "site:SiteName" -Report "c:\logs\FileName.htm" -Verbose
    
    예를 들면 다음과 같습니다.
    
        Test-CsKerberosAccountAssignment -Identity "site:Redmond" -Report "c:\logs\KerberosReport.htm" -Verbose

