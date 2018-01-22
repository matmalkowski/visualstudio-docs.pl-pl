---
title: "Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/19/2018
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: "11"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: xamarin
ms.openlocfilehash: 3a066156f66a4e89132010a8c83edc7029dbe19e
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio
Po wykonaniu kroków [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) i [Sprawdź środowisku Xamarin](../cross-platform/verify-your-xamarin-environment.md), w tym przewodniku przedstawiono sposób tworzenia aplikacji basic (pokazana poniżej) z platformy Xamarin.Forms. Z platformy Xamarin.Forms będzie pisania kodu interfejsu użytkownika raz w bibliotece klas .NET Standard. Xamarin zostanie automatycznie renderowania natywnych kontrolek interfejsu użytkownika dla systemu iOS, Android i Universal Windows Platform. Firma Microsoft zaleca takie podejście (a nie Projekt udostępniony), ponieważ biblioteka .NET Standard zawiera tylko tych interfejsów API architektury .NET, które są obsługiwane na wszystkich platformach docelowych, a ponieważ platformy Xamarin.Forms umożliwia udostępnianie kodu interfejsu użytkownika na platformach.  
  
 ![Przykładowe pogody aplikacji w systemach Android, iOS i Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
 Należy wykonać te czynności, aby go skompilować:  
  
-   [Konfigurowanie rozwiązania](#solution)  
  
-   [Pisanie kodu usługi udostępnionych danych](#dataservice)  
  
-   [Rozpocząć pisanie udostępnionego kodu interfejsu użytkownika](#uicode)  
  
-   [Testowanie aplikacji za pomocą programu Visual Studio Emulator for Android](#test)  
  
-   [Zakończ interfejsu użytkownika z natywnego wyglądu i działania na platformach](#finish)  
  
> [!TIP]
>  Dla tego projektu w można znaleźć kodu źródłowego pełną [xamarin forms próbek repozytorium w usłudze GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
##  <a name="solution"></a>Konfigurowanie rozwiązania  
 Te kroki tworzenie rozwiązań platformy Xamarin.Forms, które zawiera .NET Standard biblioteki klas dla udostępnionego kodu i dwa pakiety NuGet dodany.  
  
1.  W programie Visual Studio Utwórz nową **i Platform aplikacji (platformy Xamarin.Forms)** rozwiązania i nadaj mu nazwę **WeatherApp**. Wyszukaj szablonu, wybierając **Visual C#** i **wieloplatformowych** z listy znajdującej się po lewej stronie.  
  
     Jeśli nie jest, może być konieczne Zainstaluj program Xamarin, lub włączyć funkcję Visual Studio 2017, zobacz [Instalatora i zainstaluj](../cross-platform/setup-and-install.md).  
  
     ![Tworzenie nowej aplikacji puste &#40; Obsługujący wiele Platform aplikacji platformy Xamarin.Forms &#41; Projekt](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Po kliknięciu przycisku OK, należy wybrać kilka opcji. Wybierz **pusta aplikacja**, **platformy Xamarin.Forms** i **.NET Standard**:

     ![Tworzenie nowego projektu aplikacji dla wielu Platform](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  Po kliknięciu przycisku OK spowoduje utworzenie rozwiązania, będziesz mieć liczbę pojedynczych projektów:  
  
    -   **WeatherApp**: Biblioteka .NET Standard, gdzie będzie napisać kod, który jest współużytkowany przez platform, w tym wspólne logiki biznesowej i kodu interfejsu użytkownika przy użyciu platformy Xamarin.Forms.  
  
    -   **WeatherApp.Android**: projekt, który zawiera natywnego kodu dla systemu Android. To jest ustawiony jako domyślny projekt startowy.  
  
    -   **WeatherApp.iOS**: projekt, który zawiera kod macierzysty z systemem iOS.  
  
    -   **WeatherApp.UWP**: projekt, który zawiera kod platformy uniwersalnej systemu Windows do systemu Windows 10.  
  
    > [!NOTE]
    >  Można go dowolnie Usuń wszystkie projekty dla platformy, która nie docelowych.   
  
     W ramach każdego natywnego projektu mają dostęp do natywnej projektanta dla odpowiednich platform i można zaimplementować ekranów platformy i funkcji w razie potrzeby.  
  
4.  Uaktualnienie pakietu platformy Xamarin.Forms NuGet w rozwiązaniu do najnowsza stabilna wersja w następujący sposób. Firma Microsoft zaleca w ten sposób, podczas tworzenia nowego rozwiązania Xamarin:  
  
    -   Wybierz **Narzędzia > Menedżera pakietów NuGet > Zarządzaj pakietami NuGet dla rozwiązania**.  
  
    -   W obszarze **aktualizacje** karcie wyboru **platformy Xamarin.Forms** pakiet, a następnie sprawdź, czy zaktualizować wszystkie projekty w rozwiązaniu. (Uwaga: nie zaznaczaj żadnych aktualizacji dla Xamarin.Android.Support wyboru.)  
  
    -   Aktualizacja **wersji** do **najnowsze stabilny** wersji, która jest dostępna.  
  
    -   Kliknij przycisk **zainstalować**.  
  
         ![Aktualizowanie pakietu NuGet platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
5.  Dodaj **Newtonsoft.Json** pakiet NuGet do **WeatherApp** projektu, który zostanie użyty do przetwarzania informacji z usługi danych pogody:  
  
    -   Wybierz w Menedżera pakietów NuGet (wciąż otwarty z kroku 4), **Przeglądaj** karcie i wyszukaj **Newtonsoft**.  
  
    -   Wybierz **Newtonsoft.Json**.  
  
    -   Sprawdź **WeatherApp** projektu (dotyczy tylko projektów, w którym należy zainstalować pakiet).  
  
    -   Upewnij się, **wersji** pole jest ustawione na **najnowsze stabilny** wersji.  
  
    -   Kliknij przycisk **zainstalować**.  
  
    ![Znajdowanie i instalowanie pakietu Newtonsoft.Json NuGet](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  Powtórz krok 5, aby znaleźć i zainstalować **Microsoft.Net.Http** pakietu.  
  
7.  Skompiluj rozwiązanie i sprawdź, czy nie ma żadnych błędów kompilacji.  
  
##  <a name="dataservice"></a>Pisanie kodu usługi udostępnionych danych  
 **WeatherApp** projekt jest, gdzie będzie napisać kod .NET Standard biblioteki, która jest współużytkowana przez wszystkie platformy. Ta biblioteka jest automatycznie uwzględnione w aplikacji pakietów kompilacji przez iOS, Android i Windows projektów.  
  
 Aby uruchomić ten przykład, należy najpierw utworzysz wolnego klucz interfejsu API w [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
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
  
5.  Dodawanie klasy innych **WeatherApp** projektu o nazwie **Core** których będzie umieścić udostępnionych logiki biznesowej. Ten kod formularzy ciąg zapytania z kodem pocztowym, wywołuje usługę danych pogodą i wypełnia wystąpienia **pogody** klasy.  
  
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
                string key = "YOUR KEY HERE";  
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
  
7.  Tworzenie **WeatherApp** projektu biblioteki, aby się upewnić, że kod jest poprawny.  
  
##  <a name="uicode"></a>Rozpocząć pisanie udostępnionego kodu interfejsu użytkownika  
 Platformy Xamarin.Forms umożliwiają wdrożenie udostępnionego kodu interfejsu użytkownika w bibliotece .NET Standard. W tych kroków zostanie dodana do projektu z przycisku, który aktualizacji jego tekstu z danych zwróconych przez dane pogody usługi kodzie dodanym w poprzedniej sekcji strony:  
  
1.  Dodaj **strony zawartości** o nazwie **WeatherPage.cs** przez kliknięcie prawym przyciskiem myszy **WeatherApp** projekt i wybierając **Dodaj > Nowy element...** . W **Dodaj nowy element** okno dialogowe, wybierz opcję **strony zawartości**. Nie można więc wybierz **strony zawartości (C#)** lub **widok zawartości**. Nadaj mu nazwę **WeatherPage.cs**.  
  
     ![Dodawanie nowej strony XAML platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     Platformy Xamarin.Forms jest oparty na języku XAML, więc tworzy ten krok **WeatherPage.xaml** pliku wraz z pliku zagnieżdżonego kodem **WeatherPage.xaml.cs**. Dzięki temu można wygenerować interfejsu użytkownika przy użyciu języka XAML lub kodu. Należy to zrobić niektóre zarówno w tym przewodniku.  
  
2.  Aby dodać do ekranu WeatherPage przycisk, Zastąp zawartość **WeatherPage.xaml** następującym kodem:  
  
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
  
     Zwróć uwagę, że nazwa przycisku musi być zdefiniowana przy użyciu **x: Name** atrybutu, dzięki czemu możesz odwoływać ten przycisk według nazwy z wewnątrz pliku CodeBehind.  
  
3.  Aby dodać program obsługi zdarzeń dla przycisku **kliknięto element** zdarzeń, aby zaktualizować tekst przycisku, Zastąp zawartość **WeatherPage.xaml.cs** przy użyciu poniższego kodu. (Możesz także zmienić "60601" na inny kod pocztowy).  
  
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
  
4.  Aby otworzyć **WeatherPage** jako pierwszy ekran po uruchomieniu aplikacji, Zastąp konstruktora domyślnego w **App.cs** następującym kodem:  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Tworzenie **WeatherApp** projektu, aby się upewnić, że kod jest poprawny.  
  
##  <a name="test"></a>Testowanie aplikacji za pomocą programu Visual Studio Emulator for Android  
 Teraz możesz przystąpić do uruchomienia aplikacji! Umożliwia uruchamianie tylko wersji dla systemu Android teraz sprawdzić, czy aplikacja jest pobieranie danych z usługi pogody. Później również uruchomisz systemów iOS i wersje platformy uniwersalnej systemu Windows po dodaniu więcej elementów interfejsu użytkownika.   
  
1.  Ustaw **WeatherApp.Android** projekt jako projekt startowy ją prawym przyciskiem myszy i wybierając **Ustaw jako projekt startowy**.  
  
2.  Na pasku narzędzi programu Visual Studio, zobaczysz **WeatherApp.Android** wymienionym projektu docelowego. Wybierz jedną z systemem Android emulatorów do debugowania i trafień **F5**. Zalecamy użycie jednej z **VisualStudio** opcje emulatora, które będą uruchamiane aplikacji w Visual Studio Emulator for Android.  
  
     ![Wybieranie obiektu docelowego debugowania w emulatorze systemu Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  Po uruchomieniu aplikacji w emulatorze, kliknij przycisk **uzyskać pogody** przycisku. Powinien zostać wyświetlony tekst przycisku zaktualizowany do **Chicago**, która jest *tytuł* właściwości dane pobrane z usługi pogody.  
  
     ![Pogodowe aplikacji przed i po naciśnięcie przycisku](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a>Zakończ interfejsu użytkownika z natywnego wyglądu i działania na platformach  
 Platformy Xamarin.Forms renderuje natywnych kontrolek interfejsu użytkownika dla każdej platformy, dzięki czemu aplikacja ma automatycznie natywnego wyglądu i działania. Aby zobaczyć więcej wyraźnie, umożliwia zakończenie interfejsu użytkownika z pola wejściowego dla kodu pocztowego, a następnie Wyświetl dane pogody zostanie zwrócona przez usługę.  
  
1.  Zastąp zawartość **WeatherPage.xaml** przy użyciu poniższego kodu. Elementy, które są przypisywane przy użyciu **x: Name** atrybutu zgodnie z wcześniejszym opisem można odwoływać się z kodu. Udostępnia szereg platformy Xamarin.Forms [opcje układu](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com). W tym miejscu używa WeatherPage [siatki](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) (xamarin.com) i [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).  
  
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
  
     Chociaż nie jest tutaj widoczny, możesz użyć **OnPlatform** tag, aby wybrać wartość właściwości, która jest specyficzna dla bieżącej platformie, na którym działa aplikacja (zobacz [niezbędne składni języka XAML](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (xamarin.com). W pliku związanym z kodem, można użyć [Device.OnPlatform API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) do takiej obsługi.  
  
2.  W **WeatherPage.xaml.cs**, Zastąp **GetWeatherBtn_Clicked** obsługi zdarzeń przy użyciu poniższego kodu. Sprawdza ten kod, który jest kod pocztowy w polu wpisu, pobiera dane dla tego kodu pocztowego, ustawia kontekst powiązania całej strony powstałe w ten sposób **pogody** wystąpienia, a następnie ustawia tekst przycisku "Wyszukaj ponownie." Należy pamiętać, że każda etykieta w interfejsie użytkownika jest powiązana z właściwością **pogody** klasy, dlatego podczas ustawiania kontekstu powiązania ekranu **pogody** wystąpienia, te etykiety automatycznej aktualizacji.  
  
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
  
3.  Uruchom aplikację na wszystkich platformach trzy — Android, iOS i Windows — przez kliknięcie prawym przyciskiem myszy odpowiedni projekt, wybierając **Ustaw jako projekt startowy**i uruchamianie aplikacji na urządzeniu lub w emulatorem ani symulatorem. Wprowadź prawidłowy kod pocztowy 5 cyfrowy w Stanach Zjednoczonych i naciśnij klawisz **uzyskać pogody** przycisk, aby wyświetlić dane pogody dla regionu, jak pokazano poniżej. Musisz mieć Visual Studio podłączone do komputera z systemem Mac OS X w sieci dla projektu iOS.  
  
     ![Przykładowe pogody aplikacji w systemach Android, iOS i Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
 Kod źródłowy pełną dla tego projektu jest [xamarin forms próbek repozytorium w usłudze GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).