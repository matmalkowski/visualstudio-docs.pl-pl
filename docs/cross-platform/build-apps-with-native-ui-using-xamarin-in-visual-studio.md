---
title: Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika za pomocą platformy Xamarin w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 1b70ea2cc12530065b2a297e54ff494bcc765c9c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757256"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika przy użyciu platformy Xamarin w programie Visual Studio

Większość deweloperzy, którzy wybierz do pisania aplikacji dla urządzeń przenośnych i platform Xamarin i C# za pomocą platformy Xamarin.Forms. Platformy Xamarin.Forms definiuje interfejs użytkownika, który jest mapowany na kontrolki natywne w systemie iOS, Android i platformy uniwersalnej systemu Windows (UWP). Platformy Xamarin.Forms jest opisana w artykule [Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio](learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).

W tym artykule opisano różne podejścia, która obejmuje dostęp do interfejsów API natywnego interfejsu użytkownika dla każdej z platform. Praca z macierzystych interfejsów API jest znacznie trudniejsze podejścia, niż platformy Xamarin.Forms, ponieważ wymaga ona doskonałej znajomości każdej platformy. Zaletą jest to, że podczas udostępniania nadal podstawowej logiki biznesowej, można dostosować interfejsu użytkownika do konkretnej mocnych i możliwości poszczególnych platform.

Po wykonaniu kroków [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) i [Sprawdź środowisku Xamarin](../cross-platform/verify-your-xamarin-environment.md), w tym przewodniku przedstawiono sposób tworzenia Podstawowa aplikacja Xamarin z macierzystego warstwy interfejsu użytkownika. Udostępniony kod znajduje się w bibliotece .NET Standard natywnego interfejsu użytkownika, i projekty poszczególnych platform zawierają definicje interfejsu użytkownika. W tym miejscu to aplikacja, która będzie kompilacji systemem (od lewej do prawej) z systemem iOS i telefony z systemem Android i Windows 10 desktop.

![Aplikacja Xamarin w systemach iOS, Android i Windows](../cross-platform/media/cross-plat-xamarin-build-1-Large.png#lightbox)

Należy wykonać te czynności, aby go skompilować:

- [Konfigurowanie rozwiązania](#solution)

- [Pisanie kodu usługi udostępnionych danych](#dataservice)

- [Projektowanie interfejsu użytkownika dla systemu Android](#Android)

- [Projektowanie interfejsu użytkownika dla systemu Windows](#Windows)

- [Następne kroki](#next), który obejmuje projektowanie interfejsu użytkownika dla systemu iOS

> [!TIP]
> Dla tego projektu w można znaleźć kodu źródłowego pełną [mobile przykłady repozytorium w usłudze GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Jeśli masz problemy lub wystąpiły błędy, Opublikuj pytania na [forums.xamarin.com](http://forums.xamarin.com). Wiele błędów można rozwiązać, aktualizując do SDK najnowsze wymagane przez program Xamarin, które są opisane w [informacje o wersji programu Xamarin](https://developer.xamarin.com/releases/) dla każdej platformy.

> [!NOTE]
> Dokumentacja dla deweloperów w programie Xamarin oferuje kilka wskazówki szybkiego startu jak również nowości sekcje wymienione poniżej. Na tych stronach upewnij się, czy wybrano "Visual Studio", aby wyświetlić wskazówki specyficzne dla programu Visual Studio.
>
>  -   Xamarin aplikacji za pomocą natywnego interfejsu użytkownika:
>     -   [Witaj, Android](/xamarin/android/get-started/hello-android/) (prosta aplikacja z jednym ekranie)
>     -   [Witaj, Android Wieloekranowy](/xamarin/android/get-started/hello-android-multiscreen/) (aplikacja z nawigacją między ekranami)
>     -   [Android wskazówki fragmenty](/xamarin/android/platform/fragments/implementing-with-fragments/) (używanych do ekranów wzorzec/szczegół, między innymi)
>     -   [Witaj, iOS](/xamarin/ios/get-started/hello-iOS/)
>     -   [Witaj, iOS Multiscreen (wiele ekranów)](/xamarin/ios/get-started/hello-iOS-multiscreen/)

>  -   Z platformy Xamarin.Forms (udostępnionego UI) przy użyciu aplikacji Xamarin
>     -   [Witaj, Xamarin.Forms](/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart/)
>     -   [Witaj, Xamarin.Forms (wiele ekranów)](/xamarin/xamarin-forms/get-started/hello-xamarin-forms-multiscreen/)

<a name="solution" />

##  <a name="set-up-your-solution"></a>Konfigurowanie rozwiązania

Program Visual Studio nie ma szablon rozwiązania do tworzenia natywnych aplikacji interfejsu użytkownika platformy .NET Standard biblioteki udostępnionej. Jednak nie jest trudne do rozwiązania w poszczególnych projektach kompilacji. Te kroki tworzenia rozwiązania Xamarin z projektów dla każdego typu platforma aplikacji i .NET Standard biblioteki udostępnionej kodu.

1.  W programie Visual Studio Utwórz nową **biblioteki klas (.NET Standard)** rozwiązania i nadaj mu nazwę **WeatherApp**. Tego szablonu można znaleźć najłatwiej wybierając **Visual C#** po lewej stronie, a następnie **.NET Standard**:

    ![Tworzenie rozwiązania .NET Standard](../cross-platform/media/cross-plat-xamarin-build-2.png)

    Po kliknięciu przycisku OK, **WeatherApp** rozwiązania składa się z jednego projektu o nazwie **WeatherApp**.

2.  Jeśli chcesz docelowy z systemem iOS, Dodaj projekt dla systemu iOS do rozwiązania. Kliknij prawym przyciskiem myszy nazwę rozwiązania w **Eksploratora rozwiązań** i wybierz **Dodaj** i **nowy projekt**.  W **nowy projekt** okna dialogowego, w oknie po lewej stronie wybierz **Visual C#**, a następnie **iOS** i **uniwersalnych**. (Jeśli nie jest, może być konieczne Zainstaluj program Xamarin, lub włączyć funkcję Visual Studio 2017, zobacz [Instalatora i zainstaluj](../cross-platform/setup-and-install.md).) Na liście szablonów wybierz **pojedynczego widoku aplikacji (iOS)**. Nadaj mu nazwę **WeatherApp.iOS**.

3.  Jeśli chcesz przeanalizować systemu Android, Dodaj projekt systemu Android do rozwiązania. W **nowy projekt** okna dialogowego, w oknie po lewej stronie wybierz **Visual C#** i **Android**. Na liście szablonów wybierz **pusta aplikacja (Android)**. Nadaj mu nazwę **WeatherApp.Android**.

4. Jeśli chcesz przeanalizować platformy uniwersalnej systemu Windows, w **nowy projekt** okna dialogowego, w oknie po lewej stronie wybierz **Visual C#** i **uniwersalnych systemu Windows**. Na liście szablonów wybierz **pusta aplikacja (uniwersalna systemu Windows)** i nadaj mu nazwę **WeatherApp.UWP**.

5. Dla każdej aplikacji projektów (z systemem iOS, Android i platformy uniwersalnej systemu Windows), kliknij prawym przyciskiem myszy **odwołania** sekcji **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**. W **Menedżera odwołań** okna dialogowego, w oknie po lewej stronie wybierz **projektu** i **rozwiązania**. Zobaczysz listę wszystkich projektów w rozwiązaniu z wyjątkiem odwołania, których zarządzasz projektu:

   ![Ustawianie odwołania do projektu .NET Standard](../cross-platform/media/cross-plat-xamarin-build-3.png)

   Zaznacz pole wyboru obok pozycji **WeatherApp**.

   Po sprawdzeniu to pole dla poszczególnych projektów aplikacji, wszystkie projekty zawierają odwołania do biblioteki standardowej .NET i mogą udostępniać kodu w tej bibliotece.

6. Dodaj **Newtonsoft.Json** pakiet NuGet do projektu .NET Standard, który zostanie użyty do przetwarzania informacji z usługi danych pogody:

    -   Kliknij prawym przyciskiem myszy **WeatherApp** projektu w **Eksploratora rozwiązań** i wybierz **Zarządzaj pakietami NuGet...** .

         W oknie NuGet wybierz **Przeglądaj** karcie i wyszukaj **Newtonsoft**.

    -   Wybierz **Newtonsoft.Json**.

    -   Upewnij się, **wersji** pole jest ustawione na **najnowsze stabilny** wersji.

    -   Kliknij przycisk **zainstalować**.

7.  Powtórz kroki od 6 do znajdować i instalować **Microsoft.CSharp** pakiet w projekcie .NET Standard. Ta biblioteka jest koniecznych do używania języka C# `dynamic` typu danych przechowywanych w bibliotece .NET Standard.

8.  Skompiluj rozwiązanie i sprawdź, czy nie ma żadnych błędów kompilacji.

<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Pisanie kodu usługi udostępnionych danych

 **WeatherApp** projekt jest biblioteką .NET Standard. Ten projekt jest, gdzie będzie pisania kodu, który jest udostępniany na wszystkich platformach. Ponieważ każdy projekt aplikacji ma odwołanie do biblioteki .NET Standard, biblioteka jest dołączony do systemu iOS, Android i platformy uniwersalnej systemu Windows pakietów aplikacji.

 Poniższe kroki Dodaj kod do biblioteki .NET Standard dostęp do przechowywania danych pochodzących z tej usługi pogody:

1.  Najpierw Załóż bezpłatne pogody klucz interfejsu API w [ http://openweathermap.org/appid ](http://openweathermap.org/appid). Ten klucz interfejsu API umożliwi aplikacji do uzyskiwania pogody dla dowolnego kodu pocztowego Stanów Zjednoczonych. (Go nie działa w przypadku kodów pocztowych poza Stanami Zjednoczonymi.)

2.  Kliknij prawym przyciskiem myszy **WeatherApp** projekt i wybierz **Dodaj > klasy...** . W **Dodaj nowy element** okna dialogowego, nazwa pliku **Weather.cs**. Ta klasa będzie używane do przechowywania danych z usługi data pogody.

3.  Zastąp całą zawartość **Weather.cs** następującym kodem:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```

4.  Dodaj kolejną klasę do .NET Standard projektu o nazwie **DataService.cs**. Użyjesz tej klasy do przetwarzania danych JSON usługi pogody danych.

5.  Zastąp całą zawartość **DataService.cs** następującym kodem:

    ```csharp
    using System.Net.Http;
    using System.Threading.Tasks;
    using Newtonsoft.Json;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> GetDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

6.  Dodaj klasę innych do biblioteki .NET Standard o nazwie **Core.cs**. Klasa będzie używana do tworzą ciąg zapytania z kodem pocztowym, wywołania tej usługi danych pogody i wypełniania wystąpienia **pogody** klasy.

7.  Zastąp zawartość **Core.cs** następującym kodem:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR API KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.GetDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

8. Zamień na pierwsze wystąpienie *tutaj klucz interfejsu API YOUR* przy użyciu klucza interfejsu API uzyskane w kroku 1. Nadal wymaga cudzysłowów wokół niego!

9. Usuń **MyClass.cs** w bibliotece programu .NET Standard, ponieważ nie będzie używany.

10. Tworzenie **WeatherApp** projektu, aby się upewnić, że kod jest poprawny.

<a name="Android" />

## <a name="design-ui-for-android"></a>Projektowanie interfejsu użytkownika dla systemu Android

 Teraz można zaprojektować interfejsu użytkownika, podłącz go do udostępnionego kodu, a następnie uruchom aplikację.

### <a name="design-the-look-and-feel-of-your-app"></a>Projekt wyglądu i działania aplikacji

1.  W **Eksploratora rozwiązań**, rozwiń węzeł **WeatherApp.Droid > Zasoby > układu** folderu i Otwórz **Main.axml**. To polecenie powoduje otwarcie pliku w Projektancie visual. (Jeśli zostanie wyświetlony błąd związany z języka Java, zobacz ten [wpis w blogu](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    >  Istnieje wiele plików w projekcie. Eksploracja ich jest poza zakres tego artykułu, ale jeśli chcesz przejść do struktury projektu dla systemu Android nieco więcej, zobacz [część 2 nowości](/xamarin/android/get-started/hello-android/hello-android-deepdive/) Hello Android artykułu.

2.  Otwórz przybornika **Widok > innych okien > przybornika**.

3.  Z **przybornika**, przeciągnij **RelativeLayout** formantu do projektanta. Ten formant będzie używany jako kontenera nadrzędnego dla innych formantów.

    > [!TIP]
    >  Jeśli w dowolnym momencie układ nie powiodła się ją poprawnie wyświetlić, Zapisz plik i przełączanie między **projekt** i **źródła** karty, aby odświeżyć.

4.  W **właściwości** ustaw **tła** właściwości (w grupie styl) `#545454`.  Upewnij się, że w pozycji w **właściwości** oknie, w którym jest instalowana w tle **RelativeLayout**.

5.  Z **przybornika**, przeciągnij **TextView** kontrolować na **RelativeLayout** formantu.

6.  W **właściwości** okna, ustaw te właściwości. (Ułatwia Aby posortować listę alfabetycznie za pomocą przycisku sortowania w pasku narzędzi okna właściwości.):

    |Właściwość|Wartość|
    |--------------|-----------|
    |**tekst**|**Wyszukiwanie według kod pocztowy**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginStart**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**textStyle**|`bold`|

    > [!TIP]
    >  Należy zauważyć, że wiele właściwości nie mogą zawierać rozwijalna lista wartości, które można wybrać.  Może być trudne do odgadnięcia, jakie wartości ciągu do użycia dla dowolnego danej właściwości. Masz sugestie, spróbuj wyszukiwania dla nazwy właściwości w [R.attr](http://developer.android.com/reference/android/R.attr.html) klasy strony.
    >
    >  Ponadto wyszukiwania w szybkiej sieci web często prowadzi do strony [ http://stackoverflow.com/ ](http://stackoverflow.com/) gdzie inne używane tej samej właściwości.

     Odwołania, po przejściu do **źródła** widoku, powinien zostać wyświetlony następujący kod dla tego elementu:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_marginStart="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

7.  Z **przybornika**, przeciągnij **TextView** kontrolować na **RelativeLayout** kontroli i umieść je poniżej ZipCodeSearchLabel formantu. Usuwanie nowego formantu w odpowiednich krawędzi istniejącego formantu. Pomaga powiększenie w Projektancie nieco położenie formantu.

8. W **właściwości** okna, ustaw te właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**tekst**|**Kod pocztowy**|
    |**id**|`@+id/ZipCodeLabel`|
    |**layout_marginStart**|`10dp`|
    |**layout_marginTop**|`6dp`|
    |**textColor**|`@android:color/white`|

    Oto, jak kod w **źródła** widok powinien wyglądać:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginStart="10dp"
        android:layout_marginTop="6dp"
        android:textColor="@android:color/white" />
    ```

9. Z **przybornika**, przeciągnij **numer** kontrolować na **RelativeLayout**, umieść ją poniżej **kod pocztowy** etykiety. Następnie ustaw następujące właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginStart**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**width**|`165dp`|
    |**textColor**|`@android:color/white`|

    **Numer** formant jest wpisuje użytkownika w 5 cyfrowy kod pocztowy w Stanach Zjednoczonych. Oto kod znaczników, który odpowiada tej kontrolki:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginStart="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp"
        android:textColor="@android:color/white" />
    ```

10. Z **przybornika**, przeciągnij **przycisk** na **RelativeLayout** kontroli i umieść je z prawej strony zipCodeEntry formantu. Następnie ustaw te właściwości:

    |Właściwość|Wartość|
    |--------------|-----------|
    |**id**|`@+id/weatherBtn`|
    |**tekst**|**Pobierz pogody**|
    |**layout_marginStart**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**width**|`165dp`|

    ```xml
    <Button
        android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginStart="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

11. Teraz wiesz, aby utworzyć podstawowy interfejs użytkownika przy użyciu projektanta dla systemu Android. Interfejs użytkownika można także utworzyć przez dodanie znaczników bezpośrednio do pliku Main.axml strony. Pozostała część interfejsu użytkownika, który, przejdź do widoku źródłowego w Projektancie kompilacji, a następnie wklej następujący kod znaczników *pod* `</RelativeLayout>` tagu końcowego. (Ponieważ są to następujące elementy muszą być poniżej tagu *nie* zawartych w `RelativeLayout`.)

    ```xml
    <TextView
        android:text="Location"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/locationLabel"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/locationText"
        android:layout_marginStart="20dp"
        android:layout_marginBottom="10dp" />
    <TextView
        android:text="Temperature"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/tempLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/tempText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Wind Speed"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/windLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/windText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Humidity"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/humidtyLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/humidityText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Visibility"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/visibilityLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/visibilityText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Time of Sunrise"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunriseLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunriseText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    <TextView
        android:text="Time of Sunset"
        android:textAppearance="?android:attr/textAppearanceSmall"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunsetLabel"
        android:layout_marginStart="10dp" />
    <TextView
        android:textAppearance="?android:attr/textAppearanceMedium"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/sunsetText"
        android:layout_marginBottom="10dp"
        android:layout_marginStart="20dp" />
    ```

12. Zapisz plik i przejdź do **projekt** widoku. Twój interfejs użytkownika powinna wyglądać następująco:

     ![Interfejs użytkownika dla aplikacji systemu Android](../cross-platform/media/xamarin_androidui.png)

13. Otwórz **MainActivity.cs**. Oto, jak powinna wyglądać kodu:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

14. Tworzenie projektu dla systemu Android, aby sprawdzić swoją pracę. Proces kompilacji dodaje sterowanie identyfikatorów do **Resource.Designer.cs** plików, dzięki czemu mogą odwoływać się do formantów według nazwy w kodzie.

### <a name="consume-your-shared-code"></a>Korzystać z udostępnionego kodu

1.  Otwórz **MainActivity.cs** pliku **WeatherApp** projektu w edytorze kodu i zastąp jego zawartość przy użyciu poniższego kodu. Ten kod wywołuje `GetWeather` metodę, która jest zdefiniowana w kodzie udostępnionego. Następnie w Interfejsie użytkownika aplikacji, zawiera dane, które są pobierane z tej metody.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App",
                  Theme = "@android:style/Theme.Material.Light",
                  MainLauncher = true)]
        public class MainActivity : Activity
        {
            protected override void OnCreate(Bundle bundle)
            {
                base.OnCreate(bundle);

                SetContentView(Resource.Layout.Main);

                Button button = FindViewById<Button>(Resource.Id.weatherBtn);

                button.Click += Button_Click;
            }

            private async void Button_Click(object sender, EventArgs e)
            {
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);

                if (!String.IsNullOrEmpty(zipCodeEntry.Text))
                {
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;
                }
            }
        }
    }
    ```

    Zwróć uwagę, że działanie została podana motyw światła tła.

### <a name="run-the-app-and-see-how-it-looks"></a>Uruchom aplikację i sprawdzić, jak wygląda

1.  W **Eksploratora rozwiązań**, upewnij się, że **WeatherApp.Droid** projekt został ustawiony jako projekt startowy.

2.  Wybierz odpowiednie urządzenia lub emulatora docelowego, a następnie uruchomić aplikację, naciskając klawisz F5.

    > [!NOTE]
    > Jeśli program Visual Studio wskazuje, że projekt systemu Android nie można odnaleźć pliku Newtonsoft.Json, dodać tego pakietu NuGet do projektu systemu Android.

3.  Na urządzeniu lub w emulatorze, wpisz prawidłowy kod pocztowy 5 cyfrowy Stanów Zjednoczonych w pole edycji, a następnie naciśnij klawisz **uzyskać pogody**. Dane pogody dla regionu pojawia się w formantach.

    [![Aplikacja Xamarin w systemie Android](../cross-platform/media/cross-plat-xamarin-build-1-android.png)](../cross-platform/media/cross-plat-xamarin-build-1-android-Large.png#lightbox)

> [!TIP]
>  Kod źródłowy pełną dla tego projektu jest [mobile przykłady repozytorium w usłudze GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

<a name="Windows" />

## <a name="design-ui-for-windows"></a>Projektowanie interfejsu użytkownika dla systemu Windows

Następnym krokiem jest projektowanie interfejsu użytkownika dla systemu Windows, podłącz go do udostępnionego kodu, a następnie uruchom aplikację.

### <a name="design-the-look-and-feel-of-your-app"></a>Projekt wyglądu i działania aplikacji

 Proces projektowania natywnego interfejsu użytkownika platformy uniwersalnej systemu Windows w aplikacji platformy Xamarin nie różni się od innych natywnych aplikacji platformy uniwersalnej systemu Windows. Z tego powodu Użyj projektanta nie omówione w tym miejscu. Aby uzyskać szczegółowe informacje, zapoznaj się [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 Zamiast tego otworzyć **MainPage.xaml** i Zastąp całą zawartość XAML następujący kod:

```xaml
<Page
    x:Class="WeatherApp.UWP.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.UWP"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel HorizontalAlignment="Left"
                    VerticalAlignment="Top"
                    Height="40" Margin="10,0,0,0" Width="400">
            <TextBlock Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left"
                    VerticalAlignment="Top"
                    Height="120" Margin="10,40,0,0" Width="400"
                    Background="#FF545454">

            <TextBlock Text="Search by Zip Code" TextWrapping="Wrap"
                       HorizontalAlignment="Left" Margin="10,10,0,0"
                       Foreground="White" FontSize="18" FontWeight="Bold" />

            <TextBlock Text="Zip Code" TextWrapping="Wrap"
                       Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>

            <StackPanel Orientation="Horizontal">

                <TextBox x:Name="zipCodeEntry" Text=""
                         Margin="10,10,0,0" VerticalAlignment="Top"
                         InputScope="Number" Width="165" />

                <Button x:Name="weatherBtn" Content="Get Weather"
                        Foreground="White" Width="165" Margin="20,0,0,0" Height="60"
                        Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>

        <StackPanel Margin="10,175,0,0">
            <StackPanel.Resources>
                <Style x:Key="commonText" TargetType="TextBlock">
                    <Setter Property="HorizontalAlignment" Value="Left" />
                    <Setter Property="VerticalAlignment" Value="Top" />
                    <Setter Property="TextWrapping" Value="Wrap" />
                </Style>

                <Style x:Key="labelText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="14" />
                    <Setter Property="Foreground" Value="#FFA8A8A8" />
                </Style>

                <Style x:Key="valueText" TargetType="TextBlock" BasedOn="{StaticResource commonText}">
                    <Setter Property="FontSize" Value="18" />
                    <Setter Property="Margin" Value="10, 0, 0, 10" />
                </Style>
            </StackPanel.Resources>

            <TextBlock Text="Location" Style="{StaticResource labelText}" />
            <TextBlock x:Name="locationText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="tempText" Style="{StaticResource valueText}" />

            <TextBlock Text="Wind Speed" Style="{StaticResource labelText}" />
            <TextBlock x:Name="windText" Style="{StaticResource valueText}" />

            <TextBlock Text="Humidity" Style="{StaticResource labelText}" />
            <TextBlock x:Name="humidityText" Style="{StaticResource valueText}" />

            <TextBlock Text="Temperature" Style="{StaticResource labelText}" />
            <TextBlock x:Name="visibilityText" Style="{StaticResource valueText}" />

            <TextBlock Text="Time of Sunrise" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunriseText" Style="{StaticResource valueText}" />

            <TextBlock Text="Time of Sunset" Style="{StaticResource labelText}" />
            <TextBlock x:Name="sunsetText" Style="{StaticResource valueText}" />
        </StackPanel>
    </Grid>
</Page>
```

### <a name="consume-your-shared-code"></a>Korzystać z udostępnionego kodu

W **MainPage.xaml.cs** CodeBehind pliku, Dodaj następujący program obsługi zdarzeń dla przycisku:

```csharp
private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)
{
    if (!String.IsNullOrEmpty(zipCodeEntry.Text))
    {
        Weather weather = await Core.GetWeather(zipCodeEntry.Text);
        locationText.Text = weather.Title;
        tempText.Text = weather.Temperature;
        windText.Text = weather.Wind;
        visibilityText.Text = weather.Visibility;
        humidityText.Text = weather.Humidity;
        sunriseText.Text = weather.Sunrise;
        sunsetText.Text = weather.Sunset;

        weatherBtn.Content = "Search Again";
    }
}
```

Ten kod wywołuje `GetWeather` metodę, która jest zdefiniowana w kodzie udostępnionego. `GetWeather` jest to metoda tej samej nazwie w aplikacji systemu Android. Ten kod zawiera również dane pobrane z tej metody w formantach interfejsu użytkownika aplikacji.

### <a name="run-the-app-and-see-how-it-looks"></a>Uruchom aplikację i sprawdzić, jak wygląda

1.  W **Eksploratora rozwiązań**ustaw **WeatherApp.UWP** projekt jako projekt startowy.

2.  W **platformy rozwiązania** listy rozwijanej wybierz pozycję **x86** i wybierz **komputera lokalnego** do wdrożenia aplikacji na pulpicie systemu Windows 10.

3.  Uruchom aplikację, naciskając klawisz F5.

4.  Wpisz prawidłowy Stanów Zjednoczonych 5 cyfrowy kod pocztowy w pole edycji, a następnie naciśnij klawisz **uzyskać pogody**. Dane pogody dla regionu pojawia się na stronie.

    [![Aplikacja Xamarin na platformy uniwersalnej systemu Windows](../cross-platform/media/cross-plat-xamarin-build-1-uwp.png)](../cross-platform/media/cross-plat-xamarin-build-1-uwp-Large.png#lightbox)

> [!TIP]
>  Kod źródłowy pełną dla tego projektu jest [mobile przykłady repozytorium w usłudze GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).

<a name="next" />

## <a name="next-steps"></a>Następne kroki

 **Dodawanie interfejsu użytkownika dla systemu iOS do rozwiązania**

 W tym przykładzie należy rozszerzyć przez dodanie natywnego interfejsu użytkownika dla systemu iOS. Do testowania kodu w systemie iOS, należy nawiązać Mac w sieci lokalnej, która ma Xcode i Xamarin zainstalowane. Po wykonaniu tej czynności, można użyć projektanta iOS bezpośrednio w programie Visual Studio. Zobacz [mobile przykłady repozytorium w usłudze GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) dla ukończonej aplikacji.

 Należy także zapoznać się [Hello, iOS](/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?tabs=vswin) wskazówki.

 **Dodaj kod specyficzne dla platformy w projekcie udostępnionym**

 Udostępniony kod w bibliotece .NET Standard jest niezależny od platformy. Biblioteki są kompilowane raz i zawarte w każdy pakiet aplikacji dla poszczególnych platform. Jeśli chcesz zapisać udostępniony kod, który używa kompilacji warunkowej do izolowania kodu specyficzne dla platformy, możesz użyć *udostępnionego* projektu. Aby uzyskać więcej informacji, zobacz [opcje udostępniania kodu](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/practical-code-sharing-strategies).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja środowiska Xamarin](http://docs.microsoft.com/xamarin)
- [Centrum deweloperów systemu Windows](https://dev.windows.com/en-us)
- [Plakat krótkimi opisami SWIFT i C#](http://aka.ms/scposter)
