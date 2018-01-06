---
title: "Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
ms.openlocfilehash: b25344afa89c3b1244203a914b9b64347223870d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Dowiedz się podstawowe informacje dotyczące tworzenia aplikacji z platformy Xamarin.Forms w programie Visual Studio
Po wykonaniu kroków [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) i [Sprawdź środowisku Xamarin](../cross-platform/verify-your-xamarin-environment.md), w tym przewodniku przedstawiono sposób tworzenia aplikacji basic (pokazana poniżej) z platformy Xamarin.Forms. Z platformy Xamarin.Forms będzie pisania kodu interfejsu użytkownika raz w bibliotece klas przenośnych (PCL). Xamarin zostanie automatycznie renderowania natywnych kontrolek interfejsu użytkownika dla systemu iOS, Android i Windows Platform. Zalecamy takie podejście, ponieważ opcja PCL najlepiej obsługuje przy użyciu tylko tych interfejsów API architektury .NET, które są obsługiwane na wszystkich platformach docelowych, a ponieważ platformy Xamarin.Forms umożliwia udostępnianie kodu interfejsu użytkownika na platformach.  
  
 ![Przykładowe pogody aplikacji w systemach Android, iOS i Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
 Należy wykonać te czynności, aby go skompilować:  
  
-   [Konfigurowanie rozwiązania](#solution)  
  
-   [Pisanie kodu usługi udostępnionych danych](#dataservice)  
  
-   [Rozpocząć pisanie udostępnionego kodu interfejsu użytkownika](#uicode)  
  
-   [Testowanie aplikacji za pomocą programu Visual Studio Emulator for Android](#test)  
  
-   [Zakończ interfejsu użytkownika z natywnego wyglądu i działania na platformach](#finish)  
  
> [!TIP]
>  Dla tego projektu w można znaleźć kodu źródłowego pełną [xamarin forms próbek repozytorium w usłudze GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
##  <a name="solution"></a>Konfigurowanie rozwiązania  
 Te kroki tworzenie rozwiązań platformy Xamarin.Forms, które zawiera PCL dla udostępnionego kodu i dwa pakiety NuGet dodany.  
  
1.  W programie Visual Studio Utwórz nową **pusta aplikacja (przenośna platformy Xamarin.Forms)** rozwiązania i nadaj mu nazwę **WeatherApp**. Tego szablonu można znaleźć najłatwiej wprowadzając **platformy Xamarin.Forms** do pola wyszukiwania.  
  
     Jeśli nie jest, może być konieczne Zainstaluj program Xamarin, lub włączyć funkcję Visual Studio 2015, zobacz [Instalatora i zainstaluj](../cross-platform/setup-and-install.md).  
  
     ![Tworzenie nowej aplikacji puste &#40; Przenośne platformy Xamarin.Forms &#41; Projekt](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")  
  
2.  Po kliknięciu przycisku OK spowoduje utworzenie rozwiązania, będziesz mieć liczbę pojedynczych projektów:  
  
    -   **WeatherApp (przenośny)**: PCL, w którym będzie pisania kodu, który jest współużytkowany przez platform, w tym wspólne logiki biznesowej i korzystanie z platformy Xamarin.Forms kodu interfejsu użytkownika.  
  
    -   **WeatherApp.Droid**: projekt, który zawiera natywnego kodu dla systemu Android. To jest ustawiony jako domyślny projekt startowy.  
  
    -   **WeatherApp.iOS**: projekt, który zawiera kod macierzysty z systemem iOS.  
  
    -   **WeatherApp.UWP**: projekt, który zawiera kod platformy uniwersalnej systemu Windows do systemu Windows 10.  
  
    -   **WeatherApp.Windows (Windows 8.1)**: projekt, który zawiera kod natywny Windows 8.1.  
  
    -   **WeatherApp.WinPhone (Windows Phone 8.1)**: projekt, który zawiera kod macierzysty Windows Phone.  
  
    > [!NOTE]
    >  Można go dowolnie Usuń wszystkie projekty dla platformy, która nie docelowych. Na potrzeby tego przewodnika firma Microsoft będzie odwoływać się do projektów dla systemu Android, iOS i Windows Phone 8.1. Projekty platformy uniwersalnej systemu Windows i Windows 8.1 jest bardzo podobny do pracy z projektu Windows Phone 8.1.  
  
     W ramach każdego natywnego projektu mają dostęp do natywnej projektanta dla odpowiednich platform i można zaimplementować ekranów platformy i funkcji w razie potrzeby.  
  
3.  Uaktualnienie pakietu platformy Xamarin.Forms NuGet w rozwiązaniu do najnowsza stabilna wersja w następujący sposób. Firma Microsoft zaleca w ten sposób, podczas tworzenia nowego rozwiązania Xamarin:  
  
    -   Wybierz **Narzędzia > Menedżera pakietów NuGet > Zarządzaj pakietami NuGet dla rozwiązania**.  
  
    -   W obszarze **aktualizacje** karcie wyboru **platformy Xamarin.Forms** aktualizacji i sprawdź, czy zaktualizować wszystkie projekty w rozwiązaniu. (Uwaga: nie zaznaczaj żadnych aktualizacji dla Xamarin.Android.Support wyboru.)  
  
    -   Aktualizacja **wersji** do **najnowsze stabilny** wersji, która jest dostępna.  
  
    -   Kliknij przycisk **aktualizacji**.  
  
         ![Aktualizowanie pakietu NuGet platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
4.  Dodaj **Newtonsoft.Json** i pakiet NuGet do projektu PCL, który zostanie użyty do przetwarzania informacji z usługi danych pogody:  
  
    -   Wybierz w Menedżera pakietów NuGet (wciąż otwarty w kroku 3), **Przeglądaj** karcie i wyszukaj **Newtonsoft**.  
  
    -   Wybierz **Newtonsoft.Json**.  
  
    -   Sprawdź **WeatherApp** projektu (dotyczy tylko projektów, w którym należy zainstalować pakiet).  
  
    -   Upewnij się, **wersji** pole jest ustawione na **najnowsze stabilny** wersji.  
  
    -   Kliknij przycisk **zainstalować**.  
  
    -   ![Znajdowanie i instalowanie pakietu Newtonsoft.Json NuGet](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
5.  Powtórz kroki od 4 do znajdować i instalować **Microsoft.Net.Http** pakietu.  
  
6.  Skompiluj rozwiązanie i sprawdź, czy nie ma żadnych błędów kompilacji.  
  
##  <a name="dataservice"></a>Pisanie kodu usługi udostępnionych danych  
 **WeatherApp (przenośny)** projekt jest, gdzie będzie napisać kod biblioteki klas przenośnych (PCL), która jest współużytkowana przez wszystkie platformy. PCL jest automatycznie uwzględnione w aplikacji pakietów kompilacji przez iOS, Android i Windows Phone projektów.  
  
 Aby uruchomić ten przykład musi najpierw utworzysz wolnego klucz interfejsu API w [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
 Poniższe kroki następnie dodaj kod do PCL dostęp do przechowywania danych pochodzących z tej usługi pogody:  
  
1.  Kliknij prawym przyciskiem myszy **WeatherApp** projekt i wybierz **Dodaj > klasy...** . W **Dodaj nowy element** okna dialogowego, nazwa pliku **Weather.cs**. Ta klasa będzie używane do przechowywania danych z usługi data pogody.  
  
2.  Zastąp całą zawartość **Weather.cs** następującym kodem:  
  
    ```csharp  
    namespace WeatherApp  
    {  
        public class Weather  
        {  
            public string Title { get; set; }  
            public string Temperature { get; set; }  
            public string Wind { get; set; }  
            public string Humidity { get; set; }  
            public string Visibility { get; set; }  
            public string Sunrise { get; set; }  
            public string Sunset { get; set; }  
  
            public Weather()  
            {  
                //Because labels bind to these values, set them to an empty string to  
                //ensure that the label appears on all platforms by default.  
                this.Title = " ";  
                this.Temperature = " ";  
                this.Wind = " ";  
                this.Humidity = " ";  
                this.Visibility = " ";  
                this.Sunrise = " ";  
                this.Sunset = " ";  
            }  
        }  
    }  
    ```  
  
3.  Dodaj kolejną klasę do projektu PCL o nazwie **DataService.cs** , w którym będziesz używać do przetwarzania danych JSON z pogodą usługi danych.  
  
4.  Zastąp całą zawartość **DataService.cs** następującym kodem:  
  
    ```csharp  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
    using System.Net.Http;  
  
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
  
5.  Dodaj klasę innych do PCL o nazwie **Core** których będzie umieścić udostępnionych logiki biznesowej, takich jak logiki, który wchodzi w skład ciąg zapytania z kodem pocztowym, wywołuje usługę danych pogody i wypełnia wystąpienia **pogody**klasy.  
  
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
  
7.  Tworzenie **WeatherApp** PCL projektu, aby się upewnić, że kod jest poprawny.  
  
##  <a name="uicode"></a>Rozpocząć pisanie udostępnionego kodu interfejsu użytkownika  
 Platformy Xamarin.Forms umożliwiają wdrożenie udostępnionego kodu interfejsu użytkownika w PCL. W tych krokach warto ekranu PCL z przycisku, który aktualizacji jego tekstu z danych zwróconych przez dane pogody usługi kodzie dodanym w poprzedniej sekcji:  
  
1.  Dodaj **strony Xaml formularzy** o nazwie **WeatherPage.cs** przez kliknięcie prawym przyciskiem myszy **WeatherApp** projekt i wybierając **Dodaj > Nowy element...** . W **Dodaj nowy element** okna dialogowego, wyszukaj frazę "Form", wybierz **strony Xaml formularzy**i nadaj mu nazwę **WeatherPage.cs**.  
  
     Platformy Xamarin.Forms jest oparty na języku XAML, więc tworzy ten krok **WeatherPage.xaml** pliku wraz z pliku zagnieżdżonego kodem **WeatherPage.xaml.cs**. Dzięki temu można wygenerować interfejsu użytkownika przy użyciu języka XAML lub kodu. Należy to zrobić niektóre zarówno w tym przewodniku.  
  
     ![Dodawanie nowej strony XAML platformy Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
2.  Aby dodać do ekranu WeatherPage przycisk, Zastąp zawartość WeatherPage.xaml następujące czynności:  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage">  
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>  
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
                this.Title = "Sample Weather App";  
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;  
  
                //Set the default binding to a default object for now  
                this.BindingContext = new Weather();  
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
        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Skompiluj projekt WeatherApp PCL, aby upewnić się, że kod jest poprawny.  
  
##  <a name="test"></a>Testowanie aplikacji za pomocą programu Visual Studio Emulator for Android  
 Teraz możesz przystąpić do uruchomienia aplikacji! Umożliwia uruchamianie tylko wersji dla systemu Android teraz sprawdzić, czy aplikacja jest pobieranie danych z usługi pogody. Później również uruchomisz systemów iOS i Windows Phone wersji po dodaniu więcej elementów interfejsu użytkownika. (Uwaga: Jeśli korzystasz z programu Visual Studio w systemie Windows 7, będzie wykonać te same czynności, ale zamiast tego zostanie Xamarin Player.)  
  
1.  Ustaw **WeatherApp.Droid** projekt jako projekt startowy ją prawym przyciskiem myszy i wybierając **Ustaw jako projekt startowy**.  
  
2.  Na pasku narzędzi programu Visual Studio, zobaczysz **WeatherApp.Droid** wymienionym projektu docelowego. Wybierz jedną z systemem Android emulatorów do debugowania i trafień **F5**. Zalecamy użycie jednej z **emulatora VS** opcje, które będą uruchamiane aplikacji w Visual Studio Emulator for Android opcje.  
  
     ![Wybieranie obiektu docelowego debugowania programu VS emulatora](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  Po uruchomieniu aplikacji w emulatorze, kliknij przycisk **uzyskać pogody** przycisku. Powinien zostać wyświetlony tekst przycisku zaktualizowany do **Chicago, IL**, która jest *tytuł* właściwości dane pobrane z usługi pogody.  
  
     ![Pogodowe aplikacji przed i po naciśnięcie przycisku](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a>Zakończ interfejsu użytkownika z natywnego wyglądu i działania na platformach  
 Platformy Xamarin.Forms renderuje natywnych kontrolek interfejsu użytkownika dla każdej platformy, dzięki czemu aplikacja ma automatycznie natywnego wyglądu i działania. Aby zobaczyć więcej wyraźnie, umożliwia zakończenie interfejsu użytkownika z pola wejściowego dla kodu pocztowego, a następnie Wyświetl dane pogody zostanie zwrócona przez usługę.  
  
1.  Zastąp zawartość **WeatherPage.xaml** przy użyciu poniższego kodu. Należy pamiętać, że każdy element ma nazwę przy użyciu **x: Name** atrybutu zgodnie z wcześniejszym opisem tak, aby element można odwoływać się z kodu. Udostępnia szereg platformy Xamarin.Forms [opcje układu](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com); w tym miejscu używa WeatherPage [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage">  
  
      <ContentPage.Resources>  
        <ResourceDictionary>  
          <Style x:Key="labelStyle" TargetType="Label">  
            <Setter Property="TextColor" Value="#a8a8a8" />  
            <Setter Property="FontSize" Value="Small" />  
          </Style>  
          <Style x:Key="fieldStyle" TargetType="Label">  
            <Setter Property="TextColor">  
              <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />  
            </Setter>  
            <Setter Property="FontSize" Value="Medium" />  
          </Style>  
          <Style x:Key="fieldView" TargetType="ContentView">  
            <Setter Property="Padding" Value="10,0,0,0" />  
          </Style>  
        </ResourceDictionary>  
      </ContentPage.Resources>  
  
      <ContentPage.Content>  
        <ScrollView>  
          <StackLayout>  
            <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"  
                  BackgroundColor="#545454">  
              <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">  
                <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"  
                    FontSize="Medium" />  
                <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />  
                <Entry x:Name="zipCodeEntry" />  
              </StackLayout>  
              <StackLayout Padding="0,0,0,10" VerticalOptions="End">  
                <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >  
                  <!-- Set iOS colors; use defaults on other platforms -->  
                  <Button.TextColor>  
                    <OnPlatform x:TypeArguments="Color" iOS="White"/>  
                  </Button.TextColor>  
                  <Button.BorderColor>  
                    <OnPlatform x:TypeArguments="Color" iOS="White"/>  
                  </Button.BorderColor>  
                </Button>  
              </StackLayout>  
            </StackLayout>  
            <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">  
              <Label Text="Location" Style="{StaticResource labelStyle}" />  
              <ContentView Style="{StaticResource fieldView}">  
                <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />  
              </ContentView>  
              <Label Text="Temperature" Style="{StaticResource labelStyle}" />  
              <ContentView Style="{StaticResource fieldView}">  
                <Label x:Name="tempLabel" Text="{Binding Temperature}"  
                    Style="{StaticResource fieldStyle}" />  
              </ContentView>  
              <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />  
              <ContentView Style="{StaticResource fieldView}">  
                <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />  
              </ContentView>  
              <Label Text="Humidity" Style="{StaticResource labelStyle}" />  
              <ContentView Style="{StaticResource fieldView}">  
                <Label x:Name="humidityLabel" Text="{Binding Humidity}"  
                    Style="{StaticResource fieldStyle}" />  
              </ContentView>  
              <Label Text="Visibility" Style="{StaticResource labelStyle}" />  
              <ContentView Style="{StaticResource fieldView}">  
                <Label x:Name="visibilitylabel" Text="{Binding Visibility}"  
                    Style="{StaticResource fieldStyle}" />  
              </ContentView>  
              <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />  
              <ContentView Style="{StaticResource fieldView}">  
                <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"  
                    Style="{StaticResource fieldStyle}" />  
              </ContentView>  
              <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />  
              <ContentView Style="{StaticResource fieldView}">  
                <Label x:Name="sunsetLabel" Text="{Binding Sunset}"  
                    Style="{StaticResource fieldStyle}" />  
              </ContentView>  
            </StackLayout>  
          </StackLayout>  
        </ScrollView>  
      </ContentPage.Content>  
    </ContentPage>  
    ```  
  
     Zwróć uwagę na użycie **OnPlatform** tag w platformy Xamarin.Forms. **OnPlatform** wybiera wartość właściwości, która jest specyficzna dla bieżącej platformie, na którym działa aplikacja (zobacz [zewnętrznych składni języka XAML](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (xamarin.com). Używamy go w tym miejscu można ustawić inny kolor tekstu dla pól danych: białe w systemach Android i Windows Phone, czarne w systemie iOS. Można użyć **OnPlatform** żadnych właściwości i wszystkie typy danych, aby dostosować specyficzne dla platformy dowolnym z XAML. W pliku związanym z kodem, można użyć [Device.OnPlatform API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) do takiej obsługi.  
  
2.  W **WeatherPage.xaml.cs**, Zastąp **GetWeatherBtn_Clicked** obsługi zdarzeń przy użyciu poniższego kodu. Sprawdza ten kod, który jest kod pocztowy w polu wpisu, pobiera dane dla tego kodu pocztowego, ustawia kontekst powiązania cały ekran wynikowy wystąpienia pogody, a następnie ustawia tekst przycisku "Wyszukaj ponownie." Należy pamiętać, że każda etykieta w interfejsie użytkownika jest powiązany z właściwością klasy pogody tak podczas ustawioną kontekstu powiązania ekranu **pogody** wystąpienia, te etykiety automatycznej aktualizacji.  
  
    ```csharp  
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
    {  
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
        {  
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
            this.BindingContext = weather;  
            getWeatherBtn.Text = "Search Again";  
        }  
    }  
    ```  
  
3.  Uruchom aplikację na wszystkich platformach trzy — Android, iOS i Windows Phone — prawym przyciskiem myszy odpowiedni projekt, wybierając Ustaw jako projekt startowy i uruchamianie aplikacji na urządzeniu lub w emulatorem ani symulatorem. Wprowadź prawidłowy kod pocztowy Stanów Zjednoczonych (na przykład 60601) i kliknij przycisk Pobierz pogody do wyświetlania danych o pogodzie w danym regionie, jak pokazano poniżej. Oczywiście musisz mieć Visual Studio podłączone do komputera z systemem Mac OS X w sieci dla projektu iOS.  
  
     ![Przykładowe pogody aplikacji w systemach Android, iOS i Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
 Kod źródłowy pełną dla tego projektu jest [xamarin forms próbek repozytorium w usłudze GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).