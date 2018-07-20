---
title: Zestaw debugowania i zwalniania konfiguracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea27fdccaadc70f22d9c9c02d75ddef98a11be13
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153101"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Zestaw debugowania i zwalniania konfiguracji w programie Visual Studio
Projektów programu Visual Studio mają oddzielnych wersji i konfiguracji programu do debugowania. Jak sugerują nazwy kompilujesz wersję debugera do debugowania i wersję zwolnienia do ostatecznej dystrybucji zwolnienia.  
  
Konfiguracja debugowania programu została skompilowana z informacji pełnego symbolicznego debugowania i bez optymalizacji. Optymalizacja komplikuje debugowanie, ponieważ relacja między kodem źródłowym i wygenerowanymi instrukcjami jest bardziej złożona.  
  
Konfiguracja wydania programu nie zawiera żadnych informacji symbolicznego debugowania i jest w pełni zoptymalizowana. Debugowanie informacje mogą być generowane w plikach .pdb [w zależności od opcji kompilatora](#BKMK_symbols_release) które są używane. Tworzenie plików .pdb może być bardzo przydatne, jeśli później trzeba debugować swoje wersje.  
  
Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md).  
  
Możesz zmienić konfigurację kompilacji z **kompilacji** menu na pasku narzędzi lub na stronach właściwości projektu. Strony właściwości projektu są specyficzne dla języka. Poniższa procedura pokazuje, jak zmienić konfigurację kompilacji w menu i paska narzędzi. Aby uzyskać więcej informacji o tym, jak zmienić konfigurację kompilacji w projektach w różnych językach zobacz poniżej sekcję Zobacz też.  
  
## <a name="change-the-build-configuration"></a>Zmień konfigurację kompilacji  
  
1.  Z **kompilacji** menu, wybierz opcję **programu Configuration Manager**, a następnie wybierz **debugowania** lub **wersji**.  
  
2.  Na pasku narzędzi wybierz **debugowania** lub **wersji** z **konfiguracje rozwiązania** pola listy.  
  
     ![Konfiguracja kompilacji narzędzi](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Ten pasek narzędzi nie jest dostępny w wersji Express. Możesz użyć **Kompiluj rozwiązanie F6** i **Rozpocznij debugowanie F5** elementy menu, aby wybrać konfigurację.

## <a name="BKMK_symbols_release"></a>Generowanie plików symboli (.pdb) dla kompilacji

Dla większości typów projektów pliki .pdb są generowane domyślnie dla obu debugowania i kompilacje wydania, ale domyślne ustawienia są różne w zależności od Twojego projektu określonego typu i wersji programu Visual Studio. Można skonfigurować tego, czy kompilator generuje pliki .pdb i jakiego rodzaju informacje debugowania.

> [!IMPORTANT] 
> Debuger będzie ładował tylko plik .pdb dla pliku wykonywalnego, który dokładnie pasuje do pliku .pdb, który z kolei został utworzony podczas kompilowania pliku wykonywalnego (czyli .pdb musi być plikiem oryginalnym lub kopią oryginalnego pliku .pdb). Aby uzyskać więcej informacji, zobacz [Dlaczego Visual Studio wymaga, aby debuger symbol dokładnej zgodności plików plików binarnych, które zostały skompilowane?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Każdy typ projektu może mieć inny sposób ustawienia tych opcji.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generuj pliki symboli dla projektów C#, ASP.NET lub Visual Basic

Aby uzyskać szczegółowe informacje na temat ustawień projektu dla konfiguracji debugowania w języku C#, zobacz [ustawienia konfiguracji debugowania języka C# projektu](../debugger/project-settings-for-csharp-debug-configurations.md). Dla języka Visual Basic, zobacz [w tym temacie](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **właściwości**.

2. Wybierz **wersji** lub **debugowania** opracowano na podstawie **konfiguracji** listy.

2. Wybierz **kompilacji** ustawienia, a następnie kliknij przycisk **zaawansowane** przycisku.

    W języku Visual Basic, możesz wybrać **skompilować** ustawienia i **zaawansowane opcje kompilacji** zamiast tego przycisku.

3. Wybierz **pełne**, **przenośne**, lub **pdb_only** w **informacje o debugowaniu** pole listy (**Generuj informacje debugowania** w języku Visual Basic).

    Przenośne format jest najbardziej aktualną format dla wielu platform .NET Core. Aby uzyskać więcej informacji na temat opcji, zobacz [okno dialogowe Zaawansowane ustawienia kompilacji (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![Generowanie plików PDB dla kompilacji w języku C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Skompilowanie projektu.

    Utworzone pliki symboli w tym samym folderze co plik wykonywalny lub plik wyjściowy głównego.

### <a name="generate-symbol-files-for-a-c-project"></a>Generuj pliki symboli dla projektu w języku C++

1. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **właściwości**.

2. Wybierz **wersji** lub **debugowania** opracowano na podstawie **konfiguracji** listy.

2. W obszarze **konsolidatora > debugowanie**, wybierz żądane opcje **Generuj informacje o debugowaniu**.

    Aby uzyskać szczegółowe informacje na temat ustawień projektu dla konfiguracji debugowania w języku C++, zobacz [ustawienia konfiguracji debugowania języka C++ projektu](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Skonfiguruj opcje generowania plików bazy danych programu

    W większości projektów C++, wartość domyślna to `$(OutDir)$(TargetName).pdb`, które generuje pliki .pdb w folderze wyjściowym.

    ![Generowanie plików PDB dla kompilacji w języku C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Skompilowanie projektu.

    Utworzone pliki symboli w tym samym folderze co plik wykonywalny lub plik wyjściowy głównego.
  
## <a name="see-also"></a>Zobacz też  
 [Określanie plików symboli (.pdb) i plików źródłowych w debugerze integrujące Studio](../debugger/debugger-settings-and-preparation.md)  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Ustawienia projektu dla języka C# konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
