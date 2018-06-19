---
title: 'Samouczek: Azure Functions'
description: Przy użyciu funkcji platformy Azure w programie Visual Studio dla komputerów Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: 80c04182733204a18ee669d3851deab867cc56cd
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33877335"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Samouczek: Wprowadzenie do korzystania z usługi Azure Functions

W tym laboratorium dowiesz się, jak rozpocząć tworzenie funkcji platformy Azure przy użyciu programu Visual Studio dla komputerów Mac. Zostanie również zintegrować z tabelami magazynu Azure, które reprezentują jedną z wielu rodzajów powiązania i wyzwalaczy dostępna dla deweloperów usługi Azure Functions.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Tworzenie i debugowanie lokalne usługi Azure Functions
> * Integracja z sieci web i zasobami magazynu platformy Azure
> * Organizowanie obejmujące wiele funkcji Azure przepływu pracy

## <a name="requirements"></a>Wymagania

- Program Visual Studio dla komputerów Mac w wersji 7.5 lub nowszy.
- Subskrypcja platformy Azure (dostępne wolne od [ https://azure.com/free ](https://azure.com/free)).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Ćwiczenie 1: Tworzenie projektu usługi Azure Functions

1. Uruchom **programu Visual Studio for Mac**.

1. Wybierz **Plik > nowe rozwiązanie**.

1. Z **chmury > Ogólne** kategorii, wybierz opcję **usługi Azure Functions** szablonu. Użyjesz C# do tworzenia biblioteki klas .NET obsługującego usługi Azure Functions. Kliknij przycisk **Dalej**.

    ![Wybieranie szablonu funkcji platformy Azure](media/azure-functions-lab-image1.png)

1. Ustaw **Nazwa projektu** do **"AzureFunctionsLab"** i kliknij przycisk **Utwórz**.

    ![Nazewnictwo i tworzenie projektu platformy azure — funkcja](media/azure-functions-lab-image2.png)

1. Rozwiń węzły w **konsoli rozwiązania**. Domyślny szablon projektu zawiera NuGet odwołania do różnych zadań Webjob Azure pakietów, jak pakiet Newtonsoft.Json. 

     Istnieją również trzy pliki:- **host.json** opisu globalnej opcji konfiguracji dla hostów — **local.settings.json** do konfigurowania ustawień usługi. 
        — Szablon projektu tworzy także domyślne HttpTrigger. Dla tego laboratorium, należy usunąć **HttpTrigger.cs** plik z projektu.

    Otwórz **local.settings.json**. Domyślnie po dwa połączenia pusty ciąg ustawienia.

    ![Plik local.settings.json wyświetlania konsoli rozwiązania](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Ćwiczenie 2: Tworzenie konta magazynu platformy Azure

1. Zaloguj się do konta platformy Azure na [ https://portal.azure.com ](https://portal.azure.com).
 
1. W obszarze **ulubione** sekcji znajdujący się po lewej stronie ekranu wybierz **kont magazynu**:

    ![Ulubione części elementu konta magazynu Azure przedstawiający portalu](media/azure-functions-lab-image4.png)

1. Wybierz **Dodaj** do utworzenia nowego konta magazynu:

    ![Przycisk, aby dodać nowe konto magazynu](media/azure-functions-lab-image5.png)

1. Wprowadź globalnie unikatowej nazwy dla **nazwa** i ponowne użycie go w celu **grupy zasobów**. Domyślnie można zachować wszystkie inne elementy.

    ![szczegółów nowego konta magazynu](media/azure-functions-lab-image6.png)

1. Kliknij przycisk **Utwórz**. Może upłynąć kilka minut, aby utworzyć konto magazynu. Otrzymasz powiadomienie, gdy został pomyślnie utworzony.

    ![powiadomienie pomyślnym wdrożeniu](media/azure-functions-lab-image7.png)

1. Wybierz **przejdź do zasobu** przycisk od powiadomienia.

1. Wybierz **klucze dostępu** kartę.

    ![Ustawienie klucza dostępu](media/azure-functions-lab-image8.png)

1. Skopiuj pierwszy **ciąg połączenia**. Ten ciąg jest używany do integracji magazynu platformy Azure z funkcji Azure później.

    ![informacje dotyczące klucza 1](media/azure-functions-lab-image9.png)

1. Wróć do **programu Visual Studio for Mac** i Wklej w ciągu połączenia pełne jako **AzureWebJobsStorage** w **local.settings.json**. Teraz możesz odwoływać się nazwa ustawienia w atrybutach dla funkcji, które wymagają dostępu do zasobów.

    ![Plik ustawień lokalnych z wprowadzony klucz połączenia](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Przykład 3: Tworzenie i debugowanie funkcji platformy Azure

1. Teraz możesz rozpocząć dodawanie kodu. Podczas pracy z biblioteki klas .NET, funkcje platformy Azure są dodawane jako metody statyczne. Z **konsoli rozwiązania**, kliknij prawym przyciskiem myszy **AzureFunctions** węzeł projektu i wybierz **Dodaj > dodawania funkcji...** :

    ![Dodawanie funkcji-opcja](media/azure-functions-lab-image11.png)

1. W oknie dialogowym Nowe funkcje platformy Azure wybierz szablon ogólny element webhook. Ustaw **nazwa** do **Dodaj** i kliknij przycisk **Ok** można utworzyć funkcji:

    ![Okno dialogowe nowego usługę azure functions](media/azure-functions-lab-image12.png)

1. Na początku nowego pliku Dodaj **przy użyciu** dyrektywy poniżej:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```
1. Usuń istniejące `Run` — metoda i Dodaj do klasy jako funkcja Azure metody poniżej:

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```
1. Przejdźmy definicja metody element przez element. 
    
    Jest najpierw zobaczysz **FunctionName** atrybut umożliwiający oznaczenie tej metody jako funkcję platformy Azure. Ten atrybut określa nazwę publiczną funkcji. Nazwa atrybutu nie musi odpowiadać nazwie rzeczywiste — metoda.

    ![Nowa metoda uruchamiania atrybutem FunctionName wyróżnione](media/azure-functions-lab-image13.png)

1. Następnie metoda jest oznaczona jako **publiczne statyczne** metodę, która jest wymagana. Należy także zauważyć, że wartość zwracana jest **int**. Inaczej przy użyciu metody atrybutów, zwracana wartość inny niż void żadnych funkcji platformy Azure jest zwracana do klienta jako tekst. Domyślnie jest zwracana jako **XML**, ale można zmienić na **JSON**, którego należy to zrobić później w środowisku laboratoryjnym.

    ![Nowa metoda wykonywania z wyróżnioną pozycją inicjalizacją — metoda](media/azure-functions-lab-image14.png)

1. Pierwszy parametr jest oznaczony atrybutem **HttpTrigger** atrybut, który wskazuje, że ta metoda jest wywoływana przez żądania HTTP. Atrybut określa również poziom autoryzacji metody, a także obsługuje zleceń (tylko **"GET"** w takim przypadku). Można również zdefiniować **trasy** który zastępuje ścieżki do metody i daje możliwość automatycznego wyodrębniania zmienne ze ścieżki. Ponieważ **trasy** ma wartość null, domyślnie zostanie ustawiona ścieżka do tej metody **/api/Dodaj**.

    ![Nowa metoda wykonywania z parametrem wyróżnione](media/azure-functions-lab-image15.png)

1. Ostatni parametr metody jest **TraceWriter** który może służyć do logowania się komunikaty diagnostyki i błędów.

    ![Nowa metoda wykonywania z wyróżnioną pozycją TraceWriter](media/azure-functions-lab-image16.png)

1. Ustaw punkt przerwania na **zwracać** linia metody, klikając na marginesie wiersza:

    ![Punkt przerwania ustawiony w wierszu return](media/azure-functions-lab-image17.png)

1. Tworzenie i uruchamianie projektu podczas sesji debugowania, naciskając klawisz **F5** lub wybierając **Uruchom > Rozpocznij debugowanie**. Można też kliknąć **Uruchom** przycisku. Opcje te wykonania tego samego zadania. Odwołuje się do pozostałej części tego laboratorium **F5**, ale można użyć metody, można znaleźć najbardziej Ci.

    ![Tworzenie i uruchamianie projektu](media/azure-functions-lab-image18.png)

1. Uruchamianie projektu zostanie automatycznie uruchomiona terminali aplikacji.

1. Projekt przechodzi przez proces wykrywania usługi Azure Functions, na podstawie atrybutów — metoda i Konwencji pliku, który jest uwzględnione w dalszej części tego artykułu. W takim przypadku wykryje jednej funkcji platformy Azure i "generuje" 1 funkcję zadania.

    ![Dane wyjściowe funkcji platformy Azure w terminalu](media/azure-functions-lab-image19.png)

1. Na dole komunikaty uruchomienia hosta usługi Azure Functions drukuje adresy URL wszystkie interfejsy API wyzwalacza HTTP. Powinny istnieć tylko jedna. Skopiuj ten adres URL i wklej go na nowej karcie przeglądarki.

    ![Adres URL funkcji platformy Azure, interfejsu API](media/azure-functions-lab-image20.png)

1. Punkt przerwania powinno spowodować natychmiast. Żądanie sieci web zostanie rozesłany do funkcji i może być debugowany. Wskaźnik myszy na **x** zmiennej, aby wyświetlić jego wartość. 

    ![Wyzwalane punktu przerwania](media/azure-functions-lab-image21.png)

1. Usuń punkt przerwania przy użyciu tej samej metody dodać ją wcześniej (kliknij na marginesie lub wybierz wiersza i naciśnij klawisz **F9**).

1. Naciśnij klawisz **F5** dalsze działanie.

1. W przeglądarce wynik XML metoda będzie renderowany. Zgodnie z oczekiwaniami, operacja dodawania zapisane na stałe tworzy wiarygodne sum. Uwaga: Jeśli zostanie wyświetlona tylko wtedy "3" w programie Safari, go, aby **Safari > Preferencje > Zaawansowane** i znaczników "**opracowanie Pokaż menu na pasku menu**" wyboru i ponownie załaduj stronę.

1. W **programu Visual Studio for Mac**, kliknij przycisk **zatrzymać** przycisk, aby zakończyć sesję debugowania. Aby upewnić się, że nowe zmiany są pobierane, nie zapomnij o ponowne uruchomienie (Zatrzymaj i uruchom) sesji debugowania.

    ![Zatrzymaj debugowanie opcji](media/azure-functions-lab-image22.png)

1. W **Uruchom** metody, Zastąp **x** i **y** definicje przy użyciu poniższego kodu. Ten kod wyodrębnia wartości z ciągu zapytania w adresie URL tak, aby operacja dodawania może zostać wykonana dynamicznie w zależności od podanych parametrów.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```
1. Uruchom aplikację.

1. Wróć do okna przeglądarki i Dołącz ciąg `/?x=2&y=3` do adresu URL. Cały adres URL powinien być teraz `http://localhost:7071/api/Add?x=2&y=3`. Przejdź do nowego adresu URL.

1. Teraz wynik powinien odzwierciedlać nowe parametry. Możesz także uruchomić projekt o różnych wartościach. Należy pamiętać, że nie wszystkie błąd podczas sprawdzania, więc nieprawidłowe lub brakujące parametry zgłosi błąd.

1. Zatrzymaj sesję debugowania.


## <a name="exercise-4-working-with-functionjson"></a>Ćwiczenie 4: Praca z function.json

1.  W starszych wykonywania wspomniano, Visual Studio for Mac "wygenerowania" funkcji dla funkcji platformy Azure, zdefiniowany w bibliotece. Jest tak, ponieważ usługi Azure Functions faktycznie nie są używane atrybuty metody w czasie wykonywania, ale raczej używa konwencji systemu pliku kompilacji, aby skonfigurować lokalizacje i w jaki sposób usługi Azure Functions stają się dostępne. Z **konsoli rozwiązania**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **ujawnić w wyszukiwarce**.

     ![Wyświetlanie w opcji menu wyszukiwania](media/azure-functions-lab-image23.png)

1. Przechodzenia do systemu plików, aż dojdziesz **bin/Debug/netstandard2.0**. Powinien istnieć folder o nazwie **Dodaj**. Ten folder został utworzony do funkcji atrybutu nazwy w kodzie języka C#. Rozwiń folder Dodaj ujawnienie pojedynczy **function.json** pliku. Ten plik jest używany przez program obsługi do zarządzania funkcji platformy Azure. Dla innych modeli języka nie obsługują kompilacji (na przykład skryptu C# lub JavaScript) tych folderów muszą można ręcznie tworzyć i obsługiwać. C# deweloperom są one automatycznie generowane z atrybutu metadanych podczas kompilacji. Kliknij prawym przyciskiem myszy **function.json** i wybierz, aby otworzyć go w programie Visual Studio.

    ![Function.JSON w katalogu plików](media/azure-functions-lab-image24.png)

1. Podana poprzednie kroki tego samouczka, należy mieć podstawową wiedzę na temat atrybutów języka C#. Który uwzględnieniu, JSON powinna wyglądać znajomo. Istnieje jednak kilka elementów, które nie zostały uwzględnione w starszych ćwiczeń. Na przykład każdy **powiązania** musi mieć jego **kierunek** ustawiony. Jako użytkownik może wnioskować, **"w"** oznacza, że parametr jest danych wejściowych, podczas gdy **"out"** wskazuje, czy parametr jest zwracane wartości (za pośrednictwem **$return**) lub **limit** parametru do metody. Należy również określić **plik_skryptu** (względem tej lokalizacji końcowej) i **punktu wejścia** — metoda (publiczna i statyczna) w zestawie. W ciągu następnych kilku kroków dodasz ścieżką funkcji niestandardowych za pomocą tego modelu tak skopiuj zawartość tego pliku do Schowka.

    ![w programie visual studio Otwórz plik Function.JSON dla komputerów mac](media/azure-functions-lab-image25.png)

1. W **konsoli rozwiązania**, kliknij prawym przyciskiem myszy **AzureFunctionsLab** węzeł projektu i wybierz **Dodaj > Nowy Folder**. Nazwa nowego folderu **metoda dodająca**. Konwencja domyślną nazwę tego folderu zostanie określenia ścieżki do interfejsu API, takich jak **interfejsu api/moduł**.

    ![Nowa opcja folderu](media/azure-functions-lab-image26.png)

1. Kliknij prawym przyciskiem myszy **metoda dodająca** i wybierz polecenie **Dodaj > Nowy plik**.

    ![Nowa opcja pliku](media/azure-functions-lab-image27.png)

1. Wybierz **Web** kategorii i **pusty plik JSON** szablonu. Ustaw **nazwa** do **funkcja** i kliknij przycisk **nowy**.

    ![Opcja pliku json pusty](media/azure-functions-lab-image28.png)

1. Wklej zawartość innych **function.json** (z kroku nr 3) w celu zastąpienia domyślnej zawartości nowo utworzonego pliku.

1. Usuń następujące linie z góry pliku json:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Na końcu pierwszego powiązania (po **"name": "wymagane"** wiersza), Dodaj poniższe właściwości. Nie zapomnij zawierać przecinka w poprzednim wierszu. Ta właściwość zastępuje głównych domyślnego w taki sposób, aby teraz wyodrębni **int** parametry ze ścieżki i umieszczenie ich w parametry metody, które są nazywane **x** i **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Dodaj inny powiązanie poniżej pierwszy. To powiązanie obsługuje zwracana wartość funkcji. Nie zapomnij zawierać przecinka w poprzednim wierszu:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Zaktualizuj **punktu wejścia** właściwości w dolnej części pliku przy użyciu metody o nazwie **"Add2"**, tak jak pokazano poniżej. Aby zilustrować, który jest ścieżka **interfejsu api/składniki...**  można mapować do odpowiedniej metody z żadną nazwą (**Add2** tutaj).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Twoje final **function.json** pliku powinno wyglądać podobnie do następującego formatu json:

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. Jeden ostatnim krokiem wymagane do przygotowania to pracy jest nakazać programowi Visual Studio for Mac skopiować ten plik do tej samej ścieżce względnej w katalogu wyjściowego każdej zmianie. Z plikiem wybrana, wybierz kartę właściwości z po prawej stronie paska, a także **Kopiuj do katalogu wyjściowego** wybierz **Kopiuj, jeśli nowszy**:

    ![Opcje właściwości dla pliku json](media/azure-functions-lab-image30.png)

1. W **Add.cs**, Zastąp `Run` — metoda (w tym atrybucie) przy użyciu następującej metody do spełnienia oczekiwanych funkcji. Jest bardzo podobny do `Run`, ale korzysta z żadnych atrybutów, a ma jawne parametry **x** i **y**.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```
1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

1. Ponieważ kompilacja zostaje ukończona i się obraca platformy, teraz wskaże dostępne dla żądań, które mapy do nowo dodanego metody jest drugi trasy:

    ![Adres URL dla funkcji Http](media/azure-functions-lab-image31.png)

1. Zwraca okno przeglądarki i przejdź do **http://localhost:7071/api/Adder/3/5**.

1. Teraz działa metoda jeszcze raz ściąganie parametry ze ścieżki i Tworzenie sumy.

1. Wróć do **programu Visual Studio for Mac** i zakończenia sesji debugowania.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Ćwiczenie 5: Praca z tabelami magazynu Azure

Często usługi, którą kompilacji może być znacznie bardziej skomplikowane niż co możemy wykonanej do tej pory utworzone, a wymaga dużo czasu i/lub infrastruktury do wykonania. W tym przypadku może być bardzo skuteczne do akceptowania żądań, które są umieszczane w kolejce do przetwarzania, gdy będą dostępne zasoby, które usługi Azure Functions zapewnia obsługę. W innych przypadkach należy do centralnego przechowywania danych. Tabelach magazynu platformy Azure umożliwiają szybkie zrobić. 

1. Dodaj klasę poniżej, aby **Add.cs**. Powinien być kierowany wewnątrz obszaru nazw, ale poza istniejącej klasy.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```
1. W ramach **Dodaj** klasy, Dodaj kod poniżej, aby wprowadzić inną funkcję. Należy pamiętać, że ta unikatowy wykonanej do tej pory, nie obejmują odpowiedzi HTTP. Końcowego wiersza zwraca nową **wymagają elementu** wypełniane przy użyciu niektóre informacje o kluczu, która ułatwi późniejszą można pobrać później (**PartitionKey** i **RowKey**), a także jej Parametry i sum. Kod w metodzie używa również **TraceWriter** aby ułatwić ustalenie, po uruchomieniu funkcji.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");
    
        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```
1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

1. Na karcie przeglądarki przejdź do **http://localhost:7071/api/Process/4/6**. Spowoduje to umieszczenie kolejną wiadomość do kolejki, co ostatecznie powinno spowodować dodawane do tabeli z wartością innego wiersza.

1. Wróć do **terminali** , zwracając uwagę na przychodzące żądania dla **4 + 6**.

    ![Żądania dodanie przedstawiający końcowych wyjścia](media/azure-functions-lab-image32.png)

1. Wróć do przeglądarki, aby odświeżyć żądania do tego samego adresu URL. Teraz zostanie wyświetlony błąd **procesu** metody. Jest to spowodowane kod próbuje dodać wiersz do tabeli magazynu tabel Azure przy użyciu kombinacji klawiszy partycji i wiersza, która już istnieje.

    ``` 
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Zakończenie sesji debugowania.

1. Aby uniknąć błąd, Dodaj następujący parametr do definicji metody bezpośrednio przed **TraceWriter** parametru. Ten parametr nakazuje platformy Azure Functions próba pobrania **wymagają elementu** z **wyniki** tabeli na **PartitionKey** używamy do przechowywania wyniki. Jednak niektóre rzeczywiste magic wejścia play po można zauważyć, że **RowKey** jest generowany dynamicznie oparty na innych **x** i **y** parametrów dla tej samej Metoda. Jeśli ten wiersz już nie istnieje, **wymagają elementu** będą mieli go, gdy metoda rozpoczyna się od żadne dodatkowe czynności wymagane przez projektanta. Jeśli wiersz nie istnieje, a następnie po prostu będzie mieć wartości null. Tego rodzaju wydajności umożliwia deweloperom skoncentrować się na logiki biznesowej ważne i nie infrastruktury.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```
1. Dodaj poniższy kod do początku metody. Jeśli **wymagają elementu** nie jest wartość null, a następnie mamy już mieć wyniki dla żądanej operacji i można przywrócić go bezpośrednio. W przeciwnym razie funkcja nadal co poprzednio. To nie może być najbardziej niezawodna sposób, aby zwrócić dane, przedstawiono punktu, że można organizować bardzo zaawansowane operacje na wielu warstw skalowalne kodem bardzo mało.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```
1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

1. Na karcie przeglądarki Odśwież adresu URL w **http://localhost:7071/api/Process/4/6**. Ponieważ istnieje wiersz tabeli dla tego rekordu, powinien on zwrócić natychmiast i bez błędów. Ponieważ nie ma żadnych danych wyjściowych HTTP, widoczne dane wyjściowe w terminalu.

    ![Istnieje terminali danych wyjściowych już przedstawiający wiersza tabeli](media/azure-functions-lab-image33.png)

1. Adres URL, który nie odzwierciedlają kombinacji jeszcze przetestowane, takich jak aktualizacja **http://localhost:7071/api/Process/5/7**. Należy pamiętać, wiadomości w terminalu, co oznacza, że wiersz tabeli nie znaleziono (zgodnie z oczekiwaniami).

    ![Nowy proces przedstawiający terminali danych wyjściowych](media/azure-functions-lab-image34.png)

1. Wróć do **programu Visual Studio for Mac** i zakończenia sesji debugowania.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON. 

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Podsumowanie

W tym laboratorium kiedy znasz już jak rozpocząć tworzenie funkcji platformy Azure z programem Visual Studio dla komputerów Mac.

