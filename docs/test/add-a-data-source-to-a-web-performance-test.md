---
title: Dodawanie źródła danych do testu wydajności sieci web w programie Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 1ec0171efa5f394551aff8caeb7d8a0622db9207
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844810"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Dodawanie źródła danych do testu wydajności sieci Web

Powiązanie danych, aby zapewnić różne wartości tych testów, na przykład, aby zapewnić parametrów post różne wartości do formularza.

 ![Wiązanie danych do testu wydajności sieci web](../test/media/web_test_databinding_conceptual.png)

 Chcemy użyć przykładowej aplikacji ASP.NET. Składa się z trzech strony .aspx — domyślnej strony, strony czerwony i niebieski strony. Domyślna strona zawiera formant radiowych, aby wybrać czerwony lub niebieski i przycisk przesyłania. Dwie pozostałe strony .aspx są bardzo proste. Jeden z nich ma etykietę o nazwie Red i innych ma etykietę o nazwie niebieski. Po wybraniu przesłać na stronie domyślnej wyświetli jeden z innych stron. Możesz pobrać [ColorWebApp](http://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) przykładowe lub po prostu wykonaj, wraz z aplikacji sieci web.

 ![Aplikacją sieci web ma zostać przetestowana](../test/media/web_test_databinding_runwebapp.png)

 Rozwiązanie powinno również uwzględniać testu wydajności sieci web, które umożliwia wyszukanie na stronach w aplikacji sieci web.

 ![Rozwiązania z testem wydajności sieci web](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Utwórz bazę danych SQL

1. Jeśli nie masz programu Visual Studio Enterprise cand można go pobrać z [programu Visual Studio pobiera](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) strony.

2. Utwórz bazę danych SQL.

     ![Dodaj nową bazę danych SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Utwórz projekt bazy danych.

     ![Utwórz nowy projekt z bazy danych](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Dodawanie tabeli do projektu bazy danych.

     ![Dodaj nową tabelę do projektu bazy danych](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Dodawanie pól do tabeli.

     ![Dodawanie pól do tabeli](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Publikuj projekt bazy danych.

     ![Publikowanie bazy danych projektu w Eksploratorze rozwiązań](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Dodawanie danych do pola.

     ![Dodawanie danych do pól](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

## <a name="add-the-data-source"></a>Dodawanie źródła danych

1. Dodawanie źródła danych.

     ![Dodawanie źródła danych do testu wydajności sieci web](../test/media/web_test_databinding_sql_adddatasource.png)

2. Wybierz typ źródła danych i nadaj mu nazwę.

     ![Nazwa źródłowej bazy danych](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Utwórz połączenie.

     ![Wybierz nowe połączenie](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Wprowadź informacje dotyczące połączenia.

     ![Wprowadź właściwości połączenia bazy danych SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Wybierz tabelę, która ma być używany dla testu.

     ![Dodaj jako źródło danych w tabeli kolorów](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     Powiązana tabela jest test.

     ![Dodaj węzeł źródła danych do testu wydajności sieci web](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Zapisz testu.

## <a name="bind-the-data"></a>Powiązanie danych

1. Powiązać pole ColorName.

     ![Powiązać pole ColorName RadioButtonList1 wartości](../test/media/web_test_databinding_sql_binddatasource.png)

2. Otwórz plik Local.testsettings w Eksploratorze rozwiązań i wybierz jeden przebieg poszczególnych opcji wiersz źródła danych.

     ![Edytuj plik ustawień testu](../test/media/web_test_databinding_sql_testsettings.png)

3. Zapisz testu wydajności sieci web.

## <a name="run-the-test-with-the-data"></a>Uruchom test z danymi

1. Uruchom test.

     ![Uruchamianie testu wydajności sieci web, aby sprawdzić powiązania](../test/media/web_test_databinding_sql_runtest.png)

     Dla każdego wiersza danych są wyświetlane dwa przebiegi. Uruchom 1 wysyła żądanie strony Red.aspx i uruchom 2 wysyła żądanie strony Blue.aspx.

     ![Wyniki uruchomienia testu](../test/media/web_test_databinding_sql_runresults.png)

     Po powiązaniu ze źródłem danych, może naruszyć domyślną regułę adres URL odpowiedzi. W takim przypadku błąd podczas uruchamiania 2 jest spowodowany przez reguły, która oczekuje stronę Red.aspx z oryginalnego rejestrowania testu, ale teraz powiązania danych kieruje je do strony Blue.aspx.

2. Popraw błąd sprawdzania poprawności, usuwanie reguły sprawdzania poprawności adresu URL odpowiedzi i ponowne uruchomienie testu.

     ![Usuń regułę walidacji adresu URL odpowiedzi](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Test wydajności sieci web przechodziła używanie powiązania danych.

     ![Test zakończył się pomyślnie używanie powiązania danych](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Pytanie: jakie bazy danych można użyć jako źródła danych?

**Odpowiedź:** można użyć następujących:

- Microsoft SQL Azure.

- Dowolna wersja programu Microsoft SQL Server 2005 lub nowszego.

- Plik bazy danych programu Microsoft SQL Server (w tym programu SQL Express).

- Microsoft ODBC.

- Plik programu Microsoft Access za pomocą dostawcy .NET Framework dla OLE DB.

- Oracle 7.3, 8i, 9i lub 10 GB/s.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Pytanie: jak używać plik tekstowy (CSV) wartości rozdzielonych przecinkami jako źródło danych?

**Odpowiedź:** Oto jak:

1. Utwórz folder do organizowania artefakty bazy danych z projektów i dodać element.

     ![Dodaj nowy element do folderu danych](../test/media/web_test_databinding_foldernewitem.png)

2. Utwórz plik tekstowy.

     ![Nazwa nowego pliku tekstowego ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Edytuj plik tekstowy i dodaj następujące informacje:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Wykonaj kroki w [Dodaj źródło danych](#add-the-data-source), ale wybierz plik CSV jako źródła danych.

     ![Wprowadź nazwę i wybierz plik CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Pytanie: co zrobić, jeśli Mój istniejący plik CSV nie zawiera nagłówki kolumn?

**Odpowiedź:** , jeśli nie można dodać nagłówków kolumn, można użyć pliku opisu schematu można traktować jako baza danych pliku CSV.

1. Dodaj nowy plik tekstowy o nazwie schema.ini.

     ![Dodaj plik schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Edytuj plik schema.ini, aby dodać informacje opisujące struktury danych. Na przykład plik schematu opisujący plik CSV może wyglądać następująco:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Dodawanie źródła danych do testu.

     ![Dodawanie źródła danych do testu wydajności sieci web](../test/media/web_test_databinding_sql_adddatasource.png)

4. Jeśli używasz Plik schema.ini, wybierz bazę danych (nie plik CSV), jako źródło danych i nadaj mu nazwę.

     ![Dodawanie źródła danych bazy danych](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Utwórz nowe połączenie.

     ![Wybierz nowe połączenie](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Wybierz dla programu .NET Framework Data Provider for OLE DB.

     ![Wybierz dostawcy danych OLE DB programu .NET framework](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Wybierz pozycję Zaawansowane.

     ![Wybierz polecenie Zaawansowane](../test/media/web_test_databinding_advanced.png)

8. Dla właściwości dostawcy wybierz Microsoft.Jet.OLEDB.4.0, a następnie ustaw właściwości rozszerzone do tekstu; HDR = NIE.

     ![Zastosuj właściwości zaawansowane](../test/media/web_test_databinding_advancedproperties.png)

9. Wpisz nazwę folderu, który zawiera plik schematu i przetestować połączenie.

     ![Wprowadź ścieżkę do folderu danych](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Wybierz plik CSV, który ma być używany.

     ![Zaznacz plik tekstowy](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Po zakończeniu zostanie wyświetlony plik CSV jako tabelę.

     ![Źródło danych dodane do testowania](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Pytanie: jak używać pliku XML jako źródło danych?

**Odpowiedź:** tak.

1. Utwórz folder do organizowania artefakty bazy danych z projektów i dodać element.

     ![Dodaj nowy element do folderu danych](../test/media/web_test_databinding_foldernewitem.png)

2. Tworzenie pliku XML.

     ![Dodaj plik ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Edytuj plik XML i dodać dane:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Wykonaj kroki w [Dodaj źródło danych](#add-the-data-source), ale wybierz plik XML jako źródła danych.

     ![Wprowadź nazwę i wybierz plik XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Pytanie: czy można dodać powiązania danych na żądanie usługi sieci web, która używa protokołu SOAP?

**Odpowiedź:** tak, ręcznie należy zmienić plik XML protokołu SOAP.

1. Wybierz żądanie usługi sieci web w drzewie żądania i w oknie właściwości, wybierz wielokropek (...) we właściwości ciągów tekstowych.

     ![Edycja ciągów tekstowych usługi sieci web](../test/media/web_test_databinding_webservicerequest.png)

2. Zastąp wartości w treści protokołu SOAP wartości powiązane z danymi przy użyciu następującej składni:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Na przykład, jeśli masz następujący kod:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Można zmienić go do tego:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Zapisz testu.