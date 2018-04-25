---
title: Microsoft Exchange Server 통합 메시징을 실행하는 서버에서 인증서 구성
TOCTitle: Microsoft Exchange Server 통합 메시징을 실행하는 서버에서 인증서 구성
ms:assetid: 74c883b4-cef6-41a9-b2eb-7212be32fea4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398564(v=OCS.15)
ms:contentKeyID: 49304045
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Exchange Server 통합 메시징을 실행하는 서버에서 인증서 구성

 

_**마지막으로 수정된 항목:** 2012-09-26_

계획 설명서의 [Lync Server 2013의 Exchange 통합 메시징 통합 계획](lync-server-2013-planning-for-exchange-unified-messaging-integration.md)에 설명된 대로 Exchange 통합 메시징(UM)을 배포한 경우 조직의 Enterprise Voice 사용자에게 Exchange UM 기능을 제공하려면 다음 절차에 따라 Exchange UM을 실행하는 서버에서 인증서를 구성할 수 있습니다.


> [!IMPORTANT]
> 내부 인증서의 경우 Lync Server 2013을 실행하는 서버와 Microsoft Exchange를 실행하는 서버에 모두 신뢰할 수 있는 루트 인증 기관 인증서가 있어야 하며 이들 인증서가 상호 신뢰되어야 합니다. CA(인증 기관)는 같을 수도 있고, 서버의 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증 기관의 루트 인증서가 등록되어 있는 경우에는 인증 기관이 달라도 됩니다.



Lync Server 2013에 연결하려면 서버 인증서를 사용하여 Exchange Server를 구성해야 합니다.

1.  Exchange Server에 대한 CA 인증서를 다운로드합니다.

2.  Exchange Server에 대한 CA 인증서를 설치합니다.

3.  Exchange Server의 신뢰할 수 있는 루트 CA 목록에 해당 CA가 있는지 확인합니다.

4.  Exchange Server에 대한 인증서 요청을 만들고 인증서를 설치합니다.

5.  Exchange Server에 대한 인증서를 지정합니다.

## CA 인증서를 다운로드하려면

1.  Exchange UM을 실행하는 서버에서 **시작**, **실행**을 차례로 클릭하고 **http://\<발급 CA 서버 이름\>/certsrv**를 입력한 다음 **확인**을 클릭합니다.

2.  **작업 선택**에서 **CA 인증서, 인증서 체인 또는 CRL 다운로드**를 클릭합니다.

3.  **CA 인증서, 인증서 체인 또는 CRL 다운로드**에서 **기준 64에 대한 인코딩 방법**을 선택하고 **CA 인증서 다운로드**를 클릭합니다.
    

    > [!NOTE]
    > 이 단계에서 DER(Distinguished Encoding Rules) 인코딩을 지정할 수도 있습니다. DER 인코딩을 선택하는 경우 이 절차 다음 단계와 <STRONG>CA 인증서를 설치하려면</STRONG>의 10단계에서 파일 형식은 .cer이 아닌 .p7b입니다.



4.  **파일 다운로드** 대화 상자에서 **저장**을 클릭한 다음 파일을 서버의 하드 디스크에 저장합니다. 이전 단계에서 선택한 인코딩에 따라 파일의 확장명은 .cer 또는 .p7b가 됩니다.

## CA 인증서를 설치하려면

1.  Exchange UM을 실행하는 서버에서 **시작**, **실행**을 차례로 클릭하고 **열기** 상자에 **mmc**를 입력한 다음 **확인**을 클릭하여 MMC(Microsoft Management Console)를 엽니다.

2.  **파일** 메뉴에서 **스냅인 추가/제거**를 클릭한 다음 **추가**를 클릭합니다.

3.  **독립 실행형 스냅인 추가** 상자에서 **인증서**를 클릭한 다음 **추가**를 클릭합니다.

4.  **인증서 스냅인** 대화 상자에서 **컴퓨터 계정**을 클릭한 다음 **다음**을 클릭합니다.

5.  **컴퓨터 선택** 대화 상자에서 **로컬 컴퓨터: (이 콘솔이 실행되고 있는 컴퓨터)** 확인란이 선택되었는지 확인한 다음 **마침**을 클릭합니다.

6.  **닫기**를 클릭한 다음 **확인**을 클릭합니다.

7.  콘솔 트리에서 **인증서(로컬 컴퓨터)**, **신뢰할 수 있는 루트 인증 기관**을 차례로 확장한 다음 **인증서**를 클릭합니다.

8.  **인증서**를 마우스 오른쪽 단추로 클릭하고 **모든 작업**을 클릭하고 **가져오기**를 클릭합니다.

9.  **다음**을 클릭합니다.

10. **찾아보기**를 클릭하여 파일을 찾은 다음 **다음**을 클릭합니다. **CA 인증서를 다운로드하려면**의 3단계에서 선택한 인코딩에 따라 파일의 확장명은 .cer 또는 .p7b가 됩니다.

11. **모든 인증서를 다음 저장소에 저장**을 클릭합니다.

12. **찾아보기**를 클릭한 다음 **신뢰할 수 있는 루트 인증 기관**을 선택합니다.

13. **다음**을 클릭하여 설정을 확인한 다음 **마침**을 클릭합니다.

## CA가 신뢰할 수 있는 루트 CA 목록에 있는지 확인하려면

1.  Exchange UM을 실행하는 서버의 MMC에서 **인증서(로컬 컴퓨터)**, **신뢰할 수 있는 루트 인증 기관**을 차례로 확장한 다음 **인증서**를 클릭합니다.

2.  세부 정보 창에서 해당 CA가 신뢰할 수 있는 CA 목록에 있는지 확인합니다.

## Lync Server에서 Exchange Server 2013 UM을 구성하려면

1.  자세한 내용은 Exchange Server 설명서에서 "Microsoft Lync Server 2013"([http://go.microsoft.com/fwlink/?linkid=265372\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=265372%26clcid=0x412))을 참조하십시오.

## Exchange Server 2007(SP1)에서 인증서 요청을 만들고 인증서를 설치하려면

1.  Exchange UM을 실행하는 서버에서 **시작**, **실행**을 차례로 클릭하고 **http://\<***발급 CA 서버 이름***\>/certsrv**를 입력한 다음 **확인**을 클릭합니다.

2.  **작업 선택**에서 **인증서 요청**을 클릭합니다.

3.  **인증서 요청**에서 **고급 인증서 요청**을 클릭합니다.

4.  **고급 인증서 요청**에서 **이 CA에 요청을 만들어 제출합니다**를 클릭합니다.

5.  **고급 인증서 요청**에서 **웹 서버** 또는 서버 인증을 위해 구성된 다른 서버 인증서 템플릿을 선택합니다.

6.  **오프라인 템플릿의 정보 확인 중** 아래의 **이름** 상자에 Exchange Server의 FQDN(정규화된 도메인 이름)을 입력합니다.
    

    > [!NOTE]
    > Exchange Server의 FQDN을 입력해야 통신이 이루어집니다.



7.  **키 옵션**에서 **인증서를 로컬 컴퓨터의 인증서 저장소에 저장** 확인란을 클릭합니다.

8.  웹 페이지 아래쪽에서 **제출** 단추를 클릭합니다.

9.  확인하는 대화 상자가 열리면 **예**를 클릭합니다.

10. 발급된 인증서 페이지의 **발급된 인증서**에서 **이 인증서 설치**를 클릭합니다.

11. 확인하는 대화 상자가 열리면 **예**를 클릭합니다.

12. "새 인증서가 설치되었습니다."라는 메시지가 나타나는지 확인합니다.

## Exchange Server 2010에서 인증서를 만들려면

1.  Exchange UM을 실행하는 서버에 적절한 사용자 권한으로 로그온합니다. 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=195499\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=195499%26clcid=0x412)의 "클라이언트 액세스 권한"을 참조하십시오.

2.  인증서를 만들려면 다음 절차를 참조하십시오.
    
    1.  [http://go.microsoft.com/fwlink/?linkid=195494\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=195494%26clcid=0x412)의 "새 Exchange 인증서 만들기"
    
    2.  [http://go.microsoft.com/fwlink/?linkid=195496\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=195496%26clcid=0x412)의 "Exchange 인증서 가져오기"
    

    > [!NOTE]
    > 인증서 <STRONG>주체 이름</STRONG>에 Exchange Server의 FQDN을 입력해야 통신이 이루어집니다.



## Exchange Server 2007(SP1)에서 인증서를 지정하려면

1.  Exchange UM을 실행하는 서버에서 MMC를 엽니다.

2.  콘솔 트리에서 **개인**을 확장하고 **인증서**를 클릭합니다.

3.  세부 정보 창에서 개인 인증서가 표시되는지 확인합니다.

4.  세부 정보를 볼 인증서를 두 번 클릭하고 유효한지 확인합니다.
    

    > [!NOTE]
    > 인증서가 유효한 것으로 표시될 때까지 몇 분 정도 걸릴 수 있습니다.



5.  Microsoft Exchange 통합 메시징 서비스를 다시 시작합니다.
    

    > [!NOTE]
    > Exchange Server 2007 SP1 통합 메시징을 실행하는 서버에서 올바른 인증서를 자동으로 검색합니다.



6.  이벤트 뷰어를 열고 이벤트 ID 1112를 찾습니다. 이 이벤트는 Exchange Server 2007 SP1 통합 메시징을 실행하는 서버가 검색한 인증서를 지정합니다.

## Exchange Server 2010에서 인증서를 지정하려면

1.  Exchange UM을 실행하는 서버에 적절한 사용자 권한으로 로그온합니다. 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=195499\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=195499%26clcid=0x412)의 "클라이언트 액세스 권한"을 참조하십시오.

2.  인증서를 지정하는 절차는 [http://go.microsoft.com/fwlink/?linkid=195497\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=195497%26clcid=0x412)의 "인증서에 서비스 지정"을 참조하십시오.

