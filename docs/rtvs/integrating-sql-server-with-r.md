---
title: Integrowanie programu SQL Server z języka R
description: Program Visual Studio obsługuje tworzenie i uruchamianie zapytania SQL z R i możliwość wykonywania R, aby pracować z procedur składowanych.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 31d02ffb64539f906d91f68d18c6ad52b347e4e6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="working-with-sql-server-and-r"></a>Praca z programu SQL Server i R

Znakomity obsługi programu Visual Studio dla programu SQL Server ułatwia dane, które służące pracować z bazami danych SQL i R dzięki możliwości do tworzenia i uruchamiania kwerend SQL i do pracy z procedur składowanych.

> [!Note]
> Aby współpracować z SQL i R, musi mieć SQL Server Data Tools zainstalowane:
> - Visual Studio 2017: uruchom Instalator programu Visual Studio i wybierz magazyn danych i przetwarzania obciążenia, w tym narzędzi danych programu SQL Server.
> - Visual Studio 2015: postępuj zgodnie z instrukcjami [pobierania programu SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (witrynie youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ) Omówienie programu SQL Server i R (3 m 03s). |

## <a name="creating-and-running-sql-queries"></a>Tworzenie i uruchamianie zapytań SQL

RTVS obsługuje dodawanie zapytania SQL w projektach R, umożliwiając wielokrotnie powtarzane tworzenie zapytań SQL w kontekście oddzielne do momentu uzyskania wyników, którego szukasz.

Aby dodać plik zapytania SQL, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań wybierz **Dodaj > Nowy element...** i wybierz **zapytania SQL** typ pliku:

![Dodaj element zapytanie SQL do projektu](media/sql-add-item.png)

To polecenie otwiera plik w edytorze języka Transact-SQL programu Visual Studio, który zapewnia pełne IntelliSense dla SQL i możliwość uruchamiania zapytań. Dla tych funkcji należy nawiązać połączenia z bazą danych za pomocą przycisku Połącz w edytorze paska narzędzi lub przy próbie uruchomienia kwerendy (Ctrl + Shift + E, które działa także w wyborze). W obu przypadkach wyświetlenie okna dialogowego połączenia:

![Okno dialogowe połączenia SQL](media/sql-connection-dialog.png)

Po nawiązaniu połączenia można uruchamiać zapytania i wyświetlić wyniki:

![Wyniki zapytania SQL okna](media/sql-query-results.png)

Edytor języka Transact-SQL obsługuje wiele innych funkcji, takich jak wyświetlanie plan wykonania zapytania i debuger zapytania.
Aby uzyskać więcej informacji, zobacz [Użyj edytora języka Transact-SQL do edycji i wykonywanie skryptów](https://msdn.microsoft.com/library/hh272706.aspx).

## <a name="working-with-sql-server-stored-procedures"></a>Procedury składowane w pracy z programem SQL Server

[Usług SQL Server R](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) procedury składowanej (SQL Server 2016 lub nowszy) umożliwia osadzanie i uruchamiać kod języka R z T-SQL. Można uruchomić R kodu na komputerze programu SQL Server, działają na dane zwrócone w wyniku zapytania SQL i wygenerować zestaw wyników SQL, które mogą być przetwarzane przez dalsze SQL lub zwracana do klienta.

RTVS upraszcza inaczej niewygodna błędów oraz łączenia kodu SQL i R wewnątrz jednej instrukcji SQL, zgodnie z opisem w poniższych sekcjach:

- [Dodaj połączenie z bazą danych](#add-a-database-connection)
- [Pisania i testowania procedury składowane SQL](#write-and-test-a-sql-stored-procedure)
- [Publikowanie procedury składowane SQL](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (witrynie youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ) omówienie R i SQL przechowywanych procedur (6 mln 09s). |

### <a name="add-a-database-connection"></a>Dodaj połączenie z bazą danych

1. Wybierz **narzędzia R > danych > Dodaj połączenie z bazą danych** można wyświetlić **właściwości połączenia** okna dialogowego. W tym miejscu Określ nazwę źródła danych (SQL Server, w tym przypadku), nazwę serwera, tryb uwierzytelniania i nazwę bazy danych. Wybierz **Testuj połączenie** Aby sprawdzić wprowadzone dane przed zamknięciem okna dialogowego.

    ![W oknie dialogowym połączenia SQL](media/sql-connection-string-dialog.png)

1. Po wybraniu **OK** prawidłowe połączenie z programu Visual Studio generuje ciąg połączenia o nazwie `dbConnection` w nowym `settings.R` pliku. RTVS automatycznie źródeł (działa) tego pliku, dzięki czemu można od razu użyć połączenia ze skryptów R:

![Plik SQL Settings.R](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Pisania i testowania procedury składowane SQL

Aby dodać nowe procedury składowanej SQL, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj > Nowy element...** , wybierz pozycję **procedury składowanej SQL z R** z listy szablonów, nadaj plikowi nazwę (`StoredProcedure.R` w tym przykładzie) i wybierz **OK**.

RTVS tworzy trzy pliki dla procedury składowanej: `.R` pliku dla kodu języka R, `.Query.sql` kod SQL w pliku i `.Template.sql` pliku, który łączy dwa. Ostatnie dwa są wyświetlane w Eksploratorze rozwiązań jako elementy podrzędne są `.R` pliku:

![Eksplorator rozwiązań rozszerzony widok procedury składowanej SQL z języka R](media/sql-solution-explorer-expanded.png)

`StoredProcedure.R` (w tym przykładzie) jest, gdzie należy wpisać kod R. Wartości domyślne są:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Prostu, kod odbiera dataframe R o nazwie `InputDataSet` i zwraca wyniki w `OutputDataSet`, kodem szablonu jedynie kopiowania danych wejściowych do danych wyjściowych.

> [!Note]
> Nazwy tych dataframes są kontrolowane przez `@input_data_1_name` i `@output_data_1_name` parametrów w wywołaniu `sp_execute_external_script` procedury składowanej systemu. Aby uzyskać więcej informacji na temat projektowania Konwencja wywoływania i przykłady ich użycia, zobacz [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Wygenerowany kod (w komentarzach) zawiera skrypt teście małych, który używa [pakietu RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) do przesyłania instrukcję SQL z programem SQL Server, uruchom go i pobrać jego zestawu wyników jako dataframe R. Użytkownik może usuń znaczniki komentarza Ustaw ten kod testu, aby interaktywnie wpisz swój kod R wyniku uzyskanie programu SQL Server.

`StoredProcedure.Query.sql` Zapis i przetestować zapytanie SQL, które generuje dane dotyczące `InputDataSet`. Z tym `.sql` plik, Edytor zawiera wszystkie funkcje języka Transact-SQL zwykle do Ciebie.

Po zakończeniu modyfikowania swoim własnym kodem SQL, zintegrować ją z kodu języka R w `StoredProcedure.R` przeciągając `.sql` pliku na Otwórz edytor dla `.R` pliku. Na ilustracji poniżej `StoredProcedure.Query.sql` został przeciągnięty do punktu po przecinku w `sqlQuery(channel, )`:

![Odczytywanie plików SQL do zmiennej ciągu R](media/sql-reference-sql-file-from-r.png)

Jak widać, w tym kroku proste automatycznie generuje kod języka R, aby otworzyć `.sql` , odczytać jego zawartości na ciąg znaków, a następnie przekaż go do pakietu RODBC do wysyłania do programu SQL Server.

Możesz teraz interaktywnie zapisu R obsługujące `InputDataSet` dataframe zgodnie z potrzebami. Należy pamiętać, że można po prostu wybierz R kodu w edytorze i wysyłać je do [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md) przez naciśnięcie klawiszy Ctrl + Enter.

`StoredProcedure.Template.sql`, zawiera wreszcie szablonu służącego do generowania procedury składowanej SQL:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- `_RCODE_` Symbol zastępczy zostanie zastąpiony przez zawartość `StoredProcedure.R`.
- `_INPUT_QUERY_` Symbol zastępczy zostanie zastąpiony przez zawartość `StoredProcedure.Query.sql`.
- Edytuj `WITH RESULT SETS` klauzuli do opisywania schemat zestawu zwrócone z procedury składowanej wyników. W szczególności zidentyfikować kolumny z `OutputDataSet` dataframe, który chcesz przywrócić do obiektu wywołującego procedurę składowaną. 

Na przykład dla następującej kwerendy:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Należy użyć następujących `WITH RESULT SETS` klauzuli, aby określić typy wartości zwracanych danych:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Publikowanie procedury składowane SQL

1. Wybierz **narzędzia R > danych > Publikowanie za pomocą opcji...**  polecenia menu.
1. W oknie dialogowym, zmień **publikowania:** do **bazy danych**, określ cel, wybierz **publikowania**, i RTVS kompilacje i publikuje procedury składowanej:

    ![Procedura składowana okna dialogowego publikowania](media/sql-publish-with-options.png)

1. Aby opublikować wszystkie procedury składowane w projekcie, można użyć **narzędzia R > danych > publikować procedur składowanych** polecenia, które jest również dostępna po kliknięciu prawym przyciskiem myszy projekt w Eksploratorze rozwiązań.

> [!Tip]
> Jeśli masz Eksplorator obiektów SQL Server Otwórz w programie Visual Studio, Twoja procedura składowana opublikowanych pojawia się w **programowania > procedur składowanych** folder bazy danych. Można również uruchomić go w Eksploratorze obiektów prawym przyciskiem myszy i wybierając **wykonaj procedurę**, lub przez wywołanie metody interakcyjnie z `.sql` oknie zapytania.
