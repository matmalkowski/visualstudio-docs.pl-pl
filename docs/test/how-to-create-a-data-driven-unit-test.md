---
title: 'Porady: Tworzenie testu jednostkowego opartego na danych | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 74d271b6d1c9124d323b9c1ecbbfe9e716b1c5b8
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Porady: tworzenie testu jednostkowego opartego na danych
Za pomocą frameworka testów jednostkowych Microsoft dla kodu zarządzanego, można skonfigurować metody testowej jednostki można pobrać wartości używanych w metodzie testowej ze źródła danych. Metoda jest uruchamiane kolejno dla każdego wiersza w źródle danych, co ułatwia testowanie różnych danych wejściowych przy użyciu pojedynczej metody.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Metoda w ramach testu](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [Tworzenie źródła danych](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [Dodawanie TestContext do klasy testowej](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [Pisanie metody testowej](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [Określanie DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [Aby uzyskać dostęp do danych za pomocą TestContext.DataRow](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [Uruchamianie testu i wyświetlanie wyników](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 Tworzenie testów jednostkowych opartych na danych obejmuje następujące kroki:  
  
1.  Utwórz źródło danych, która zawiera wartości, które używają w metodzie testowej. Źródła danych mogą być dowolnego typu, która jest zarejestrowana na komputerze z systemem testu.  
  
2.  Dodaj prywatnej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pola i publiczny `TestContext` właściwości klasy testowej.  
  
3.  Utwórz metody testowej jednostki i Dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> do niej atrybut.  
  
4.  Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> właściwości indeksatora można pobrać wartości używanych w teście.  
  
##  <a name="BKMK_The_method_under_test"></a>Metoda w ramach testu  
 Na przykład załóżmy, że firma Microsoft zostały utworzone:  
  
1.  Rozwiązanie o nazwie `MyBank` akceptuje i przetwarzania transakcji dla różnych typów kont.  
  
2.  Projekt w `MyBank` o nazwie `BankDb` który zarządza transakcji dla kont.  
  
3.  Klasa o nazwie `Maths` w `DbBank` projektu, który wykonuje funkcji matematycznych w celu zapewnienia korzystne Bankowi każdej transakcji.  
  
4.  Testu jednostkowego do projektu o nazwie `BankDbTests` do testowania zachowanie `BankDb` składnika.  
  
5.  Klasa o nazwie testu jednostkowego do `MathsTests` Aby sprawdzić zachowanie `Maths` klasy.  
  
 Firma Microsoft będzie testuje metody w `Maths` dodaje dwie liczb całkowitych za pomocą pętli:  
  
```  
public int AddIntegers(int first, int second)  
{  
    int sum = first;  
    for( int i = 0; i < second; i++)  
    {  
        sum += 1;  
    }  
    return sum;  
}  
```  
  
##  <a name="BKMK_Creating_a_data_source"></a>Tworzenie źródła danych  
 Aby przetestować `AddIntegers` metody, utworzymy źródła danych, która określa zakres wartości dla parametrów i sum, które mają zostać zwrócone. W naszym przykładzie tworzymy bazy danych Sql Compact `MathsData` i tabela o nazwie `AddIntegersData` zawiera następujące nazwy kolumn i wartości  
  
|Pierwszaliczba|SecondNumber|Suma|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|-3|-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a>Dodawanie TestContext do klasy testowej  
 Framework testów jednostkowych tworzy `TestContext` obiekt, aby zapisać informacje o źródle danych dla testów opartych na danych. Następnie ustawia ten obiekt jako wartość w ramach `TestContext` właściwość, która utworzymy.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 W metodę testu, możesz uzyskać dostęp do danych za pośrednictwem `DataRow` właściwości indeksatora `TestContext`.  
  
##  <a name="BKMK_Writing_the_test_method"></a>Pisanie metody testowej  
 Metoda testowa dla `AddIntegers` jest dość proste. Dla każdego wiersza w źródle danych nazywamy `AddIntegers` z **Pierwszaliczba** i **Drugaliczba** wartości kolumny jako parametry i zweryfikowanie wartości zwracanej przed **suma**wartość kolumny:  
  
```  
  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]  
[TestMethod()]  
public void AddIntegers_FromDataSourceTest()  
{  
    var target = new Maths();  
  
    // Access the data  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.IntegerMethod(x, y);  
    Assert.AreEqual(expected, actual,  
        "x:<{0}> y:<{1}>",  
        new object[] {x, y});  
  
}  
  
```  
  
 Należy pamiętać, że `Assert` metoda zawiera komunikat, który wyświetla `x` i `y` wartości iteracji nie powiodło się. Domyślnie potwierdzona wartości `expected` i `actual`, znajdują się już w szczegółach testu nie powiodło się.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a>Określanie DataSourceAttribute  
 `DataSource` Atrybut określa parametry połączenia dla źródła danych i nazwę tabeli, którego używasz w metodzie testowej. Dokładne informacje w parametrach połączenia różni się w zależności od tego, jakiego rodzaju źródła danych są używane. W tym przykładzie użyliśmy SqlServerCe bazy danych.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 Atrybut źródła danych ma trzy konstruktorów.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Konstruktora z jednym parametrem używa informacji o połączeniu, który jest przechowywany w pliku app.config dla rozwiązania. *DataSourceSettingsName* jest nazwa elementu Xml w pliku konfiguracji, który określa informacje o połączeniu.  
  
 Przy użyciu pliku app.config umożliwia zmianę lokalizacji źródła danych bez wprowadzania zmian do samego testu jednostkowego. Aby uzyskać informacje o sposobie tworzenia i używania pliku app.config, zobacz [wskazówki: Korzystanie z pliku konfiguracji do określania źródła danych](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 `DataSource` Konstruktora z dwoma parametrami określa parametry połączenia dla źródła danych oraz nazwę tabeli, która zawiera dane dla metody testowej.  
  
 Parametry połączenia są zależne od typu Typ źródła danych, ale musi on zawierać element dostawcy, który określa niezmienną nazwę dostawcy danych.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a>Aby uzyskać dostęp do danych za pomocą TestContext.DataRow  
 Aby uzyskać dostęp do danych `AddIntegersData` tabeli, należy użyć `TestContext.DataRow` indeksatora. `DataRow`jest <xref:System.Data.DataRow> obiektów, co możemy pobieranie według nazw indeksu lub kolumny wartości w kolumnie. Ponieważ wartości są zwracane jako obiekty, musimy przekonwertować je na odpowiedni typ:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a>Uruchamianie testu i wyświetlanie wyników  
 Po zakończeniu zapisu metody testowej kompilacji projektu testowego. Metoda testowa jest wyświetlany w oknie Eksploratora testów w **nie Uruchom testy** grupy. Jak uruchamiać, zapisu i ponownie uruchomić testy narzędzia Eksplorator testów wyświetla wyniki w grupach **testy nie powiodło się**, **przekazany testy**, i **nie Uruchom testy**. Możesz wybrać **Uruchom wszystkie** do uruchomienia wszystkich testów, lub wybierz **Uruchom...**  wybranie podzestawu testów do uruchomienia.  
  
 Na pasku wyników testu w górnej części Eksploratora jest animowany podczas działania testu. Po zakończeniu uruchomienia testu pasek będzie zielonego, jeśli wszystkie testy zostały pomyślnie sprawdzone lub czerwony Jeśli którykolwiek z testów nie powiodło się. Podsumowanie uruchomienia testu zostanie wyświetlony w okienku szczegółów w dolnej części okna Eksploratora testów. Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku.  
  
 W przypadku uruchomienia `AddIntegers_FromDataSourceTest` metody w naszym przykładzie czerwony pasek wyników i metody testowej jest przenoszony do **testy nie powiodło się** testu opartego na danych kończy się niepowodzeniem, jeśli źródło dowolnej z metod iterated z danych kończy się niepowodzeniem. W przypadku niepowodzenia testu opartego na danych w oknie Eksploratora testów, w okienku szczegółów są wyświetlane wyniki każdej iteracji, który jest identyfikowany przez indeks wiersza danych. W naszym przykładzie wynika, że `AddIntegers` algorytm poprawnie nie obsługuje wartości ujemnych.  
  
 Po testowana metoda jest usuwana testu, uruchom ponownie, na pasku wyniki włącza zielony i metody testowej jest przenoszony do **przekazany Test** grupy.  
  
## <a name="see-also"></a>Zobacz także

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>  
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>  
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>  
<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>  
[Testowanie jednostek kodu](../test/unit-test-your-code.md)  
[Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)  
[Pisanie testów jednostkowych dla .NET Framework za pomocą struktury testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)
