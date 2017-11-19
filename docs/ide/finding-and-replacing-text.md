---
title: "Znajdowanie i zastępowanie tekstu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a2b925e32711e1624a4dfbe74fb5614ee6e0b062
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="finding-and-replacing-text"></a>Znajdowanie i zastępowanie tekstu
Można znaleźć i Zastąp tekst w edytorze kodu programu Visual Studio i niektórych windows tekstowych danych wyjściowych takich jak **znaleźć wyników** systemu windows, za pomocą **Znajdź i Zamień** kontroli lub **znaleźć / Zastąp w plikach**. Można również Wyszukaj i Zamień w niektórych projektanta systemu windows, takich jak projektanta XAML i Projektant formularzy systemu Windows i okien narzędzi  
  
 Można określić zakres wyszukiwania do bieżącego dokumentu, bieżące rozwiązanie lub niestandardowy zestaw folderów. Można również określić zestaw rozszerzeń nazw plików do wyszukiwania wielu plików. Składnia poleceń wyszukiwania można dostosować za pomocą wyrażeniach regularnych programu .NET.  
  
 Do znajdowania i zamieniania wyrażeń regularnych, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  **Find/Command** pole jest dostępna jako formantu paska narzędzi, ale nie jest już widoczna domyślnie. Można wyświetlić **Find/Command** pola, wybierając **Dodaj lub usuń przyciski** na **standardowe** narzędzi, a następnie wybierając **znaleźć**. Aby uzyskać więcej informacji, zobacz [Find/Command — pole](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Znajdź i Zamień formantu  
 **Znajdź i Zamień** formant jest widoczny w prawym górnym rogu okna edytora kodu. **Znajdź i Zamień** kontroli natychmiast prezentuje wszystkie wystąpienia podanego ciągu w bieżącym dokumencie. Można przechodzić z jednego wystąpienia na inny, wybierając **Znajdź następny** przycisk lub **Znajdź poprzednie** przycisku kontrolki wyszukiwania.  
  
 Dostępne opcje zastępowania wybierając przycisk Dalej, aby **znaleźć** pola tekstowego. Aby jedno zastąpienie w czasie, wybierz polecenie **Zastąp dalej** znajdujący się obok **Zastąp** pola tekstowego. Aby zastąpić wszystkie dopasowania, wybierz **Zamień wszystkie** przycisku.  
  
 Aby zmienić kolor wyróżnienia dopasowań, wybierz **narzędzia** menu, wybierz opcję **opcje**, a następnie wybierz pozycję **środowiska**i wybierz **czcionki i kolory** . W **Pokaż ustawienia dla** listy, wybierz **Edytor tekstu**, a następnie w **wyświetlania elementów** listy, wybierz **znaleźć Wyróżnij (rozszerzenie)**.  
  
### <a name="searching-tool-windows"></a>Wyszukiwanie okien narzędzi  
 Można użyć **znaleźć** kontroli kodu lub tekstu systemu Windows, takich jak **dane wyjściowe** systemu windows, i **znaleźć wyników** systemu windows, wybierając **Znajdź i Zamień**na **Edytuj** menu lub (CTRL + F).  
  
 Wersja kontrolki Znajdź jest również dostępna w niektórych okien narzędzi. Na przykład można filtrować teraz na liście kontrolek w **przybornika** okna, wpisując tekst w polu wyszukiwania. Inne okna narzędzi, które umożliwiają teraz wyszukiwania ich zawartość obejmują **Eksploratora rozwiązań**, **właściwości** okno i **Team Explorer**, między innymi.  
  
## <a name="findreplace-in-files"></a>Znajdź/Zamień w plikach  
 **Znajdź/Zamień w plikach** działa, takich jak **Znajdź i Zamień** kontrolować, z wyjątkiem tego, że można zdefiniować zakres wyszukiwania. Nie można wyszukać bieżący plik otwarty w edytorze, tylko można także przeszukać wszystkie otwarte dokumenty, całe rozwiązanie, bieżącego projektu, a wybrany folder zestawów. Można także przeszukać przez rozszerzenie nazwy pliku. Aby uzyskać dostęp do **Znajdź/Zamień w plikach** oknie dialogowym wybierz **Znajdź i Zamień** na **Edytuj** menu (lub CTRL + SHIFT + F).  
  
 Po wybraniu **Znajdź wszystkie**, **znaleźć wyników** okno otwiera i lista pasujących do wyszukiwania. Wybieranie wynik na liście Wyświetla plik skojarzony i zaznacza dopasowania. Jeśli plik nie jest już otwarty do edycji, jest otwierany na karcie podglądu po prawej stronie karty oraz. Można użyć **znaleźć** formantu do przeszukiwania **znaleźć wyników** listy.  
  
### <a name="creating-custom-search-folder-sets"></a>Tworzenie zestawów Folder wyszukiwania niestandardowego  
 Można zdefiniować zakres wyszukiwania, wybierając **wybierz foldery wyszukiwania** przycisk (prawdopodobnie **...** ) obok pozycji **Szukaj w** pole. W **wybierz foldery wyszukiwania** okno dialogowe, można określić zestaw folderów wyszukiwania i można zapisać specyfikację, dzięki czemu można używać go później. Foldery na zdalnym komputerze można określić tylko wtedy, gdy zamapowaniu jego dysku na komputerze lokalnym.  
  
### <a name="creating-custom-component-sets"></a>Tworzenie zestawów niestandardowych składników  
 Ustawia składnika można zdefiniować jako zakres wyszukiwania, wybierając **edytowanie zestawu składnika niestandardowe** znajdujący się obok **Szukaj w** pole. Można określić zainstalowanych .NET lub COM składników, projektów programu Visual Studio, które są uwzględnione w rozwiązaniu lub dowolnego zestawu lub typ biblioteki (.dll, .tlb, .olb, .exe i ocx). Aby przeszukać odwołania, zaznacz **Szukaj w odwołaniach** pole.  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)