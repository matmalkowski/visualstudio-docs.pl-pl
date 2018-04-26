---
title: 'Wskazówki: Korzystanie z pliku konfiguracji do określania źródła danych w programie Visual Studio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0fee742129d852ff3793b2a7dd367fc157367750
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Wskazówki: korzystanie z pliku konfiguracji do określania źródła danych

W tym przewodniku pokazano, jak używać źródła danych zdefiniowanej w *app.config* pliku w celu przeprowadzania testów jednostkowych. Dowiesz się tworzenie pliku app.config, który definiuje źródła danych, które mogą być używane przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> klasy. Zadania przedstawione w tym przewodniku są następujące:

-   Tworzenie pliku app.config.

-   Definiowanie sekcji konfiguracji niestandardowej.

-   Definiowanie ciągów połączenia.

-   Definiowanie źródeł danych.

-   Dostęp do danych źródła przy użyciu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> klasy.

## <a name="prerequisites"></a>Wymagania wstępne
 W tym przewodniku, należy:

-   Visual Studio Enterprise

-   Program Microsoft Access albo programu Microsoft Excel dostarczający dane dla co najmniej jednej z metod testu.

-   Rozwiązania Visual Studio, który zawiera projekt testowy.

## <a name="create-the-appconfig-file"></a>Tworzenie pliku App.config

### <a name="to-add-an-appconfig-file-to-the-project"></a>Aby dodać plik app.config do projektu

1.  Jeśli projekt testowy już pliku app.config, przejdź do [definiują sekcję konfiguracji niestandardowej](#DefineCustomConfigurationSection).

2.  Kliknij prawym przyciskiem myszy projekt testowy w **Eksploratora rozwiązań**, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **nowy element**.

     **Dodaj nowy element** zostanie otwarte okno.

3.  Wybierz **pliku konfiguracji aplikacji** szablon i kliknij przycisk **Dodaj**.

##  <a name="DefineCustomConfigurationSection"></a> Definiują sekcję konfiguracji niestandardowej
 Zapoznaj się z plikiem app.config. Zawiera ona co najmniej deklaracja XML i elementu głównego.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Aby dodać sekcję konfiguracji niestandardowej w pliku app.config

1.  Element główny pliku app.config powinna być `configuration` elementu. Utwórz `configSections` w elemencie `configuration` elementu. `configSections` Powinien być pierwszym elementem w pliku app.config.

2.  W ramach `configSections` elementu, Utwórz `section` elementu.

3.  W `section` elementu, Dodaj atrybut o nazwie `name` i przypisz jej wartość równą `microsoft.visualstudio.testtools`. Dodaj inny atrybut o nazwie `type` i przypisz jej wartość równą `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

 `section` Element powinien wyglądać podobnie do poniższego:

```
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
```

> [!NOTE]
> Nazwa zestawu musi odpowiadać kompilacji programu Microsoft Visual Studio .NET Framework, którego używasz. Ustaw wersję do 9.0.0.0, jeśli używasz programu Visual Studio .NET Framework 3.5. Jeśli używasz programu Visual Studio .NET Framework 2.0, Ustaw wersję do 8.0.0.0.


## <a name="define-connection-strings"></a>Zdefiniuj parametry połączenia
 Parametry połączenia zdefiniuj informacji specyficznych dla dostawcy do uzyskiwania dostępu do źródeł danych. Parametry połączenia zdefiniowane w plikach konfiguracji udostępnianie informacji o dostawcy danych do ponownego użycia w aplikacji. W tej sekcji utworzysz dwa parametry połączenia, które będą używane przez źródeł danych, które są zdefiniowane w sekcji konfiguracji niestandardowej.

### <a name="to-define-connection-strings"></a>Aby określić parametry połączenia

1.  Po `configSections` elementu, Utwórz `connectionStrings` elementu.

2.  W ramach `connectionStrings` elementu, utworzyć dwa `add` elementów.

3.  W pierwszym `add` elementu, utwórz następujące atrybuty i wartości dla połączenia z bazą danych programu Microsoft Access:

|Atrybut|Wartości|
|---------------|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

 W ciągu sekundy `add` elementu, utwórz następujące atrybuty i wartości dla połączenia do arkusza kalkulacyjnego programu Microsoft Excel:

|||
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

 `connectionStrings` Element powinien wyglądać podobnie do poniższego:

```
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definiowanie źródeł danych
 Sekcja źródeł danych zawiera cztery atrybuty, które są używane przez aparat testu do pobierania danych ze źródła danych.

-   `name` Określa tożsamość używane przez <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> do określania źródła danych do użycia.

-   `connectionString` Określa parametry połączenia, utworzony w poprzedniej sekcji Zdefiniuj parametry połączenia.

-   `dataTableName` Określa tabelę lub arkusz, która przechowuje dane do użycia w teście.

-   `dataAccessMethod` definiuje technikę do uzyskiwania dostępu do wartości danych w źródle danych.

 W tej sekcji zostaną zdefiniowane dwóch źródeł danych do użycia w testu jednostkowego.

### <a name="to-define-data-sources"></a>Aby zdefiniować źródeł danych

1.  Po `connectionStrings` elementu, Utwórz `microsoft.visualstudio.testtools` elementu. W tej sekcji został utworzony w Definiuj sekcji konfiguracji niestandardowej.

2.  W ramach `microsoft.visualstudio.testtools` elementu, Utwórz `dataSources` elementu.

3.  W ramach `dataSources` elementu, utworzyć dwa `add` elementów.

4.  W pierwszym `add` elementu, utwórz następujące atrybuty i wartości dla źródła danych programu Microsoft Access:

|Atrybut|Wartości|
|---------------|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

 W ciągu sekundy `add` elementu, utwórz następujące atrybuty i wartości dla źródła danych programu Microsoft Excel:

|||
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

`microsoft.visualstudio.testtools` Element powinien wyglądać podobnie do poniższego:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Plik app.config końcowego powinny wyglądać podobnie do poniższego:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>Tworzenie testu jednostkowego korzystanie ze źródeł danych zdefiniowanych w pliku app.config
 Teraz, gdy zdefiniowano pliku app.config, utworzysz testu jednostkowego, który używa danych znajdujących się w źródłach danych, które są zdefiniowane w pliku app.config. W tej sekcji zostaną wykonane następujące czynności:

-   Tworzenie źródła danych znaleziono w pliku app.config.

-   Użyj źródeł danych w dwie metody testowe, które umożliwia porównanie wartości w każdym źródle danych.

### <a name="to-create-a-microsoft-access-data-source"></a>Aby utworzyć źródło danych programu Microsoft Access

1.  Utwórz bazę danych programu Microsoft Access o nazwie `testdatasource.accdb`.

2.  Utwórz tabelę i nadaj mu nazwę `MyDataTable` w `testdatasource.accdb`.

3.  Utwórz dwa pola w `MyDataTable` o nazwie `Arg1` i `Arg2` przy użyciu `Number` — typ danych.

4.  Dodaj jednostki pięciu do `MyDataTable` z następującymi wartościami dla `Arg1` i `Arg2`odpowiednio: (10,50), (3,2) (6,0) (0,8) i (12312,1000).

5.  Zapisz i zamknij bazy danych.

6.  Zmień parametry połączenia, aby wskazać lokalizację bazy danych. Zmień wartość `Data Source` do uwzględnienia lokalizacji bazy danych.

### <a name="to-create-a-microsoft-excel-data-source"></a>Aby utworzyć źródło danych programu Microsoft Excel

1.  Utwórz arkusz kalkulacyjny programu Microsoft Excel o nazwie `data.xlsx`.

2.  Utwórz arkusz o nazwie `Sheet1` Jeśli go jeszcze nie istnieje w `data.xlsx`.

3.  Utwórz dwa nagłówki kolumn i ich nazwy `Val1` i `Val2` w `Sheet1`.

4.  Dodaj jednostki pięciu do `Sheet1` z następującymi wartościami dla `Val1` i `Val2`odpowiednio: (1,1), (2,2) (3,3) (4,4) i (5,0).

5.  Zapisz i zamknij arkusz kalkulacyjny.

6.  Zmień parametry połączenia, aby wskazać lokalizację arkusza kalkulacyjnego. Zmień wartość `dbq` do uwzględnienia lokalizacji arkusza kalkulacyjnego.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Aby utworzyć testu jednostkowego przy użyciu pliku app.config źródeł danych

1.  Dodawanie testu jednostkowego do projektu testowego.

2.  Zastąp zawartość automatycznego generowania testu jednostkowego z następującym kodem:

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3.  Sprawdź, czy atrybutów elementu DataSource. Zwróć uwagę, nazwy ustawień z pliku app.config.

4.  Skompiluj i uruchom testy MyTestMethod i MyTestMethod2.

> [!IMPORTANT]
> Wdrażanie elementów, takich jak źródła danych, tak aby były dostępne dla testu w katalogu wdrożenia.

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostek kodu](../test/unit-test-your-code.md)
- [Instrukcje: tworzenie testu jednostkowego opartego na danych](../test/how-to-create-a-data-driven-unit-test.md)