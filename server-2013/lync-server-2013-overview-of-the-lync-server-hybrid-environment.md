---
title: 'Lync Server 2013: Lync Server 하이브리드 환경 개요'
TOCTitle: Lync Server 2013 하이브리드 환경 개요
ms:assetid: 0d16ec3a-28f0-4483-96e7-8e68f30398fa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204669(v=OCS.15)
ms:contentKeyID: 49302790
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 하이브리드 환경 개요

 

_**마지막으로 수정된 항목:** 2014-05-28_

Lync Server 2013 하이브리드 환경이란 사용자가 온-프레미스 Lync Server 2013 및 Lync Online에 모두 있지만 user@contoso.com과 같은 동일한 도메인을 공유하는 배포를 의미합니다.

## 가이드 정보

이 가이드에서는 Lync Online과 상호 작용하도록 Lync Server 2013 환경을 구성한 다음 온-프레미스 배포에서 Lync Online을 사용하도록 사용자를 이동하기 위해 수행해야 하는 작업을 설명합니다.

## 필요 조건

하이브리드용 배포를 구성하기 위한 작업을 완료하려면 다음 응용 프로그램과 유틸리티를 설치해야 합니다. 이러한 파일의 설치 관리자는 배포용으로 제공된 설치 미디어에도 포함되어 있고 아래 목록의 링크에서도 제공됩니다.

  - [AD FS(Active Directory Federation Services) 2.0](http://go.microsoft.com/fwlink/p/?linkid=257305)

  - [Microsoft 디렉터리 동기화 도구 9.1](http://go.microsoft.com/fwlink/p/?linkid=257307)

  - [AD FS를 사용하는 Single Sign-On을 위한 Windows PowerShell 설치](http://go.microsoft.com/fwlink/p/?linkid=398710)

  - Microsoft Online Services 로그인 도우미(msoidcli-7.0.msi)는 Office 365 관리 포털에서 연결된 다운로드 페이지에 있는 Office 365용 데스크톱 설치에 포함되어 있습니다.

## 관리자 자격 증명

관리자 자격 증명을 제공하라는 메시지가 나타나면 Office 365 테넌트를 위한 관리자 계정의 사용자 이름과 암호를 사용합니다. AD FS(Active Directory Federation Services) 2.0, 디렉터리 동기화, Single Sign-On, 페더레이션을 구성하고 사용자를 Lync Online으로 이동할 때에도 이러한 자격 증명을 사용합니다.

## Lync Online PowerShell에 연결

관리자는 이제 Windows PowerShell을 사용해 Lync Online 및 해당 Lync Online 사용자 계정을 관리할 수 있습니다. 이렇게 하려면 먼저 Microsoft 다운로드 센터(http://go.microsoft.com/fwlink/?LinkId=294688)에서 Lync Online 커넥터 모듈을 다운로드하고 설치해야 합니다. Lync Online 커넥터 모듈 다운로드, 설치, 사용과 Windows PowerShell을 사용해 Lync Online을 관리하는 방법에 대한 자세한 내용은 [Windows PowerShell을 사용하여 Lync Online 관리](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)를 참고하세요.

