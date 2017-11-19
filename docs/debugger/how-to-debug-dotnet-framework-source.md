---
title: "Porady: debugowanie źródła .NET Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
helpviewer_keywords: debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9da2cd7b8a99d750692a69be406c9c8f82c461d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-net-framework-source"></a>Porady: debugowanie źródła .NET Framework
Najnowszą wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] udostępnia nowe funkcje [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] debugowania. Aby debugować [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] źródła, musi mieć dostęp do debugowania symbole dla kodu. Należy również włączyć wykonywanie krok po kroku do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] źródła.  
  
 Można włączyć [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wykonywanie krok po kroku i symbol pobierania w **opcje** okno dialogowe. Po włączeniu symbol pobierania można pobrać symboli lub po prostu włącz opcję pobierania później. Jeśli nie pobieraj natychmiast symbole, symbole zostaną pobrane przy następnym uruchomieniu debugowania aplikacji. Możesz także zrobić ręcznego pobrania z **modułów** okna lub **stos wywołań** okna.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Aby włączyć debugowanie źródła .NET Framework  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcji**s.  
  
2.  W **opcje** okno dialogowe, kliknij przycisk **debugowanie** kategorii.  
  
3.  W **ogólne** należy ustawić **włączyć .NET Framework** krokowe wykonywanie źródła.  
  
    1.  Jeśli były włączone tylko mój kod, okno dialogowe informuje, czy tylko mój kod jest teraz wyłączony. Kliknij przycisk **OK**.  
  
    2.  Jeśli nie masz lokalizacji pamięci podręcznej symboli, ustaw inne okno dialogowe Ostrzeżenie informuje, teraz ustawiono domyślnej lokalizacji pamięci podręcznej symboli. Kliknij przycisk **OK**.  
  
4.  W obszarze **debugowanie** kategorii, kliknij przycisk **symbole**.  
  
5.  Jeśli chcesz zmienić lokalizację pamięci podręcznej symboli:  
  
    1.  Otwórz **debugowanie** węzła w polu po lewej stronie.  
  
    2.  W obszarze **debugowanie** węzła, kliknij przycisk **symbole**.  
  
    3.  Edytowanie lokalizacji w **pamięci podręcznej symboli z serwerów symboli w tym katalogu** lub kliknij przycisk **Przeglądaj** aby wybrać lokalizację.  
  
6.  Jeśli chcesz natychmiast pobrać symboli, kliknij przycisk **załadować symbole, używając powyższych lokalizacjach**.  
  
     Ten przycisk jest niedostępny w trybie projektowania.  
  
     Jeśli użytkownik nie chce Pobierz symbole, symbole będą pobierane automatycznie podczas następnego uruchomienia debugowania programu.  
  
7.  Kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Aby załadować symbole Framework korzystanie z okna modułów  
  
1.  W **modułów** okna, kliknij prawym przyciskiem myszy, a moduł, dla którego nie załadowano symboli. Można określić, czy załadowano symbole nie analizując **stan symbole** kolumny.  
  
2.  Wskaż **Załaduj symbole z** i kliknij przycisk **serwerów symboli firmy Microsoft** pobieranie symboli z serwera symboli publicznych firmy Microsoft lub **ścieżki symboli** załadować z katalogu której uprzednio zapisano symboli.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Aby załadować symbole Framework w oknie stosu wywołań  
  
1.  W **stos wywołań** okna, kliknij prawym przyciskiem myszy, a ramki, dla którego nie załadowano symboli. Ramki będzie wygaszone.  
  
2.  Wskaż **Załaduj symbole z** i kliknij przycisk **serwerów symboli firmy Microsoft** lub **ścieżki symboli**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)