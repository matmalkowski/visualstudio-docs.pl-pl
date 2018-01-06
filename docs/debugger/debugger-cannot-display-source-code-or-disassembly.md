---
title: "Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8795ee33a5fc96c979cb67636d3ce5dd23c1b665
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
Odczytuje ten błąd:  
  
 Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji dla bieżącej lokalizacji, gdzie wykonywanie zostało zatrzymane.  
  
 Ten komunikat o błędzie może wystąpić z kilku powodów:  
  
-   Może mieć trafień punktu przerwania w lokalizacji, dla której nie ma żadnego kodu źródłowego podczas debugowania języka, który nie obsługuje dezasemblacji. Otwórz **punktów przerwania** okna, zlokalizuj punkt przerwania i usuń go.  
  
-   Jeśli debugowania skryptu, może osiągnięto punkt przerwania, gdy nie było żadnych wątków programu. Wybierz **krok** lub **Kontynuuj** z **debugowania** menu, aby wznowić debugowania.  
  
-   Zagadnienia dotyczące zabezpieczeń mógł zostać debugera z odczytu stosu wątku, rejestru i inne informacje o kontekście z debugowany program. Jest to najbardziej prawdopodobne, jeśli są debugowanie aplikacji sieci Web i nie masz odpowiedniego uprawnienia dostępu do katalogu wirtualnego. Ustaw zabezpieczenia dla katalogu wirtualnego anonimowy, a następnie spróbuj ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md) [debugera samouczek funkcji](../debugger/debugger-feature-tour.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)