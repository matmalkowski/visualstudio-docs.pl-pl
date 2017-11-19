---
redirect_url: /visualstudio/csharp-ide/refactoring-csharp
ms.openlocfilehash: cb4e45847008d99aa17b5ce3dde83da036a53dbb
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
Tytuł: "jak: Przywracanie wstawki Refactoring C# | Ms.custom dokumentacja firmy Microsoft":" "ms.date: ms.reviewer"2016-11-04":" "ms.suite:" "ms.technology: 
  - ms.tgt_pltfrm "vs-ide — ogólne": "" ms.topic: "artykuł" helpviewer_keywords: 
  - "niebezpieczna ekspansja"
  - "rozszerzenia, niebezpieczne" ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d caps.latest.revision: 20 Autor: ms.author "gewarren": "gewarren" Menedżer: ghogen
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Porady: przywracanie refaktoryzowanych wstawek kodu C#
C# refaktoryzacji operacje korzystają wstawki kodu w następującym katalogu:  
  
 *Katalog instalacyjny*\Microsoft Visual Studio 15.0\VC#\Snippets\\*identyfikator języka*\Refactoring  
  
 Jeśli ten katalog Refactoring lub wszystkie pliki w tym katalogu zostały usunięte lub uszkodzony, następnie refaktoryzacji operacji C# mogą nie działać w środowisku IDE. Poniższe procedury ułatwiają Przywracanie refaktoryzowanych wstawek kodu kodu C#.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Aby sprawdzić, C# refaktoryzacji fragmenty są dostępne za pomocą Menedżera fragment kodu  
  
1.  W **narzędzia** menu, wybierz opcję **Menedżer wstawek kodu**.  
  
2.  W **Menedżer wstawek kodu** okno dialogowe, wybierz opcję **Visual C#** z **języka** listy rozwijanej.  
  
     A **Refactoring** folder powinien zostać wyświetlony na liście folderów w widoku drzewa.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Aby przywrócić refaktoryzacji Zobacz komentarz w Menedżer wstawek kodu  
  
1.  Jeśli **Refactoring** folderu nie są wyświetlane na liście folderu programu Menedżer wstawek kodu widoku drzewa, a następnie użyj tej procedury, aby dodać refaktoryzacji wstawki wstecz do kodu fragment menedżera.  
  
2.  W **narzędzia** menu, wybierz opcję **Menedżer wstawek kodu**.  
  
3.  W **Menedżer wstawek kodu** okno dialogowe, wybierz opcję **Visual C#** z **języka** listy rozwijanej.  
  
4.  Kliknij przycisk **Dodaj**. **Katalog wstawki kodu** zostanie wyświetlone okno dialogowe, co ułatwia znajdowanie i określ katalog, aby dodać wstecz do Menedżera fragment kodu,.  
  
5.  Zlokalizuj **Refactoring** folderze, w których ścieżka katalogu:  
  
     *Katalog instalacyjny*\Microsoft Visual Studio 15.0\VC#\Snippets\\*identyfikator języka*\Refactoring  
  
     Ścieżki rzeczywistego jest podobne do następujących dla domyślnej instalacji:  
  
     C:\Program Files\Microsoft 15.0\VC#\Snippets\1033\Refactoring programu Visual Studio.  
  
6.  Kliknij przycisk **Otwórz** w **katalog wstawki kodu** , a następnie kliknij przycisk **OK** w Menedżerze fragmentów kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wstawki kodu Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)   
 [Wstawki kodu](../ide/code-snippets.md)