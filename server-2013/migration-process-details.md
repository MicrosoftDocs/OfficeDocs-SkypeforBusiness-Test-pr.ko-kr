---
title: 마이그레이션 프로세스 - 세부 정보
TOCTitle: 마이그레이션 프로세스 - 세부 정보
ms:assetid: ca7e352c-9bde-47d9-8273-5cf2fdfdfe7e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205264(v=OCS.15)
ms:contentKeyID: 49305028
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 마이그레이션 프로세스 - 세부 정보

 

_**마지막으로 수정된 항목:** 2012-10-19_

Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2그룹 채팅 중 하나를 Lync Server 2013영구 채팅 서버로 마이그레이션하려면 다음 사전 요구 사항 및 세부 단계를 수행하십시오.

## 마이그레이션을 위한 사전 요구 사항

Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2  그룹 채팅 중 하나를 Lync Server 2013  영구 채팅 서버로 마이그레이션하기 전에 다음 사전 요구 사항을 충족하는지 확인해야 합니다.

1.  하나 이상의 Lync Server 2013 풀을 배포합니다. 여러 Lync Server 2013 풀이 있는 경우 새 Lync Server 2013  영구 채팅 서버 풀의 홈 풀로 사용할 Lync Server 2013 풀을 결정해야 합니다.

2.  Lync Server 2013영구 채팅 서버 풀을 설치합니다. 범주, 채팅방, 추가 기능 등이 전혀 없이 빈 상태일 것입니다. 기존 범주, 채팅방, 추가 기능 등을 마이그레이션하기 전에 Lync Server 2013영구 채팅 서버 배포에 채팅방, 범주, 추가 기능 등을 만들 수 있습니다.
    

    > [!IMPORTANT]
    > 새로 만든 항목이 마이그레이션하는 기존 항목과 충돌할 수 있습니다. 이름이 충돌하지 않도록 방지하십시오. 그렇지 않으면 기존 데이터를 마이그레이션할 때 덮어써집니다.



## 마이그레이션을 위해 원본 데이터 준비

다음 단계를 수행하여 마이그레이션을 위해 원본 데이터를 올바로 준비합니다.

1.  Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2  그룹 채팅에 대한 원본 데이터베이스를 백업합니다. SQL Server 백업에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=254851\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=254851%26clcid=0x412)의 "백업 개요(SQL Server)"를 참조하십시오.
    

    > [!IMPORTANT]
    > Active Directory 도메인 서비스는 동일해야 합니다. 마이그레이션 조건 중 하나로서, 다른 배포(특히 다른 Active Directory 포리스트)에 풀을 마이그레이션할 수 없습니다.



2.  Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2  그룹 채팅 채팅방 및 범주 구성을 조사합니다. 기존 배포에서 범주, 채팅방, 추가 기능 등을 변경하려면 그룹 채팅 관리 도구를 사용해야 합니다.
    

    > [!TIP]
    > Lync Server 2013영구 채팅 서버 배포의 범주, 채팅방 또는 추가 기능을 변경하는 작업은 Lync Server 제어판 또는 Windows PowerShell cmdlet을 사용하여 수행합니다.

    
    다음 단계를 수행하여 기존 시스템을 마이그레이션할 준비를 합니다.
    
    1.  영구 채팅 서버는 다단계 계층 구조의 범주가 아닌 단일 수준의 범주를 지원합니다. 마이그레이션이 완료되면 하위 범주 앞에 전체 상위 범주 이름이 붙습니다. 기존 범주 구조를 단일 계층으로 단순화하여 요구 사항에 맞는 결과 구조를 만들 수도 있습니다.
    
    2.  루트 범주에 **관리자**가 있는지 확인합니다. 이 루트 수준에 관리자가 존재하면 마이그레이션 이후 해당 사용자는 **모든 채팅방의 관리자**로 추가됩니다. 관리자가 조직 요구 사항이 아니면 루트 범주에서 이들 관리자를 제거해야 합니다.
    
    3.  채팅방 이름의 길이를 확인합니다. 마이그레이션 이후 단순화된 범주 구조로 인해 하위 범주를 보유한 채팅방은 이름 앞에 상위 범주의 전체 이름이 붙습니다. 이름은 상위 범주 이름을 포함하여 256자로 제한됩니다. 채팅방 이름의 길이를 확인한 후, 이름이 너무 긴 경우 가능하면 길이를 줄입니다.
    
    4.  Lync Server 2013에서 범주 **초대** 설정이 참으로 설정된 경우 해당 범주 아래 채팅방에 대한 초대를 참 또는 거짓으로 선택할 수 있습니다. 하지만 범주 초대 설정이 거짓으로 설정된 경우 해당 범주 아래의 채팅방은 해제됩니다. 마이그레이션 전에 특정 범주 아래에 채팅방을 유지하려면 기존 Lync Server  그룹 채팅 서버 버전에서 초대 설정을 다시 설정해야 합니다. 그렇지 않으면 마이그레이션하는 동안 Lync Server 2013에서 경고를 표시하고 채팅방을 기본값인 거짓으로 설정합니다.
    
    5.  채팅방에서 파일을 사용한 경우 마이그레이션 이후 새 영구 채팅 파일 저장소로 파일을 수동으로 복사(XCOPY)해야 합니다. 이는 자동으로 수행되지 않습니다.
    
    6.  페더레이션 사용자가 있거나 페더레이션 사용자가 있는 채팅방이 있으면 영구 채팅 서버에서 페더레이션이 지원되지 않는다는 사실에 유의하십시오. 페더레이션 사용자가 있는 채팅방은 마이그레이션되지만 페더레이션 액세스가 지원되지 않으므로 사용자 자신은 콘텐츠에 액세스할 수 없습니다.
    
    7.  마이그레이션하지 않으려는 채팅방을 식별하여 사용 안 함으로 표시합니다.
    
    8.  채팅방 콘텐츠를 마이그레이션하기 시작할 날짜를 식별합니다. 예를 들어 2010년 1월 1일 이전의 메시지는 오래되었거나 마이그레이션과 관련이 없다는 이유로 마이그레이션하지 않으려 할 수 있습니다.

## 마이그레이션 수행

다음 단계를 수행하여 기존 그룹 채팅 서버를 마이그레이션합니다.

1.  Lync Server 2010, 그룹 채팅, Office Communications Server 2007 R2  그룹 채팅 또는 Lync Server 2013영구 채팅 서버 서비스를 종료합니다. 모든 서비스가 중지되어야 합니다. 따라서 충분한 가동 중단 시간이 확보되는 시점에 마이그레이션하도록 계획해야 합니다. 이전에 설명한 대로 현재 그룹 채팅 데이터베이스를 백업해야 합니다.

2.  영구 채팅 관리자 RBAC 역할(CsPersistentChatAdministrator)의 구성원으로 Windows PowerShell**Export-CsPersistentChatData** cmdlet을 실행합니다. 내보내기/가져오기 cmdlet에 대한 자세한 내용은 [Lync Server 2013에서 Windows PowerShell cmdlet으로 영구 채팅 서버 구성 문제 해결](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md) 섹션을 참조하십시오.
    
    내보낸 콘텐츠를 조사합니다.

3.  가져올 준비를 마치기 전에 Lync Server 2013영구 채팅 서버 서비스를 종료합니다. 모든 서비스가 중지되어야 합니다. 따라서 충분한 가동 중단 시간이 확보되는 시점에 마이그레이션하도록 계획해야 합니다.

4.  Lync Server 2013 배포에 범주, 채팅방, 추가 기능 등을 만든 경우 마이그레이션하기 전에 영구 채팅 데이터베이스를 백업합니다. 내보내기/가져오기 프로세스를 통해 기존 데이터를 Lync Server 2013 배포에 병합할 수 있지만 실수로 콘텐츠를 덮어쓰는 경우(예: 이름 충돌)에 대비해 데이터베이스를 백업할 수 있습니다.

5.  Windows PowerShell**Import-CsPersistentChatData** cmdlet(가져오기 도구)을 **WhatIf** 명령과 함께 실행하여 영구 채팅 서버 풀의 백 엔드 서버를 마이그레이션 데이터로 채웁니다. 단순화된 관리 모델을 적용하는 과정에서 일부 메시지가 표시될 수 있습니다. 나타나는 오류 또는 경고를 수정합니다.

6.  영구 채팅 관리자 RBAC 역할(CsPersistentChatAdministrator)의 구성원으로 영구 채팅 서버Windows PowerShell**Import-CsPersistentChatData** cmdlet을 실행합니다. 내보내기/가져오기 cmdlet에 대한 자세한 내용은 [Lync Server 2013에서 Windows PowerShell cmdlet으로 영구 채팅 서버 구성 문제 해결](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md) 섹션을 참조하십시오.

7.  새 Lync Server 2013영구 채팅 파일 저장소로 모든 업로드된 파일(전체 폴더)을 복사(XCOPY)해야 합니다.
    

    > [!IMPORTANT]
    > Lync 2013(클라이언트)은 채팅방의 파일 업로드 또는 보기를 지원하지 않습니다. 채팅방의 파일을 보고 게시하기 위해 기존 클라이언트를 계속 사용할 수 있습니다.



8.  Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2  그룹 채팅 Lookup Server URI를 Lync Server 2013영구 채팅 서버 대화 상대 개체로 포팅(port)합니다. 마이그레이션 이후 클라이언트 측 구성 변경 없이 Lync 2010 그룹 채팅 또는 Office Communicator 2007 R2  그룹 채팅 클라이언트를 최신 Lync 2013, 영구 채팅(클라이언트)에 연결해야 하면 다음 단계를 수행해야 합니다.
    
      - ocschat@ *\<도메인 이름\>* .com 조회 서버 사용자 계정을 삭제합니다. 이는 Lync Server 2010, 그룹 채팅에서 조회 서비스를 가리키는 데 사용됩니다. 풀을 제거하고 신뢰할 수 있는 항목을 나중에 제거할 수 있습니다.
    
      - 동일한 SIP URI로 Windows PowerShell cmdlet인 **New-CsPersistentChatEndpoint**를 실행하여 기존 끝점( 영구 채팅 서버 대화 상대 개체)을 만듭니다. 그래야 서비스가 다시 시작되었을 때 기존 클라이언트가 효과적으로 작동합니다.
    
    이제 필수 마이그레이션 프로세스를 완료했습니다. Lync 2010 그룹 채팅(클라이언트) 또는 Office Communicator 2007 R2그룹 채팅(클라이언트)를 새 영구 채팅 서버 풀에 원활하게 연결할 수 있습니다.
    
    다음과 같이 Lync Server 2010, 그룹 채팅 또는 Office Communications Server 2007 R2그룹 채팅에 대해 추가 역할 해제 단계를 수행합니다.

9.  새 영구 채팅 서버 풀의 모든 컴퓨터를 켜서 영구 채팅 서버 서비스를 시작합니다.

10. Lync Server 제어판 및 Windows PowerShell cmdlet을 사용하여 데이터가 성공적으로 마이그레이션되었는지 확인합니다.

11. 그룹 채팅 서버 풀의 컴퓨터에서 Lync 2010 그룹 채팅 또는 Office Communicator 2007 R2그룹 채팅을 제거합니다.

12. Windows PowerShell cmdlet을 사용하여 신뢰할 수 있는 응용 프로그램 및 신뢰할 수 있는 응용 프로그램 풀을 삭제합니다. 그러면 중앙 관리 저장소에서 해당 항목 및 Active Directory에서 관련 TSE(신뢰할 수 있는 서비스 항목)가 삭제됩니다. 또는 토폴로지 작성기를 사용하여 이 단계를 수행할 수 있습니다. 여기에는 신뢰할 수 있는 응용 프로그램/풀에 대한 전용 노드가 있습니다.

13. 새 클라이언트를 통해 영구 채팅 서버 기능을 사용하도록 설정할 수 있습니다. 영구 채팅 서버를 사용하도록 설정하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 영구 채팅 서버 배포](lync-server-2013-deploying-persistent-chat-server.md) 섹션을 참조하십시오.
    

    > [!IMPORTANT]
    > Lync Server 2013은 여러 영구 채팅 서버 풀을 지원합니다. 하지만 Lync 2010 그룹 채팅 또는 Office Communications Server 2007 R2&nbsp; 그룹 채팅 풀을 단일 Lync Server 2013영구 채팅 서버 풀로만 마이그레이션할 수 있습니다. 조직 규정에 따라 배포 환경에 새 영구 채팅 서버 풀을 더 추가할 수 있습니다(예: 데이터를 지정된 지역 내에 유지하려는 경우).


