---
title: 'Lync Server 2013: Active Directory에 SBA(Survivable Branch Appliance) 추가'
TOCTitle: Active Directory에 SBA(Survivable Branch Appliance) 추가
ms:assetid: 3e63507c-d60b-40ec-8bbe-586b1d707c3e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425906(v=OCS.15)
ms:contentKeyID: 49303405
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Active Directory에 SBA(Survivable Branch Appliance) 추가

 

_**마지막으로 수정된 항목:** 2012-09-23_

SBA(Survivable Branch Appliance)를 배포하려면 Active Directory 도메인 서비스에 SBA(Survivable Branch Appliance)를 추가해야 합니다. 중앙 사이트에서 다음 절차를 수행합니다.


> [!IMPORTANT]
> 이 절차는 SBA(Survivable Branch Appliance)를 배포하는 경우에만 수행합니다. 지속 가능 분기 서버를 배포하는 경우에는 이 절차를 수행하지 마십시오.



## Survivable Branch Appliance를 Active Directory 도메인 서비스에 추가하려면

1.  Enterprise Admins 그룹의 구성원으로 구성원 서버에 로그온합니다.

2.  **시작** , **관리 도구** , **Active Directory 사용자 및 컴퓨터** 를 차례로 클릭합니다.

3.  **동작** 메뉴에서 **새로 만들기** 를 클릭한 다음 **컴퓨터** 를 클릭합니다.

4.  **새 개체 - 컴퓨터** 대화 상자에서 SBA(Survivable Branch Appliance) 컴퓨터 개체의 이름(예: BranchOffice1)을 입력하고 **변경** 을 클릭합니다.

5.  **사용자 또는 그룹 선택** 대화 상자에서 RTCUniversalSBATechnicians 그룹을 추가하고 **확인** 을 클릭합니다.
    

    > [!NOTE]
    > 분기 사이트의 RTCUniversalSBATechnicians 그룹 구성원이 나중에 이 장치를 도메인에 추가합니다.



6.  **확인** 을 클릭하여 SBA(Survivable Branch Appliance) 컴퓨터 개체를 저장합니다.

7.  **시작** , **관리 도구** 를 차례로 클릭한 다음 **ADSI 편집** 을 클릭합니다.

8.  **ADSI 편집** 에서, 이전 단계에서 만든 컴퓨터 개체를 마우스 오른쪽 단추로 클릭하고 **속성** 을 클릭합니다.

9.  특성 목록에서 **servicePrincipalName** 을 클릭하고 **편집** 을 클릭합니다.

10. **추가할 값** 필드에 HOST/\<SBA FQDN\>을 입력합니다. 여기서 \<SBA FQDN\>은 SBA(Survivable Branch Appliance)의 FQDN(정규화된 도메인 이름)입니다. 예를 들어 **HOST/BranchOffice1.contoso.com** 을 입력합니다.

11. **확인** 을 클릭하여 **servicePrincipalName** 특성 설정을 저장하고 **확인** 을 클릭하여 컴퓨터 개체 속성을 저장합니다.

12. **Active Directory 사용자 및 컴퓨터** 에서 **사용자** 를 마우스 오른쪽 단추로 클릭하고 **새로 만들기** 를 클릭한 후에 **사용자** 를 클릭합니다.

13. 마법사에 정보를 입력하여 SBA(Survivable Branch Appliance) 기술자용 도메인 사용자 계정을 만듭니다.

14. **Active Directory 사용자 및 컴퓨터** 에서 **사용자** 를 클릭하고 사용자 개체를 마우스 오른쪽 단추로 클릭한 후에 **그룹에 추가** 를 클릭합니다.

15. **선택할 개체 이름을 입력하십시오** 에 **RTCUniversalSBATechnicians** 를 입력하고 **확인** 을 클릭합니다.

16. 각 분기 사이트 기술자에 대해 12-15단계를 반복합니다.

**다음 단계**: [Lync Server 2013에서 토폴로지에 분기 사이트 추가](lync-server-2013-add-branch-sites-to-your-topology.md)

