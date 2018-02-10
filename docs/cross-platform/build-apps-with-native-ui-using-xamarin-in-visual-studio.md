---
title: "Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika za pomocą platformy Xamarin w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: d9d9ecfd180ce3d4bbd54eb091e6c0e3153bd7cd
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika za pomocą platformy Xamarin w programie Visual Studio
Po wykonaniu kroków [Instalatora i zainstaluj](../cross-platform/setup-and-install.md) i [Sprawdź środowisku Xamarin](../cross-platform/verify-your-xamarin-environment.md), w tym przewodniku przedstawiono sposób tworzenia aplikacji platformy Xamarin basic (pokazana poniżej) z natywnego warstwy interfejsu użytkownika. Udostępniony kod znajduje się w bibliotece klas przenośnych (PCL) natywnego interfejsu użytkownika, i projekty poszczególnych platform zawierają definicje interfejsu użytkownika.  
  
 ![Aplikacja Xamarin w systemach Android i Windows Phone](../cross-platform/media/cross-plat-xamarin-build-1.png "kompilacji usługi Xamarin Plat między 1")  
  
 Należy wykonać te czynności, aby go skompilować:  
  
-   [Konfigurowanie rozwiązania](#solution)  
  
-   [Pisanie kodu usługi udostępnionych danych](#dataservice)  
  
-   [Projektowanie interfejsu użytkownika dla systemu Android](#Android)  
  
-   [Projektowanie interfejsu użytkownika dla Windows Phone](#Windows)  
  
-   [Następne kroki](#next)  
  
> [!TIP]
>  Dla tego projektu w można znaleźć kodu źródłowego pełną [mobile przykłady repozytorium w usłudze GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
>   Jeśli masz problemy lub wystąpiły błędy, Opublikuj pytania na [forums.xamarin.com](http://forums.xamarin.com). Wiele błędów można rozwiązać, aktualizując do SDK najnowsze wymagane przez program Xamarin, które są opisane w [informacje o wersji programu Xamarin](https://developer.xamarin.com/releases/) dla każdej platformy.    
  
> [!NOTE]
>  Dokumentacja dla deweloperów w programie Xamarin oferuje kilka wskazówki szybkiego startu jak również nowości sekcje wymienione poniżej. Na tych stronach upewnij się, że wybrano "Visual Studio", w prawym górnym rogu strony, aby wyświetlić wskazówki dotyczące programu Visual Studio.  
>   
>  -   Xamarin aplikacji za pomocą natywnego interfejsu użytkownika:  
>   
>      -   [Witaj, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (prosta aplikacja z jednym ekranie)  
>     -   [Witaj, Android Wieloekranowy](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (aplikacja z nawigacją między ekranami)  
>     -   [Android wskazówki fragmenty](http://developer.xamarin.com/guides/android/platform_features/fragments/fragments_walkthrough/) (używanych do ekranów wzorzec/szczegół, między innymi)  
>     -   [Witaj, z systemem iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)  
>     -   [Witaj, iOS Multiscreen](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)  
> -   Z platformy Xamarin.Forms (udostępnionego UI) przy użyciu aplikacji Xamarin  
>   
>      -   [Witaj, platformy Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)  
>     -   [Witaj, Wieloekranowy platformy Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)  
  
##  <a name="solution"></a>Konfigurowanie rozwiązania  
 Te kroki tworzenia rozwiązania Xamarin z natywnego interfejsu użytkownika, który zawiera PCL dla udostępnionego kodu i dwa pakiety NuGet dodany.  
  
1.  W programie Visual Studio Utwórz nową **pusta aplikacja (Native przenośne)** rozwiązania i nadaj mu nazwę **WeatherApp**. Tego szablonu można znaleźć najłatwiej wprowadzając **natywnego przenośne** do pola wyszukiwania.  
  
     Jeśli nie jest, może być konieczne Zainstaluj program Xamarin, lub włączyć funkcję Visual Studio 2015, zobacz [Instalatora i zainstaluj](../cross-platform/setup-and-install.md).  
  
2.  Po kliknięciu przycisku OK spowoduje utworzenie rozwiązania, będziesz mieć liczbę pojedynczych projektów:  
  
    -   **WeatherApp (przenośny)**: PCL, w którym będzie pisania kodu, który jest współużytkowany przez platform, w tym wspólne logiki biznesowej i korzystanie z platformy Xamarin.Forms kodu interfejsu użytkownika.  
  
    -   **WeatherApp.Droid**: projekt, który zawiera natywnego kodu dla systemu Android. To jest ustawiony jako domyślny projekt startowy.  
  
    -   **WeatherApp.iOS**: projekt, który zawiera kod macierzysty z systemem iOS.  
  
    -   **WeatherApp.WinPhone (Windows Phone 8.1)**: projekt, który zawiera kod macierzysty Windows Phone.  
  
     W ramach każdego natywnego projektu mają dostęp do natywnej projektanta dla odpowiednich platform i można zaimplementować ekrany określonych platform.  
  
3.  Dodaj **Newtonsoft.Json** i pakiet NuGet do projektu PCL, który zostanie użyty do przetwarzania informacji z usługi danych pogody:  
  
    -   Kliknij prawym przyciskiem myszy **rozwiązania "WeatherApp"** w Eksploratorze rozwiązań i wybierz **Zarządzaj pakietami NuGet rozwiązania...** .  
  
         W oknie NuGet wybierz **Przeglądaj** karcie i wyszukaj **Newtonsoft**.  
  
    -   Wybierz **Newtonsoft.Json**.  
  
    -   Po prawej stronie okna, sprawdź **WeatherApp** projektu (dotyczy tylko projektów, w którym należy zainstalować pakiet).  
  
    -   Upewnij się, **wersji** pole jest ustawione na **najnowsze stabilny** wersji.  
  
    -   Kliknij przycisk **zainstalować**.  
  
    -   ![Znajdowanie i instalowanie pakietu Newtonsoft.Json NuGet](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
4.  Powtórz kroki od 3 do znajdować i instalować **Microsoft.Net.Http** pakietu.  
  
5.  Skompiluj rozwiązanie i sprawdź, czy nie ma żadnych błędów kompilacji.  
  
##  <a name="dataservice"></a>Pisanie kodu usługi udostępnionych danych  
 **WeatherApp (przenośny)** projekt jest, gdzie będzie napisać kod biblioteki klas przenośnych (PCL), która jest współużytkowana przez wszystkie platformy. PCL jest automatycznie uwzględnione w pakiety aplikacji utworzony przez system iOS, Android i Windows Phone projektów.  
  
 Poniższe kroki następnie dodaj kod, aby PCL dostęp do przechowywania danych pochodzących z tej usługi pogody:  
  
1.  Aby uruchomić ten przykład musi najpierw utworzysz wolnego klucz interfejsu API w [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
2.  Kliknij prawym przyciskiem myszy **WeatherApp** projekt i wybierz **Dodaj > klasy...** . W **Dodaj nowy element** okna dialogowego, nazwa pliku **Weather.cs**. Ta klasa będzie używane do przechowywania danych z usługi data pogody.  
  
3.  Zastąp całą zawartość **Weather.cs** następującym kodem:  
  
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
  
4.  Dodaj kolejną klasę do projektu PCL o nazwie **DataService.cs** , w którym będziesz używać do przetwarzania danych JSON z pogodą usługi danych.  
  
5.  Zastąp całą zawartość **DataService.cs** następującym kodem:  
  
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
  
6.  Dodaj klasę innych do PCL o nazwie **Core** których będzie umieścić udostępnionych logiki biznesowej, takich jak logiki, który wchodzi w skład ciąg zapytania z kodem pocztowym, wywołuje usługę danych pogody i wypełnia wystąpienia **pogody**klasy.  
  
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
                string key = "YOUR KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }
  
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
  
8.  Zastąp *SWÓJ klucz tutaj* w kodu przy użyciu klucza interfejsu API uzyskanym w kroku 1 (nadal wymaga cudzysłowów wokół niego).  
  
9. Usuń MyClass.cs w PCL, ponieważ firma Microsoft nie będzie go używać.  
  
10. Tworzenie **WeatherApp** PCL projektu, aby się upewnić, że kod jest poprawny.  
  
##  <a name="Android"></a>Projektowanie interfejsu użytkownika dla systemu Android  
 Teraz firma Microsoft będzie Projektowanie interfejsu użytkownika, podłącz go do udostępnionego kodu, a następnie uruchom aplikację.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Projekt wyglądu i działania aplikacji  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **WeatherApp.Droid**>**zasobów**>**układu** folderu i Otwórz **Main.axml**. Spowoduje to otwarcie pliku w Projektancie visual. (Jeśli zostanie wyświetlony błąd związany z języka Java, zobacz ten [wpis w blogu](http://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)  
  
    > [!TIP]
    >  Istnieje wiele plików w projekcie. Eksploracja ich jest poza zakres tego tematu, ale jeśli chcesz przejść do struktury projektu dla systemu Android nieco więcej, zobacz [część 2 nowości](http://developer.xamarin.com/guides/android/getting_started/hello,android/hello,android_deepdive/) Hello Android tematu na xamarin.com.  
  
2.  Wybierz i usuń przycisk domyślny, która jest wyświetlana w projektancie.  
  
3.  Otwórz przybornika **Widok > innych okien > przybornika**.  
  
4.  Z **przybornika**, przeciągnij **RelativeLayout** formantu do projektanta. Ten formant będzie używany jako kontenera nadrzędnego dla innych formantów.  
  
    > [!TIP]
    >  Jeśli w dowolnym momencie układ nie powiodła się ją poprawnie wyświetlić, Zapisz plik i przełączanie między **projekt** i **źródła** karty, aby odświeżyć.  
  
5.  W **właściwości** ustaw **tła** właściwości (w grupie styl) `#545454`.  
  
6.  Z **przybornika**, przeciągnij **TextView** kontrolować na **RelativeLayout** formantu.  
  
7.  W **właściwości** okna, ustaw te właściwości (Uwaga: Aby posortować listę alfabetycznie za pomocą przycisku sortowania w pasku narzędzi okna właściwości może pomóc):  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**tekst**|**Wyszukiwanie według kod pocztowy**|  
    |**id**|`@+id/ZipCodeSearchLabel`|  
    |**layout_marginLeft**|`10dp`|  
    |**textColor**|`@android:color/white`|  
    |**textStyle**|`bold`|  
  
    > [!TIP]
    >  Należy zauważyć, że wiele właściwości nie mogą zawierać rozwijalna lista wartości, które można wybrać.  Może być trudne do odgadnięcia, jakie wartości ciągu do użycia dla dowolnego danej właściwości. Masz sugestie, spróbuj wyszukiwania dla nazwy właściwości w [R.attr](http://developer.android.com/reference/android/R.attr.html) klasy strony.  
    >   
    >  Ponadto wyszukiwania w szybkiej sieci web często prowadzi do strony [http://stackoverflow.com/](http://stackoverflow.com/) gdzie inne używane tej samej właściwości.  
  
     Odwołania, po przejściu do **źródła** widoku, powinien zostać wyświetlony następujący kod dla tego elementu:  
  
    ```xml  
    <TextView  
        android:text="Search by Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:id="@+id/ZipCodeSearchLabel"  
        android:layout_centerVertical="true"  
        android:layout_marginLeft="10dp"  
        android:textColor="@android:color/white"  
        android:textStyle="bold" />  
  
    ```  
  
8.  Z **przybornika**, przeciągnij **TextView** kontrolować na **RelativeLayout** kontroli i umieść je poniżej ZipCodeSearchLabel formantu. W tym celu upuszczania nowego formantu w odpowiednich krawędzi istniejącej kontrolce; pomaga powiększenie dla tego projektanta w pewnym stopniu.  
  
9. W **właściwości** okna, ustaw te właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**tekst**|**Kod pocztowy**|  
    |**id**|`@+id/ZipCodeLabel`|  
    |**layout_marginLeft**|`10dp`|  
    |**layout_marginTop**|`5dp`|  
  
     Kod w **źródła** widok powinien wyglądać następująco:  
  
    ```xml  
    <TextView  
        android:text="Zip Code"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeSearchLabel"  
        android:id="@+id/ZipCodeLabel"  
        android:layout_marginTop="5dp"  
        android:layout_marginLeft="10dp" />  
    ```  
  
10. Z **przybornika**, przeciągnij **numer** kontrolować na **RelativeLayout**, umieść ją poniżej **kod pocztowy** etykiety. Następnie ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**id**|`@+id/zipCodeEntry`|  
    |**layout_marginLeft**|`10dp`|  
    |**layout_marginBottom**|`10dp`|  
    |**width**|`165dp`|  
  
     Ponownie kod:  
  
    ```xml  
    <EditText  
        android:inputType="number"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_below="@id/ZipCodeLabel"  
        android:id="@+id/zipCodeEntry"  
        android:layout_marginLeft="10dp"  
        android:layout_marginBottom="10dp"  
        android:width="165dp" />  
    ```  
  
11. Z **przybornika**, przeciągnij **przycisk** na **RelativeLayout** kontroli i umieść je z prawej strony zipCodeEntry formantu. Następnie ustaw te właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**id**|`@+id/weatherBtn`|  
    |**tekst**|**Pobierz pogody**|  
    |**layout_marginLeft**|`20dp`|  
    |**layout_alignBottom**|`@id/zipCodeEntry`|  
    |**width**|`165dp`|  
  
    ```xml  
    <Button    android:text="Get Weather"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:layout_toRightOf="@id/zipCodeEntry"  
        android:id="@+id/weatherBtn"  
        android:layout_marginLeft="20dp"  
        android:layout_alignBottom="@id/zipCodeEntry"  
        android:width="165dp" />  
    ```  
  
12. Obecnie masz za mało środowisko do tworzenia podstawowy interfejs użytkownika za pomocą projektanta dla systemu Android. Interfejs użytkownika można także utworzyć przez dodanie znaczników bezpośrednio do pliku .asxml strony. Aby utworzyć pozostałe interfejsu użytkownika w ten sposób, przejdź do widoku źródłowego w projektancie, a następnie poza następujący kod znaczników *pod* `</RelativeLayout>` tag (tak, który znajduje się pod tagu... te elementy nie są zawarte w ReleativeLayout).  
  
    ```xml  
    <TextView  
            android:text="Location"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/locationLabel"  
            android:layout_marginLeft="10dp"  
            android:layout_marginTop="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/locationText"  
            android:layout_marginLeft="20dp"  
            android:layout_marginBottom="10dp" />  
        <TextView  
            android:text="Temperature"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/tempLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/tempText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Wind Speed"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/windLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/windText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Humidity"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/humidtyLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/humidityText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Visibility"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/visibilityLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/visibilityText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Time of Sunrise"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/sunriseLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/sunriseText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
        <TextView  
            android:text="Time of Sunset"  
            android:textAppearance="?android:attr/textAppearanceSmall"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/sunsetLabel"  
            android:layout_marginLeft="10dp" />  
        <TextView  
            android:textAppearance="?android:attr/textAppearanceMedium"  
            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:id="@+id/sunsetText"  
            android:layout_marginBottom="10dp"  
            android:layout_marginLeft="20dp" />  
  
    ```  
  
13. Zapisz plik i przejdź do **projekt** widoku. Twój interfejs użytkownika powinna wyglądać następująco:  
  
     ![Interfejs użytkownika dla aplikacji systemu Android](../cross-platform/media/xamarin_androidui.png "Xamarin_AndroidUI")  
  
14. Otwórz **MainActivity.cs** i usuwania wierszy w *OnCreate* — metoda, która odwołuje się do przycisk domyślny, który został wcześniej usunięty. Kod powinien wyglądać następująco po wykonaniu tych czynności:  
  
    ```  
    protected override void OnCreate (Bundle bundle)  
    {  
        base.OnCreate (bundle);  
  
        // Set our view from the "main" layout resource  
        SetContentView (Resource.Layout.Main);  
    }  
    ```  
  
15. Tworzenie projektu dla systemu Android, aby sprawdzić swoją pracę. Należy pamiętać, że kompilowanie dodaje sterowanie identyfikatorów **Resource.Designer.cs** plików, dzięki czemu mogą odwoływać się do formantów według nazwy w kodzie.  
  
### <a name="consume-your-shared-code"></a>Korzystać z udostępnionego kodu  
  
1.  Otwórz **MainActivity.cs** pliku **WeatherApp** projektu w edytorze kodu i zastąp jego zawartość przy użyciu poniższego kodu. Ten kod wywołuje `GetWeather` metodę, która jest zdefiniowana w kodzie udostępnionego. Następnie w Interfejsie użytkownika aplikacji, zawiera dane, które są pobierane z tej metody.  
  
    ```csharp  
    using System;  
    using Android.App;  
    using Android.Widget;  
    using Android.OS;  
  
    namespace WeatherApp.Droid  
    {  
        [Activity(Label = "Sample Weather App", MainLauncher = true, Icon = "@drawable/icon")]  
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
  
### <a name="run-the-app-and-see-how-it-looks"></a>Uruchom aplikację i sprawdzić, jak wygląda  
  
1.  W **Eksploratora rozwiązań**, upewnij się, że **WeatherApp.Droid** projekt został ustawiony jako projekt startowy.  
  
2.  Wybierz odpowiednie urządzenia lub emulatora docelowego, a następnie uruchomić aplikację, naciskając klawisz F5.  
  
3.  Na urządzeniu lub w emulatorze, wpisz prawidłowy kod pocztowy w Stanach Zjednoczonych, w polu edycji (na przykład: 60601) i naciśnij klawisz **uzyskać pogody**. Dane pogody dla regionu pojawia się w formantach.  
  
     ![Pogody aplikacji dla systemów Android i Windows Phone](../cross-platform/media/xamarin_getstarted_results.png "Xamarin_GetStarted_Results")  
  
> [!TIP]
>  Kod źródłowy pełną dla tego projektu jest [mobile przykłady repozytorium w usłudze GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
##  <a name="Windows"></a>Projektowanie interfejsu użytkownika dla Windows Phone  
 Teraz możemy będzie Projektowanie interfejsu użytkownika dla Windows Phone, podłącz go do udostępnionego kodu, a następnie uruchom aplikację.  
  
### <a name="design-the-look-and-feel-of-your-app"></a>Projekt wyglądu i działania aplikacji  
 Proces projektowania natywnego interfejsu użytkownika Windows Phone w aplikacji platformy Xamarin nie różni się od innych natywnych aplikacji Windows Phone. Z tego powodu nie możemy przejść do tutaj używania projektanta. W tym odwoływać się do [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
 Zamiast tego po prostu otwórz MainPage.xaml i Zastąp kod XAML z następujących czynności:  
  
```xaml  
<Page  
    x:Class="WeatherApp.WinPhone.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:WeatherApp.WinPhone"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d"  
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
  
    <Grid>  
        <StackPanel HorizontalAlignment="Left" Height="40" Margin="10,0,0,0" VerticalAlignment="Top" Width="400">  
            <TextBlock x:Name="pageTitle" Text="Weather App" FontSize="30" />  
        </StackPanel>  
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="10,40,0,0" VerticalAlignment="Top" Width="400" Background="#FF545454">  
  
            <TextBlock x:Name="zipCodeSearchLabel" TextWrapping="Wrap" Text="Search by Zip Code" FontSize="18" FontWeight="Bold" HorizontalAlignment="Left" Margin="10,10,0,0"/>  
            <TextBlock x:Name="zipCodeLabel" TextWrapping="Wrap" Text="Zip Code" Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>  
            <StackPanel Orientation="Horizontal">  
                <TextBox x:Name="zipCodeEntry" Margin="10,10,0,0" Text="" VerticalAlignment="Top" InputScope="Number" Width="165" />  
                <Button x:Name="weatherBtn" Content="Get Weather" Width="165" Margin="20,0,0,0" Height="60" Click="GetWeatherButton_Click"/>  
            </StackPanel>  
        </StackPanel>  
        <StackPanel Margin="10,175,0,0">  
            <TextBlock x:Name="locationLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Location" VerticalAlignment="Top"/>  
            <TextBlock x:Name="locationText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="tempLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>  
            <TextBlock x:Name="tempText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="windLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Wind Speed" VerticalAlignment="Top"/>  
            <TextBlock x:Name="windText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="humidityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Humidity" VerticalAlignment="Top"/>  
            <TextBlock x:Name="humidityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="visibilityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>  
            <TextBlock x:Name="visibilityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="sunriseLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunriweatherse" VerticalAlignment="Top"/>  
            <TextBlock x:Name="sunriseText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
            <TextBlock x:Name="sunsetLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunset" VerticalAlignment="Top"/>  
            <TextBlock x:Name="sunsetText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>  
        </StackPanel>  
    </Grid>  
</Page>  
```  
  
 W widoku Projekt interfejsu użytkownika powinien wyglądać następująco:  
  
 ![Interfejs użytkownika aplikacji Windows Phone](../cross-platform/media/xamarin_winphone_finalui.png "Xamarin_WinPhone_FinalUI")  
  
### <a name="consume-your-shared-code"></a>Korzystać z udostępnionego kodu  
  
1.  W projektancie, wybierz **uzyskać pogody** przycisku.  
  
2.  W **właściwości** okna, wybierz przycisk programu obsługi zdarzeń (![ikony procedury obsługi zdarzeń programu Visual Studio](../cross-platform/media/blend_vs_eventhandlers_icon.png "blend_VS_EventHandlers_icon")).  
  
     Ta ikona jest wyświetlana w górnym rogu **właściwości** okna.  
  
3.  Obok pozycji **kliknij** zdarzeń, typ **GetWeatherButton_Click**, a następnie naciśnij klawisz ENTER.  
  
     Spowoduje to wygenerowanie program obsługi zdarzeń o nazwie `GetWeatherButton_Click`. Edytor kodu otwiera i umieszcza kursor wewnątrz bloku kodu programu obsługi zdarzeń.  Uwaga: Jeśli nie można otworzyć edytora po naciśnięciu klawisza ENTER, wystarczy kliknąć dwukrotnie nazwę zdarzenia.  
  
4.  Zastąp następujący kod programu obsługi zdarzeń.  
  
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
  
     Ten kod wywołuje `GetWeather` metodę, która jest zdefiniowana w kodzie udostępnionego. Jest to sama metoda, która wywołuje w aplikacji systemu Android. Ten kod zawiera również dane pobrane z tej metody w formantach interfejsu użytkownika aplikacji.  
  
5.  W pliku MainPage.xaml.cs jest otwarty, Usuń wszystkie kodu wewnątrz **OnNavigatedTo** metody. Ten kod po prostu obsługiwany przycisk domyślny, który został usunięty, gdy firma Microsoft zawartość MainPage.xaml.  
  
### <a name="run-the-app-and-see-how-it-looks"></a>Uruchom aplikację i sprawdzić, jak wygląda  
  
1.  W **Eksploratora rozwiązań**ustaw **WeatherApp.WinPhone** projekt jako projekt startowy.  
  
2.  Uruchom aplikację, naciskając klawisz F5.  
  
3.  W emulator Windows Phone, wpisz prawidłowy kod pocztowy w Stanach Zjednoczonych, w polu edycji (na przykład: 60601) i naciśnij klawisz **uzyskać pogody**. Dane pogody dla regionu pojawia się w formantach.  
  
     ![Wersja systemu Windows uruchomionej aplikacji](../cross-platform/media/xamarin_getstarted_results_windows.png "Xamarin_GetStarted_Results_Windows")  
  
> [!TIP]
>  Kod źródłowy pełną dla tego projektu jest [mobile przykłady repozytorium w usłudze GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather).  
  
##  <a name="next"></a>Następne kroki  
 **Dodawanie interfejsu użytkownika dla systemu iOS do rozwiązania**  
  
 W tym przykładzie należy rozszerzyć przez dodanie natywnego interfejsu użytkownika dla systemu iOS. W tym musisz nawiązać połączenia z komputerów Mac w sieci lokalnej, która ma Xcode i Xamarin zainstalowane. Gdy to zrobisz, może używać Projektanta iOS bezpośrednio w programie Visual Studio. Zobacz [mobile przykłady repozytorium w usłudze GitHub](https://github.com/xamarin/mobile-samples/tree/master/Weather) dla ukończonej aplikacji.  
  
 Należy także zapoznać się [Hello, iOS](http://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/hello,iOS_quickstart/) wskazówki (xamarin.com). Należy pamiętać, że na tej stronie można się, że "Visual Studio" jest zaznaczona w prawym górnym rogu strony na xamarin.com, tak więc poprawny zestaw instrukcji.  
  
 **Dodaj kod specyficzne dla platformy w projekcie udostępnionym**  
  
 Udostępniony kod w PCL jest niezależny od platformy, ponieważ PCL raz kompilacji i zawarte w każdy pakiet aplikacji dla poszczególnych platform. Jeśli chcesz zapisać udostępniony kod, który używa kompilacji warunkowej do izolowania kodu specyficzne dla platformy, możesz użyć *udostępnionego* projektu. Aby uzyskać więcej informacji, zobacz [opcje udostępniania nadawcy](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (xamarin.com).  
  
## <a name="see-also"></a>Zobacz też  
 [Witryny dla deweloperów platformy Xamarin](http://developer.xamarin.com/)   
 [Centrum deweloperów systemu Windows](https://dev.windows.com/en-us)   
 [Plakat krótkimi opisami SWIFT i C#](http://aka.ms/scposter)