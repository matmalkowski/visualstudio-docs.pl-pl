---
title: "Znajdź kodu za pomocą polecenia przejdź do | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 15b222eaa3e03a44f99f64e86f9c88d125e41f98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="find-code-using-go-to-commands"></a>Znajdź kodu za pomocą polecenia przejdź do  
Visual Studio **przejdź do** poleceń wyszukiwania ukierunkowanych swój kod, aby szybko znaleźć określone elementy. Można przejść do określonego wiersza, typu, symbol, plików i element członkowski z prosty, ujednolicony interfejs. Ta funkcja istnieje w programie Visual Studio 2017 i nowszych.  

### <a name="how-to-use-it"></a>Jak z niego korzystać  

Dane wejściowe        | Funkcja 
------------ | ---
**Klawiatury** | Naciśnij klawisz **Ctrl + t** lub **Ctrl +,**     
**Myszy**    | Wybierz **Edytuj**, **przejdź do**, **przejdź do wszystkich**  

Spowoduje to wyświetlenie okna małych u góry prawo do edytora kodu domyślnie.  

![Przejdź do wszystkich](media/gotoall.png)

Podczas wpisywania w polu tekstowym, wyniki są wyświetlane na liście rozwijanej poniżej pola tekstowego. Aby przejść do elementu, wybierz go na liście.    

![Przejdź do okna](../ide/media/vside_navigatetowindow.png "przejdź do okna")  

Można także wprowadzić znak zapytania (?), aby uzyskać dodatkową pomoc.  

  ![Przejdź do wszystkich pomocy](media/gotoall_help.png)

### <a name="filtered-searches"></a>Filtrowane wyszukiwania  
Domyślnie określony element jest wyszukiwany w wszystkie elementy rozwiązania. Jednak można ograniczyć wyszukiwanie kod, tak aby elementy określonych typów przez prefacing terminy wyszukiwania z niektórych znaków. Filtr wyszukiwania można szybko zmienić, wybierając przycisków na pasku przejdź do okna dialogowego Okno narzędzi. Przyciski, które zmienić filtry typów są po lewej stronie i przyciski, które spowodują zmianę zakresu wyszukiwania są po prawej stronie.  

![Przejdź do elementów członkowskich](../ide/media/vside_navigation_toolbar.png)

#### <a name="filter-to-a-specific-type-of-code-element"></a>Filtruj dla określonego typu elementu kodu  
Aby zawęzić kryteria wyszukiwania dla określonego typu elementu kodu, możesz określ prefiks, w polu wyszukiwania lub wybierz jeden z pięciu ikony filtru:  

Prefiks | Ikona | Skrót | Opis
:----: | ---- | -------- | ---
\#      | ![Ikona symbol](media/gotoall_symbolicon.png) | CTRL + 1, Ctrl + S | Przejdź do określonego symbolu
F      | ![Ikona pliku](media/gotoall_fileicon.png)     | CTRL + 1, Ctrl + F | Przejdź do określonego pliku
m      | ![Ikona elementu członkowskiego](media/gotoall_membericon.png) | CTRL + 1, Ctrl + M | Przejdź do określonego elementu członkowskiego
t      | ![Ikona typu](media/gotoall_typeicon.png)     | CTRL + 1, Ctrl + T | Przejdź do określonego typu
:      | ![Ikona linii](media/gotoall_lineicon.png)     | Ctrl+G         | Przejdź do określonego numeru wiersza

#### <a name="filter-to-a-specific-location"></a>Filtrowanie do określonej lokalizacji    
Aby zawęzić kryteria wyszukiwania do określonej lokalizacji, wybierz jedną z ikon dwóch dokumentu:  

Ikona | Opis
---- | ---
![Bieżący dokument](media/gotoall_currentdocument.png) | Wyszukiwanie tylko bieżącego dokumentu
![Dokumenty zewnętrzne](media/gotoall_external.png) | Wyszukiwanie dokumentów zewnętrznych oprócz tych projektu/rozwiązania  

### <a name="camel-casing"></a>Mieszanej wielkości liter  
Jeśli używasz [mieszanej wielkości liter](https://en.wikipedia.org/wiki/Camel_case) w kodzie, wprowadzając tylko wielkie litery w nazwie elementu kodu można znaleźć szybsze elementy kodu. Na przykład, jeśli kod ma typ o nazwie `CredentialViewModel`, wybierając filtr typu ("t"), a następnie wprowadzając tylko wielkimi literami nazwę można zawęzić wyszukiwania (`CVM`) w oknie dialogowym Przejdź do. Ta funkcja może być przydatna, jeśli kod ma długie nazwy.  

![Przejdź do okna — Wyszukiwanie z literami](../ide/media/vside_capitalsearch.png)

### <a name="settings"></a>Ustawienia  
Wybieranie koło zębate ikonę ![Koło zębate ikonę](media/gotoall_gear.png) Pozwala zmienić sposób działania tej funkcji:  

Ustawienie | Opis
------- | ---
Karta Podgląd | Wyświetl wybrany element bezpośrednio na karcie Podgląd IDE
Pokaż szczegóły    | Wyświetl projekt, plik wiersza i informacje podsumowania z komentarzy do dokumentacji w oknie
Okno Center   | Przenieś to okno do góry środka edytora kodu, zamiast prawym górnym rogu   

## <a name="see-also"></a>Zobacz też  
[Nawigowanie po kodzie](../ide/navigating-code.md)  
[Przejdź do definicji i definicji wglądu](../ide/go-to-and-peek-definition.md)  