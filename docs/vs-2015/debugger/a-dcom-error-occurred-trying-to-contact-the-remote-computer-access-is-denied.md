---
title: Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu. | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cabac4997480b626714c129daef0511643ae2a50
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694212"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputera zdalnego. Odmowa dostępu. ](https://docs.microsoft.com/visualstudio/debugger/a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied).  
  
Zdalne debugowanie używa modelu DCOM do komunikacji między komputerami lokalnymi i zdalnymi w następujących sytuacjach:  
  
-   Debuger jest ustawiona na **macierzysty tryb zgodności** lub **trybu zgodności zarządzanej** jest zaewidencjonowany **narzędzia / Opcje / Debugowanie** strony  
  
-   Debugowany zarządzany kod C++ (C + +/ CLI) kod.  
  
-   W programie Visual Studio 2013 gdy **Włączanie natywnego Edytuj i Kontynuuj** jest zaewidencjonowany **narzędzia / Opcje / Debugowanie** strony  
  
-   Niektóre innych firm debugowania scenariuszy  
  
 Ten błąd występuje, gdy proces programu Visual Studio nie może uwierzytelniać (lub podane poświadczenia zostały uznane za niewystarczające) do procesu zdalnego debugera za pośrednictwem protokołów DCOM. Co najmniej jeden z następujących rozwiązań może rozwiązać ten problem:  
  
-   Wyłącz **macierzysty tryb zgodności** i **trybu zgodności zarządzanej**.  
  
-   W programie Visual Studio 2013, wyłącz **Włączanie natywnego Edytuj i Kontynuuj**.  
  
-   Ponowne uruchomienie obu komputerów.  
  
-   Jeśli zdalne debugowanie wymaga wprowadzania poświadczeń, zaznacz opcję zapisania poświadczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



