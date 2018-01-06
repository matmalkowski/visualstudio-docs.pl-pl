---
title: "Jak można debugować funkcje API systemu Windows? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 66ed3dbd6c67fe247ea514a9d41780584ae8f1e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak można debugować funkcje API systemu Windows?
Jeśli chcesz debugować funkcji interfejsu API systemu Windows, która ma załadować symbole NT, wykonaj następujące czynności.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Aby ustawić punkt przerwania w funkcji interfejsu API systemu Windows przy użyciu symboli NT załadowany  
  
-   Wprowadź nazwę funkcji, łącznie z nazwą biblioteki DLL, w której znajduje się funkcja. W 32-bitowy kod formularz ozdobione nazwy funkcji. Aby ustawić punkt przerwania na **MessageBeep**, na przykład, musisz wprowadzić następujące.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Aby uzyskać nazwa, zobacz [wyświetlanie nazwy dekorowane](http://msdn.microsoft.com/en-us/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)