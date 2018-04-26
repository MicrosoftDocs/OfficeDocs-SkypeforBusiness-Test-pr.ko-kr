---
title: 정책 및 설정 가져오기
TOCTitle: 정책 및 설정 가져오기
ms:assetid: b25decee-2ee5-4836-b370-454411d39252
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205178(v=OCS.15)
ms:contentKeyID: 49304761
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 정책 및 설정 가져오기

 

_**마지막으로 수정된 항목:** 2012-09-28_

Office Communications Server 2007 R2 토폴로지 정보를 Lync Server 2013 파일럿 풀에 병합한 후, Lync Server 2013 관리 셸 cmdlet을 실행하여 Office Communications Server 2007 R2 정책 및 구성 설정을 Lync Server 2013 파일럿 풀에 마이그레이션해야 합니다.

**Import-CsLegacyConfiguration** cmdlet은 정책, 음성 경로, 다이얼 플랜, Communicator Web Access URL 및 전화 접속 액세스 번호를 Lync Server 2013으로 가져옵니다.

## 정책 및 설정을 마이그레이션하려면

1.  Lync Server 2013 프런트 엔드 서버에서 Lync Server 관리 셸을 시작합니다.

2.  명령줄에 다음을 입력합니다.
    
        Import-CsLegacyConfiguration
    
    정책을 가져온 후에는 이어지는 절차에 따라 Lync Server 제어판에서 가져온 정책을 확인합니다.

## 가져온 정책을 보려면

1.  Lync Server 2013 제어판을 엽니다.

2.  **음성 라우팅** 을 클릭하고 가져온 정책을 봅니다.

3.  **회의** 를 클릭하고 가져온 정책을 봅니다.

4.  **페더레이션 및 외부 액세스** 를 클릭하고 가져온 정책을 봅니다.

5.  **모니터링 및 보관** 을 클릭하고 가져온 정책을 봅니다.

