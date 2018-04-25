---
title: Lync Server 2013에서 컴퓨터에서 실행 중인 서비스의 상태 보기
TOCTitle: Lync Server 2013에서 컴퓨터에서 실행 중인 서비스의 상태 보기
ms:assetid: f41918e7-4c02-431e-840a-88a1f36ae499
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182606(v=OCS.15)
ms:contentKeyID: 49305522
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 컴퓨터에서 실행 중인 서비스의 상태 보기

 

_**마지막으로 수정된 항목:** 2013-02-22_

Lync Server 2013 제어판을 사용하여 Lync Server 토폴로지의 특정 컴퓨터에서 실행되는 모든 서비스를 보고 각 서비스의 상태를 확인할 수 있습니다.

## 컴퓨터에서 실행되는 서비스 상태를 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **토폴로지**를 클릭합니다.

4.  **상태** 페이지에서 필요에 따라 목록을 정렬하거나 검색하여 원하는 컴퓨터를 찾은 다음 컴퓨터 이름을 클릭합니다.

5.  다음을 수행합니다.
    
      - 컴퓨터에서 실행되는 서비스의 최신 상태를 보려면 **서비스 상태 가져오기**를 클릭합니다.
    
      - 컴퓨터에서 실행되는 특정 서비스 목록 및 각 서비스의 상태를 보려면 **속성**을 클릭합니다. 목록으로 돌아오려면 **닫기**를 클릭합니다.

## Lync Server 관리 셸 Cmdlet을 사용하여 서비스 상태 보기

Lync Server 관리 셸 및 **Get-CsWindowsService** cmdlet을 사용하여 서비스 상태도 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션(원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.)에서 실행할 수 있습니다.

## 서비스 상태를 보려면

  - 컴퓨터에서 서비스 상태를 보려면 다음과 비슷한 명령을 Lync Server 관리 셸에 입력하고 Enter 키를 누릅니다.
    
        Get-CsWindowsService -ComputerName atl-cs-001.litwareinc.com | Select-Object RoleName, Status
    
    이 명령은 다음과 비슷한 정보를 반환합니다.
    
        RoleName                                  Status
        --------                                  ------
        {W3SVC}                                   Running
        {CentralManagement}                       Running
        {ClsAgent}                                Running
        {Registrar, UserServer, EdgeServer}       Running
        {ApplicationServer}                       Running
        {ConferencingServer}                      Running
        {MediationServer}                         Running

자세한 내용은 [Get-CsWindowsService](get-cswindowsservice.md)를 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 장치, 전화 및 클라이언트 응용 프로그램 관리](lync-server-2013-managing-devices-phones-and-client-applications.md)

