---
title: 'Porady: Użyj macierzystego sprawdzania w trakcie wykonywania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6d47b39086f0363bd0bc610ec047213142fb7fec
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-native-run-time-checks"></a>Porady: Korzystanie z macierzystego sprawdzania w trakcie wykonywania
W programie Visual C++, można użyć natywnego [runtime_checks](/cpp/preprocessor/runtime-checks) do wychwytywania typowych błędów czasu wykonywania, takie jak:  
  
-   Uszkodzenie wskaźnika stosu.  
  
-   Przepełnienia tablice lokalnego.  
  
-   Uszkodzenie stosu.  
  
-   Zależności w niezainicjowanych zmiennych lokalnych.  
  
-   Utrata danych na przypisanie do zmiennej krótszy.  
  
 Jeśli używasz **/RTC** z zoptymalizowane (**/O**) kompilacji, wyniki błąd kompilatora. Jeśli używasz `runtime_checks` pragma w optymalizowania kompilacji pragmy nie ma wpływu.  
  
 Podczas debugowania program, który ma włączoną sprawdzania w trakcie wykonywania, domyślna akcja jest do zatrzymywania i Przerwij do debugera, gdy wystąpi błąd czasu wykonywania programu. Można zmienić to zachowanie domyślne dla każdej kontroli czasu wykonywania. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Poniższych procedurach opisano sposób włączania macierzystego sprawdzania w trakcie wykonywania kompilacji debugowania i sposobu modyfikowania zachowania macierzystego sprawdzania czasu wykonywania.  
  
 Inne tematy w tej sekcji zawierają informacje o:  
  
-   [Dostosowywanie środowiska wykonawczego sprawdza z biblioteki wykonawczej języka C](../debugger/native-run-time-checks-customization.md)  
  
-   [Sprawdza przy użyciu czasu wykonywania bez biblioteki wykonawczej języka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Aby włączyć macierzystego sprawdzania w trakcie wykonywania kompilacji debugowania  
  
-   Użyj **/RTC** opcja i Połącz z biblioteką debugowania wersja biblioteki wykonawczej języka C (/ MDd, na przykład).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Aby zmodyfikować zachowanie macierzystego sprawdzania czasu wykonywania  
  
-   Użyj `runtime_checks` pragma.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [Sprawdzanie błędów czasu wykonywania](/cpp/c-runtime-library/run-time-error-checking)