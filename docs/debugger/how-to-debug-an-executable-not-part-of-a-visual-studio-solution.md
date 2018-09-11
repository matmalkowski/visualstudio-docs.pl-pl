---
title: 'Porady: debugowanie pliku wykonywalnego, który nie jest częścią rozwiązania programu Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: ce84c4acdc2cf4324c76dbbf7fe0b39ca9715b3c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279105"
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Porady: debugowanie pliku wykonywalnego, który nie jest częścią rozwiązania programu Visual Studio
Czasami możesz chcieć debugować plik wykonywalny (plik .exe), który nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Może być wykonywalny, który został utworzony poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub wykonywalny, który otrzymałeś od kogoś innego.  
  
Zwykle rozwiązaniem tego problemu jest uruchomienie pliku wykonywalnego poza programem Visual Studio i dołączenie do niego przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugera. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Dołączanie do aplikacji wymaga dodatkowych ręcznych czynności, więc zajmuje kilka sekund. To niewielkie opóźnienie oznacza, że dołączanie nie pomoże, jeśli chcesz debugować problem, który występuje podczas uruchamiania. Ponadto Jeśli debugujesz program, który nie czeka na dane wejściowe użytkownika i szybko się kończy, możesz nie mieć czasu, aby dołączyć do niego. Jeśli masz [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] i [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] zainstalowane, można utworzyć projekt EXE dla takiego programu.

> [!NOTE]
>  Nie wszystkie języki programowania wspierają projekty EXE.

Podczas debugowania pliku wykonywalnego, który nie jest częścią rozwiązania programu Visual Studio, dostępne funkcje debugowania może być ograniczona, czy dołączyć do uruchomionego pliku wykonywalnego lub dodać plik wykonywalny do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania.

- Jeśli masz kod źródłowy, najlepszym rozwiązaniem jest zaimportowanie kodu źródłowego do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i utworzenie kompilacja do debugowania pliku wykonywalnego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
- Jeśli nie masz kod źródłowy i plik wykonywalny został skompilowany bez [informacje o debugowaniu](../debugger/how-to-set-debug-and-release-configurations.md) w zgodnym formacie, dostępne funkcje debugowania są bardzo ograniczona. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Aby utworzyć projekt EXE dla istniejącego pliku wykonywalnego  
  
1.  Na **pliku** menu, kliknij przycisk **Otwórz** i wybierz **projektu**.  
  
2.  W **Otwórz projekt** okno dialogowe, kliknij listę rozwijaną listę obok **nazwy pliku** i zaznacz **wszystkie pliki projektu**.  
  
3.  Znajdź plik wykonywalny, a następnie kliknij przycisk **OK**.  

    Tworzy to rozwiązanie tymczasowe, które zawiera plik wykonywalny.

5.  Uruchom plik wykonywalny, wybierając polecenie wykonania, takie jak **Start**, z **debugowania** menu.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Aby zaimportować plik wykonywalny do rozwiązania programu Visual Studio  
  
1.  Na **pliku** menu wskaż **Dodaj projekt**, a następnie kliknij przycisk **istniejący projekt**.  
  
2.  W **Dodaj istniejący projekt** okno dialogowe, kliknij listę rozwijaną listę obok **nazwy pliku** i zaznacz **wszystkie pliki projektu**.  
  
3.  Znajdź i zaznacz plik wykonywalny.  
  
4.  Kliknij przycisk **OK**.  
  
5.  Uruchom plik wykonywalny, wybierając polecenie wykonania, takie jak **Start**, z **debugowania** menu.    
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [DBG, pliki](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))