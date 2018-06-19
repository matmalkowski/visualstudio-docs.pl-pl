---
title: 'Porady: debugowanie źródła .NET Framework | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8377ed73479441272b2f1910767fa7e2a4ff0196
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475642"
---
# <a name="how-to-debug-net-framework-source"></a>Porady: debugowanie źródła .NET Framework
Debugowanie źródła .NET Framework, musi mieć dostęp do debugowania symbole dla kodu. Należy również włączyć wykonywanie krok po kroku do źródła .NET Framework.  
  
 Można włączyć .NET Framework wykonywanie krok po kroku i symbol pobierania w **opcje** okno dialogowe. Po włączeniu symbol pobierania można pobrać symboli lub po prostu włącz opcję pobierania później. Jeśli nie pobieraj natychmiast symbole, symbole zostaną pobrane przy następnym uruchomieniu debugowania aplikacji. Możesz także zrobić ręcznego pobrania z **modułów** okna lub **stos wywołań** okna.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Aby włączyć debugowanie źródła .NET Framework  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcji**s.  
  
2.  W **opcje** okno dialogowe, kliknij przycisk **debugowanie** kategorii.  
  
3.  W **ogólne** należy ustawić **źródła włączyć .NET Framework wykonywanie krok po kroku.**  
  
    1.  Jeśli były włączone tylko mój kod, okno dialogowe informuje, czy tylko mój kod jest teraz wyłączony. Kliknij przycisk **OK**.  
  
    2.  Jeśli nie masz lokalizacji pamięci podręcznej symboli, ustaw inne okno dialogowe Ostrzeżenie informuje, teraz ustawiono domyślnej lokalizacji pamięci podręcznej symboli. Kliknij przycisk **OK**.  
  
4.  W obszarze **debugowanie** kategorii, kliknij przycisk **symbole**.  
  
5.  Jeśli chcesz zmienić lokalizację pamięci podręcznej symboli, edytować lokalizację w **pamięci podręcznej symboli w tym katalogu** lub kliknij przycisk **Przeglądaj** aby wybrać lokalizację.  
  
6.  Jeśli chcesz natychmiast pobrać symboli, kliknij przycisk **załadować symbole, używając powyższych lokalizacjach**.  
  
     Ten przycisk jest niedostępny w trybie projektowania, ale jest dostępna podczas debugowania.  
  
     Jeśli użytkownik nie chce Pobierz symbole, symbole będą pobierane automatycznie podczas następnego uruchomienia debugowania programu.  
  
7.  Kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Aby załadować symbole Framework korzystanie z okna modułów  
  
1.  W **modułów** okna (podczas debugowania, wybierz **debugowania** > **Windows** > **modułów**), Kliknij prawym przyciskiem myszy moduł, dla którego nie załadowano symboli. Można określić, czy załadowano symbole nie analizując **stan symbole** kolumny.  
  
2.  Wskaż **ustawienia** i kliknij przycisk **serwerów symboli firmy Microsoft** pobieranie symboli z serwera symboli publicznych firmy Microsoft. Lub, kliknij prawym przyciskiem myszy modułu i wybierz **załadować symbole** załadować z katalogu, w której uprzednio zapisano symboli.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Aby załadować symbole Framework w oknie stosu wywołań  
  
1.  W **stos wywołań** okna, kliknij prawym przyciskiem myszy, a ramki, dla którego nie załadowano symboli. Ramki będzie wygaszone.  
  
2.  Wskaż **ustawienia** i kliknij przycisk **serwerów symboli firmy Microsoft**, lub kliknij prawym przyciskiem myszy modułu i wybierz polecenie **ścieżki symboli**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)