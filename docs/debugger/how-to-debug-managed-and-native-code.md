---
title: 'Samouczek: Debugowanie kodu zarządzanego i natywnego (tryb mieszany)'
description: Dowiedz się, jak można debugować natywnej biblioteki DLL z aplikacji .NET Core lub .NET Framework za pomocą debugowania w trybie mieszanym
ms.custom: ''
ms.date: 04/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 96634ddabdf955fd969d9c004c6d3b83d1e56a92
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255197"
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>Samouczek: Debugowanie kodu zarządzanego i natywnego w programie Visual Studio

Program Visual Studio umożliwia włączenie więcej niż jeden typ debugera podczas debugowania, która jest wywoływana debugowanie w trybie mieszanym. W tym samouczku ustawieniu opcji debugowania kodu zarządzane i natywne w jednej sesji debugowania. Ten samouczek pokazuje, jak można debugować kodu natywnego z zarządzanej aplikacji, ale można też wykonać odwrotna i [debugowania kodu zarządzanego z aplikacji natywnej](../debugger/how-to-debug-in-mixed-mode.md). Debuger obsługuje również inne rodzaje debugowanie w trybie mieszanym, takich jak debugowanie [Python i kod natywny](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) i korzystanie z debugera skryptów w typach aplikacji, takich jak ASP.NET.

W tym samouczku obejmują:

> [!div class="checklist"]
> * Tworzenie prostego natywnej biblioteki DLL
> * Tworzenie prostej aplikacji .NET Core lub .NET Framework do wywoływania biblioteki DLL
> * Uruchom debuger
> * Trafiony punkt przerwania w aplikacji zarządzanej
> * Wykonywanie kodu natywnego

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć zainstalowanego programu Visual Studio i **tworzenia klasycznych aplikacji w języku C++** obciążenia.

    Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

    Jeśli musisz zainstalować obciążenie, ale jeszcze programu Visual Studio, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **programowanie Node.js** obciążenia, a następnie wybierz **Modyfikuj**.

* Musi mieć również albo **tworzenia klasycznych aplikacji .NET** obciążenia lub **.NET Core cross platform programowanie** obciążenia zainstalowane, w zależności od typu aplikacji, które chcesz utworzyć.

## <a name="create-a-simple-native-dll"></a>Tworzenie prostego natywnej biblioteki DLL

1. W programie Visual Studio, wybierz **pliku** > **nowy** > **projektu**.

1. W **nowy projekt** oknie dialogowym wybierz **Visual C++**, **ogólne** z sekcji zainstalowane szablony, a następnie w środkowym okienku wybierz **pustego projektu** .

1. W **nazwa** wpisz **debugowanie tryb mieszany** i kliknij przycisk **OK**.

    Program Visual Studio tworzy pusty projekt, który jest wyświetlany w Eksploratorze rozwiązań w okienku po prawej stronie.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **pliki źródłowe** węzła w języku C++ projektu, a następnie wybierz pozycję **Dodaj** > **nowy element**, a następnie wybierz **C++ plik (.cpp)**. Nadaj nazwę plikowi **Mixed Mode.cpp**i wybierz polecenie **Dodaj**.

    Visual Studio dodaje nowy plik C++.

1. Skopiuj następujący kod do *Mixed Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **pliki nagłówkowe** węzła w języku C++ projektu, a następnie wybierz pozycję **Dodaj** > **nowy element**, a następnie wybierz  **Plik nagłówków (.h)**. Nadaj nazwę plikowi **Mixed Mode.h**i wybierz polecenie **Dodaj**.

    Visual Studio dodaje nowy plik nagłówka.

1. Skopiuj następujący kod do *Mixed Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
        __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
            return a * b;
        }
    }
    #endif
    ```

1. Na pasku narzędzi debugowania wybierz **debugowania** konfiguracji i **Any CPU** jako platformy, lub dla platformy .NET Core, wybierz **x64** jako platformę.

    > [!NOTE]
    > Na .NET Core wybierz **x64** jako platformę. Oprogramowanie .NET core zawsze działa w trybie 64-bitowym, więc jest to wymagane.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu (**debugowanie tryb mieszany**) i wybierz polecenie **właściwości**.

1. W **właściwości** wybierz pozycję **właściwości konfiguracji** > **konsolidatora** > **zaawansowane**, i następnie w **punkt wejścia nie** listy rozwijanej wybierz **nr**. Następnie Zastosuj ustawienia.

1. W **właściwości** wybierz pozycję **właściwości konfiguracji** > **ogólne**, a następnie wybierz **dynamicznej biblioteki (.dll)** z **typu konfiguracji** pola. Następnie Zastosuj ustawienia.

    ![Przełącz się do natywnej biblioteki DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Kliknij prawym przyciskiem myszy projekt i wybierz polecenie **debugowania** > **kompilacji**.

    Projekt powinien być kompilowany bez błędów.

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>Tworzenie prostej aplikacji .NET Framework lub .NET Core do wywoływania biblioteki DLL

1. W programie Visual Studio, wybierz **pliku** > **nowy** > **projektu**.

1. Wybierz szablon dla kodu aplikacji.

    Dla programu .NET Framework w **nowy projekt** okno dialogowe Wybierz **Visual C#**, **Windows Desktop** z sekcji zainstalowane szablony, a następnie w środkowym okienku wybierz  **Konsoli aplikacji (.NET Framework)**.

    Dla platformy .NET Core w **nowy projekt** oknie dialogowym wybierz **Visual C#**, **.NET Core** z sekcji zainstalowane szablony, a następnie w środkowym okienku wybierz  **Konsoli aplikacji (.NET Core)**.

1. W **nazwa** wpisz **Mixed_Mode_Calling_App** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt konsoli, która jest wyświetlana w Eksploratorze rozwiązań w okienku po prawej stronie.

1. W *Program.cs*, Zastąp domyślny kod następującym kodem:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed-Mode-Debugging\x64\Debug\Mixed-Mode-Debugging.dll
            // Here, we show a typical path for a DLL targeting the **Any CPU** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed-Mode-Debugging\Debug\Mixed-Mode-Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="configure-mixed-mode-debugging-net-framework"></a>Konfiguruj debugowanie (.NET Framework) w trybie mieszanym

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy zarządzanej **Mixed_Mode_Calling_App** projekt i wybierz pozycję **Ustaw jako projekt startowy**.

1. Kliknij prawym przyciskiem myszy zarządzanej **Mixed_Mode_Calling_App** projektu, a następnie wybierz pozycję **właściwości**, a następnie wybierz pozycję **debugowania** w okienku po lewej stronie. Wybierz **Włącz debugowanie kodu natywnego**, a następnie zamknij stronę właściwości, aby zapisać zmiany.

    ![Włącz debugowanie w trybie mieszanym](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>Konfigurowanie trybu mieszanego debugowania (.NET Core)

W większości wersji programu Visual Studio 2017, musisz włączyć debugowanie w trybie mieszanym dla natywnego kodu w aplikacji platformy .NET Core za pomocą *launchSettings.json* plików zamiast **właściwości** strony. Aby śledzić aktualizacje interfejsu użytkownika dla tej funkcji, zobacz [problem GitHub](https://github.com/dotnet/project-system/issues/1125).

1. Otwórz *launchSettings.json* w pliku *właściwości* folderu. Domyślnie plik znajduje się w tej lokalizacji.

    *C:\Users\<nazwa użytkownika > \source\repos\Mixed_Mode_Calling_App\Properties*

    Jeśli plik nie jest obecny, otwórz właściwości projektu (kliknij prawym przyciskiem myszy zarządzanej **Mixed_Mode_Calling_App** projekt w Eksploratorze rozwiązań i wybierz **właściwości**). Tymczasowe zmiany w **debugowania** karcie i skompilowanie projektu. Przywróć wprowadzone zmiany.

1. W *lauchsettings.json* plików, Dodaj następujące właściwości:

    ```
    "nativeDebugging": true
    ```

    Tak na przykład plik może wyglądać następujące czynności:

    ```
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustaw punkt przerwania i uruchomienia debugera

1. W języku C# projektu, otwórz *Program.cs* i ustaw punkt przerwania w następującym wierszu kodu, klikając na lewym marginesie:

    ```csharp
    int result = Multiply(7, 7);
    ```

    Czerwone koło pojawi się na lewym marginesie, aby wskazać, że ustawiono punktu przerwania.

1. Naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**) można uruchomić debugera.

    Debuger wstrzymuje punkt przerwania, które można ustawić. Żółta strzałka wskazuje, gdzie debugera jest obecnie wstrzymana.

## <a name="step-into-native-code"></a>Wykonywanie kodu natywnego

1. Gdy wstrzymana w aplikacji zarządzanej, naciśnij klawisz **F11** (**debugowania** > **Step Into**).

    Otwiera plik nagłówka z kodu macierzystego i zobacz żółta strzałka, w której debuger jest wstrzymana.

    ![Wykonywanie kodu natywnego](../debugger/media/mixed-mode-step-into-native-code.png)

    Teraz można wykonywać następujące czynności zestawu i trafień punktów przerwania i sprawdzić zmienne.

1. Umieść kursor nad zmienne, aby wyświetlić ich wartości.

1. Przyjrzyj się **automatycznych** i **zmiennych lokalnych** systemu windows, aby zobaczyć zmiennej i ich wartości.

    Gdy wstrzymaniu w debugerze, możesz używać innych funkcji debugera takich jak **czujki** okna i **stos wywołań** okna.

1. Naciśnij klawisz **F11** ponownie, aby poprawić debugera jeden wiersz.

1. Naciśnij klawisz **Shift + F11** (**debugowania** > **Wyjdź**) do kontynuowania wykonywania aplikacji i ponownie wstrzymywać w aplikacji zarządzanej.

1. Naciśnij klawisz **F5** kontynuowanie aplikacji.

    Gratulacje! Samouczek dotyczący debugowanie w trybie mieszanym została ukończona.

## <a name="next-steps"></a>Następne kroki

W tym samouczku przedstawiono sposób debugowania kodu natywnego z aplikacji zarządzanych przez włączenie debugowania w trybie mieszanym. Przegląd innych funkcji debugera zobacz następujący artykuł:

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)