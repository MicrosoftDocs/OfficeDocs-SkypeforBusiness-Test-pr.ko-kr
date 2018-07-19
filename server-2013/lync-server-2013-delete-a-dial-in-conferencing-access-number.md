---
title: 전화 접속 회의 액세스 번호 삭제
TOCTitle: 전화 접속 회의 액세스 번호 삭제
ms:assetid: 199c5d9c-0489-4ad5-a7f1-ca59fe0e6ac7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg520956(v=OCS.15)
ms:contentKeyID: 49302952
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전화 접속 회의 액세스 번호 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

다음 단계에 따라 전화 접속 회의 액세스 번호를 삭제합니다.

## 전화 접속 회의 액세스 번호를 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **회의**를 클릭한 다음 **전화 접속 액세스 번호**를 클릭합니다.

4.  페이지의 목록에서 삭제할 전화 접속 번호를 클릭하고 **편집**을 클릭한 후에 **삭제**를 클릭합니다.

5.  **확인**을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 전화 접속 회의 액세스 번호 제거

Windows PowerShell 및 **Remove-CsDialInConferencingAccessNumber** cmdlet을 사용하여 전화 접속 회의 액세스 번호를 삭제할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 특정 전화 접속 회의 액세스 번호 제거

  - 다음 명령은 ID가 sip:RedmondDialInAccess@litwareinc.com인 전화 접속 회의 액세스 번호를 삭제합니다.
    
        Remove-CsDialInConferencingAccessNumber -Identity "sip:RedmondDialInAccess@litwareinc.com"

## 특정 지역에 할당된 모든 전화 접속 회의 액세스 번호 제거

  - 다음 명령은 Northwest 지역과 연결된 모든 전화 접속 회의 액세스 번호를 삭제합니다.
    
        Get-CsDialInConferencingAccessNumber -Region "Northwest" | Remove-CsDialInConferencingAccessNumber

## 기본 언어를 기준으로 전화 접속 회의 액세스 번호 제거

  - 다음 명령은 기본 언어가 이탈리아어인 모든 전화 접속 회의 액세스 번호를 삭제합니다.
    
        Get-CsDialInConferencingAccessNumber | Where-Object {$_.PrimaryLanguage -eq "it-IT"} | Remove-CsDialInConferencingAccessNumber

자세한 내용은 [Remove-CsDialInConferencingAccessNumber](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsDialInConferencingAccessNumber) cmdlet에 대한 도움말 항목을 참조하십시오.

