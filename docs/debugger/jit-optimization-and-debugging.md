---
title: JIT Optymalizacja i debugowanie | Dokumentacja firmy Microsoft
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
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2c3dcd57568bdfaac3ba0f7aff33cefca8a0ee32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="jit-optimization-and-debugging"></a>Optymalizacja i debugowanie JIT
Podczas debugowania aplikacji zarządzanej, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] domyślnie powoduje pominięcie optymalizacji kodu just-in-time (JIT). Pomijanie JIT optymalizacji oznacza, że są debugowanie kodu nie są zoptymalizowane. Kod uruchamia się nieco wolniej, ponieważ nie jest zoptymalizowana, ale środowiska debugowania jest znacznie bardziej szczegółowego. Debugowanie zoptymalizowanego kodu trudniej i zalecane tylko, jeśli wystąpią usterkę, która występuje w zoptymalizowanym kodzie, ale nie można odtworzyć w wersji nie są zoptymalizowane.  
  
 Optymalizację JIT jest kontrolowany w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przez **Pomiń optymalizację JIT podczas ładowania modułu** opcji. Tej opcji można znaleźć na **ogólne** w obszarze **debugowanie** w węźle **opcje** okno dialogowe.  
  
 Jeśli wyczyścisz **Pomiń optymalizację JIT podczas ładowania modułu** opcji można debugowania zoptymalizowanego kodu JIT, ale może być ograniczony możliwość debugowania, ponieważ kod zoptymalizowany nie pasuje do kodu źródłowego. W związku z tym debugera systemu windows, takich jak **zmiennych lokalnych** i **automatycznych** okna mogą nie wyświetlać te informacje, jak gdyby zostały debugowanie kodu nie są zoptymalizowane.  
  
 Debugowanie za pomocą tylko mój kod innego dotyczy istotną różnicą. Jeśli debugowania tylko mój kod, debuger uwzględnia zoptymalizowanego kodu za kod niezwiązany z użytkownikiem, który nie powinny być wyświetlane podczas debugowania. W związku z tym jeśli są debugowanie JIT zoptymalizowany kod, prawdopodobnie chcesz wyłączyć opcję tylko mój kod. Aby uzyskać więcej informacji, zobacz [Ogranicz wykonywanie krok po kroku, aby tylko mój kod](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Należy pamiętać, że **Pomiń optymalizację JIT podczas ładowania modułu** opcja powoduje pominięcie optymalizacji kodu po załadowaniu modułów. Możesz dołączyć do procesu, który jest już uruchomiony, mogą zawierać kod, który jest już załadowany, kompilacji JIT i zoptymalizowane. **Pomiń optymalizację JIT podczas ładowania modułu** opcji nie ma wpływu na taki kod, mimo że będzie miało wpływ na modułów, które są ładowane po dołączeniu. Ponadto **Pomiń optymalizację JIT podczas ładowania modułu** opcji nie ma wpływu na moduły, na przykład WinForms.dll, które są tworzone za pomocą narzędzia NGEN.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proces zarządzanego wykonania](/dotnet/standard/managed-execution-process)