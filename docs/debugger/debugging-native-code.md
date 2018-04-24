---
title: Debugowanie kodu natywnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: f57f1e559452c64f9f1a7b019d75b52384081d65
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-native-code"></a>Debugowanie kodu natywnego
Sekcji opisano niektóre typowe problemy debugowania i techniki natywnych aplikacji. Techniki omówione w tej sekcji są techniki wysokiego poziomu. Aby mechanika za pomocą debugera programu Visual Studio, zobacz [plan debugera](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md)  
 Zapewnia wskazówki dotyczące debugowanie kodzie zoptymalizowanym, w szczególności, dlatego należy debugowania zoptymalizowanego wersji z programu, domyślne ustawienia optymalizacji konfiguracje Debug i Release i porady dotyczące znajdowania usterki, które są wyświetlane tylko w zoptymalizowanym kodzie (włączenie Optymalizacja w konfiguracji kompilacji debugowania).  
  
 [DebugBreak i __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 W tym artykule opisano Win32 `DebugBreak` funkcji i Link do jego temat referencyjny w zestawie SDK platformy. Opisano również `__debugbreak` wewnętrznej.  
  
 [Potwierdzenia C/C++](../debugger/c-cpp-assertions.md)  
 W tym artykule omówiono instrukcji potwierdzania, jak działają, korzystanie z nich (połowowe błędy logiczne, sprawdzanie wyniki operacji i testowania warunki błędów), ich interakcji z `_DEBUG`oraz typy potwierdzeń obsługiwane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Porady: debugowanie kodu zestawu wbudowanego](../debugger/how-to-debug-inline-assembly-code.md)  
 Zawiera krótkie instrukcje dotyczące używania dezasemblacja, okno, aby wyświetlić instrukcje zestawu i z okna rejestrów, aby wyświetlić zawartość rejestru oraz linki do tematów dotyczących tych systemu windows.  
  
 [Techniki testowania MFC](../debugger/mfc-debugging-techniques.md)  
 Łącza do debugowania techniki programy MFC, w tym: afxdebugbreak —, TRACE — makro, wykrywanie pamięci przecieków w MFC, MFC potwierdzeń i zmniejszenie rozmiaru MFC debugowania kompilacji.  
  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)  
 Sterta debugowania łącza do debugowania techniki biblioteki C Run-Time, łącznie z biblioteki debugowania CRT, makra dla raportowania, różnice między — funkcja malloc i _malloc_dbg —, zapisywanie debugowanie funkcji punktów zaczepienia i CRT.  
  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)  
 Zawiera odpowiedzi na często zadawane pytania dotyczące debugowania programów Visual C++  
  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)  
 Zawiera informacje dotyczące debugowania aplikacji modelu COM i ActiveX, w tym narzędzia, których można użyć dla modelu COM i debugowanie ActiveX.  
  
 [Porady: debugowanie wprowadzonego kodu](../debugger/how-to-debug-injected-code.md)  
 Zawiera wskazówki dotyczące debugowanie kodu, który używa atrybutów. Instrukcje zawierają włączanie adnotacji źródła, jak wyświetlić wprowadzony kod i sposób wyświetlania kodu dezasemblacji w bieżącym punkcie wykonywania.  
  
 [Wskazówki: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Informacje dotyczące używania **zadań równoległych** i **stosów równoległych** narzędzia systemu windows do debugowania aplikacji równoległych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Zawiera łącza do tematów opisujących sposób debugowania natywnego projektu typy utworzone przez Szablony projektów Visual C++.  

 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md) zawiera informacje dotyczące debugowania natywnego i zarządzanego biblioteki dll.
  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)  
 Zawiera łącza do większych sekcji debugowania. Informacje obejmują, co jest nowego w debugerze, ustawienia i przygotowanie, punkty przerwania, obsługa wyjątków, Edytuj i Kontynuuj, debugowanie zarządzanego kodu, debugowanie kodu natywnego, debugowania SQL i odwołania do interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)  
 [Debugowanie w programie Visual Studio](../debugger/index.md) [debugera samouczek funkcji](../debugger/debugger-feature-tour.md)