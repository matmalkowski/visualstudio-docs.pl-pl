---
title: "Tworzenie opartego na danych kodowanego testu interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: coded UI tests, data-driven
ms.assetid: 5838f02d-001f-49ce-adce-c9ea1afaec2f
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: cb7e1e231cda62f5312be7dd1058667e5b9ae363
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-data-driven-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika opartego na danych
Aby przetestować inne warunki, można uruchomić testów wiele razy z innym parametrem wartości. Oparte na danych kodowanego interfejsu użytkownika są testy wygodny sposób, aby to zrobić. Określ wartości parametrów w źródle danych, a każdy wiersz w źródle danych jest iteracji kodowanego testu interfejsu użytkownika. Ogólne wyniki testu będą oparte na wynik dla wszystkich iteracji. Na przykład jeden iterację testu nie powiedzie się, ogólną wynik testu jest błąd.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
## <a name="create-a-data-driven-coded-ui-test"></a>Tworzenie kodowanego testu opartego na danych interfejsu użytkownika  
 Ten przykład tworzy kodowanego testu interfejsu użytkownika w aplikacji Kalkulator systemu Windows. On dodaje dwie liczby i używa potwierdzenia do sprawdzania, czy suma jest poprawna. Następnie potwierdzenie i wartości parametrów dla dwóch liczb są zakodowane staje się danymi i przechowywane w pliku wartości rozdzielanych przecinkami (CSV).  
  
#### <a name="step-1---create-a-coded-ui-test"></a>Krok 1 — Tworzenie kodowanego testu interfejsu użytkownika  
  
1.  Tworzenie projektu.  
  
     ![Utwórz projekt kodowanego testu interfejsu użytkownika](../test/media/cuit_datadriven_.png "CUIT_dataDriven_")  
  
2.  Wybierz zarejestrować akcje.  
  
     ![Zarejestruje akcje](../test/media/cuit_datadriven_generatecodedialog.png "CUIT_dataDriven_GenerateCodeDialog")  
  
3.  Otwórz aplikację Kalkulator i rozpocząć nagrywanie testu.  
  
     ![Rejestruj akcje](../test/media/cuit_datadriven_cuitbuilder.png "CUIT_dataDriven_CUITBuilder")  
  
4.  Dodaj 1 i 2, wstrzymać Rejestrator i generowanie metody testowej. Firma Microsoft będzie później zastąpić wartości tych danych wejściowych użytkownika z wartościami z pliku danych.  
  
     ![Metoda testowa Genetate](../test/media/cuit_datadriven_cuitbuildergencode.png "CUIT_dataDriven_CUITBuilderGenCode")  
  
     Zamknąć Konstruktora testu. Metoda został dodany do testu:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
  
    }  
    ```  
  
5.  Użyj `AddNumbers()` metody, aby sprawdzić, czy test jest uruchomiony. Umieść kursor w metodzie testowej przedstawionych powyżej, otwórz menu kontekstowe i wybierz polecenie **Uruchom testy**. (Skrót klawiaturowy: Ctrl + R, T).  
  
     Wynik testu, który pokazuje, czy test przekazany lub niepowodzenie jest wyświetlany w oknie Eksploratora testów. Aby otworzyć okno Eksploratora testów z **testu** menu, wybierz **Windows** , a następnie wybierz **Eksploratora testów**.  
  
6.  Ponieważ źródło danych może także służyć do wartości parametrów potwierdzenia — które są używane przez testu do weryfikowania oczekiwanych wartości — Dodajmy potwierdzenia, aby sprawdzić, czy sumę dwóch liczb jest poprawna. Umieść kursor w metodzie testowej przedstawionych powyżej, otwórz menu kontekstowe i wybierz polecenie **Generuj kod dla kodowanego testu interfejsu użytkownika**, a następnie **Użyj konstruktora kodowanego interfejsu użytkownika testu**.  
  
     Mapy formantu tekstu w Kalkulator, który wyświetla sumę.  
  
     ![Mapowanie tekst formantu interfejsu użytkownika](../test/media/cuit_datadriven_addassertion.png "CUIT_dataDriven_AddAssertion")  
  
7.  Dodaj potwierdzenie, która sprawdza, czy wartość sumy jest poprawna. Wybierz **Wyświetlany_tekst** właściwość, która ma wartość **3** , a następnie wybierz **Dodaj potwierdzenie**. Użyj **AreEqual** komparatora i sprawdź, czy wartość porównania **3**.  
  
     ![Konfigurowanie potwierdzenia](../test/media/cuit_datadriven_builderaddassertion2.png "CUIT_dataDriven_BuilderAddAssertion2")  
  
8.  Po skonfigurowaniu potwierdzenia należy ponownie wygenerować kod z konstruktora. Spowoduje to utworzenie nowej metody dla weryfikacji.  
  
     ![Generowanie metody potwierdzenia](../test/media/cuit_datadriven_assertiongencode.png "CUIT_dataDriven_AssertionGenCode")  
  
     Ponieważ `ValidateSum` metoda sprawdza wyniki `AddNumbers` metody, przenieś go do dolnej części bloku kodu.  
  
    ```csharp  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
    ```  
  
9. Sprawdź, czy test jest uruchamiany za pomocą `ValidateSum()` metody. Umieść kursor w metodzie testowej przedstawionych powyżej, otwórz menu kontekstowe i wybierz polecenie **Uruchom testy**. (Klawiatury skrótu: Ctrl + R, T).  
  
     W tym momencie wszystkie parametry są definiowane w ich metod jako stałe. Następnie utwórz zestaw danych, aby naszych testów opartych na danych.  
  
#### <a name="step-2---create-a-data-set"></a>Krok 2 — Tworzenie zestawu danych  
  
1.  Dodaj plik tekstowy do projektu dataDrivenSample o nazwie `data.csv`.  
  
     ![Dodaj do projektu pliku wartości rozdzielone przecinkami](../test/media/cuit_datadriven_addcsvfile.png "CUIT_dataDriven_AddCSVFile")  
  
2.  Wypełnij plik CSV zawierający następujące dane:  
  
    |Num1|Num2|Suma|  
    |----------|----------|---------|  
    |3|4|7|  
    |5|6|11|  
    |6|8|14|  
  
     Po dodaniu danych, plik powinna wyglądać w następujący sposób:  
  
     ![Wypełnij. Plik CSV z danymi](../test/media/cuit_datadriven_adddatatocsvfile.png "CUIT_dataDriven_AddDataToCSVFile")  
  
3.  Należy zapisać plik CSV przy użyciu kodowania poprawne. Na **pliku** menu, wybierz **zaawansowane opcje zapisywania** i wybierz polecenie **Unicode (UTF-8 bez podpisu) - strona kodowa 65001** jako kodowania.  
  
4.  Plik CSV należy skopiować do katalogu wyjściowego, lub nie można uruchomić testu. Korzystanie z okna właściwości, aby go skopiować.  
  
     ![Wdrażanie. Plik CSV](../test/media/cuit_datadriven_deploycsvfile.png "CUIT_dataDriven_DeployCSVFile")  
  
     Teraz, gdy mamy zestaw danych utworzone teraz powiązać danych testu.  
  
#### <a name="step-3---add-data-source-binding"></a>Krok 3 — Dodaj powiązanie źródła danych  
  
1.  Aby powiązać ze źródłem danych, należy dodać `DataSource` atrybutu wewnątrz istniejącego `[TestMethod]` atrybutu, który jest od razu powyżej metody testowej.  
  
    ```  
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSum();  
  
    }  
  
    ```  
  
     Źródło danych jest teraz dostępna do użycia w tę metodę testową.  
  
    > [!TIP]
    >  Zobacz [przykłady atrybut źródła danych](#CreateDataDrivenCUIT_QA_DataSourceAttributes) w funkcji pytań i sekcja przykłady użycia inne typy źródeł danych, takich jak XML, SQL Express i programu Excel.  
  
2.  Uruchom test.  
  
     Należy zauważyć, że test jest uruchamiany za pomocą trzech iteracji. Jest to spowodowane źródła danych, która została powiązana zawiera trzy wiersze danych. Jednak należy również zauważyć, czy testu jest nadal przy użyciu wartości parametru stałej i dodawanie 1 + 2 z 3 sumę zawsze.  
  
     Dalej skonfigurujemy test, aby użyć wartości w pliku źródła danych.  
  
#### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>Krok 4 — Korzystanie z danych kodowanego testu interfejsu użytkownika  
  
1.  Dodaj `using Microsoft.VisualStudio.TestTools.UITesting.WinControls` na początku pliku CodedUITest.cs:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text.RegularExpressions;  
    using System.Windows.Input;  
    using System.Windows.Forms;  
    using System.Drawing;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
    ```  
  
2.  Dodaj `TestContext.DataRow[]` w `CodedUITestMethod1()` metody, które będą miały zastosowanie wartości ze źródła danych. Stałe przypisane do UIMap formantów za pomocą formantów zastąpienie wartości źródła danych `SearchProperties`:  
  
    ```  
    public void CodedUITestMethod1()  
    {  
  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
        this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();this.UIMap.UICalculatorWindow.UIItemWindow21.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();  
        this.UIMap.AddNumbers();  
        this.UIMap.ValidateSumExpectedValues.UIItem2TextDisplayText = TestContext.DataRow["Sum"].ToString();  
        this.UIMap.ValidateSum();  
  
    }  
    ```  
  
     Aby dowiedzieć się, które właściwości wyszukiwania, aby dane do kodu, użyj edytora kodowanego testu interfejsu użytkownika.  
  
    -   Otwórz plik UIMap.uitest.  
  
         ![Otwórz Edytor testu kodowanego interfejsu użytkownika](../test/media/cuit_datadriven_opentesteditor.png "CUIT_dataDriven_OpenTestEditor")  
  
    -   Wybranie akcji interfejsu użytkownika i obserwować odpowiednie mapowanie formantów interfejsu użytkownika. Zwróć uwagę, jak mapowanie odnosi się do kodu, na przykład `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button`.  
  
         ![Użyj edytora kodowanego testu interfejsu użytkownika z kodu](../test/media/cuit_datadriven_testeditor.png "CUIT_dataDriven_TestEditor")  
  
    -   W oknie właściwości Otwórz **właściwości wyszukiwania**. Właściwości wyszukiwania **nazwa** wartość to, co jest zmieniany w kodzie za pomocą źródła danych. Na przykład `SearchProperties` jest ona obecnie przypisywana wartości z pierwszej kolumny każdego wiersza danych: `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. Dla trzech iteracji zmieni ten test **nazwa** wartości dla właściwości wyszukiwania, aby 3, a następnie 5, a na koniec 6.  
  
         ![Użyj właściwości wyszukiwania w kodowania](../test/media/cuit_datadriven_searchproperties.png "CUIT_dataDriven_SearchProperties")  
  
3.  Zapisz rozwiązanie.  
  
#### <a name="step-5---run-the-data-driven-test"></a>Krok 5. Uruchamianie testu opartego na danych  
  
1.  Sprawdź, czy test jest oparte na danych przez ponowne uruchomienie testu.  
  
     Powinny pojawić się uruchomienie testu za pomocą trzech iteracji, używając wartości z pliku CSV. Sprawdzanie poprawności powinny również działać i testu powinien być wyświetlany jako przekazaną w Eksploratorze testów.  
  
 **Wskazówki**  
  
 Aby uzyskać dodatkowe informacje, zobacz [testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 2: testów jednostkowych: testowanie wewnątrz](http://go.microsoft.com/fwlink/?LinkID=255188) i [testowanie pod kątem ciągłego dostarczania w programie Visual Studio 2012 — rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
###  <a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a>Jakie są atrybuty źródła danych na inne typy źródeł danych, takich jak program SQL Express lub XML?  
 Skopiować je do kodu i wprowadzając niezbędne dostosowania służy parametry źródła danych przykładowych w poniższej tabeli.  
  
 **Typy źródeł danych i atrybuty**  
  
-   CSV  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`  
  
-   Excel  
  
     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`  
  
-   Przypadek testowy na serwerze Team Foundation Server  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`  
  
-   XML  
  
     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`  
  
-   SQL Express  
  
     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`  
  
### <a name="q-can-i-use-data-driven-tests-on-my-windows-phone-app"></a>Pytanie: czy można użyć testów opartych na danych w mojej aplikacji Windows Phone?  
 **Odpowiedź:** tak. Oparte na danych kodowanych testów interfejsu użytkownika dla Windows Phone są definiowane dla metody testowej przy użyciu atrybutu element DataRow. Następujące przykładowe, x i y Użyj wartości 1 i 2 pierwszej iteracji i -1 -2 dla drugiego iteracji testu.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
 Aby uzyskać więcej informacji, zobacz [opartych na danych użyj kodowanych testów interfejsu użytkownika w aplikacji Windows Phone](../test/test-windows-phone-8-1-apps-with-coded-ui-tests.md#TestingPhoneAppsCodedUI_DataDriven).  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Pytanie: Dlaczego nie można zmodyfikować kod w pliku UIMap.Designer?  
 **Odpowiedź:** wprowadzone w pliku UIMapDesigner.cs zmiany kodu zostaną zastąpione zawsze Generuj kod przy użyciu UIMap — Konstruktor kodowanego testu interfejsu użytkownika. W tym przykładzie, w większości przypadków wymagane do włączenia test, aby używać źródła danych zmian w kodzie możliwe do pliku kodu źródłowego testu (czyli CodedUITest1.cs).  
  
 Jeśli trzeba zmodyfikować nagraną metodę, należy skopiować ją do pliku UIMap.cs i zmienić jej nazwę. Plik UIMap.cs może służyć do zastępowania metod i właściwości w pliku UIMapDesigner.cs. Musisz usunąć odwołanie do oryginalnej metody w pliku Coded UITest.cs, a następnie zastąpić je zmienioną nazwą metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
