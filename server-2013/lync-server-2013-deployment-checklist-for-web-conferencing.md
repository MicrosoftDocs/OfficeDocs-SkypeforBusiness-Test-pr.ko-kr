---
title: Lync Server 2013의 웹 회의를 위한 배포 검사 목록
TOCTitle: Lync Server 2013의 웹 회의를 위한 배포 검사 목록
ms:assetid: 9908ebe0-e5d3-4920-b9b1-85021f7e69e9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205104(v=OCS.15)
ms:contentKeyID: 49304478
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 웹 회의를 위한 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

다른 Lync Server 2013 구성 요소와 마찬가지로 웹 회의를 배포하려면 토폴로지 작성기를 사용하여 회의가 포함된 토폴로지를 만들고 게시해야 합니다.

## 배포 순서

초기 토폴로지를 배포할 때 회의를 동시에 배포하거나 하나 이상의 프런트 엔드 풀 또는 Standard Edition 서버를 배포한 후에 회의를 배포할 수 있습니다.

## 회의 배포 프로세스

다음 표에서는 기존 토폴로지에 회의를 배포하는 데 필요한 단계를 간략하게 보여 줍니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>단계</th>
<th>작업</th>
<th>역할 및 그룹 구성원</th>
<th>설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>하드웨어 및 소프트웨어 필수 구성 요소 설치</strong></p></td>
<td><p>회의는 프런트 엔드 풀 및 Standard Edition 서버의 프런트 엔드 서버에서 실행됩니다. 이러한 서버를 설치하는 데 필요한 것 이외에 별도로 필요한 하드웨어 또는 소프트웨어는 없습니다.</p>


> [!NOTE]
> Lync Server 2013에서는 Office Web Apps와 Office Web Apps 서버를 사용하여 PowerPoint 프레젠테이션 공유 및 렌더링을 처리합니다. Office Web Apps 서버를 설치하고 구성하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md">Office Online Server 및 Lync Server 2013과 통합 구성</A>를 참조하십시오.


</td>
<td><p>로컬 Administrators 그룹의 구성원인 도메인 사용자</p></td>
<td><p>지원 가능성 설명서의 <a href="lync-server-2013-supported-hardware.md">Lync Server 2013에서 지원되는 하드웨어</a></p>
<p>지원 가능성 설명서의 <a href="lync-server-2013-server-software-and-infrastructure-support.md">Lync Server 2013의 서버 소프트웨어 및 인프라 지원</a></p>
<p>계획 설명서의 <a href="lync-server-2013-determining-your-system-requirements.md">Lync Server 2013의 시스템 요구 사항 확인</a></p>
<p>계획 설명서의 <a href="lync-server-2013-technical-requirements-for-archiving.md">Lync Server 2013의 보관에 대한 기술 요구 사항</a></p>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>회의를 지원하는 데 적절한 내부 토폴로지 만들기</strong></p></td>
<td><p>회의를 토폴로지에 추가하고 토폴로지를 게시하려면 토폴로지 작성기를 실행합니다.</p></td>
<td><p>토폴로지를 정의하려면 로컬 Users 그룹의 구성원 계정 필요</p>
<p>토폴로지를 게시하려면 Domain Admins 그룹 및 RTCUniversalServerAdmins 그룹의 구성원이고 Lync Server 2013 파일 저장소에 사용할 파일 공유에 대한 모든 권한(읽기/쓰기/수정)(토폴로지 작성기에서 필요한 DACL을 구성하는 데 필요함)</p></td>
<td><p>배포 설명서의 <a href="lync-server-2013-define-and-configure-a-topology-in-topology-builder.md">Lync Server 2013에 대한 토폴로지 작성기에서 토폴로지 정의 및 구성</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>회의 정책 및 지원 구성</strong></p></td>
<td><p>Lync Server 2013 제어판 또는 Lync Server 관리 셸을 사용하여 회의 설정을 구성합니다.</p></td>
<td><p>RTCUniversalServerAdmins 그룹( Windows PowerShell에만) 또는 사용자를 [] 또는 CSAdministrator 역할에 할당</p></td>
<td><p>작업 설명서의 <a href="lync-server-2013-conferencing-policies.md">Lync Server 2013의 회의 정책</a></p></td>
</tr>
</tbody>
</table>


Lync Server 2013에는 이제 회의 중 업로드할 수 있는 파일 크기를 제한하는 **MaxUploadFileSizeMb** 설정이 포함되어 있습니다. 이 설정의 기본값은 500MB입니다. **Set-CsConferencingConfiguration** cmdlet을 사용하여 **MaxUploadFileSizeMb**를 조정할 수 있습니다.

**MaxUploadFileSizeMb**는 Lync Web App의 파일 업로드 설정은 제한하지 않습니다. Lync Web App의 파일 크기 업로드 제한은 약 30MB로 설정되어 있으며 IIS web.config 파일(/DataCollabWeb/Int\[Ext\]/Handler/web.config)을 통해 제어됩니다. Lync Web App의 파일 크기 업로드 제한을 구성하려면 web.config 파일에서 아래와 같이 `maxRequestLength` 및 `maxAllowedContentLength`를 업데이트합니다.

    <system.web>
        <!-- 
            Since this handler is used to upload files to DMCU the request size (in kilobytes) 
            has to fit max allowed file size uploaded by LWA client.
            The timeout has to reflect the min client bandwidth. Timeout of 600 secs 
            and 512 Kbits of *client* bandwidth would result into aproximately 30 Mbytes 
            for LWA upload size limit.
        -->
          <httpRuntime maxRequestLength="500000" executionTimeout="600" />
    
    
    
                    <security>
                    <requestFiltering>
                               <requestLimits maxAllowedContentLength="524288000" />
                    </requestFiltering>
                    </security>

각 프런트 엔드 서버의 web.config 파일을 업데이트해야 합니다.

