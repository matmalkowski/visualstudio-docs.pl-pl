---
title: Tworzenie i konfigurowanie TableAdapters | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 11086ba17f3f2fb7af99d76b3efadece4a23c426
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="create-and-configure-tableadapters"></a>Tworzenie i konfigurowanie TableAdapters
TableAdapters zapewniają komunikację pomiędzy aplikacją i bazą danych. Łączą się z bazy danych, uruchom zapytania lub procedur składowanych i zwrócenie danych nowej tabeli lub wypełnienia istniejące <xref:System.Data.DataTable> z zwróconych danych. TableAdapters może także wysłać zaktualizowane dane z aplikacji w bazie danych.  
  
TableAdapters są tworzone automatycznie podczas wykonywania jednej z następujących czynności:  
  
-   Uruchom [Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png) i wybierz opcję **bazy danych** lub **usługi sieci Web** typ źródła danych.  
  
-   Przeciągnij obiekty z **Eksploratora serwera** do **Projektant obiektów Dataset**.  
  
Można również utworzyć nowy obiekt TableAdapter i skonfiguruj ją ze źródłem danych, przeciągając TableAdapter z przybornika do pustego regionu w **Projektant obiektów Dataset** powierzchni.  
  
Aby obejrzeć wprowadzenie do TableAdapters, zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>Za pomocą Kreatora konfiguracji TableAdapter  
Uruchom **TableAdapter Kreator konfiguracji** do tworzenia lub edytowania TableAdapters i ich skojarzonych DataTables. Można skonfigurować istniejącą TableAdapter przez kliknięcie prawym przyciskiem myszy w **Projektant obiektów Dataset**.  
  
![raddata Kreatora konfiguracji adaptera tabeli](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata Kreatora konfiguracji adaptera tabeli")  
  
Jeśli nowy obiekt TableAdapter jest przeciągnij z przybornika po **Projektant obiektów Dataset** skupić się uruchomieniu kreatora i monitów, możesz określić, które dane źródłowe TableAdapter powinien połączyć się z. Na następnej stronie Kreator zapyta, jakiego rodzaju polecenia go powinna być używana do komunikacji z bazą danych, instrukcji SQL lub procedur składowanych. (Nie zobaczysz to w przypadku konfigurowania TableAdapter, która jest już skojarzony ze źródłem danych.)  
  
-   Masz opcję, aby utworzyć nową procedurę składowaną w bazie danych, jeśli masz odpowiednie uprawnienia do bazy danych. Jeśli użytkownik nie ma tych uprawnień, będzie to opcja.  
  
-   Można również uruchomić istniejących procedur składowanych **wybierz**, **Wstaw**, **aktualizacji**, i **usunąć** polecenia TableAdapter. Procedury przechowywanej, która jest przypisana do **aktualizacji** polecenia, na przykład jest uruchomiony, jeśli `TableAdapter.Update()` metoda jest wywoływana.  
  
Mapuj parametry z wybranej procedury składowanej na odpowiednie kolumny w tabeli danych. Na przykład, jeśli Twoja procedura składowana akceptuje parametr o nazwie `@CompanyName` przesyłanego do `CompanyName` zestawu kolumn w tabeli, **kolumny źródłowej** z `@CompanyName` parametr `CompanyName`.  
  
> [!NOTE]
>  Procedury przechowywanej, która jest przypisana do wybierz polecenie jest uruchamiane, wywołując metodę TableAdapter o nazwie w następnym kroku kreatora. Domyślną metodą jest `Fill`, więc jest kod, który jest zwykle używane do uruchamiania procedury wybierz `TableAdapter.Fill(tableName)`. Jeśli zmienisz nazwę domyślną z `Fill`, Zastąp `Fill` o nazwie przypisać i zastąp "TableAdapter" rzeczywistą nazwą TableAdapter (na przykład `CustomersTableAdapter`).  
  
-   Wybieranie **Utwórz metody wysyłania aktualizacje bezpośrednio z bazą danych** opcja jest równoważna wartości ustawienia `GenerateDBDirectMethods` właściwości na wartość true. Opcja jest niedostępna, jeśli oryginalna instrukcja SQL nie zawiera wystarczającej ilości informacji lub zapytania nie można aktualizować zapytania. Taka sytuacja może wystąpić, na przykład w **JOIN** zapytania i zapytań zwracających pojedynczą wartość (skalarną).  
  
**Zaawansowane opcje** w Kreatorze umożliwiają:  
- Generuj instrukcje INSERT, UPDATE i DELETE na instrukcji SELECT, która jest zdefiniowana na podstawie **instrukcji SQL Generowanie** strony
- Użyj optymistycznej współbieżności
- Określ, czy Odśwież tabelę danych po WSTAWIENIU i są uruchamiane w instrukcji UPDATE  
  
## <a name="configure-a-tableadapters-fill-method"></a>Skonfiguruj TableAdapter Fill — metoda  
Czasami można zmienić schemat tabeli TableAdapter. W tym celu należy zmodyfikować podstawowy element TableAdapter `Fill` metody. TableAdapters są tworzone za pomocą podstawowego `Fill` metodę, która definiuje schemat tabeli skojarzonych danych. Podstawowy `Fill` metoda jest oparta na zapytanie lub procedura składowana wprowadzone podczas konfigurowania pierwotnie TableAdapter. Jest to pierwszy (metody najwyższego poziomu) w tabeli danych w Projektancie obiektów DataSet.  
  
![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif "TableAdapter")  
  
Wszelkie zmiany wprowadzone w TableAdapter obiektu głównego `Fill` metody są uwzględniane w schemat tabeli skojarzonych danych. Na przykład usunięcie kolumny z zapytania w głównym `Fill` metody spowoduje również usunięcie kolumny z tabeli skojarzonych danych. Ponadto usunięcie kolumny z głównym `Fill` — metoda usuwa kolumnę z żadnych dodatkowych zapytań dla tej TableAdapter.  
  
Kreator konfiguracji zapytania TableAdapter służy do tworzenia i edycji dodatkowych zapytań TableAdapter. Te dodatkowe zapytania musi być zgodna z schemat tabeli, chyba że zwracają wartość skalarną.  Każdy dodatkowego zapytania ma nazwę użytkownika.  
 
Poniższy przykład przedstawia sposób wywołania dodatkowe kwerendę o nazwie `FillByCity`:  
 
`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Aby uruchomić Kreator konfiguracji zapytania TableAdapter z nowej kwerendy  
  
1.  Otwórz zestaw danych w **Projektant obiektów Dataset**.  
  
2.  W przypadku tworzenia nowego zapytania, przeciągnij **zapytania** obiekt z **DataSet** karty **przybornika** na <xref:System.Data.DataTable>, lub wybierz **Dodaj zapytanie**menu skrótów TableAdapter. Możesz także przeciągnąć **zapytania** obiektu na pustym obszarem **Projektant obiektów Dataset**, co powoduje TableAdapter bez skojarzonego <xref:System.Data.DataTable>. Te zapytania można tylko zwrócić jednej wartości (skalarnych) lub uruchom UPDATE, INSERT lub usunąć poleceń w bazie danych.  
  
3.  Na **wybierz połączenie danych** ekranu wybierz lub Utwórz połączenie, który będzie używany przez zapytanie.  
  
    > [!NOTE]
    >  Ten ekran jest wyświetlany tylko, gdy projektant nie może określić prawidłowego połączenia do użycia, lub jeśli nie są dostępne żadne połączenia.  
  
4.  Na **wybierz typ polecenia** ekranu wybierz jedną z następujących metod pobieranie danych z bazy danych:  
  
    -   **Użyj instrukcji SQL** umożliwia wpisz instrukcję SQL, aby wybrać dane z bazy danych.  
  
    -   **Utwórz nową procedurę składowaną** umożliwia, aby Kreator tworzenia nowego przechowywane procedury (w bazie danych) na podstawie określonej instrukcji SELECT.  
  
    -   **Użyj istniejących procedur składowanych** umożliwia uruchamianie istniejącą procedurę składowaną podczas uruchamiania zapytania.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Aby uruchomić Kreatora konfiguracji zapytania TableAdapter na istniejące zapytanie  
  
-   Jeśli edytujesz istniejące zapytanie TableAdapter, kliknij prawym przyciskiem myszy kwerendę, a następnie wybierz **Konfigurowanie** z menu skrótów.  
  
    > [!NOTE]
    >  Prawym przyciskiem myszy główne zapytanie TableAdapter spowoduje zmianę konfiguracji TableAdapter i <xref:System.Data.DataTable> schematu. Jednak prawym przyciskiem myszy dodatkowych zapytań w TableAdapter, konfiguruje wybrane zapytanie. **TableAdapter Kreator konfiguracji** ponownie konfiguruje definicji TableAdapter, podczas gdy Kreator konfiguracji zapytania TableAdapter ponownie konfiguruje wybrane zapytanie.  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Aby dodać zapytanie globalne do TableAdapter  
  
-   *Zapytania globalne* zapytań SQL, które zwraca pojedynczą wartość (skalarną) lub brak wartości. Zwykle funkcje globalne wykonywać operacje bazy danych, takie jak usuwa operacji wstawienia, aktualizacje. Agregować one również informacje, takie jak liczba klientów w tabeli lub sumę opłat dla wszystkich elementów w określonej kolejności.  
  
     Dodawanie zapytań globalnych przeciągając **zapytania** obiekt z **DataSet** karty **przybornika** na pustym obszarem **Projektant obiektów Dataset**.  
  
-   Podaj kwerendę, która wykonuje żądane zadanie, na przykład `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Przeciąganie **zapytania** obiekt bezpośrednio na **Projektant obiektów Dataset** tworzy metodę, która zwraca tylko (jeden) wartość skalarną. Gdy zapytanie lub procedura składowana, którą wybierzesz może zwrócić więcej niż jedną wartość, metody, która jest tworzony przez kreatora tylko zwraca pojedynczą wartość. Na przykład zapytanie może zwrócić pierwszą kolumnę pierwszego wiersza zwrócone dane.

## <a name="see-also"></a>Zobacz także
[Wypełnianie zbiorów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)