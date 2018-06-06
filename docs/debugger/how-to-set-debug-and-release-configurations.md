---
title: 'Porady: Ustawianie debugowania i konfiguracje wydania | Dokumentacja firmy Microsoft'
ms.custom: H1HackMay2017
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.openlocfilehash: 6ae43c5cab67d79450cea1dc024da98fe25c5375
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34690669"
---
# <a name="how-to-set-debug-and-release-configurations-in-visual-studio"></a>Porady: Ustawianie debugowania i wydania konfiguracji w programie Visual Studio
Projektów programu Visual Studio mają oddzielne wersji i konfiguracje programu do debugowania. Jako nazwy oznacza kompilacji wersji do debugowania do debugowania i wersji ostatecznej wersji dystrybucji.  
  
Konfiguracja debugowania programu jest skompilowana przy użyciu informacji o debugowaniu pełne symboliczne i Brak optymalizacji. Optymalizacja komplikuje debugowania, ponieważ relacja między kodu źródłowego i instrukcje wygenerowanego jest bardziej złożony.  
  
Do konfiguracji wydania programu nie zawiera żadnych informacji debugowania symboliczne i jest zoptymalizowany. Debugowanie w .pdb, pliki, można wygenerować informacji [w zależności od opcji kompilatora](#BKMK_symbols_release) używane. Tworzenie plików PDB może być bardzo przydatne, jeśli masz później do debugowania z wersji.  
  
Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).  
  
Możesz zmienić konfigurację kompilacji z **kompilacji** menu, paska narzędzi lub na stronach właściwości projektu. Strony właściwości projektu są specyficzne dla języka. Poniższa procedura przedstawia sposób zmień konfigurację kompilacji, z menu i paska narzędzi. Aby uzyskać więcej informacji na temat zmiany konfiguracji kompilacji w projektach w różnych językach zobacz sekcję Zobacz też poniżej.  
  
## <a name="change-the-build-configuration"></a>Zmień konfigurację kompilacji  
  
1.  Z **kompilacji** menu, wybierz opcję **programu Configuration Manager**, a następnie wybierz pozycję **debugowania** lub **wersji**.  
  
2.  Na pasku narzędzi wybierz **debugowania** lub **wersji** z **konfiguracje rozwiązania** pola listy.  
  
     ![Konfiguracja kompilacji narzędzi](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Ten pasek narzędzi nie jest dostępna w wersji Express. Można użyć **kompilacji F6 rozwiązania** i **rozpocząć debugowanie F5** elementów menu, aby wybrać konfigurację.

## <a name="BKMK_symbols_release"></a>Generuj pliki symboli (.pdb) do kompilacji

Dla większości typów projektów .pdb, pliki są generowane domyślnie dla obu debugowania i wydania z kompilacji, ale domyślne ustawienia są różne w zależności od Twojego projektu określonego typu i wersji programu Visual Studio. Można skonfigurować czy kompilator generuje .pdb, pliki i jakiego rodzaju informacje debugowania do uwzględnienia.

> [!IMPORTANT] 
> Debuger będzie ładował tylko plik .pdb dla pliku wykonywalnego, który dokładnie pasuje do pliku .pdb, który z kolei został utworzony podczas kompilowania pliku wykonywalnego (czyli .pdb musi być plikiem oryginalnym lub kopią oryginalnego pliku .pdb). Aby uzyskać więcej informacji, zobacz [Dlaczego Visual Studio wymaga symbol debugera dokładnej zgodności plików pliki binarne, które zostały skompilowane?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Każdy typ projektu może mieć inny sposób ustawiania tych opcji.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generuj pliki symboli dla projektu C# ASP.NET i Visual Basic

Aby uzyskać szczegółowe informacje na temat ustawień projektu dla konfiguracji debugowania w języku C#, zobacz [projektu ustawienia konfiguracji debugowania C#](../debugger/project-settings-for-csharp-debug-configurations.md). W języku Visual Basic, zobacz [w tym temacie](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **właściwości**.

2. Wybierz **wersji** lub **debugowania** kompilacji z **konfiguracji** listy.

2. Wybierz **kompilacji** ustawienia, a następnie kliknij przycisk **zaawansowane** przycisku.

    W języku Visual Basic, możesz wybrać **skompilować** ustawienia i **zaawansowane opcje kompilacji** zamiast tego przycisku.

3. Wybierz **pełne**, **przenośne**, lub **pdb_only** w **informacji o debugowaniu** pole listy (**Generuj informacje debugowania** w języku Visual Basic).

    Format przenośnej jest najnowszych format i platform .NET Core. Aby uzyskać więcej informacji na temat opcji, zobacz [okno dialogowe Zaawansowane ustawienia kompilacji (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![Generuj pliki PDB dla kompilacji w języku C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Skompilowanie projektu.

    W tym samym folderze co plik wykonywalny lub plik wyjściowy głównej tworzone pliki symboli.

### <a name="generate-symbol-files-for-a-c-project"></a>Generuj pliki symboli dla projektów C++

1. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **właściwości**.

2. Wybierz **wersji** lub **debugowania** kompilacji z **konfiguracji** listy.

2. W obszarze **konsolidatora > debugowanie**, wybierz żądany opcje **Generuj informacje o debugowaniu**.

    Aby uzyskać szczegółowe informacje na temat ustawień projektu dla konfiguracji debugowania w języku C++, zobacz [projektu ustawienia konfiguracji debugowania z C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Skonfiguruj opcje generowania plików bazy danych programu

    W większości projektów C++, wartością domyślną jest `$(OutDir)$(TargetName).pdb`, który generuje .pdb, pliki w folderze wyjściowym.

    ![Generuj pliki PDB dla kompilacji w języku C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Skompilowanie projektu.

    W tym samym folderze co plik wykonywalny lub plik wyjściowy głównej tworzone pliki symboli.
  
## <a name="see-also"></a>Zobacz też  
 [Określanie plików symboli (.pdb) i plików źródłowych w debugerze Visua Studio](../debugger/debugger-settings-and-preparation.md)  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Ustawienia projektu dla konfiguracji debugowania z C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Konfiguracje debugowania ustawienia projektu w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
