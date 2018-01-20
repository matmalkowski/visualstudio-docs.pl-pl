---
title: Debugowanie kontrolki WebView (UWP) | Dokumentacja firmy Microsoft
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
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 8c463bc443540e136b2cffd1a4abdda2cc543d05
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Debugowanie kontrolki WebView w aplikacji platformy uniwersalnej systemu Windows
  
 Do przeglądania i debugowania `WebView` formantów w aplikacji środowiska wykonawczego systemu Windows, można skonfigurować programu Visual Studio można dołączyć debugera skryptów po uruchomieniu aplikacji. Użytkownik ma dwa sposoby interakcji z `WebView` steruje korzystanie z debugera:  
  
-   Otwórz [Eksploratora modelu DOM](../debugger/quickstart-debug-html-and-css.md) dla `WebView` wystąpienia i sprawdź elementy modelu DOM, badania problemów stylów CSS i przetestowania dynamicznie renderowanych zmiany do stylów.  
  
-   Wybierz stronę sieci Web lub `iFrame` wyświetlane w `WebView` wystąpienia jako cel w [konsoli JavaScript](../debugger/javascript-console-commands.md) okna, a następnie współdziałał z strony sieci Web za pomocą konsoli poleceń. Konsolę zapewnia dostęp do bieżącego kontekstu wykonywania skryptu.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Dołącz debuger (C#, VB, C++)  
  
1.  W programie Visual Studio, Dodaj `WebView` formantu do aplikacji środowiska wykonawczego systemu Windows.  
  
2.  W Eksploratorze rozwiązań Otwórz właściwości projektu, wybierając **właściwości** z menu skrótów dla projektu.  
  
3.  Wybierz **debugowania**. W **procesu aplikacji** wybierz **skryptu**.  
  
     ![Dołącz debuger skryptu](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Opcjonalnie) Wersje-Express programu Visual Studio można wyłączyć debugowanie just-in-time (JIT), wybierając **Narzędzia > Opcje > debugowanie > Just In Time**, i następnie wyłączenie JIT debugowanie skryptu.  
  
    > [!NOTE]
    >  Debugowanie JIT jest wyłączona, można ukryć okien dialogowych służących do nieobsługiwanych wyjątków pojawiające się na kilka stron sieci Web. W programie Visual Studio Express debugowanie JIT zawsze jest wyłączona.  
  
5.  Naciśnij klawisz F5, aby rozpocząć debugowania.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Skorzystaj z Eksploratora modelu DOM do przeglądania i debugowanie kontrolki WebView  
  
1.  (C#, VB, C++) Dołącz debugera skryptów do aplikacji. Zobacz sekcję pierwszą, aby uzyskać instrukcje.  
  
2.  Jeśli nie jest jeszcze Dodaj `WebView` kontroli do aplikacji i naciśnij klawisz F5, aby rozpocząć debugowania.  
  
3.  Przejdź do strony `Webview` doświadczeniach kontrolnych.  
  
4.  Otwórz okno Eksploratora DOM dla `WebView` kontroli, wybierając **debugowania**, **Windows**, **Eksploratora modelu DOM**, a następnie wybierz adres URL `WebView` że Czy chcesz sprawdzić.  
  
     ![Otwieranie Eksploratora modelu DOM](../debugger/media/js_dom_webview.png "JS_DOM_WebView")  
  
     W Eksploratorze DOM skojarzone z `WebView` pojawia się jako nową kartę w programie Visual Studio.  
  
5.  Wyświetlanie i modyfikowanie na żywo elementy modelu DOM i style CSS, zgodnie z opisem w [stylów CSS debugowania przy użyciu Eksploratora modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Korzystanie z okna konsoli języka JavaScript do przeglądania i debugowanie kontrolki WebView  
  
1.  (C#, VB, C++) Dołącz debugera skryptów do aplikacji. Zobacz sekcję pierwszą, aby uzyskać instrukcje.  
  
2.  Jeśli nie jest jeszcze Dodaj `WebView` kontroli do aplikacji i naciśnij klawisz F5, aby rozpocząć debugowania.  
  
3.  Otwieranie okna konsoli języka JavaScript dla `WebView` kontroli, wybierając **debugowania**, **Windows**, **konsoli JavaScript**.  
  
     Zostanie wyświetlone okno konsoli JavaScript.  
  
4.  Przejdź do strony `Webview` doświadczeniach kontrolnych.  
  
5.  W oknie konsoli wybierz stronę sieci Web lub `iFrame` wyświetlanych przez `WebView` kontroli w **docelowej** listy.  
  
     ![Docelowa zaznaczenia w oknie konsoli JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Za pomocą konsoli, pozwala na interakcję z pojedynczym `WebView`, `iFrame`, udostępnić kontraktu lub procesu roboczego w sieci web w czasie. Każdy element wymaga oddzielnego wystąpienia hosta platformy sieci web (WWAHost.exe). Możliwość interakcji z jednego hosta, w czasie.  
  
6.  Wyświetl i Modyfikuj zmienne w aplikacji lub użyj polecenia konsoli, zgodnie z opisem w [Szybki Start: debugowanie JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) i [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)