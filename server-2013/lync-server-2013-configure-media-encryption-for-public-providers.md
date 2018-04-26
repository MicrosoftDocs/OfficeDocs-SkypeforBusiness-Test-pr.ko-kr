---
title: 'Lync Server 2013: 공용 공급자용 미디어 암호화 구성'
TOCTitle: 공용 공급자용 미디어 암호화 구성
ms:assetid: a95814cf-c5a9-4652-8ffc-c469a2653153
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205149(v=OCS.15)
ms:contentKeyID: 49304664
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 공용 공급자용 미디어 암호화 구성

 

_**마지막으로 수정된 항목:** 2014-12-12_

라이선스 요구 사항 및 프로비전 프로세스를 완료하는 방법에 대한 자세한 내용은 "Microsoft Lync Server Office Communications Server 및 Live Communications Server의 공용 IM 연결 프로비전 가이드"( <http://go.microsoft.com/fwlink/?linkid=155970>)를 참조하십시오.

Windows Live Messenger와의 A/V(오디오/비디오) 페더레이션을 구현하는 경우에는 Lync Server 암호화 수준과 EnablePublicCloudAccess 정책이라는 두 가지 매개 변수를 수정해야 합니다. 기본적으로 암호화 수준은 필수로 설정됩니다. 이 설정을 지원됨으로 변경해야 합니다. EnablePublicCloudAccess 정책이 false로 설정된 경우, 이를 **True** 로 설정해야 합니다. 이 작업은 Lync Server 관리 셸에서 수행할 수 있습니다.


> [!IMPORTANT]
> Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL(클라이언트 액세스 라이선스) 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. 내년에는 Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 IM 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.



## Windows Live에 대한 페더레이션 구성

1.  프런트 엔드 서버에서 Lync Server 관리 셸을 시작합니다. **시작** , **모든 프로그램** , **Microsoft Lync Server 2013**, **Lync Server 관리 셸**을 차례로 클릭합니다.

2.  명령 프롬프트에 다음 명령을 입력합니다.
    
        Set-CsMediaConfiguration -EncryptionLevel SupportEncryption
    
        Set-CsExternalAccessPolicy Global -EnablePublicCloudAccess $true -EnablePublicCloudAudioVideoAccess $true
    

    > [!NOTE]
    > Windows Live Messenger에서는 오디오/비디오 암호화를 지원하지 않기 때문에 이 단계가 필요합니다. 이 명령은 오디오/비디오 암호화를 요구하는 대신 지원 암호화로 전역 정책을 설정합니다. Lync 2013을 비롯한 암호화를 지원하는 클라이언트에서는 여전히 암호화가 사용됩니다.


