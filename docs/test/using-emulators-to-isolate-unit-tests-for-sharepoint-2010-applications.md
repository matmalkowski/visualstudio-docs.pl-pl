---
title: Izolowanie testów jednostkowych aplikacji Sharepoint 2010 przy użyciu emulatorów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 994e13d7155dd5490d3f3f02865b14845bae498b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-emulators-to-isolate-unit-tests-for-sharepoint-2010-applications"></a>Izolowanie testów jednostkowych aplikacji SharePoint 2010 przy użyciu emulatorów
Pakiet Microsoft.SharePoint.Emulators zawiera zestaw bibliotek, które ułatwiają tworzenie testów jednostkowych izolowanych aplikacji Microsoft SharePoint 2010. Użyj emulatory [podkładek](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) z [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) izolacji platformę, by utworzyć lekkie obiekty w pamięci, które imitują najczęściej obiekty i metody interfejsu API programu SharePoint. Jeśli metoda programu SharePoint nie jest emulowana, lub aby zmienić domyślne zachowanie emulatora, można utworzyć elementów sztucznych podkładek do udostępniania wyników, które mają.

 Klasy i metody testowe istniejących można łatwo zamienić na uruchomienie w kontekście emulatora. Ta funkcja umożliwia tworzenie testów podwójnego zastosowania. Test podwójnego zastosowania można przełączać integracji testy, do rzeczywistych interfejsu API programu SharePoint i testów jednostkowych izolowanego, które używają emulatorów.

##  <a name="BKMK_Requirements"></a> Wymagania

-   Program Microsoft SharePoint 2010 (SharePoint 2010 Server lub SharePoint 2010 Foundation)

-   Microsoft Visual Studio Enterprise

-   Pakiet NuGet emulatory programu Microsoft SharePoint

 Należy także zapoznać się z [podstawy testowania w programie Visual Studio jednostek](../test/unit-test-basics.md) i niektóre wiedzy [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

##  <a name="BKMK_The_AppointmentsWebPart_example"></a> Przykład AppointmentsWebPart
 AppointmentsWebPart umożliwia wyświetlanie i zarządzanie nimi listy programu SharePoint o terminach.

 ![Terminy składnik Web Part](../test/media/ut_emulators_appointmentswebpart.png "UT_EMULATORS_AppointmentsWebPart")

 Firma Microsoft przetestujesz dwie metody części sieci web, w tym przykładzie:

-   `ScheduleAppointment` Metoda sprawdza poprawność wartości elementu listy przekazywany do metody i tworzy nowy wpis na liście w określonej sieci web programu SharePoint.

-   `GetAppointmentsForToday` Metoda zwraca szczegóły współczesnych terminów.

##  <a name="BKMK_Converting_an_existing_test"></a> Konwertowanie istniejącego testu
 W teście typowe metody w składniku programu SharePoint metody testowej tworzy tymczasowy lokacji w programie SharePoint Foundation i dodaje składników SharePoint do witryny, która wymaga testowanego kodu. Metoda testowa następnie tworzy i wykonuje wystąpienia składnika. Po zakończeniu testu lokacji będzie działo.

 `ScheduleAppointment` Metody naszego kodu w ramach testu jest prawdopodobnie jednej z metod pierwszy zapisywane dla tego składnika:

```
// method under test
public bool ScheduleAppointment(SPWeb web, string listName, string name,
    string phone, string email, string age, DateTime date, out string errorMsg)
{
    errorMsg = string.Empty;
    var badFormat = this.checkInput(name, phone, email, age);
    if (badFormat)
    {
        errorMsg = "Bad Format";
        return false;
    }
    var exists = this.CheckDuplicate(listName, web, name, phone, email, age, date);
    if (exists)
    {
        errorMsg = "Item already exists";
        return false;
    }
    SPListItemCollection items = web.Lists[listName].Items;
    // create item and populate fields
    SPListItem item = items.Add();
    item["Name"] = name;
    item["Phone"] = phone;
    item["Email"] = email;
    item["Age"] = age;
    item["Date"] = date.ToString("D");
    item.Update();
    return true;
}

```

 Pierwszego testu w funkcji `ScheduleAppointment` metody może wyglądać następująco:

```csharp

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

 Mimo że ta metoda upewnij się, że `ScheduleAppointment` metody poprawnie dodaje nowy wpis do listy, jest bardziej integracji testu składnika web part niż testu określone zachowanie kodu. Zależności zewnętrzne do programu SharePoint i interfejsu API programu SharePoint może spowodować test, aby zakończyć się niepowodzeniem z powodów innych niż przez kod użytkownika `ScheduleAppointment` metody. Obciążenie związane z tworzeniem i niszczenie witryny programu SharePoint można również ustawić testu zbyt wolno do uruchomienia w ramach standardowych procesu kodowania. Tylko wykonywania instalacji i likwidacja lokacji dla każdej metody testowej związki problem tworzenie wydajnych deweloperów testy jednostkowe.

 Emulatory Microsoft SharePoint zapewniają zestaw obiektów i metoda "symulacyjnych", które imitują zachowanie najczęściej interfejsy API programu SharePoint. Metody emulowane są lekkie implementacji interfejsu API programu SharePoint, które nie wymagają programu SharePoint do uruchomienia. Przy użyciu Microsoft Fakes można przekierować wywołania interfejsu API programu SharePoint na symulacyjnych metody programu SharePoint emulatory, izolowanie testów i upewnij się, że testowany kod, który ma. Podczas wywoływania metod programu SharePoint, które nie są emulowane, można użyć elementów sztucznych bezpośrednio, aby utworzyć zachowanie.

###  <a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a> Dodawanie pakietu emulatory do projektu testowego
 Aby dodać emulatory programu SharePoint do projektu testowego:

1.  Wybierz projekt testowy w Eksploratorze rozwiązań.

2.  Wybierz **Zarządzaj pakietami NuGet...**  menu skrótów.

3.  Wyszukiwanie **Online** kategorię `Microsoft.SharePoint.Emulators`, a następnie wybierz pozycję **zainstalować**.

 ![Pakiet NuGet emulatory SharePoint](../test/media/ut_emulators_nuget.png "UT_EMULATORS_Nuget")

###  <a name="BKMK__Running_a_test_method_in_the_emulation_context"></a> Uruchomione z emulacji metody testowej
 Instalowanie pakietu dodaje odwołania do bibliotek wymaganych do projektów. Aby umożliwić łatwe w użyciu emulatorów w istniejącej klasy testu, Dodaj przestrzenie nazw `Microsoft.SharePoint.Emulators` i `Microsoft.QualityTools.Testing.Emulators`.

 Aby włączyć emulacji w metody testu, opakuj treści metody w `using` instrukcji, która tworzy `SharePointEmulationScope` obiektu. Na przykład:

```csharp

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // create the emulation scope with a using statement
    using (new SharePointEmulationScope())
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}

```

 Podczas wykonywania metody testowej środowiska uruchomieniowego emulatora wywołuje Microsoft Fakes dynamicznie iniekcję kodu do metod programu SharePoint na kierowanie wywołań do tych metod do delegatów, które są zadeklarowane w Microsoft.SharePoint.Fakes.dll. Microsoft.SharePoint.Emulators.dll implementuje delegatów dla metod emulowanej ściśle mimicking rzeczywiste zachowanie programu SharePoint. Gdy metody testowej lub składnik w ramach testu wywołuje metodę programu SharePoint, powoduje zachowanie jest emulacji.

 ![Przepływ wykonania emulatora](../test/media/ut_emulators_flowchart.png "UT_EMULATORS_FlowChart")

##  <a name="BKMK_Creating_dual_use_classes_and_methods"></a> Tworzenie podwójnego zastosowania klasy i metody
 Aby utworzyć metod, które mogą być używane zarówno testów integracji do rzeczywistego interfejsu API programu SharePoint i testów jednostkowych izolowanego, które używają emulatory, należy użyć przeładowanego konstruktora `SharePointEmulationScope(EmulationMode)` opakowywać kodu metody testowego. Dwie wartości `EmulationMode` wyliczenia Określ, czy zakres używa emulatory (`EmulationMode.Enabled`) lub czy zakres używa interfejsu API programu SharePoint (`EmulationMode.Passthrough`).

 Na przykład Oto jak można zmodyfikować poprzedni test za podwójnego zastosowania:

```csharp

// class level field specifies emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled;

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // emulation scope determined by emulatorMode
    using( SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

## <a name="using-testinitialize-and-testcleanup-attributes-to-create-a-dual-use-test-class"></a>Przy użyciu TestInitialize i TestCleanup atrybutów, aby utworzyć podwójnego zastosowania testu — klasa

Po uruchomieniu wszystkie lub większość z testów w klasie przy użyciu `SharePointEmulationScope`, korzystając z techniki poziomie klasy można ustawić trybu emulacji.

-   Testowanie metody klasy, które z <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> i <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> można tworzyć i zniszcz zakresu.

-   Ustawienie `EmulationMode` w klasie poziom można umożliwiają automatyzację zmiana trybu między `EmulationMode.Enabled` i `EmulationMode.Passthrough`.

 Metody klasy, która ma atrybut `[TestInitialize]` jest uruchamiane na początku każdej metody i metody, która ma atrybut `[TestCleanup]` działa na końcu każdej metody. Można zadeklarować pole prywatne dla `SharePointEmulationScope` obiektów na poziomie klasy, Zainicjuj go w `TestInitialize` przypisanych metody, a następnie usuwania obiektu w `TestCleanup` przypisanych metody.

 Można użyć dowolnej metody do automatyzowania wybrana `EmulationMode`. Jednym ze sposobów jest Sprawdź istnienie symbol za pomocą dyrektywy preprocesora. Na przykład, aby uruchomić metod w klasie przy użyciu emulatorów, można zdefiniować symbol takich jak `USE_EMULATION` w pliku projektu testowego lub w wierszu polecenia kompilacji. Jeśli symbol jest zdefiniowany, poziom klasy `EmulationMode` stała jest zadeklarowana i `Enabled`. W przeciwnym razie ma ustawioną wartość stałej `Passthrough`.

 Oto przykład klasy testowej, która przedstawia sposób użycia dyrektywy preprocesora oraz `TestInitialize` i `TestCleanup` przypisanych metod, aby ustawić tryb emulacji.

```csharp
//namespace declarations
...

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATIONprivate const EmulationMode emulatorMode = EmulationMode.Enabled;#elseprivate const EmulationMode emulatorMode = EmulationMode.Passthrough;#endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]public void InitializeTest(){this.emulationScope = new SharePointEmulationScope(emulatorMode);}

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]public void CleanupTest(){this.emulationScope.Dispose();}

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        ...// More tests

    }
}
```

##  <a name="BKMK_Handling_non_emulated_SharePoint_methods"></a> Obsługa nie jest emulowana metod programu SharePoint
 Nie wszystkie typy programu SharePoint są emulowane, a nie wszystkie metody w niektórych typów emulowane są emulowane. Jeśli kod w ramach testu wywołuje metodę programu SharePoint, która nie jest emulowana, metoda wygeneruje `NotSupportedException` wyjątku. Po wystąpieniu wyjątku, możesz dodać elementów sztucznych podkładki dla metody programu SharePoint.

 **Konfigurowanie programu Sharepoint elementów sztucznych**

 Aby jawnie wywołać Microsoft Fakes podkładek:

1.  Jeśli chcesz użyć podkładek klasy programu SharePoint, która nie jest emulowana, przeprowadź edycję pliku Microsoft.SharePoint.fakes i Dodaj klasę do listy klas zastąpionym podkładką. Zobacz [Konfigurowanie generowania kodu klas zastępczych i podkładek](http://msdn.microsoft.com/library/hh708916.aspx#bkmk_configuring_code_generation_of_stubs) sekcji [kodu generowania, kompilowania i nazywania w Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md).

     ![Folder w Eksploratorze rozwiązań substytutów](../test/media/ut_emulators_fakesfilefolder.png "UT_EMULATORS_FakesFileFolder")

2.  Odbuduj projekt testowy co najmniej raz, po zainstalowaniu pakietu Microsoft SharePoint emulatorów i edytując plik Microsoft.SharePoint.Fakes. Tworzenie projektu tworzy i wypełnia **FakesAssembly** folderu w folderze głównym projektu na dysku.

     ![FakesAssembly folder](../test/media/ut_emulators_fakesassemblyfolder.png "UT_EMULATORS_FakesAssemblyFolder")

3.  Dodaj odwołanie do **Microsoft.SharePoint.14.0.0.0.Fakes.dll** zestawu, który znajduje się w **FakesAssembly** folderu.

4.  (Opcjonalnie) Dodaj dyrektywy dla przestrzeni nazw do klasa testowa dla `Microsoft.QualityTools.Testing.Fakes`, `Microsoft.SharePoint.Fakes` i zagnieżdżone przestrzeni nazw z `Microsoft.SharePoint.Fakes`którego chcesz używać.

 **Implementowanie delegata podkładki dla metody programu SharePoint**

 W naszym przykładzie projektu `GetAppointmentsForToday` wywołania metody [SPList.GetItems(SPQuery)](http://msdn.microsoft.com/library/ms457534.aspx) metody interfejsu API programu SharePoint.

```csharp
// method under test
public string GetAppointmentsForToday(string listName, SPWeb web)
{
    SPList list = web.Lists[listName];
    DateTime today = DateTime.Now;
    var listQuery = new SPQuery{Query = String.Format("<Where><Eq><FieldRef Name='Date'/>" +"<Value Type='Text'>{0}</Value>" +"</Eq></Where>", today.ToString("D"))};
    var result = new System.Text.StringBuilder();
    foreach (SPListItem item in list.GetItems(listQuery))
    {
        result.AppendFormat("Name: {0}, Phone: {1}, Email: {2}, Age: {3}, Date: {4}\n",
            item["Name"], item["Phone"], item["Email"], item["Age"], item["Date"]);
    }
    return result.ToString();
}

```

 `SPList.GetItems(SPQuery)` Wersji przeciążone `GetItems` — metoda nie jest emulowana. Dlatego właśnie zawijania istniejącego testu dla `GetAppointmentsForToday` w `SharePoint.Emulation.Scope` nie powiedzie się. Aby utworzyć test pracy, trzeba napisać implementację delegata elementów sztucznych `ShimSPList.GetItemsSPQuery` które zwraca wyniki, które chcesz przetestować.

 Oto modyfikacji istniejących metody testowej `GetAppointmentsForTodayReturnsOnlyTodaysAppointments`, implementującej delegata substytutami. Wymagane zmiany są wywoływane w komentarzach:

> [!IMPORTANT]
>  Testowanie metody, które jawnie tworzyć sztuczne elementy throw podkładek `ShimNotSupported` wyjątku, gdy test jest uruchomiony `EmulationMode.Passthrough` kontekstu. Aby uniknąć tego problemu, należy użyć zmiennej można ustawić `EmulationMode` wartość i zastępowania jakiegokolwiek kodu elementów sztucznych `if` instrukcji sprawdzający wartość.

```csharp
// class level field to set emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled

[TestMethod]
public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
{

    // create the emulation scope with a using statement
    using (var emulationScope = new SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);
        // insert 2 items into list
        AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
            "raisa@outlook.com", "55", date.ToString("D") });
        AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
            "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

        // use Fakes shims only if emulation is enabled
        if (emulatorMode == EmulationMode.Enabled){var sList = new ShimSPList(list);sList.GetItemsSPQuery = (query) =>{var shim = new ShimSPListItemCollection();shim.Bind(new[] { list.Items[0] });return shim.Instance;}}

        // Act
        string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
        list.Delete();

        // Assert
        Assert.IsTrue(result.Contains(String.Format(
            "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
            "Age: 55, Date: {0}", date.ToString("D"))));
        Assert.IsFalse(result.Contains("Name: Francis Totten"));
    }
}

```

 W przypadku tej metody najpierw testujemy włączenia emulacji. Jeśli tak jest, utworzymy obiekt elementów sztucznych podkładki dla naszych `SPList` listy, a następnie utwórz i przypisz metodę jego `GetItemsSPQuery` delegowanie. Delegat używa elementów sztucznych `Bind` metodę, aby dodać element listy poprawny `ShimSPListItemCollection` który jest zwracany do obiektu wywołującego.

##  <a name="BKMK_Writing_emulation_tests_from_scratch__and_a_summary"></a> Emulacja pisania testów od początku i podsumowanie
 Mimo że technik tworzenia emulacji i testy podwójnego zastosowania, które zostały opisane w poprzednich sekcjach założono konwertowania istniejących testów, umożliwia także techniki napisać testy od nowa. Poniższa lista zawiera podsumowanie poniższych metod:

-   Aby użyć emulatory projektu testowego, Dodaj pakiet Microsoft.SharePoint.Emulators NuGet do projektu.

-   W metodzie testowej przy użyciu emulatorów, utworzyć `SharePointEmulationScope` obiektu na początku metody. Będzie można emulować wszystkich obsługiwanych interfejsów API programu SharePoint, dopóki nie zostanie usunięty, zakres.

-   Wpisz swój kod testu, tak jakby były zapisywane go do rzeczywistego interfejsu API programu SharePoint. Kontekst emulacji przekierowuje automatycznie wywołań do metod programu SharePoint do ich emulatory.

-   Nie wszystkie obiekty programu SharePoint są emulowane, a nie wszystkie metody niektórych obiektów emulowane są emulowane. A `NotSupportedException` wyjątek podczas korzystania z systemem innym niż emulowane obiektu lub metody. W takim przypadku jawnie utworzenia delegata podkładki elementów sztucznych metody do zwrócenia wymagane zachowanie.

-   Aby utworzyć testy podwójnego zastosowania, użyj `SharePointEmulationScope(EmulationMode)` konstruktora w celu utworzenia obiektu zakresu emulacji. `EmulationMode` Wartość określa, czy wywołania programu SharePoint są emulowane lub wykonywane rzeczywistych witryny programu SharePoint.

-   Jeśli wszystkie lub większość z metody testu w klasie testu jest wykonywany w kontekście emulacji, możesz użyć poziomie klasy `TestInitialize` przypisanych metodę w celu utworzenia `SharePointEmulationScope` obiekt i pola poziomie klasy, aby ustawić tryb emulacji. Pomoże to zautomatyzować zmianę trybu emulacji. Następnie użyj `TestCleanup` przypisanych metody zlikwidować obiektu zakresu.

##  <a name="BKMK_Example"></a> Przykład
 W tym miejscu jest ostatnim przykładzie uwzględniająca techniki emulatora programu SharePoint, które są opisane powyżej:

```csharp
using System;
//other namespace declarations
...
// code under test
using MySPApps;
using Microsoft.SharePoint;
// unit testing and emulators
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.QualityTools.Testing.Emulators;
using Microsoft.SharePoint.Emulators;
// explicit Fakes shims
using Microsoft.QualityTools.Testing.Fakes;
using Microsoft.SharePoint.Fakes

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATION
            private const EmulationMode emulatorMode = EmulationMode.Enabled;
        #else
            private const EmulationMode emulatorMode = EmulationMode.Passthrough;
        #endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]
        public void InitializeTest()
        {
            this.emulationScope = new SharePointEmulationScope(emulatorMode);
        }

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]
        public void Cleanup()
        {
            this.emulationScope.Dispose();
        }

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        [TestMethod]
        public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
        {

            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);
                // insert 2 items into list
                AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
                    "raisa@outlook.com", "55", date.ToString("D") });
                AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
                    "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

                // use Fakes shims only if emulation is enabled
                if (emulatorMode == EmulationMode.Enabled)
                {
                    var sList = new ShimSPList(list);

                    sList.GetItemsSPQuery = (query) =>
                    {
                        var shim = new ShimSPListItemCollection();
                        shim.Bind(new[] { list.Items[0] });
                        return shim.Instance;
                    }
                }

                // Act
                string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
                list.Delete();

                // Assert
                Assert.IsTrue(result.Contains(String.Format(
                    "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
                    "Age: 55, Date: {0}", date.ToString("D"))));
                Assert.IsFalse(result.Contains("Name: Francis Totten"));
            }
        }

        ...// More tests

    }
}

```

##  <a name="BKMK_Emulated_SharePoint_types"></a> Emulowane typów programu SharePoint
 [Microsoft.SharePoint.SPField](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPField)

 [Microsoft.SharePoint.SPFieldIndex](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndex)

 [Microsoft.SharePoint.SPFieldIndexCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndexCollection)

 [Microsoft.SharePoint.SPFieldLink](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLink)

 [Microsoft.SharePoint.SPFieldLinkCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLinkCollection)

 [Microsoft.SharePoint.SPFieldUrlValue](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldUrlValue)

 [Microsoft.SharePoint.SPFile](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFile)

 [Microsoft.SharePoint.SPFileCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFileCollection)

 [Microsoft.SharePoint.SPFolder](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolder)

 [Microsoft.SharePoint.SPFolderCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolderCollection)

 [Microsoft.SharePoint.SPItem](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItem)

 [Microsoft.SharePoint.SPItemEventDataCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventDataCollection)

 [Microsoft.SharePoint.SPItemEventProperties](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventProperties)

 [Microsoft.SharePoint.SPList](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPList)

 [Microsoft.SharePoint.SPListCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListCollection)

 [Microsoft.SharePoint.SPListEventProperties](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListEventProperties)

 [Microsoft.SharePoint.SPListItem](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItem)

 [Microsoft.SharePoint.SPListItemCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItemCollection)

 [Microsoft.SharePoint.SPQuery](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPQuery)

 [Microsoft.SharePoint.SPRoleAssignment](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignment)

 [Microsoft.SharePoint.SPRoleAssignmentCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignmentCollection)

 [Microsoft.SharePoint.SPSecurableObject](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurableObject)

 [Microsoft.SharePoint.SPSecurity](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity)

 [Microsoft.SharePoint.SPSite](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite)

 [Microsoft.SharePoint.SPUser](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPUser)

 [Microsoft.SharePoint.SPUserCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserCollection)

 [Microsoft.SharePoint.SPView](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPView)

 [Microsoft.SharePoint.SPViewCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewCollection)

 [Microsoft.SharePoint.SPViewContext](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewContext)

 [Microsoft.SharePoint.SPWeb](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb)

 [Microsoft.SharePoint.SPWebCollection](http://msdn.microsoft.com/library/Microsoft.SharePoint.SPWebCollection)

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostek kodu](../test/unit-test-your-code.md)
- [Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)
- [Opracowywanie rozwiązań SharePoint](/office-dev/office-dev/developing-sharepoint-solutions)
