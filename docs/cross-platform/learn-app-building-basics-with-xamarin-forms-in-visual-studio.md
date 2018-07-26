---
title: Dowiedz się, podstawy tworzenia aplikacji przy użyciu zestawu narzędzi Xamarin.Forms w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 2a8851a48d1629b5324d0eb7615c2f2c9f2719e0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251858"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Podstawowe informacje dotyczące tworzenia aplikacji za pomocą platformy Xamarin.Forms w programie Visual Studio

Po wykonaniu kroków [Instalator i instalacja](../cross-platform/setup-and-install.md) i [Sprawdź swoje środowisko Xamarin](../cross-platform/verify-your-xamarin-environment.md), w tym instruktażu dowiesz się, jak utworzyć podstawową aplikację za pomocą zestawu narzędzi Xamarin.Forms. Za pomocą zestawu narzędzi Xamarin.Forms Ty napiszesz całości kodu interfejsu użytkownika raz w bibliotece klas programu .NET Standard. Xamarin zostaną automatycznie renderowania natywne kontrolki interfejsu użytkownika dla systemów iOS, Android i Windows Universal platform.

Jest to zazwyczaj lepiej jest użyć biblioteki .NET Standard, a nie Projekt udostępniony dla tego wspólnego kodu. Biblioteki .NET Standard obejmuje tych interfejsów API platformy .NET, które można uruchamiać na wszystkich platformach docelowych.

Poniżej przedstawiono aplikację, którą utworzysz. Działa on (od lewej do prawej) w systemach iOS i telefony z systemem Android i Windows platformy Uniwersalnej systemu Windows 10:

[![Przykład pogody aplikacji w systemach iOS, Android i platformy uniwersalnej systemu Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)

Wykonasz poniższe kroki, aby tworzyć tej aplikacji:

-   [Konfigurowanie rozwiązania programu](#solution)

-   [Pisanie kodu usług udostępnionych danych](#dataservice)

-   [Zacznij pisanie współdzielonym kodem interfejsu użytkownika](#uicode)

-   [Przetestuj swoją aplikację przy użyciu programu Visual Studio Emulator for Android](#test)

-   [Zakończ interfejsu użytkownika za pomocą natywnego wyglądu i działania na platformach](#finish)

> [!TIP]
> Możesz znaleźć pełnego kodu źródłowego dla tego projektu w [przykłady środowiska xamarin — formularze repozytorium w serwisie GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

<a name="solution" />

## <a name="set-up-your-solution"></a>Konfigurowanie rozwiązania programu

Te kroki służą utworzeniu rozwiązanie Xamarin.Forms, które zawiera bibliotekę klas .NET Standard dla udostępnionego kodu i dwa dodano pakiety NuGet.

1. W programie Visual Studio Utwórz nowy **aplikacji dla wielu Platform (xamarin)** rozwiązania i nadaj mu nazwę **WeatherApp**. Wyszukaj szablon, wybierając **Visual C#** i **dla wielu Platform** z listy po lewej stronie.

    ![Tworzenie nowego projektu aplikacji platformy Xamarin.Forms dla wielu Platform](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

    Jeśli szablon nie jest dostępne, może być konieczne instalacji Xamarin lub włączyć funkcję Visual Studio 2017. Zobacz [Instalator i instalacja](../cross-platform/setup-and-install.md).

2.  Po kliknięciu przycisku **OK**, musisz wybrać kilka opcji. Wybierz **pusta aplikacja** i **.NET Standard**:

    ![Tworzenie nowego projektu aplikacji obejmujące wiele Platform](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")

3.  Po kliknięciu przycisku **OK** do utworzenia rozwiązania, będziesz mieć rozwiązań z czterema projektami:

    -   **WeatherApp**: biblioteki .NET Standard, gdzie Ty napiszesz kod, który jest współużytkowany przez platform, w tym wspólnej logiki biznesowej i kodu interfejsu użytkownika przy użyciu zestawu narzędzi Xamarin.Forms.

    -   **WeatherApp.Android**: projekt, który zawiera natywnego kodu dla systemu Android.

    -   **WeatherApp.iOS**: projekt, który zawiera kod natywny dla systemu iOS.

    -   **WeatherApp.UWP**: projekt, który zawiera kod platformy uniwersalnej systemu Windows do systemu Windows 10.

    > [!NOTE]
    >  Możesz usunąć wszystkie projekty, które nie są przeznaczone dla platformy.

     W ramach każdego natywnego projektu mają dostęp do natywnych projektanta dla odpowiednich platform i zaimplementować ekrany specyficzne dla platformy i funkcjonalność, zgodnie z potrzebami.

4.  Uaktualnij pakiet Xamarin.Forms NuGet w rozwiązaniu do najnowszej stabilnej wersji w następujący sposób:

    -   Wybierz **Narzędzia > Menedżer pakietów NuGet > Zarządzaj pakietami NuGet dla rozwiązania**.

    -   W obszarze **aktualizacje** karcie wyboru **Xamarin.Forms** pakietu, a następnie sprawdź, zaktualizuj wszystkie projekty w rozwiązaniu. (Nie należy wybierać aktualizacje dla bibliotek pomocy technicznej platformy Xamarin Android).

    -   Aktualizacja **wersji** pole **najnowszy stabilny** wersji, która jest dostępna.

    -   Kliknij przycisk **zainstalować**.

         ![Aktualizowanie pakietu Xamarin.Forms NuGet](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

    Powinna pojawić się wykonywać uaktualnienia wersji zestawu narzędzi Xamarin.Forms przy każdym utworzeniu nowego rozwiązania Xamarin.Forms. Nie aktualizuj żadnych biblioteki obsługi systemu Android. Jeśli to konieczne, te biblioteki zostaną zaktualizowane podczas aktualizacji wersji zestawu narzędzi Xamarin.Forms.

5.  Dodaj **Newtonsoft.Json** pakietu NuGet **WeatherApp** projektu. Ta biblioteka jest używana do przetwarzania informacji pobrane z usługi danych o pogodzie:

    -   W Menedżera pakietów NuGet (wciąż otwarty z kroku 4), wybierz **Przeglądaj** kartę i wyszukaj **Newtonsoft**.

    -   Wybierz **Newtonsoft.Json**.

    -   Sprawdź **WeatherApp** projektu, który jest tylko projektu, w którym należy zainstalować pakiet.

    -   Upewnij się, **wersji** pole jest ustawione na **najnowszy stabilny** wersji.

    -   Kliknij przycisk **zainstalować**.

    ![Znajdowanie i instalowanie pakietu Newtonsoft.Json NuGet](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

6.  Powtórz krok 5, aby znaleźć i zainstalować **Microsoft.CSharp** pakiet w projekcie .NET Standard. Ta biblioteka jest niezbędne do korzystania z języka C# `dynamic` danych wpisz biblioteki .NET Standard.

7.  Skompiluj rozwiązanie i upewnij się, że żadne błędy kompilacji.

<a name="dataservice" />

## <a name="write-shared-data-service-code"></a>Pisanie kodu usług udostępnionych danych

**WeatherApp** projekt biblioteki .NET Standard to, gdzie Ty napiszesz kod, który jest udostępniany na wszystkich platformach. Ta biblioteka odwołuje się do aplikacji pakiety kompilacji przez system iOS, Android i Windows projektów.

Aby uruchomić ten przykład, musisz najpierw zarejestrować się bezpłatny klucz interfejsu API w [ http://openweathermap.org/appid ](http://openweathermap.org/appid).

Poniższe kroki następnie dodać kod do biblioteki .NET Standard do przechowywania danych z tej usługi pogody i dostęp do:

1.  Kliknij prawym przyciskiem myszy **WeatherApp** projektu, a następnie wybierz **Dodaj > klasa...** . W **Dodaj nowy element** okno dialogowe, nazwij plik **Weather.cs**. Ta klasa będzie używane do przechowywania danych z usługi danych o pogodzie.

2.  Zastąp całą zawartość *Weather.cs* następującym kodem:

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

3.  Dodaj klasę do **WeatherApp** projektu o nazwie **DataService.cs** które będzie używane do przetwarzania danych JSON z usługi danych o pogodzie.

4.  Zastąp całą zawartość **DataService.cs** następującym kodem:

    ```csharp
    using System.Net.Http;
    using System.Threading.Tasks;
    using Newtonsoft.Json;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
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

5.  Dodawanie klasy innych **WeatherApp** projektu o nazwie **Core.cs** którym zostanie umieszczony udostępnione logiki biznesowej. Ten kod tworzy ciąg zapytania z kod pocztowy, wywołuje usługę danych o pogodzie i wypełnia wystąpienie `Weather` klasy.

6.  Zastąp zawartość **Core.cs** następującym kodem:

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

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

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

7. Zastąp *tutaj klucz interfejsu API usługi* przy użyciu klucza interfejsu API został uzyskany. Nadal wymaga ją w cudzysłowie!

8.  Tworzenie **WeatherApp** projektu biblioteki, aby upewnić się, kod jest poprawny.

 <a name="uicode" />

## <a name="begin-writing-shared-ui-code"></a>Zacznij pisanie współdzielonym kodem interfejsu użytkownika

Zestaw narzędzi Xamarin.Forms umożliwia Implementowanie współdzielonym kodem interfejsu użytkownika w bibliotece programu .NET Standard. W ramach tej procedury dodasz stronę do projektu przy użyciu przycisku. Ten przycisk Aktualizacje tekstu na stronie przy użyciu danych zwróconych przez usługę pogody był wyświetlany w poprzedniej sekcji:

1.  Dodaj **strony zawartości** o nazwie **WeatherPage** przez kliknięcie prawym przyciskiem myszy **WeatherApp** projektu i wybierając polecenie **Dodaj > Nowy element...** . W **Dodaj nowy element** okno dialogowe, wybierz opcję **strony zawartości**. Nie można więc wybrać **strony zawartości (C#)** lub **widok zawartości**. Nadaj mu nazwę **WeatherPage.xaml**.

    ![Dodawanie nowej strony XAML zestawu narzędzi Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

     Zestaw narzędzi Xamarin.Forms jest oparte na XAML, więc tego kroku jest tworzony **WeatherPage.xaml** plików wraz z plikiem zagnieżdżonych związanym z kodem **WeatherPage.xaml.cs**. Logika interfejsu użytkownika można pisać w XAML lub kodu. Należy to zrobić część zarówno w tym przewodniku.

2.  Aby dodać przycisk, aby **WeatherPage** ekranu, Zastąp zawartość **WeatherPage.xaml** następującym kodem:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">
      <Button x:Name="getWeatherBtn"
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />
    </ContentPage>
    ```

     Należy zauważyć, że nazwa przycisku musi być zdefiniowany przy użyciu `x:Name` atrybutu, aby za pomocą nazwy z wewnątrz pliku związanego z kodem można odwoływać się tego przycisku.

3.  Aby dodać program obsługi zdarzeń dla przycisku `Clicked` zdarzeń Aktualizowanie tekstu przycisku, Zastąp zawartość **WeatherPage.xaml.cs** z poniższym kodem. (Możesz zmienić "60601" inny kod pocztowy.)

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();

                //Set the default binding to a default object for now
                BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4.  Aby otworzyć **WeatherPage** jako pierwszy ekran po uruchomieniu aplikacji, Zamień Konstruktor domyślny w *App.xaml.cs* następującym kodem:

    ```csharp
    public App()
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  Tworzenie **WeatherApp** projekt, aby upewnić się, czy kod jest poprawny.

<a name="test" />

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a>Przetestuj swoją aplikację przy użyciu programu Visual Studio Emulator for Android

Teraz można przystąpić do uruchomienia aplikacji! Uruchom tylko wersja systemu Android teraz sprawdzić, czy aplikacja jest pobieranie danych z usługi o pogodzie. Później należy również uruchomić z systemem iOS i wersje platformy uniwersalnej systemu Windows po dodaniu więcej elementów interfejsu użytkownika.

1.  Ustaw **WeatherApp.Android** projekt jako projekt startowy, klikając go prawym przyciskiem myszy i wybierając polecenie **Ustaw jako projekt startowy**.

2.  Na pasku narzędzi programu Visual Studio zobaczysz **WeatherApp.Android** wymieniony jako projekt docelowy. Wybierz jedną z emulatorami systemu Android do debugowania i kliknę przycisk **F5**. Zalecamy użycie jednej z **VisualStudio** opcje emulatora, które uruchomi aplikację w Visual Studio Emulator dla systemu Android.

    ![Wybieranie obiektu docelowego debugowania w emulatorze systemu Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

    > [!NOTE]
    > Jeśli program Visual Studio wskazuje, że projekt systemu Android nie można odnaleźć pliku Newtonsoft.Json, Dodaj pakiet NuGet do projektu dla systemu Android.

3.  Po uruchomieniu aplikacji w emulatorze, kliknij przycisk **uzyskać pogody** przycisku. Powinien zostać wyświetlony tekst przycisku zaktualizowana w celu **Chicago**, czyli `Title` właściwości danych pobranych z usługi o pogodzie.

     ![Pogodowe aplikacji przed i po naciśnięciu przycisku](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

<a name="finish" />

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a>Zakończ interfejsu użytkownika za pomocą natywnego wyglądu i działania na platformach

Zestaw narzędzi Xamarin.Forms renderuje natywne kontrolki interfejsu użytkownika dla każdej platformy, aby Twoja aplikacja ma automatycznie natywnego wyglądu i działania. Widać to natywnego wyglądu i działania w wyraźniej za pomocą interfejsu użytkownika, aby uwzględnić pole wejściowe, kod pocztowy i formantów do wyświetlania danych o pogodzie.

1.  Zastąp zawartość **WeatherPage.xaml** ze znacznikami poniżej. Elementy, które są nazwane za pomocą `x:Name` atrybut zgodnie z wcześniejszym opisem mogą być przywoływane z kodu. Zestaw narzędzi Xamarin.Forms również udostępnia wiele [opcje układu](/xamarin/xamarin-forms/user-interface/controls/layouts). W tym miejscu używa WeatherPage [siatki](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) i [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/).

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>

                <Label Text="Search by Zip Code"
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />

                <Label x:Name="zipCodeLabel" Text="Zip Code:"
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />

                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />

                <Button x:Name="getWeatherBtn" Text="Get Weather"
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />

                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>
     ```

     Chociaż nie jest tutaj widoczny, możesz użyć `OnPlatform` tagu w plikach XAML, aby wybrać wartość właściwości, które są specyficzne dla bieżącej platformy, na którym uruchomiona jest aplikacja (zobacz [Essential składnia XAML](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax/).) W pliku związanym z kodem, możesz określić platformy aplikacja jest uruchomiona podstawie porównania ilości [ `Device.RuntimePlatform` ](https://developer.xamarin.com/api/property/Xamarin.Forms.Device.RuntimePlatform/) właściwość o stałe zdefiniowane w [ `Device` ](https://developer.xamarin.com/api/type/Xamarin.Forms.Device/) klasę o nazwie [ `Device.iOS` ](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.iOS/), [ `Device.Android` ](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.Android/), i [ `Device.UWP` ](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.UWP/).

2.  W *WeatherPage.xaml.cs*, Zastąp `GetWeatherBtn_Clicked` programu obsługi zdarzeń z poniższym kodem. Ten kod sprawdza, że nie jest kod pocztowy w pole wprowadzania i pobiera dane dla tego kodu pocztowego. Następnie ustawia kontekst powiązania całej strony powstałe `Weather` wystąpienia. Kod stwierdza, ustawiając tekst przycisku "Wyszukaj ponownie." Każdej etykiety w interfejsie użytkownika jest powiązana z właściwością `Weather` klasy. Po ustawieniu kontekst powiązania ekranu na `Weather` wypadku te etykiety automatycznej aktualizacji.

    ```csharp
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            BindingContext = weather;
            getWeatherBtn.Text = "Search Again";
        }
    }
    ```

3.  Uruchom aplikację na wszystkich trzech platformach, klikając prawym przyciskiem myszy odpowiedni projekt, wybierając **Ustaw jako projekt startowy**i uruchamianie aplikacji na urządzenia lub emulatora. Wprowadź prawidłowy kod pocztowy 5 cyfrowy w Stanach Zjednoczonych i naciśnij klawisz **uzyskać pogody** przycisk, aby wyświetlić dane o pogodzie dla tego regionu. Należy mieć podłączony do komputera Mac w sieci dla projektu systemu iOS z programu Visual Studio.

     [![Przykład pogody aplikacji w systemach iOS, Android i platformy uniwersalnej systemu Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)

Trwa pełnego kodu źródłowego dla tego projektu [przykłady środowiska xamarin — formularze repozytorium w serwisie GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
