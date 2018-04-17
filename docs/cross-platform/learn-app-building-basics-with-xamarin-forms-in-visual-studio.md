---
title: Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 608eebc113c9df7a8978299cc69907e28d81a16f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio

Po wykonaniu kroków [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) i [Sprawdź środowisku Xamarin](../cross-platform/verify-your-xamarin-environment.md), w tym przewodniku przedstawiono sposób tworzenia podstawowej aplikacji z platformy Xamarin.Forms. Z platformy Xamarin.Forms będzie pisania kodu interfejsu użytkownika raz w bibliotece klas .NET Standard. Xamarin zostanie automatycznie renderowania natywnych kontrolek interfejsu użytkownika dla systemu iOS, Android i Universal Windows Platform. 

Jest to zazwyczaj lepiej jest użyć biblioteki .NET Standard, a nie Projekt udostępniony dla tego wspólnego kodu. Biblioteka .NET Standard zawiera tych interfejsów API architektury .NET, które można uruchomić na wszystkich platformach docelowych.  

W tym miejscu to aplikacja, która będzie kompilacji. (Z lewej strony, aby zapisać) działa w systemach iOS i telefony z systemem Android i Windows platformy Uniwersalnej systemu Windows 10:
  
[![Przykładowe pogody aplikacji w systemach iOS, Android i platformy uniwersalnej systemu Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)
  
Należy to zrobić tych kroków, aby uruchomić tę aplikację:  
  
-   [Konfigurowanie rozwiązania](#solution)  
  
-   [Pisanie kodu usługi udostępnionych danych](#dataservice)  
  
-   [Rozpocząć pisanie udostępnionego kodu interfejsu użytkownika](#uicode)  
  
-   [Testowanie aplikacji za pomocą programu Visual Studio Emulator for Android](#test)  
  
-   [Zakończ interfejsu użytkownika z natywnego wyglądu i działania na platformach](#finish)  
  
> [!TIP]
> Dla tego projektu w można znaleźć kodu źródłowego pełną [xamarin forms próbek repozytorium w usłudze GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
<a name="solution" />

## <a name="set-up-your-solution"></a>Konfigurowanie rozwiązania  

Te kroki tworzenie rozwiązań platformy Xamarin.Forms, które zawiera .NET Standard biblioteki klas dla udostępnionego kodu i dwa pakiety NuGet dodany. 
  
1. W programie Visual Studio Utwórz nową **i Platform aplikacji (platformy Xamarin.Forms)** rozwiązania i nadaj mu nazwę **WeatherApp**. Wyszukaj szablonu, wybierając **Visual C#** i **wieloplatformowych** z listy znajdującej się po lewej stronie.  
    
    ![Tworzenie nowego projektu i Platform aplikacji platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

    Jeśli szablon nie jest dostępne, może być konieczne Zainstaluj program Xamarin, lub włączyć funkcję Visual Studio 2017 r. Zobacz [Instalatora i zainstaluj](../cross-platform/setup-and-install.md).  

2.  Po kliknięciu przycisku OK, należy wybrać kilka opcji. Wybierz **pusta aplikacja** i **.NET Standard**:

    ![Tworzenie nowego projektu aplikacji dla wielu Platform](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  Po kliknięciu przycisku OK spowoduje utworzenie rozwiązania, będziesz mieć rozwiązania z czterech projektów:  
  
    -   **WeatherApp**: Biblioteka .NET Standard, gdzie będzie napisać kod, który jest współużytkowany przez platform, w tym wspólne logiki biznesowej i kodu interfejsu użytkownika przy użyciu platformy Xamarin.Forms.  
  
    -   **WeatherApp.Android**: projekt, który zawiera natywnego kodu dla systemu Android.  
  
    -   **WeatherApp.iOS**: projekt, który zawiera kod macierzysty z systemem iOS.  
  
    -   **WeatherApp.UWP**: projekt, który zawiera kod platformy uniwersalnej systemu Windows do systemu Windows 10.  
  
    > [!NOTE]
    >  Można go dowolnie Usuń wszystkie projekty dla platformy, która nie docelowych.   
  
     W ramach każdego natywnego projektu mają dostęp do natywnej projektanta dla odpowiednich platform i zaimplementować ekrany specyficzne dla platformy i funkcji w razie potrzeby.  
  
4.  Zaktualizuj pakiet NuGet platformy Xamarin.Forms w rozwiązaniu do najnowsza stabilna wersja w następujący sposób:  
  
    -   Wybierz **Narzędzia > Menedżera pakietów NuGet > Zarządzaj pakietami NuGet dla rozwiązania**.  
  
    -   W obszarze **aktualizacje** karcie wyboru **platformy Xamarin.Forms** pakiet, a następnie sprawdź, czy zaktualizować wszystkie projekty w rozwiązaniu. (Nie należy wybierać aktualizacje dla bibliotek pomocy technicznej dla systemu Xamarin Android).  
  
    -   Aktualizacja **wersji** do **najnowsze stabilny** wersji, która jest dostępna.  
  
    -   Kliknij przycisk **zainstalować**.  
  
         ![Aktualizowanie pakietu NuGet platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  

    Należy uzyskać w celu przejrzenia uaktualniania wersji platformy Xamarin.Forms, podczas tworzenia nowego rozwiązania platformy Xamarin.Forms. Nie aktualizuj żadnych bibliotek Obsługa systemu Android. Jeśli to konieczne, te biblioteki zostanie zaktualizowany po zaktualizowaniu wersji platformy Xamarin.Forms.
  
5.  Dodaj **Newtonsoft.Json** pakiet NuGet do **WeatherApp** projektu. Ta biblioteka jest używane do przetwarzania pobrane z usługi danych pogody informacje:  
  
    -   Wybierz w Menedżera pakietów NuGet (wciąż otwarty z kroku 4), **Przeglądaj** karcie i wyszukaj **Newtonsoft**.  
  
    -   Wybierz **Newtonsoft.Json**.  
  
    -   Sprawdź **WeatherApp** projektu, który jest jedynym projektu, w którym należy zainstalować pakiet.  
  
    -   Upewnij się, **wersji** pole jest ustawione na **najnowsze stabilny** wersji.  
  
    -   Kliknij przycisk **zainstalować**.  
  
    ![Znajdowanie i instalowanie pakietu Newtonsoft.Json NuGet](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  Powtórz krok 5, aby znaleźć i zainstalować **Microsoft.CSharp** pakiet w projekcie .NET Standard. Ta biblioteka jest koniecznych do używania języka C# `dynamic` typu danych przechowywanych w bibliotece .NET Standard.
  
7.  Skompiluj rozwiązanie i sprawdź, czy nie ma żadnych błędów kompilacji.  
  
<a name="dataservice" /> 

## <a name="write-shared-data-service-code"></a>Pisanie kodu usługi udostępnionych danych  

**WeatherApp** .NET Standard projektu biblioteki jest, gdzie będzie pisania kodu, który jest udostępniany na wszystkich platformach. Ta biblioteka jest przywoływany przez aplikację pakietów kompilacji przez iOS, Android i Windows projektów.  
  
Aby uruchomić ten przykład, należy najpierw utworzysz wolnego klucz interfejsu API w [ http://openweathermap.org/appid ](http://openweathermap.org/appid).  
  
Poniższe kroki następnie dodaj kod do biblioteki .NET Standard dostęp do przechowywania danych pochodzących z tej usługi pogody:  
  
1.  Kliknij prawym przyciskiem myszy **WeatherApp** projekt i wybierz **Dodaj > klasy...** . W **Dodaj nowy element** okna dialogowego, nazwa pliku **Weather.cs**. Ta klasa będzie używane do przechowywania danych z usługi data pogody.  
  
2.  Zastąp całą zawartość **Weather.cs** następującym kodem:  
  
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
  
3.  Dodaj kolejną klasę do **WeatherApp** projektu o nazwie **DataService.cs** które będzie używane do przetwarzania danych JSON usługi pogody danych.  
  
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
  
5.  Dodawanie klasy innych **WeatherApp** projektu o nazwie **Core.cs** których będzie umieścić udostępnionych logiki biznesowej. Ten kod formularzy ciąg zapytania z kodem pocztowym, wywołuje usługę danych pogodą i wypełnia wystąpienia `Weather` klasy.  
  
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

7. Zastąp *tutaj klucz interfejsu API YOUR* przy użyciu klucza interfejsu API został uzyskany. Nadal wymaga cudzysłowów wokół niego!     
  
8.  Tworzenie **WeatherApp** projektu biblioteki, aby się upewnić, że kod jest poprawny.  
  
 <a name="uicode" /> 

## <a name="begin-writing-shared-ui-code"></a>Rozpocząć pisanie udostępnionego kodu interfejsu użytkownika  

Platformy Xamarin.Forms umożliwia implementowania udostępnionego kodu interfejsu użytkownika w bibliotece programu .NET Standard. W tych kroków zostanie dodana do projektu z przyciskiem strony. Ten przycisk Aktualizacje tekstu na stronie z danymi zwrócona przez usługę pogody był wyświetlany w poprzedniej sekcji:  
  
1.  Dodaj **strony zawartości** o nazwie **WeatherPage** przez kliknięcie prawym przyciskiem myszy **WeatherApp** projekt i wybierając **Dodaj > Nowy element...** . W **Dodaj nowy element** okno dialogowe, wybierz opcję **strony zawartości**. Nie można więc wybierz **strony zawartości (C#)** lub **widok zawartości**. Nadaj mu nazwę **WeatherPage.xaml**.  
  
    ![Dodawanie nowej strony XAML platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     Platformy Xamarin.Forms jest oparty na języku XAML, więc tworzy ten krok **WeatherPage.xaml** pliku wraz z pliku zagnieżdżonego kodem **WeatherPage.xaml.cs**. Logika interfejsu użytkownika można pisać w języku XAML lub kodu. Należy to zrobić niektóre zarówno w tym przewodniku.  
  
2.  Aby dodać przycisk, aby **WeatherPage** ekranu, Zastąp zawartość **WeatherPage.xaml** z następujący kod:  
  
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
  
     Zwróć uwagę, że nazwa przycisku musi być zdefiniowana przy użyciu `x:Name` atrybutu, dzięki czemu możesz odwoływać ten przycisk według nazwy z wewnątrz pliku CodeBehind.  
  
3.  Aby dodać program obsługi zdarzeń dla przycisku `Clicked` zdarzeń, aby zaktualizować tekst przycisku, Zastąp zawartość **WeatherPage.xaml.cs** przy użyciu poniższego kodu. (Możesz także zmienić "60601" na inny kod pocztowy).  
  
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
  
4.  Aby otworzyć **WeatherPage** jako pierwszy ekran po uruchomieniu aplikacji, Zastąp konstruktora domyślnego w **App.xaml.cs** następującym kodem:  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Tworzenie **WeatherApp** projektu, aby się upewnić, że kod jest poprawny.  
  
<a name="test" /> 

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a>Testowanie aplikacji za pomocą programu Visual Studio Emulator for Android  

Teraz możesz przystąpić do uruchomienia aplikacji! Umożliwia uruchamianie tylko wersji dla systemu Android teraz sprawdzić, czy aplikacja jest pobieranie danych z usługi pogody. Później również uruchomisz systemów iOS i wersje platformy uniwersalnej systemu Windows po dodaniu więcej elementów interfejsu użytkownika.   
  
1.  Ustaw **WeatherApp.Android** projekt jako projekt startowy ją prawym przyciskiem myszy i wybierając **Ustaw jako projekt startowy**.  
  
2.  Na pasku narzędzi programu Visual Studio, zobaczysz **WeatherApp.Android** wymienionym projektu docelowego. Wybierz jedną z systemem Android emulatorów do debugowania i trafień **F5**. Zalecamy użycie jednej z **VisualStudio** opcje emulatora, które będą uruchamiane aplikacji w Visual Studio Emulator for Android.  
  
    ![Wybieranie obiektu docelowego debugowania w emulatorze systemu Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

    > [!NOTE]
    > Jeśli program Visual Studio wskazuje, że projekt systemu Android nie można odnaleźć pliku Newtonsoft.Json, dodać tego pakietu NuGet do projektu systemu Android.   
  
3.  Po uruchomieniu aplikacji w emulatorze, kliknij przycisk **uzyskać pogody** przycisku. Powinien zostać wyświetlony tekst przycisku zaktualizowany do **Chicago**, która jest `Title` właściwości dane pobrane z usługi pogody.  
  
     ![Pogodowe aplikacji przed i po naciśnięcie przycisku](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  

<a name="finish" /> 

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a>Zakończ interfejsu użytkownika z natywnego wyglądu i działania na platformach  

Platformy Xamarin.Forms renderuje natywnych kontrolek interfejsu użytkownika dla każdej platformy, dzięki czemu aplikacja ma automatycznie natywnego wyglądu i działania. Spowoduje to natywnego wyglądu i działania dokładniej za pomocą interfejsu użytkownika, aby uwzględnić pole wejściowe dla kodu pocztowego i służy do wyświetlania danych pogody.  
  
1.  Zastąp zawartość **WeatherPage.xaml** ze znacznikami poniżej. Elementy, które są przypisywane przy użyciu `x:Name` atrybutu zgodnie z wcześniejszym opisem można odwoływać się z kodu. Udostępnia szereg platformy Xamarin.Forms [opcje układu](/xamarin/xamarin-forms/controls/layouts/). W tym miejscu używa WeatherPage [siatki](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) i [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/).  
  
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
  
     Chociaż nie jest tutaj widoczny, możesz użyć `OnPlatform` tag w plikach XAML, aby wybrać wartość właściwości, która jest specyficzna dla bieżącej platformie, na którym działa aplikacja (zobacz [niezbędne składni języka XAML](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax/).) W pliku CodeBehind można określić platformy aplikacja działa na podstawie porównania ilości [ `Device.RuntimePlatform` ](https://developer.xamarin.com/api/property/Xamarin.Forms.Device.RuntimePlatform/) właściwości za pomocą stałych zdefiniowane w [ `Device` ](https://developer.xamarin.com/api/type/Xamarin.Forms.Device/) klasy o nazwie [ `Device.iOS` ](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.iOS/), [ `Device.Android` ](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.Android/), i [ `Device.UWP` ](https://developer.xamarin.com/api/field/Xamarin.Forms.Device.UWP/).  
  
2.  W **WeatherPage.xaml.cs**, Zastąp `GetWeatherBtn_Clicked` obsługi zdarzeń przy użyciu poniższego kodu. Ten kod sprawdza, czy jest kod pocztowy w pole wprowadzania i pobiera dane dla tego kodu pocztowego. Następnie ustawia kontekst powiązania całej strony powstałe w ten sposób `Weather` wystąpienia. Kod stwierdza, ustawiając tekst przycisku "Wyszukaj ponownie." Każda etykieta w interfejsie użytkownika jest powiązana z właściwością `Weather` klasy. Podczas ustawiania kontekstu powiązania ekranu `Weather` wystąpienia, te etykiety automatycznej aktualizacji.  
  
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
  
3.  Uruchom aplikację na wszystkich platformach trzy, klikając prawym przyciskiem myszy odpowiedni projekt, wybierając **Ustaw jako projekt startowy**i uruchamianie aplikacji na urządzenia lub emulatora. Wprowadź prawidłowy kod pocztowy 5 cyfrowy w Stanach Zjednoczonych i naciśnij klawisz **uzyskać pogody** przycisk, aby wyświetlić dane pogody dla regionu. Musisz mieć Visual Studio podłączonych do komputera Mac w sieci dla projektu iOS.  
  
     [![Przykładowe pogody aplikacji w systemach iOS, Android i platformy uniwersalnej systemu Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")](../cross-platform/media/crossplat-xamarin-formsguide-1-Large.png#lightbox)
  
Kod źródłowy pełną dla tego projektu jest [xamarin forms próbek repozytorium w usłudze GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).