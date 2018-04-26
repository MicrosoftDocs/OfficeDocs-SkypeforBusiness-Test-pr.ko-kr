---
title: 'Lync Server 2013: 부록 B: SBA(Survivable Branch Appliance) 관리'
TOCTitle: '부록 B: SBA(Survivable Branch Appliance) 관리'
ms:assetid: 2ec9d505-6d39-491c-9524-8cf36866b855
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425797(v=OCS.15)
ms:contentKeyID: 49303192
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 부록 B: Lync Server 2013에서 SBA(Survivable Branch Appliance) 관리

 

_**마지막으로 수정된 항목:** 2012-10-18_

이 항목에서는 SBA(Survivable Branch Appliance) 관리 절차에 대해 설명합니다. 구체적으로는 SBA(Survivable Branch Appliance)를 대체하고 이름을 바꾸는 방법, 그리고 SBA(Survivable Branch Appliance)가 연결된 Lync Server 2013 프런트 엔드 풀을 변경하는 방법에 대해 설명합니다.

## SBA(Survivable Branch Appliance)를 대체하려면

1.  SBA(Survivable Branch Appliance)에서 모든 Lync Server 2013 서비스를 중지합니다. 자세한 내용은 SBA(Survivable Branch Appliance) 공급업체 설명서를 참조하십시오.

2.  (권장) 도메인에서 SBA(Survivable Branch Appliance)를 제거합니다.

3.  다음 단계에 따라 Active Directory 도메인 서비스에서 SBA(Survivable Branch Appliance) 컴퓨터 개체를 삭제합니다.
    
      - Enterprise Admins 그룹의 구성원으로 구성원 서버에 로그온합니다.
    
      - **시작** , **관리 도구** , **Active Directory 사용자 및 컴퓨터** 를 차례로 클릭합니다.
    
      - SBA(Survivable Branch Appliance) 개체를 마우스 오른쪽 단추로 클릭하고 **삭제** 를 클릭합니다.

4.  SBA(Survivable Branch Appliance) 컴퓨터 개체를 다시 추가합니다. 자세한 내용은 [Lync Server 2013에서 Active Directory에 SBA(Survivable Branch Appliance) 추가](lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md)를 참조하십시오.

5.  Active Directory 복제가 수행될 때까지 기다립니다.

6.  Lync Server 관리 셸을 열고 **Enable-CSTopology** 를 입력합니다.

7.  새 SBA(Survivable Branch Appliance)를 네트워크에 연결하고, [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 중앙 사이트 작업](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md) 및 [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 분기 사이트 작업](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md)의 단계를 수행합니다.

## SBA(Survivable Branch Appliance)의 이름을 바꾸려면

1.  사용자를 중앙 사이트로 이동합니다. 자세한 내용은 [다른 풀로 사용자 이동](lync-server-2013-move-users-to-another-pool.md)을 참조하십시오.

2.  SBA(Survivable Branch Appliance)에서 모든 Lync Server 2013 서비스를 중지합니다. 자세한 내용은 SBA(Survivable Branch Appliance) 공급업체 설명서를 참조하십시오.

3.  다음 단계에 따라 토폴로지에서 SBA(Survivable Branch Appliance)를 제거합니다.
    
      - **시작** , **모든 프로그램** , **Microsoft Lync Server** 를 차례로 클릭한 다음 **Lync Server 토폴로지 작성기** 를 클릭합니다.
    
      - 콘솔 트리에서 **분기 사이트** 를 확장하고 SBA(Survivable Branch Appliance)를 클릭한 후에 동작 창에서 **삭제** 를 클릭합니다.

4.  도메인에서 SBA(Survivable Branch Appliance)를 제거합니다.

5.  다음 단계에 따라 Active Directory에서 SBA(Survivable Branch Appliance) 컴퓨터 개체를 삭제합니다.
    
      - Enterprise Admins 그룹의 구성원으로 도메인 컨트롤러에 로그온합니다.
    
      - **시작** , **관리 도구** , **Active Directory 사용자 및 컴퓨터** 를 차례로 클릭합니다.
    
      - SBA(Survivable Branch Appliance) 개체를 마우스 오른쪽 단추로 클릭하고 **삭제** 를 클릭합니다.

6.  SBA(Survivable Branch Appliance)를 공장 기본값으로 복원합니다. 자세한 내용은 SBA(Survivable Branch Appliance) 공급업체 설명서를 참조하십시오.

7.  [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 중앙 사이트 작업](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md) 및 [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 분기 사이트 작업](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md)의 단계를 수행합니다.

8.  이름이 바뀐 SBA(Survivable Branch Appliance)로 사용자를 이동합니다. 자세한 내용은 [다른 풀로 사용자 이동](lync-server-2013-move-users-to-another-pool.md)을 참조하십시오.

## SBA(Survivable Branch Appliance)가 연결된 Lync Server 프런트 엔드 풀을 변경하려면

1.  SBA(Survivable Branch Appliance)에서 중앙 사이트의 Lync Server 프런트 엔드 풀로 사용자를 이동합니다. 자세한 내용은 [다른 풀로 사용자 이동](lync-server-2013-move-users-to-another-pool.md)을 참조하십시오.

2.  SBA(Survivable Branch Appliance)에서 모든 Lync Server 서비스를 중지합니다. 자세한 내용은 SBA(Survivable Branch Appliance) 공급업체 설명서를 참조하십시오.

3.  다음 단계에 따라 SBA(Survivable Branch Appliance)가 연결된 Lync Server 프런트 엔드 풀을 업데이트합니다.
    
      - **시작** , **모든 프로그램** , **Microsoft Lync Server** 를 차례로 클릭한 다음 **Lync Server 토폴로지 작성기** 를 클릭합니다.
    
      - **분기 사이트** 를 확장합니다.
    
      - 수정할 SBA(Survivable Branch Appliance) 개체를 마우스 오른쪽 단추로 클릭하고 **편집** 을 클릭합니다.
    
      - 탄성에서 SBA(Survivable Branch Appliance)를 연결할 새 프런트 엔드 풀을 선택하고 **다음** 을 클릭합니다.
    
      - 콘솔 트리에서 새 SBA(Survivable Branch Appliance)를 마우스 오른쪽 단추로 클릭하고 **토폴로지** 를 클릭한 후에 **게시** 를 클릭합니다.

4.  SBA(Survivable Branch Appliance)에서 모든 Lync Server 서비스를 다시 시작합니다.

5.  SBA(Survivable Branch Appliance)를 테스트합니다. 자세한 내용은 [Lync Server 2013의 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버에 사용자 두기](lync-server-2013-home-users-on-a-survivable-branch-appliance-or-server.md)을 참조하십시오.

6.  중앙 사이트의 Lync Server 프런트 엔드 풀에서 SBA(Survivable Branch Appliance)로 사용자를 이동합니다.

