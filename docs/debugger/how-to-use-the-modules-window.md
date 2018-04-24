---
title: Wyświetlanie biblioteki dll i plików wykonywalnych w debugerze | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46dc913b95396e16f208611bcfc926378609bef6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Wyświetlanie biblioteki dll i plików wykonywalnych korzystanie z okna modułów w debugerze programu Visual Studio
 
**Modułów** okno zawiera listę bibliotek DLL i pliki wykonywalne (EXE) są używane przez program, który zawiera istotne informacje dla każdego. 

> [!NOTE]
>  Ta funkcja nie jest dostępna dla bazy danych SQL lub debugowanie skryptu. 
  
### <a name="to-display-the-modules-window"></a>Aby wyświetlić okno modułów  
  
-   Podczas debugowania, wybierz **Debuguj > Windows** , a następnie kliknij przycisk **modułów**.  
  
     Domyślnie **modułów** okna sortowania kolejność ładowania modułów. Jednak można sortować według dowolnej kolumny.  
  
### <a name="to-sort-by-any-column"></a>Aby sortować według dowolnej kolumny  
  
-   Kliknij przycisk u góry kolumny.  
  
     Można załadować symboli lub określ ścieżkę symboli z **modułów** okna przy użyciu menu skrótów.  
  
## <a name="loading-symbols"></a>Ładowanie symboli  
 W **modułów** okna, zostanie wyświetlony, które moduły mają załadować symboli debugowania. Informacje te pojawiają się w **stan Symbol** kolumny. Jeśli stan jest wyświetlany komunikat **loadingCannot pomijane znaleźć lub otworzyć pliku PDB**, lub **ładowanie wyłączone przez ustawienie dołączania/wykluczania**, można kierować debugera tak, aby pobrać symboli z symboli publicznych firmy Microsoft serwery lub załadować symbole z katalogu symbol na tym komputerze. Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Aby ręcznie załadować symbole  
  
1.  W **modułów** okna, kliknij prawym przyciskiem myszy, a moduł, dla którego nie załadowano symbole.  
  
2.  Wskaż **Załaduj symbole z** , a następnie kliknij przycisk **serwerów symboli firmy Microsoft** lub **ścieżki symboli**.  
  
#### <a name="to-change-symbol-load-settings"></a>Aby zmienić ustawienia ładowania symboli  
  
1.  W **modułów** okna, kliknij prawym przyciskiem myszy każdy moduł.  
  
2.  Kliknij przycisk **symbolu ustawienia**.  
  
     Można teraz zmienić ustawienia obciążenia, zgodnie z opisem w [Określ lokalizacje symboli i zachowania ładowania](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Zmiany nie będą obowiązywać dopiero po ponownym uruchomieniu sesji debugowania.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Aby zmienić zachowanie ładowania symboli dla określonego modułu  
  
1.  W **modułów** okna, kliknij prawym przyciskiem myszy modułu.  
  
2.  Wskaż **ustawienia automatycznego ładowania symboli** , a następnie kliknij przycisk **zawsze obciążenia ręcznie** lub **domyślne**. Zmiany nie będą obowiązywać dopiero po ponownym uruchomieniu sesji debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przerwanie wykonywania](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)