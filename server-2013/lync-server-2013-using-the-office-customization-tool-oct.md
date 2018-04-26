---
title: OCT(Office 사용자 지정 도구) 사용
TOCTitle: OCT(Office 사용자 지정 도구) 사용
ms:assetid: 26647cb6-ba84-4ba7-8b6f-2cf86818e530
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204748(v=OCS.15)
ms:contentKeyID: 49303098
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# OCT(Office 사용자 지정 도구) 사용

 

_**마지막으로 수정된 항목:** 2012-10-02_

OCT(Office 사용자 지정 도구)는 설치 프로그램의 일부분이며 대부분의 사용자 지정 작업에 권장되는 도구입니다. OCT를 사용하여 Office를 사용자 지정하고 사용자 지정 내용을 설치 사용자 지정 .msp 파일에 저장합니다. 이 파일은 네트워크 설치 지점의 Updates 폴더에 저장합니다. Office를 설치할 때 설치 프로그램은 Updates 폴더에서 설치 사용자 지정 파일을 찾은 다음 사용자 지정 내용을 적용합니다. Updates 폴더는 초기 Office 2013 설치 중에 소프트웨어 업데이트를 배포하는 데만 사용할 수 있습니다.

OCT는 설치 프로그램의 일부분이며 제품의 볼륨 라이선스 버전에 포함되어 있습니다. Office 2013 원본 파일이 포함된 네트워크 설치 지점 루트에서 명령줄에 `setup.exe /admin`을 입력하여 OCT를 실행합니다. 예를 들면 다음과 같은 명령을 사용합니다.

`\\server\share\Office15\setup.exe /admin`

관리자는 OCT를 사용하여 설치 사용자 지정 .msp 파일을 만듭니다. Microsoft Office 2010 OCT에서와 같이 관리자는 다음과 같은 영역을 사용자 지정할 수 있습니다.

  - **설치** 클라이언트의 기본 설치 위치와 기본 조직 이름, 추가 네트워크 설치 원본, 제품 키, 최종 사용자 사용권 계약, 표시 수준, 제거할 이전 Office 버전, 설치 중에 실행할 사용자 지정 프로그램, 보안 설정 및 설치 프로그램 속성을 지정하는 데 사용됩니다.

  - **기능** 사용자 설정을 구성하고 Office 기능 설치 방법을 사용자 지정하는 데 사용됩니다. 관리자는 OCT를 사용하여 사용자에 대해 Office 응용 프로그램 설정의 초기 기본값을 지정할 수 있습니다. 사용자는 설치 후에 대부분의 설정을 수정할 수 있습니다.

  - **추가 콘텐츠** 파일과 레지스트리 항목을 추가/제거하고 바로 가기를 구성하는 데 사용됩니다.

  - **Outlook** 사용자의 기본 Outlook 프로필을 사용자 지정하고, Exchange 설정을 지정하고, 계정을 추가하고, 계정을 제거하고, 설정을 내보내고, 보내기/받기 그룹을 지정하는 데 사용됩니다.

OCT에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=267516\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=267516%26clcid=0x412)를 참조하십시오.

