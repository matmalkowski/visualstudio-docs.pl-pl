---
title: 'Porady: debugowanie pliku wykonywalnego, który nie jest częścią rozwiązania Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d73b122bf882ee1ccf7ce7e35e8a36cd91f2eb07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Porady: debugowanie pliku wykonywalnego, który nie jest częścią rozwiązania programu Visual Studio
Czasami może chcesz debugować plik wykonywalny (.exe plik), który nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Może być utworzony poza plik wykonywalny [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub pliku wykonywalnego otrzymany od kogoś innego.  
  
Zwykle odpowiedzią na ten problem ma uruchomić plik wykonywalny poza Visual Studio i Dołącz do niej przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugera. Aby uzyskać więcej informacji, zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Dołączanie do aplikacji wymaga niektórych ręczne wykonanie czynności, dlatego zajmuje kilka sekund. To niewielkie opóźnienie oznacza, że dołączanie nie pomoże, jeśli chcesz debugować problem występujący podczas uruchamiania. Ponadto jeśli debugowany program, który nie oczekuje danych wejściowych użytkownika i kończy się szybko, nie masz czasu można dołączyć do niego. Jeśli masz [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] i [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] zainstalowana, można utworzyć projektu EXE dla takiego programu.

> [!NOTE]
>  Nie wszystkie języki programowania obsługuje projekty EXE.

Podczas debugowania pliku wykonywalnego, który nie jest częścią rozwiązania Visual Studio, dostępne funkcje debugowania można ograniczyć, czy dołączyć do uruchomienia pliku wykonywalnego lub Dodaj plik wykonywalny do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania.

- Jeśli masz kod źródłowy, najlepiej zaimportować kodu źródłowego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i Utwórz kompilację debugowania pliku wykonywalnego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
- Jeśli nie masz kod źródłowy i plik wykonywalny został skompilowany bez [informacje o debugowaniu](../debugger/how-to-set-debug-and-release-configurations.md) w formacie zgodnym z, dostępne funkcje debugowania są bardzo ograniczone. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Aby utworzyć plik EXE projektu dla istniejącego pliku wykonywalnego  
  
1.  Na **pliku** menu, kliknij przycisk **Otwórz** i wybierz **projektu**.  
  
2.  W **Otwórz projekt** okno dialogowe, kliknij przycisk Dalej, aby wyświetlić listę listy rozwijanej **nazwę pliku** i wybierz **wszystkie pliki projektu**.  
  
3.  Zlokalizuj plik wykonywalny, a następnie kliknij przycisk **OK**.  

    Spowoduje to utworzenie tymczasowego rozwiązania, które zawiera pliku wykonywalnego.

5.  Uruchom plik wykonywalny, wybierając polecenie wykonywania, takie jak **Start**, z **debugowania** menu.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Aby zaimportować plik wykonywalny do rozwiązania Visual Studio  
  
1.  Na **pliku** menu wskaż **Dodawanie projektu**, a następnie kliknij przycisk **istniejący projekt**.  
  
2.  W **Dodaj istniejący projekt** okno dialogowe, kliknij przycisk Dalej, aby wyświetlić listę listy rozwijanej **nazwę pliku** i wybierz **wszystkie pliki projektu**.  
  
3.  Znajdź i zaznacz plik wykonywalny.  
  
4.  Kliknij przycisk **OK**.  
  
5.  Uruchom plik wykonywalny, wybierając polecenie wykonywania, takie jak **Start**, z **debugowania** menu.    
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [DBG, pliki](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)