---
title: 'Porady: Przywracanie Refaktoryzowanych wstawek kodu C# | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13867274ace5582b25482868ddd3642426b1f295
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42696715"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Porady: przywracanie refaktoryzowanych wstawek kodu C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Przywracanie C# refaktoryzacji fragmenty](https://docs.microsoft.com/visualstudio/ide/how-to-restore-csharp-refactoring-snippets).  
  
Operacje refaktoryzacji C# polegają na fragmenty kodu w następującym katalogu:  
  
 *Katalog instalacyjny*\Microsoft Visual Studio 14.0\VC#\Snippets\\*identyfikator języka*\Refactoring  
  
 Jeśli ten katalog Refactoring, wszystkie pliki w tym katalogu są usunięty lub uszkodzony, następnie operacji refaktoryzacji, C# mogą nie działać w środowisku IDE. Poniższe procedury ułatwia przywracanie refaktoryzowanych wstawek kodu kodu C#.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Aby sprawdzić, C# refaktoryzacji fragmenty kodu są dostępne za pomocą Menedżera fragmentów kodu  
  
1.  W **narzędzia** menu, wybierz opcję **Menedżera fragmentów kodu**.  
  
2.  W **Menedżera fragmentów kodu** okno dialogowe, wybierz opcję **Visual C#** z **języka** listy rozwijanej.  
  
     A **Refactoring** folder powinien być widoczny na liście folderów w widoku drzewa.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Aby przywrócić refaktoryzacji zobaczyć komentarz w Menedżerze fragmentu kodu  
  
1.  Jeśli **Refactoring** folderu nie są wyświetlane na liście drzewa widoku folderu Menedżera fragmentów kodu, a następnie ta procedura umożliwia dodawanie fragmentów refaktoryzacji Wstecz w Menedżerze fragmentu kodu.  
  
2.  W **narzędzia** menu, wybierz opcję **Menedżera fragmentów kodu**.  
  
3.  W **Menedżera fragmentów kodu** okno dialogowe, wybierz opcję **Visual C#** z **języka** listy rozwijanej.  
  
4.  Kliknij przycisk **Dodaj**. **Katalog fragmentów kodu** pojawi się okno dialogowe, które ułatwia znajdowanie i określ katalog, aby dodać ponownie w Menedżerze fragmentu kodu,.  
  
5.  Znajdź **Refactoring** folderu o ścieżce katalogu:  
  
     *Katalog instalacyjny*\Microsoft Visual Studio 14.0\VC#\Snippets\\*identyfikator języka*\Refactoring  
  
     Rzeczywistej ścieżce są podobne do następujących czynności w przypadku instalacji domyślnej:  
  
     C:\Program Files\Microsoft 14.0\VC#\Snippets\1033\Refactoring programu Visual Studio.  
  
6.  Kliknij przycisk **Otwórz** w **katalog fragmentów kodu** okno dialogowe, a następnie kliknij przycisk **OK** w Menedżerze fragmentów kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Fragmenty kodu Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)   
 [Fragmenty kodu](../ide/code-snippets.md)



