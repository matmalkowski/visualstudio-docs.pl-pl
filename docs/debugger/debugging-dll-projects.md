---
title: Debugowanie projektów DLL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5118aafae296d839ad182d51b996da11a6bc556
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057401"
---
# <a name="debugging-dll-projects-from-visual-studio"></a>Debugowanie projektów DLL z programu Visual Studio
Następujące szablony programu Visual Studio Utwórz biblioteki DLL:  
  
-   (C++, C# i Visual Basic) Biblioteka klas   

-   (C++): projekt DLL konsoli Win32
  
     Aby uzyskać więcej informacji, zobacz [techniki testowania MFC](../debugger/mfc-debugging-techniques.md).

-   (C++, C# i Visual Basic): biblioteki formant formularzy systemu Windows
  
     Debugowanie Biblioteka formantów formularzy systemu Windows jest podobny do debugowania projektu biblioteki klas. W większości przypadków będzie wywoływać sterowania systemu Windows z innego projektu. Podczas debugowania projektu wywoływania wykonywanie kodu formantu systemu Windows, ustaw punkty przerwania i wykonywać inne operacje debugowania. Aby uzyskać więcej informacji, zobacz [formantów formularzy systemu Windows](/dotnet/framework/winforms/controls/index).  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Tworzenie wersji do debugowania  
 Niezależnie od tego, jak rozpocząć debugowanie upewnij się, najpierw utworzyć biblioteki DLL wersji do debugowania i upewnij się, że wersja do debugowania jest w tej lokalizacji, w którym aplikacja oczekuje go znaleźć. Może to wyglądać oczywista, ale Jeśli zapomnisz ten krok, aplikacja może znaleźć inną wersję biblioteki dll i załaduj go. Program następnie będzie kontynuował pracę, gdy zastanawiasz się, dlaczego nigdy nie został trafiony punkt przerwania. Podczas debugowania, możesz sprawdzić, które biblioteki DLL program został załadowany, otwierając debugera **modułów** okna. **Modułów** okna wyświetla każdy plik DLL lub EXE załadowany w procesie debugowania. Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md).  
 Dla debugera do dołączenia do kodu w języku C++ kod musi wysyłać `DebuggableAttribute`. Można dodać tego kodu automatycznie przez łączenie z [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) — opcja konsolidatora.  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debugowanie w trybie mieszanym  
 Aplikacja wywołująca, która wywołuje biblioteki DLL może być napisane w kodu zarządzanego i kodu natywnego. Jeśli chcesz debugować zarówno sieci zarządzanej biblioteki DLL jest wywoływany przez kod natywny, zarządzane i natywnego debugery zarówno należy włączyć. Można wybrać w  **\<projektu > strony właściwości** lub oknie dialogowym. Jak to zrobić, zależy od tego, czy uruchomić debugowanie z projektu DLL lub wywołującym projekt aplikacji. Aby uzyskać więcej informacji, zobacz [porady: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Zmienianie konfiguracji domyślnej  
 Po utworzeniu projektu aplikacji konsolowej przy użyciu szablonu projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie tworzy wymagane ustawienia konfiguracji Debug i Release. W razie potrzeby możesz zmienić te ustawienia. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [ustawienia projektu C# debugowania konfiguracji](../debugger/project-settings-for-csharp-debug-configurations.md), [ustawienia projektu dla konfiguracji debugowania Visual Basic ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), i [porady: Ustaw wartość Debug i Release konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Sposoby debugowania biblioteki DLL  
 Każdy z projektów w tej sekcji tworzy bibliotekę DLL. Nie można uruchomić biblioteki DLL bezpośrednio; musi zostać wywołany przez aplikację, zwykle EXE. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie projekty Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects). Aplikacja wywołująca mogą mieścić jeden z następujących kryteriów:  
  
-   Aplikacji utworzonej w innym projekcie w tym samym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania zawierającego biblioteki klas.  
  
-   Istniejącą aplikację już wdrożona na komputerze testowym lub produkcyjnym.  
  
-   Znajduje się w sieci Web i dostępne za pośrednictwem adresu URL.  
  
-   Aplikacji sieci Web, która zawiera stronę sieci Web, który osadza plik DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugowanie aplikacji wywołującej  
Aby debugować biblioteki DLL, uruchomić debugowanie aplikacji wywołującej, zwykle albo pliku EXE lub aplikacji sieci Web. Istnieje kilka sposobów jego debugowania.  
  
-   Jeśli projekt aplikacji wywołującej, można otworzyć tego projektu i rozpocząć wykonywania z **debugowania** menu. Aby uzyskać więcej informacji, zobacz [wprowadzenie do debugera](../debugger/getting-started-with-the-debugger.md).  
  
-   Jeśli aplikacja wywołująca jest program istniejący już wdrożona na komputerze testowym lub produkcyjnym i jest już uruchomiona można dołączyć do niego. Użyj tej metody, jeśli biblioteka DLL jest formant obsługiwanych przez program Internet Explorer lub formantu na stronie sieci Web. Aby uzyskać więcej informacji, zobacz [porady: dołączanie do procesu uruchamiania](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
-   Można debugować go z projektu DLL. Aby uzyskać więcej informacji, zobacz [porady: debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   Można debugować go z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [oknie bezpośrednim](#vxtskdebuggingdllprojectstheimmediatewindow). W takim przypadku **Immediate** okna pełni rolę aplikacji.  
  
Przed rozpoczęciem debugowania aplikacji wywołującej, zwykle można ustawić punkt przerwania w bibliotece klas. Aby uzyskać więcej informacji, zobacz [przy użyciu punktów przerwania](../debugger/using-breakpoints.md). Gdy punkt przerwania zostaje trafiony, można przejrzeć kod, obserwowania akcji w każdym wierszu, dopóki nie można ustalić przyczynę problemu. Aby uzyskać więcej informacji, zobacz [Przejdź kodu w debugerze](../debugger/navigating-through-code-with-the-debugger.md).
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> W oknie bezpośrednim  
 Będziesz w stanie ocenić funkcje i metody w bibliotece DLL bez wywoływania aplikacji. Jak debugowanie w czasie projektowania i używasz **Immediate** okna. Aby debugować w ten sposób, wykonaj wykonaj te kroki po otwarciu projektu biblioteki DLL:  
  
1.  Otwórz debuger **Immediate** okna.  
  
2.  Aby przetestować metodę o nazwie `Test` w klasie `Class1`, utworzyć wystąpienia typu obiektu `Class1` przez wpisanie następującego kodu C# w oknie bezpośrednim. Ten kod zarządzany działa Visual Basic i C++, ze zmianami odpowiedniej składni:  
  
    ```cpp
    Class1 obj = new Class1();  
    ```  
  
     W języku C# wszystkie nazwy muszą być w pełni kwalifikowana. Ponadto wszelkie metody lub zmienne, musi być w bieżącym zakresie oraz kontekstu sesji debugowania.  
  
3.  Przy założeniu, że `Test` przyjmuje jeden `int` parametru oceny `Test` przy użyciu **Immediate** okno:  
  
    ```cpp
    ?obj.Test(10)  
    ```  
  
     Wynik będą wypisywane w **Immediate** okna.  
  
4.  Można kontynuować debugowania `Test` umieszczając punkt przerwania w nim, a następnie ponownie obliczania funkcji:  
  
    ```cpp
    ?obj.Test(10);  
    ```  
  
     Punkt przerwania zostanie uruchomiona i będzie można wykonywać krokowo `Test`. Po odejściu wykonywania `Test`, debuger będzie w trybie projektowania.

## <a name="vxtskdebuggingdllprojectsexternal"></a> Debugowanie zewnętrznej biblioteki DLL z projektu C++

Jeśli projekt jest debugowany zewnętrznej biblioteki DLL, funkcje debugowania (takich jak krokowe wykonywanie kodu) będzie zależeć od [konfiguracji debugowania biblioteki dll](#vxtskdebuggingdllprojectsbuildingadebugversion) go został utworzony i czy [plik PDB](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) i innych wymaganych plików dla biblioteki DLL są dostępne.

Projektu musi być w stanie odnaleźć biblioteki DLL i plik PDB używane do debugowania. Można utworzyć zadania niestandardowej kompilacji, aby skopiować te pliki do  **\<folderu projektu > \Debug** folderu wyjściowego, lub skopiować pliki do folderu wyjściowego ręcznie.

Można łatwo ustawić lokalizacje plików *.lib i pliki nagłówkowe na stronach właściwości (kliknij prawym przyciskiem myszy projekt C++ i wybierz polecenie **właściwości widoku**, a następnie wybierz pozycję **wszystkie konfiguracje**) bez konieczności kopiowania je do folderu wyjściowego:

- Folder C/C++ (Kategoria Ogólne) — określ folder zawierający pliki nagłówkowe w **dodatkowe katalogi dołączenia** pola.
- Folder konsolidatora (Kategoria Ogólne) — określ folder zawierający plik lib w **dodatkowe katalogi bibliotek** pola. 
- Folder konsolidatora (dane wejściowe kategoria) — określ pełną ścieżkę i nazwę pliku lib w **dodatkowe zależności** pola.

Jeśli konfiguracja jest prawidłowa, można debugować przez uruchomienie wykonywania z **debugowania** menu.

Aby uzyskać więcej informacji na temat ustawień projektu, zobacz [strony właściwości (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Typy projektów Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F # i typy projektów Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ustawienia projektu dla konfiguracji debugowania z C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Konfiguracje debugowania ustawienia projektu w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
