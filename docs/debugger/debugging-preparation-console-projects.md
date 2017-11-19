---
title: "Przygotowanie debugowania: Konsoli projektów | Dokumentacja firmy Microsoft"
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
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c4b5021db951acc6ed8ed750542febab9fdfbf4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-preparation-console-projects"></a>Przygotowanie debugowania: projekty konsoli
Trwa przygotowywanie do debugowania projektu konsoli jest podobny do przygotowywanie do debugowania z kilka dodatkowych kwestii dotyczących projektu systemu Windows. Aby uzyskać więcej informacji, zobacz [aplikacjach formularzy systemu Windows](../debugger/debugging-preparation-windows-forms-applications.md), i [przygotowanie debugowania: aplikacje formularzy systemu Windows (.NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Z powodu podobieństwa wszystkich aplikacji konsoli w tym temacie omówiono następujące typy projektu:  
  
-   Aplikacji Konsolowej C#  
  
-   Aplikację konsoli języka Visual Basic  
  
-   Aplikację konsoli języka C++ (.NET)  
  
-   Aplikację konsoli języka C++ (Win32)  
  
 Należy określić argumenty wiersza polecenia dla aplikacji konsoli. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), lub [ustawienia projektu C# debugowania konfiguracji ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
 Np. wszystkie właściwości projektu, tych argumentów zachowywane między sesjami debugowania i między sesjami programu Visual Studio. W związku z tym w przypadku aplikacji konsoli, który ma zostać wcześniej debugowania, pamiętaj, że mogą być argumentami z poprzedniej sesji w  **\<projektu > strony właściwości** okno dialogowe.  
  
 Korzysta z aplikacji konsoli **konsoli** okna do przyjmowania danych wejściowych i mają być wyświetlane komunikaty wyjściowe. Można zapisać do **konsoli** okna, aplikacja musi używać **konsoli** obiektu zamiast obiektu debugowania. Można zapisać do **programu Visual Studio dane wyjściowe** okna, użyj obiektu debugowania w zwykły sposób. Pamiętaj, że wiesz, gdzie jest pisanie aplikacji lub może być szukasz komunikatów w niewłaściwym miejscu. Aby uzyskać więcej informacji, zobacz [klasy konsoli](/dotnet/api/system.console), [klasy Debug](/dotnet/api/system.diagnostics.debug), i [okno danych wyjściowych](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Uruchamianie aplikacji  
 Po uruchomieniu niektórych aplikacji konsoli, aby zostały wykonane, a następnie zamknij. To zachowanie może nie zapewniają wystarczająco dużo czasu na Przerwij wykonywanie i debugowania. Aby można było do debugowania aplikacji, użyj jednej z poniższych procedur można uruchomić aplikacji:  
  
-   Aplikacja rozpoczyna wykonywanie i działa, dopóki nie osiągnie punkt przerwania.  
  
-   Natychmiast podziały wierszy w pierwszym wierszu kodu źródłowego aplikacji i uruchamia.  
  
-   W oknie Kod źródłowy, kliknij prawym przyciskiem myszy linię, a następnie wybierz **Uruchom do kursora**.  
  
     Aplikacja rozpoczyna się i uruchamia wybranego wiersza lub punkt przerwania, gdy punkt przerwania zostaje trafiony przed wierszem.  
  
 Podczas debugowania aplikacji konsoli można uruchomić aplikacji z wiersza polecenia, a nie z programu Visual Studio. W takim przypadku można uruchomić aplikacji z wiersza polecenia i dołączyć debuger programu Visual Studio do niego. Aby uzyskać więcej informacji, zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Po uruchomieniu aplikacji konsoli w programie Visual Studio, **konsoli** czasami okno za oknem programu Visual Studio. Jeśli użytkownik próbuje uruchomić aplikację konsoli w programie Visual Studio i nic może mieć miejsce, spróbuj przenieść okno programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Typy projektów Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F # i typy projektów Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ustawienia projektu dla konfiguracji debugowania z C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)