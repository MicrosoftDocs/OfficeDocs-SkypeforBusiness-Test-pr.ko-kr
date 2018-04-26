---
title: Windows PowerShell Cmdlet, 매개 변수, 매개 변수 값
TOCTitle: Windows PowerShell Cmdlet, 매개 변수, 매개 변수 값
ms:assetid: 04615700-099f-4ac5-a801-ddeffccb9e4f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362765(v=OCS.15)
ms:contentKeyID: 56270209
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Windows PowerShell Cmdlet, 매개 변수, 매개 변수 값

 

_**마지막으로 수정된 항목:** 2015-06-22_

Windows의 모든 버전에서 표시되는 명령 창에 익숙하거나 MS-DOS에 익숙한 경우 Windows PowerShell의 사용 방법을 쉽게 배울 수 있습니다. 명령 창에서 명령을 입력하고 Enter 키를 누릅니다. 이에 응답하여 컴퓨터에서 명령 또는 실행 파일을 실행합니다. 예를 들어 현재 디렉터리의 모든 파일 및 폴더에 대한 정보를 반환하려면 명령 프롬프트에서 다음 명령을 입력한 다음 Enter 키를 누릅니다.

    dir

그러면 현재 디렉터리의 모든 파일 및 폴더에 대한 정보가 반환됩니다.

``` 
    Directory: C:\

03/21/2013  03:39 PM    <DIR>          Deploy
03/21/2013  02:55 PM    <DIR>          Intel
07/26/2012  12:33 AM    <DIR>          PerfLogs
04/10/2013  10:29 AM    <DIR>          Program Files
04/08/2013  10:28 AM    <DIR>          Program Files (x86)
03/22/2013  08:44 AM    <DIR>          Users
04/11/2013  03:00 PM    <DIR>              Windows
03/13/2013  02:53 PM                 117   pldok.log
03/21/2013  03:35 PM                 769   RHDSetup.exe
03/21/2013  03:37 PM            207   setup.doc
              3 File(s)        1,093 bytes
              7 Dir(s)21,386,002,432 bytes free
```

이는 명령 또는 실행 파일의 이름만 입력한 경우 나오는 결과의 한 예입니다. 하지만 명령 창 내에서 실행되는 많은 명령이 *인수*도 사용합니다. 인수는 명령에 전달되는 추가 정보이며, 명령의 동작을 수정합니다. 예를 들어 현재 디렉터리에 있는 파일 및 폴더의 이름만 표시하고 파일 또는 폴더의 크기, 파일 또는 폴더를 만든 날짜 및 시간 등의 다른 정보는 표시하지 않으려면 dir 명령을 실행할 때 **/b** 인수를 추가합니다.

    dir /b

**/b** 인수를 추가하면 **dir** 명령에서 현재 디렉터리에 있는 폴더 및 파일의 이름만 보고합니다.

    Deploy
    Intel
    PerfLogs
    Program Files
    Program Files (x86)
    Users
    Windows
    pldok.log
    RHDSetup.exe
    setup.doc

위의 명령에서 **/b** 인수는 반환된 데이터를 파일 및 폴더 이름으로 제한하는 데 필요한 유일한 정보입니다. 명령줄 명령의 경우 대부분 이와 비슷합니다. 인수 하나만 사용하여 명령의 동작을 변경할 수 있습니다(즉, **/b** 인수를 포함하여 추가 정보를 숨기거나 **/b** 인수를 제외하여 추가 정보를 표시할 수 있습니다). 하지만 *인수 값*을 지정해야 하는 경우도 있습니다. 인수 값은 인수 자체에 전달되는 추가 정보입니다. 예를 들어 **/o** 인수를 사용하면 dir 명령으로 반환된 데이터를 정렬하는 방법을 지정할 수 있습니다. 다양한 옵션 중에서 인수 값 **e**를 사용하면 파일 확장명을 기준으로 데이터를 정렬할 수 있고, 인수 값 **s**를 사용하면 파일 크기를 기준으로 정렬할 수 있습니다. 예를 들어 다음 명령은 파일 확장명을 기준으로 반환된 데이터를 정렬합니다. 인수 값 **e**가 **/o** 인수의 바로 뒤에 포함되는 것을 알 수 있습니다.

    dir /oe

예제 폴더를 사용하여 반환된 데이터는 다음과 같이 파일 확장명을 기준으로 사전순으로 정렬되어 표시됩니다.

``` 
    Directory: C:\

03/21/2013  03:39 PM    <DIR>          Deploy
03/21/2013  02:55 PM    <DIR>          Intel
07/26/2012  12:33 AM    <DIR>          PerfLogs
04/10/2013  10:29 AM    <DIR>          Program Files
04/08/2013  10:28 AM    <DIR>          Program Files (x86)
03/22/2013  08:44 AM    <DIR>          Users
04/11/2013  03:00 PM    <DIR>              Windows
03/21/2013  03:37 PM            207   setup.doc
03/21/2013  03:35 PM                 769   RHDSetup.exe
03/13/2013  02:53 PM                 117   pldok.log
              3 File(s)        1,093 bytes
              7 Dir(s)21,386,002,432 bytes free
```

보다 이해하기 쉽게 표시하면 정렬된 파일은 다음과 같습니다.

setup. **doc**  
RHDSetup. **exe**  
pldok. **log**

Windows PowerShell에서는 다른 용어를 사용하지만 Windows PowerShell의 기본 작업 방식은 명령 창 작업 방식과 동일합니다. 명령을 입력하고 필요한 경우 인수와 인수 값을 포함한 다음 Enter 키를 눌러 해당 명령을 실행합니다. 하지만 언급한 대로 Windows PowerShell에서는 명령 셸에서 사용하는 것과 다른 용어를 사용합니다. Windows PowerShell에서는 실행 명령을 *cmdlet*이라고 합니다. 그리고 cmdlet에 전달되는 인수를 *매개 변수*라고 하며 매개 변수에 전달되는 값을 *매개 변수 값*이라고 합니다.

위에서 내린 정의는 단순 정의로, cmdlet은 기본적으로 Windows PowerShell 환경 내에서만 실행할 수 있는 미니 응용 프로그램입니다. 하지만 명령 창에서 실행되는 대부분의 명령 및 응용 프로그램을 포함하여 Windows PowerShell에서 다른 명령 및 응용 프로그램도 실행할 수 있습니다. 예를 들어 Windows PowerShell 내에서 메모장을 시작하려면 다음을 입력하고 Enter 키를 누르기만 하면 됩니다.

    notepad.exe

하지만 비즈니스용 Skype Online을 관리할 때는 대부분의 관리자가 Windows PowerShell cmdlet에 의존하여 관리 작업을 수행합니다. 매우 드물게 비즈니스용 Skype Online을 관리하는 데 사용되는 다른 명령 또는 응용 프로그램도 있습니다. 비즈니스용 Skype Online cmdlet은 추가 인수 없이 사용됩니다(위에서 언급한 대로 Windows PowerShell에서는 인수를 매개 변수라고 합니다). 예를 들어 다음 명령은 추가 매개 변수 없이 [Get-CsOnlineUser](get-csonlineuser.md) cmdlet을 호출합니다. 이 명령 단독으로 비즈니스용 Skype Online의 모든 사용자에 대한 정보를 반환합니다.

    Get-CsOnlineUser

하지만 대부분의 비즈니스용 Skype Online cmdlet은 매개 변수(및 매개 변수 값)도 사용합니다. 다음 명령을 살펴보겠습니다.

    Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"

이 명령은 세 부분으로 구성됩니다.

  - cmdlet **Get-CsOnlineUser**

  - Identity 매개 변수. Windows PowerShell에서는 매개 변수 앞에 항상 대시(-)가 옵니다. 이는 동일한 cmdlet에서 다음 구문을 사용하여 UnassignedUser 매개 변수가 표시됨을 의미합니다.
    
        -UnassignedUser
    
    매개 변수 앞에 대시가 온다는 점뿐만 아니라 인수 앞에 슬래시(/)가 오는 명령 창과 다르다는 점에서 이는 알아 두면 유용합니다.
    
    ``` 
    /b
    ```

  - 매개 변수 값 **kenmyer@litwareinc.com**

이 명령은 특정 사용자(kenmyer@litwareinc.com이라는 ID를 가진 사용자)에 대한 정보를 반환합니다.

## 참고 항목

#### 개념

[Windows PowerShell 및 Lync Online 소개](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

