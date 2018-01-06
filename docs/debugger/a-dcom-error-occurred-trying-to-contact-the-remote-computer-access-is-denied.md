---
title: "Błąd modelu DCOM podczas próby kontaktu z komputerem zdalnym. Odmowa dostępu. | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e0d64aef8fd571032959eb8c3ea2e622a8233620
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Błąd modelu DCOM podczas próby kontaktu z komputerem zdalnym. Odmowa dostępu.
Debugowanie zdalne używa modelu DCOM do komunikacji między komputerami lokalnymi i zdalnymi w następujących sytuacjach:  
  
-   Debuger ma ustawioną wartość **natywnego trybu zgodności** lub **trybu zgodności zarządzanej** zaewidencjonowania **Narzędzia > Opcje > debugowanie** strony  
  
-   Debugowania zarządzanego języka C++ (C + +/ CLI) kodu.  
  
-   W programie Visual Studio 2013 gdy **włączyć natywnego Edytuj i Kontynuuj** zaznaczono **Narzędzia > Opcje > debugowanie** strony  
  
-   Niektóre innej debugowania scenariuszy  
  
 Ten błąd występuje, gdy proces programu Visual Studio nie może uwierzytelnić się (lub podane poświadczenia są niewystarczające) do procesu zdalnego debugera za pośrednictwem modelu DCOM. Co najmniej jeden z następujących rozwiązań może rozwiązać ten problem:  
  
-   Wyłącz **natywnego trybu zgodności** i **trybu zgodności zarządzanej**.  
  
-   W programie Visual Studio 2013, wyłącz **włączyć natywnego Edytuj i Kontynuuj**.  
  
-   Ponowny rozruch obu komputerów.  
  
-   Jeśli zdalne debugowanie wymaga wprowadzania poświadczeń, zaznacz opcję Zapisz poświadczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)