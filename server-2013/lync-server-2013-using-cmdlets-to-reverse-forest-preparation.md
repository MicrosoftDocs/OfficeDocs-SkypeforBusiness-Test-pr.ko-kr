---
title: 'Lync Server 2013: Cmdlet을 사용하여 포리스트 준비 되돌리기'
TOCTitle: Cmdlet을 사용하여 포리스트 준비 되돌리기
ms:assetid: f48c7eb3-ccb0-48e6-ac79-ab7c7062b9d3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413024(v=OCS.15)
ms:contentKeyID: 49305532
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대해 Cmdlet을 사용하여 포리스트 준비 되돌리기

 

_**마지막으로 수정된 항목:** 2013-06-19_

**Disable-CsAdForest** cmdlet를 사용하여 포리스트 준비 단계를 되돌릴 수 있습니다.


> [!WARNING]
> 이전 버전의 Lync Server가 배포된 환경에서 <STRONG>Disable-CsAdForest</STRONG> cmdlet을 실행하면 이전 버전에 대한 전역 설정도 삭제됩니다.



## cmdlet를 사용하여 포리스트 준비를 되돌리려면

1.  포리스트 루트 도메인에서 Domain Admins 그룹의 구성원으로 도메인에 가입한 컴퓨터에 로그인합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Disable-CsAdForest [-Force] [-GroupDomain <FQDN of the domain in which universal groups were created>]
    
    예를 들면 다음과 같습니다.
    
        Disable-CsAdForest -Force -GroupDomain contoso.net
    
    Force 매개 변수는 작업을 강제로 실행할지 여부를 지정합니다. 이 매개 변수가 없는 경우 Lync Server 2013에 대해 포리스트에서 하나의 도메인이라도 준비된 경우 명령이 실행되지 않습니다. 반면 Force 매개 변수가 지정된 경우에는 포리스트의 다른 도메인 상태에 상관없이 동작이 계속됩니다.
    
    GroupDomain 매개 변수를 지정하지 않을 경우 기본값은 로컬 도메인입니다.

## 참고 항목

#### 작업

[Lync Server 2013에 대한 포리스트 준비 실행](lync-server-2013-running-forest-preparation.md)  

#### 기타 리소스

[Lync Server 2013에 대한 포리스트 준비](lync-server-2013-preparing-the-forest.md)

