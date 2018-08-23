---
title: Debugowanie kodu natywnego | Dokumentacja firmy Microsoft
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
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a4c8d5c19ea397f8fc23a962a045645740a1164
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632569"
---
# <a name="debugging-native-code"></a>Debugowanie kodu natywnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [debugowanie kodu natywnego](https://docs.microsoft.com/visualstudio/debugger/debugging-native-code).  
  
Sekcji omówiono niektóre typowe problemy z debugowania i technik dla natywnych aplikacji. Technik opisanych w tej sekcji są techniki wysokiego poziomu. Mechanika przy użyciu debugera programu Visual Studio, można zobaczyć [plan debugera](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md)  
 Zawiera wskazówki dotyczące debugowania zoptymalizowane pod kątem kodu, w szczególności dlatego powinna debugowania niezoptymalizowanym wersję usługi programu, domyślne ustawienia pozycji Optymalizacja konfiguracji Debug i Release i porady dotyczące znajdowania błędów, które są wyświetlane tylko w zoptymalizowanym kodzie (włączenie Optymalizacja w konfiguracji kompilacji debugowania).  
  
 [DebugBreak i __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 W tym artykule opisano Win32 `DebugBreak` funkcji i Link do jego temat referencyjny w zestawie SDK platformy. Opisano również `__debugbreak` wewnętrzne.  
  
 [Potwierdzenia C/C++](../debugger/c-cpp-assertions.md)  
 W tym artykule omówiono instrukcji potwierdzania, jak to działa, zalety korzystania z nich (połowowe błędy logiczne, sprawdzanie wyników operacji i testowanie warunki błędu), ich interakcji z `_DEBUG`oraz typy potwierdzenia obsługiwane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 [Porady: debugowanie kodu zestawu wbudowanego](../debugger/how-to-debug-inline-assembly-code.md)  
 Zawiera instrukcje na temat korzystania z okna dezasemblacji Aby wyświetlić instrukcje zestawu i z okna rejestrów, aby wyświetlić zawartość rejestru i zawiera łącza do tematów dotyczących tych oknach.  
  
 [Techniki testowania MFC](../debugger/mfc-debugging-techniques.md)  
 Podano łącza do debugowania programów MFC, łącznie z: afxdebugbreak —, TRACE — makro, wykrywanie pamięci przecieki w MFC, MFC, asercje i zmniejszenie rozmiaru debugowania MFC kompilacji.  
  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)  
 Łącza do debugowania dla biblioteki wykonawczej C, w tym o korzystaniu z biblioteki debugowania CRT, makra dla raportowania, różnice funkcji malloc i _malloc_dbg, pisanie debugowanie funkcji punktów zaczepienia i CRT debugowania sterty.  
  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)  
 Zawiera odpowiedzi na często zadawane pytania dotyczące debugowania programów Visual C++  
  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)  
 Zawiera informacje dotyczące debugowania aplikacji modelu COM i ActiveX, w tym narzędzia, których można używać dla modelu COM i debugowanie ActiveX.  
  
 [Porady: debugowanie natywnych bibliotek DLL](../debugger/how-to-debug-native-dlls.md)  
 Wyjaśnia, jak skonfigurować debugowanie bibliotek DLL z kodu natywnego.  
  
 [Porady: debugowanie wprowadzonego kodu](../debugger/how-to-debug-injected-code.md)  
 Wskazówki dotyczące debugowania kodu, który używa atrybutów. Instrukcje zawierają włączanie adnotacji źródła, jak wyświetlić wprowadzonego kodu i sposób wyświetlić kod dezasemblacji w bieżącym punkcie Wykonywanie.  
  
 [Wskazówki: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Opisuje sposób używania **zadań równoległych** i **stosów równoległych** narzędzia systemu windows do debugowania aplikacji równoległej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Zawiera łącza do tematów opisujących sposób debugowania natywnego projektu typów, utworzone przez Szablony projektów Visual C++.  
  
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)  
 Zawiera łącza do większych sekcji dokumentacji debugowania. Informacje dotyczące nowości w debugerze, ustawienia i przygotowania, punkty przerwania, obsługa wyjątków, Edytuj i Kontynuuj, debugowanie kodu zarządzanego, debugowanie kodu natywnego, debugowanie SQL i odwołania interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)



