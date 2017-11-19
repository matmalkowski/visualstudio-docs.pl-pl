---
title: 'Porady: debugowanie z projektu DLL | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 05/24/2017
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
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 371c48282b2f775833287046ed9810f0cbc8f69e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>Porady: debugowanie z projektu DLL w programie Visual Studio
Jednym ze sposobów debugowania projektu biblioteki DLL jest określenie aplikacja wywołująca we właściwościach projektu z projektu DLL, a następnie Rozpocznij debugowanie z projektu DLL. Dla tej metody do pracy, aplikacja musi wywołać DLL i biblioteki DLL musi być w tej lokalizacji, w którym aplikacja oczekuje znajdź go (w przeciwnym razie aplikacja może znaleźć inną wersję biblioteki dll i obciążenia, który zamiast tego, a nie osiągnęła punkty przerwań). Debugowanie bibliotek DLL innych metod, zobacz [debugowanie projektów DLL](../debugger/debugging-dll-projects.md).
  
Jeśli chcesz debugować zarówno zarządzanej biblioteki DLL jest wywoływany przez kod natywny, można określić to we właściwościach projektu. Aby uzyskać więcej informacji, zobacz [porady: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).   

Strony właściwości C++ różnią się układ i zawartość z C# i Visual Basic strony właściwości. 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Aby określić aplikacja wywołująca w projektach C++  
  
1.  Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
2.  Upewnij się, że **konfiguracji** ma ustawioną wartość pola w górnej części okna **debugowania**. 

    A **debugowania** konfiguracja jest wymagana dla tej metody. 
  
3.  Przejdź do **właściwości konfiguracji > debugowanie**.  
  
4.  W **debugera, aby uruchomić** wybierz **lokalnego debugera systemu Windows** lub **zdalnego debugera systemu Windows**.  
  
5.  W **polecenia** lub **polecenia zdalnego** Dodaj nazwę w pełni kwalifikowaną ścieżkę aplikacji wywołującej (na przykład plik .exe).

    ![Debugowanie w oknie właściwości](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  Dodaj wszelkie niezbędne program argumenty **argumenty polecenia** pole.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Aby określić aplikacja wywołująca w projekcie języka C# lub Visual Basic  
  
1.  Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**, a następnie wybierz **debugowania** kartę.

2.  Upewnij się, że **konfiguracji** ma ustawioną wartość pola w górnej części okna **debugowania**.

3.  (.NET framework) Wybierz **uruchomienia programu zewnętrznego**, a następnie dodaj nazwę w pełni kwalifikowaną ścieżkę aplikacji wywołującej.

4.  (.NET core) Wybierz **plik wykonywalny** z **uruchamianie** listy, a następnie dodaj nazwę w pełni kwalifikowaną ścieżkę aplikacja wywołująca w **plik wykonywalny** pola. 
  
     Jeśli konieczne jest dodanie argumenty wiersza polecenia programu zewnętrznego, dodaj je w **argumenty wiersza polecenia** (lub **argumenty aplikacji**) pola.

    ![Debugowanie w oknie właściwości](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  Jeśli chcesz, możesz także wywołać jako adres URL aplikacji. (Można to zrobić w przypadku debugowania zarządzanej biblioteki DLL używane przez lokalne aplikacji ASP.NET.)  
  
     W obszarze **Akcja uruchamiania**, wybierz pozycję **Start przeglądarki z adresem URL:** przycisk radiowy, a następnie wprowadź adres URL.
  
### <a name="to-start-debugging-from-the-dll-project"></a>Aby rozpocząć debugowanie z projektu DLL  
  
1.  Ustaw punkty przerwania w projekcie biblioteki DLL. 

2.  Kliknij prawym przyciskiem myszy projektu biblioteki DLL i wybierz polecenie **Ustaw jako projekt startowy**. 

    (Upewnij się również, że **konfiguracji rozwiązania** pole nadal jest ustawione na **debugowania**.)   
  
3.  Rozpocznij debugowanie (naciśnij klawisz F5, kliknij zieloną strzałkę lub **Debuguj > Rozpocznij debugowanie**).

    Nastąpi trafienie punktów przerwania w bibliotece DLL. Jeśli użytkownik nie ma trafień punktów przerwania, upewnij się, że dane wyjściowe biblioteki DLL (domyślnie **project\Debug** folder) jest w lokalizacji, że aplikacja wywołująca zamierza go znaleźć.
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)   
 [Konfiguracje debugowania ustawienia projektu w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Ustawienia projektu dla konfiguracji debugowania z C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)