---
title: Edycja TableAdapters | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 995c1cfb5b125437847f364a01b66f3e551b8b4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681675"
---
# <a name="editing-tableadapters"></a>Edycja TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami możesz chcieć zmienić schemat tabeli karty. Aby to zrobić, należy zmodyfikować podstawowej karty sieciowej `Fill` metody. TableAdapters są tworzone za pomocą główna `Fill` metodę, która definiuje schemat tabeli powiązane dane. Głównym `Fill` Metoda opiera się na zapytanie lub procedura składowana wprowadzone podczas pierwotnie skonfigurowane TableAdapter; pierwszej metody (najwyższego poziomu) w tabeli danych znajduje się na [tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md).  
  
 ![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Wszelkie zmiany wprowadzone do elementu TableAdapter w głównym `Fill` metody są odzwierciedlane w schemat tabeli powiązane dane. Na przykład, usunięcie kolumny z zapytania w głównym `Fill` metoda spowoduje również usunięcie kolumny z tabeli powiązane dane. Ponadto usunięcie kolumny z głównym `Fill` metoda usuwa kolumnę z żadnych dodatkowych zapytań dla tego TableAdapter.  
  
 Możesz użyć **Kreatora konfiguracji zapytania TableAdapter** można tworzyć i edytować dodatkowych zapytań do TableAdapter. Te dodatkowe zapytania musi być zgodna z schemat tabeli, chyba że zwracają wartość skalarną.  Dodatkowe zapytania mają nazwy, który określisz (na przykład `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Aby uruchomić Kreatora konfiguracji zapytania TableAdapter za pomocą nowego zapytania  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**.  
  
2.  W przypadku tworzenia nowego zapytania, przeciągnij **zapytania** obiektu z **DataSet** karcie **przybornika** na <xref:System.Data.DataTable>, lub wybierz **Dodaj zapytanie**z menu skrótów TableAdapter. Możesz również przeciągnąć **zapytania** obiektu w pustym obszarem **Projektanta obiektów Dataset**, co powoduje utworzenie TableAdapter bez skojarzonego <xref:System.Data.DataTable>. Te zapytania są ograniczone do zwracanie wartości pojedynczej (skalarną) lub wykonaniu UPDATE, INSERT lub usunąć poleceń w bazie danych. Aby uzyskać więcej informacji, zobacz [porady: dodawanie zapytań globalnych do TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).  
  
3.  Na **wybierz połączenie danych** strony wybierz lub Utwórz połączenie, zostanie użyty.  
  
    > [!NOTE]
    >  Ta strona jest wyświetlana tylko wtedy, gdy projektant nie może określić odpowiednie połączenie lub gdy będzie dostępnych żadnych połączeń.  
  
4.  Na **wybierz typ polecenia** strony, wybierz jedną z następujących metod pobierania danych z bazy danych:  
  
    -   **Użyj instrukcji SQL** umożliwia wpisanie instrukcję SQL, aby wybrać dane z bazy danych.  
  
    -   **Utwórz nową procedurę składowaną** — wybierz tę opcję, aby kreator Tworzenie nowych procedur składowanych (w bazie danych) na podstawie określonej instrukcji SELECT.  
  
    -   **Używanie istniejących procedur składowanych** — wybierz tę opcję, aby wykonać istniejącą procedurę składowaną, podczas uruchamiania zapytania.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Aby uruchomić Kreatora konfiguracji zapytania TableAdapter na istniejące zapytanie  
  
-   Jeśli edytujesz istniejące zapytanie TableAdapter, kliknij prawym przyciskiem myszy zapytanie i wybierz polecenie **Konfiguruj** z menu skrótów.  
  
    > [!NOTE]
    >  Kliknij prawym przyciskiem myszy główne zapytanie TableAdapter ponownie konfiguruje TableAdapter i <xref:System.Data.DataTable> schematów, natomiast kliknij prawym przyciskiem myszy dodatkowych kwerend w metodzie TableAdapter umożliwia skonfigurowanie tylko wybrane zapytanie. **Kreator konfiguracji TableAdapter** ponownie konfiguruje definicji TableAdapter; **Kreatora konfiguracji zapytania TableAdapter** ponownie konfiguruje tylko wybrane zapytanie.  
  
## <a name="running-the-wizard"></a>Uruchamianie Kreatora  
 Przeciągnij zapytania na **Projektanta obiektów Dataset**, lub skonfigurować w istniejących zapytaniach (wszystkie wymienione poniżej pierwsze zapytanie zapytania).  
  
 Pierwsze zapytanie w TableAdapter jest zapytanietableadapter głównego. Otwiera do edycji tego głównego zapytania **Kreator konfiguracji TableAdapter** tworzyć i edytować schemat tabeli danych TableAdapter. Wszystkie zapytania wymienionych poniżej główne zapytanie dodatkowych zapytań i są skonfigurowane przy użyciu **Kreatora konfiguracji zapytania TableAdapter**. Aby uzyskać więcej informacji na temat uruchamiania kreatora, zobacz [porady: uruchom Kreator konfiguracji zapytania TableAdapter](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a).  
  
## <a name="choose-your-data-connection"></a>Wybierz połączenie danych  
 Wybierz istniejące połączenie z listy połączeń lub kliknij przycisk **nowe połączenie** do utworzenia połączenia z bazą danych.  
  
 Po zakończeniu **właściwości połączenia** okno dialogowe **szczegóły połączenia** obszarze są wyświetlane tylko do odczytu informacji na temat wybranego dostawcy, jak również parametry połączenia.  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>Zapisz parametry połączenia do pliku konfiguracji aplikacji  
 Wybierz **tak, Zapisz połączenie jako** do przechowywania parametrów połączenia w pliku konfiguracyjnym aplikacji. Wpisz nazwę połączenia, lub użyj podanej domyślnej nazwy.  
  
 Zapisywanie ciągów połączenia w pliku konfiguracji aplikacji upraszcza proces obsługi aplikacji, jeśli zmieni się połączenie z bazą danych. W przypadku zmiany połączenia z bazą danych możesz edytować parametry połączenia w pliku konfiguracyjnym aplikacji. Dzięki temu nie trzeba edytować kod źródłowy i ponownie skompilować aplikację. Aby uzyskać informacje na temat edytowania parametrów połączenia w pliku konfiguracyjnym aplikacji, zobacz [porady: zapisywanie i Edycja parametrów połączeń](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
> [!IMPORTANT]
>  Informacje są przechowywane w pliku konfiguracyjnym aplikacji jako zwykły tekst. Aby zmniejszyć prawdopodobieństwo nieautoryzowanego dostępu do poufnych informacji, można zaszyfrować dane. Aby uzyskać więcej informacji, zobacz [szyfrowanie i odszyfrowywanie danych](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## <a name="use-sql-statements"></a>Użyj instrukcji języka SQL  
 W tej sekcji opisano sposób wykonania **Kreatora konfiguracji zapytania TableAdapter** podczas wybierania **użyj instrukcji SQL** opcji.  
  
## <a name="choose-a-query-type"></a>Wybierz typ zapytania  
 Kreator tworzy kilka typów zapytania, w zależności od wymagań aplikacji. Możesz wybrać zapytań SELECT zwracanych wierszy danych (tabeli danych) lub wybierz zapytania oznacza zwracaną wartością skalarną (pojedynczą wartość, takie jak `Count` lub `Sum`).  
  
 Na **wybierz typ zapytania** wybierz typ zapytania do utworzenia z listy dostępnych zapytań.  
  
> [!NOTE]
>  Tworzenie instrukcji INSERT, UPDATE lub DELETE nie zastępuje polecenia TableAdapter, które są używane podczas wywoływania TableAdapter `Update` metody. Na przykład wybierając aktualizacji jako typ zapytania utworzy nową kwerendę o nazwie, które określisz później w kreatorze. To zapytanie jest wykonanie przez wywołanie tej metody o nazwie TableAdapter. Wywoływanie TableAdapter `Update` metoda wykona instrukcje utworzone podczas konfigurowania oryginalny obiekt TableAdapter.  
  
## <a name="specify-a-sql-query-type-statement"></a>Określ SQL \<typ zapytania > — instrukcja  
 Na **określić instrukcję SQL** wpisz instrukcję SQL do wykonania podczas wywoływania zapytania.  
  
> [!TIP]
>  Kreator udostępnia **konstruktora zapytań**, wizualne narzędzia do tworzenia zapytań SQL. Aby go otworzyć, kliknij przycisk **konstruktora zapytań** przycisku.  
  
## <a name="choose-methods-to-generate"></a>Wybierz metody do wygenerowania  
 Ta strona zawiera opcje dotyczące wybierania metody, które kreator generuje dla zapytania.  
  
 **Wypełnij DataTable**  
 Tworzy metodę do wypełniania tabeli danych. Przekazujesz Nazwa tabeli danych jako parametr w wywołaniu tej metody, aby wypełnić tabelę danych zwracanych danych.  
  
 Możesz również zmienić domyślną nazwę w **nazwę metody** pole. Podanie zrozumiałej nazwy mogą być pomocne podczas pracy z tym zapytaniem w kodzie.  
  
 **Zwraca DataTable**  
 Tworzy metodę, która zwraca tabelę danych wypełniony. W przypadku niektórych aplikacji może być bardziej pożądane zwracają tabelę danych wypełniony zamiast wypełnianie tabeli danych istniejących danych.  
  
 Możesz również zmienić domyślną nazwę w **nazwę metody** pole.  
  
## <a name="choose-function-name"></a>Wybierz nazwę funkcji  
 Wpisz nazwę dla tej funkcji. Trwa tworzenie zapytania TableAdapter dodaje metodę do TableAdapter o nazwie podane tutaj. Wywołaj tę metodę, aby wykonać zapytanie. Podanie zrozumiałej nazwy jest przydatne podczas pracy z tym zapytaniem w kodzie.  
  
> [!NOTE]
>  Tworzenie nowych procedur składowanych, użytkownik zostanie poproszony o dwie nazwy. Imię jest nazwa procedury składowanej, utworzone w bazie danych. Nazwa drugiego jest nazwa metody na obiekt TableAdapter, która wykonuje procedurę składowaną, gdy zostanie wywołana.  
  
## <a name="create-new-stored-procedures"></a>Tworzenie nowych procedur składowanych  
 W tej sekcji opisano sposób wykonania **Kreatora konfiguracji zapytania TableAdapter** podczas wybierania **tworzenie nowych procedur składowanych** opcji.  
  
1.  W **wygenerować procedur składowanych** wpisz instrukcję SQL do wykonania podczas wywoływania procedury składowanej.  
  
    > [!NOTE]
    >  Kreator udostępnia **konstruktora zapytań**, wizualne narzędzia do tworzenia zapytań SQL. Aby go otworzyć, kliknij przycisk **konstruktora zapytań** przycisku.  
  
2.  W **Tworzenie procedur składowanych** wykonaj następujące czynności:  
  
    1.  Wpisz nazwę dla nowej procedury składowanej.  
  
    2.  Określ, czy należy utworzyć procedurę składowaną w bazie danych.  
  
        > [!NOTE]
        >  Możliwość tworzenia procedurę składowaną w bazie danych jest określany przez ustawienia zabezpieczeń dla konkretnej bazy danych.  
  
     **Wyświetlanie wyników kreatora** strony pokazuje wyniki tworzenia zapytań TableAdapter. Jeśli kreator wykryje problemy, ta strona zawiera informacje o błędzie.  
  
## <a name="use-existing-stored-procedures"></a>Używanie istniejących procedur składowanych  
 W tej sekcji opisano sposób wykonania **Kreatora konfiguracji zapytania TableAdapter** podczas wybierania **używanie istniejących procedur składowanych** opcji.  
  
1.  Wybierz istniejącą procedurę składowaną z listy rozwijanej na **wybierz istniejącą procedurę składowaną** strony kreatora.  
  
     **Parametry** i **wyniki** dla wybranego przechowywane procedury są wyświetlane dla odwołania.  
  
2.  Kliknij przycisk **Dalej**.  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>Wybierz kształt danych zwracanych przez procedurę składowaną  
 Typ danych zwracanych przez wybranej procedury składowanej Określa, jak Kreator tworzy metody TableAdapter.  
  
 Wybierz typ danych zwracanych przez tę kwerendę.  
  
-   Wybieranie **dane tabelaryczne** otwiera **Wybierz metody do generowania** strony (opisanym wcześniej, na tej stronie pomocy), co pozwala na określenie typów, metod, nazwy metod i obsługę stronicowania ma zostać utworzony.  
  
-   Wybieranie **pojedynczą wartość** tworzy wpisanej metody, która zwraca pojedynczą wartość. Ta opcja umożliwia otwarcie **wybierz nazwę funkcji** strony (opisanym wcześniej na tej stronie pomocy).  
  
-   Wybieranie **żadnej wartości** tworzy wpisane metodę, która wykonuje procedurę składowaną i oczekuje, że żadne dane, które mają zostać zwrócone. Ta opcja umożliwia otwarcie **wybierz nazwę funkcji** strony (opisanym wcześniej na tej stronie pomocy).  
  
## <a name="view-wizards-results"></a>Wyświetlanie wyników kreatorów  
 **Wyświetlanie wyników kreatora** strony pokazuje wyniki tworzenia zapytań TableAdapter. Jeśli kreator wykryje problemy, szczegółowe informacje są wyświetlane na tej stronie.  
  
## <a name="see-also"></a>Zobacz też  
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Porady: edytowanie zapytań TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Przegląd aplikacji w programie Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)