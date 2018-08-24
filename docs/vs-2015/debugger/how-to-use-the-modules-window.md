---
title: 'Porady: Korzystanie z okna modułów | Dokumentacja firmy Microsoft'
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
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f7a5c71a95c0e4c366b7001a3adf86d5bacc9c8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676041"
---
# <a name="how-to-use-the-modules-window"></a>Porady: korzystanie z okna modułów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wyświetlanie modułów, biblioteki dll i plików wykonywalnych w debugerze](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-modules-window).  
  
UWAGA]
>  Ta funkcja nie jest dostępna dla bazy danych SQL lub debugowania skryptu.  
  
 **Modułów** okno zawiera listę bibliotek DLL i EXE, które są używane przez program i ukazuje istotne informacje dla każdego.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Aby wyświetlić okno modułów w trybie przerwania lub w trybie uruchamiania  
  
-   Na **debugowania** menu, wybierz **Windows**, a następnie kliknij przycisk **modułów**.  
  
     Domyślnie **modułów** okna sortuje moduły według kolejności ładowania. Można sortować według dowolnej kolumny.  
  
### <a name="to-sort-by-any-column"></a>Aby sortować według dowolnej kolumny  
  
-   Kliknij przycisk u góry kolumny.  
  
     Możesz załadować symbole lub określenie ścieżki symbolu z **modułów** oknie za pomocą menu skrótów.  
  
## <a name="loading-symbols"></a>Ładowanie symboli  
 W **modułów** okna, możesz zobaczyć, które moduły mają załadowane symbole debugowania. Te informacje są wyświetlane w **stan symboli** kolumny. Jeśli stan jest wyświetlany komunikat **loadingCannot pomijane znaleźć lub otworzyć pliku PDB**, lub **ładowanie wyłączone przez ustawienie dołączania lub wykluczania**, można kierować debugera, aby pobrać symbole z publicznego symboli firmy Microsoft serwery lub załadować symbole z katalogu symboli na komputerze. Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Aby ręcznie załadować symbole  
  
1.  W **modułów** okna, kliknij prawym przyciskiem myszy moduł, dla której symbole nie zostały załadowane.  
  
2.  Wskaż **Załaduj symbole z** a następnie kliknij przycisk **serwery symboli firmy Microsoft** lub **ścieżki symboli**.  
  
#### <a name="to-change-symbol-load-settings"></a>Aby zmienić ustawienia ładowania symboli  
  
1.  W **modułów** okna, kliknij prawym przyciskiem myszy dowolny moduł.  
  
2.  Kliknij przycisk **ustawienia symboli**.  
  
     Można teraz zmienić ustawienia ładowania symboli, zgodnie z opisem w [Określ lokalizacje symboli i zachowanie ładowania](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Zmiana zostanie wprowadzona dopiero po ponownym uruchomieniu sesji debugowania.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Aby zmienić zachowanie ładowania symboli dla określonego modułu  
  
1.  W **modułów** okna, kliknij prawym przyciskiem myszy moduł.  
  
2.  Wskaż **ustawienia automatycznego ładowania symboli** a następnie kliknij przycisk **zawsze obciążenia ręcznie** lub **domyślne**. Zmiana zostanie wprowadzona dopiero po ponownym uruchomieniu sesji debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przerwanie wykonywania](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)





