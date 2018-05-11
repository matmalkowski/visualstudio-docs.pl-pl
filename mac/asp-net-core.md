---
title: Wprowadzenie do platformy ASP.NET Core
description: W tym artykule opisano, jak rozpocząć pracę z programem ASP.NET w programie Visual Studio for Mac, w tym instalacji i tworzenia nowego projektu.
author: asb3993
ms.author: amburns
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.openlocfilehash: 23a76b4d101acb0c917168515a27f2835c322415
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="getting-started-with-aspnet-core"></a>Wprowadzenie do platformy ASP.NET Core

 Visual Studio for Mac ułatwia tworzenie aplikacji usługi z obsługą jego najnowszej platformy programistycznej sieci Web platformy ASP.NET Core. Platformy ASP.NET Core działa na .NET Core najnowsze zmiany w .NET Framework i środowiska wykonawczego. Ma została dostosowana pod kątem duża wydajność, brana pod uwagę w przypadku instalacji małych rozmiarów i ponownie możliwy do uruchomienia na systemie Linux i macOS oraz systemu Windows.

## <a name="installing-net-core"></a>Instalowanie platformy .NET Core

.NET core 1.1 jest instalowany automatycznie podczas instalowania programu Visual Studio dla komputerów Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Tworzenie aplikacji platformy ASP.NET Core w programie Visual Studio dla komputerów Mac

Otwieranie programu Visual Studio dla komputerów Mac. Na stronie powitalnej zaznacz **nowy projekt...**

![Okno dialogowe nowego projektu](media/asp-net-core-image1.png)

Spowoduje to wyświetlenie okna dialogowego Nowy projekt, umożliwiając wybranie szablonu do utworzenia aplikacji.

Istnieje wiele projektów, które mają dostęp do wbudowanych szablonów, aby rozpocząć tworzenie aplikacji platformy ASP.NET Core. Są to:

- **Oprogramowanie .NET core > aplikacji pusty sieci Web platformy ASP.NET Core**
- **Oprogramowanie .NET core > aplikacji sieci Web platformy ASP.NET Core**
- **Oprogramowanie .NET core > interfejsu API sieci Web platformy ASP.NET Core**
- **Wieloplatformowe > aplikacji > połączenia aplikacji**

![Opcje projektu programu ASP.NET](media/asp-net-core-image11.png)

Wybierz **pustą aplikację sieci Web platformy ASP.NET Core** i naciśnij klawisz **dalej**. Nadaj projektu, nazwę i naciśnij klawisz **Utwórz**. Spowoduje to utworzenie nowej aplikacji platformy ASP.NET Core, który powinien wyglądać podobnie jak na poniższym obrazie:

![Nowy widok platformy ASP.NET Core pustego projektu](media/asp-net-core-image4.png)

Pusta aplikacja sieci Web ASP.NET Core tworzy aplikację sieci web z dwoma plikami domyślne: **Program.cs** i **Startup.cs**, które opisano szczegółowo poniżej. Tworzy folder Dependencies, która zawiera zależności pakietów NuGet projektu, takich jak ASP.NET Core framework .NET Core i celami programu MSBuild, które kompilacji projektu:

![Wyświetlanie zależności konsoli rozwiązania](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Otwórz i sprawdzić **Program.cs** pliku w projekcie. Zwróć uwagę, że dwie czynności są wykonywane w `Main` metodą — wpis w swojej aplikacji:

```csharp
public static void Main(string[] args)
{
    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

    host.Run();
}
```
Aplikacja platformy ASP.NET Core tworzy serwera sieci web metody main, konfigurowanie i uruchamianie hosta za pomocą wystąpienia [ `WebHostBuilder` ](https://docs.microsoft.com/aspnet/core/fundamentals/hosting). Ten konstruktor udostępnia metody umożliwiające hosta do skonfigurowania. W szablonie aplikacji są używane następujące konfiguracje:

 * `UseKestrel`: Określa, że serwer Kestrel będzie używany przez aplikację
 * `UseContentRoot(Directory.GetCurrentDirectory())`: Używa folderu głównego projektu sieci web jako główny zawartości aplikacji podczas uruchamiania aplikacji z tego folderu
 * `.UseIISIntegration()`: Określa, że aplikacja powinien współpracować z usługami IIS. Aby używać usług IIS z platformy ASP.NET Core zarówno `UseKestrel` i `UseIISIntegration` muszą być określone.
 * `.UseStartup<Startup>()`: Określa klasę uruchamiania.

 Kompilowanie i uruchamianie metod kompilacji IWebHost, który będzie hostować aplikację i uruchom ją nasłuchuje przychodzących żądań HTTP.

### <a name="startupcs"></a>Startup.CS

Klasa uruchamiania aplikacji określonego w `UseStartup()` metoda `WebHostBuilder`. Jest w tej klasie określi żądania obsługi potoku, i konfigurować żadnych usług.

Otwórz i sprawdzić **Startup.cs** pliku w projekcie:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddConsole();

        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            await context.Response.WriteAsync("Hello World!");
        });
    }
}
```

Ta klasa uruchamiania zawsze muszą spełniać następujące reguły:

 - Zawsze musi być publiczny
 - Musi zawierać dwóch metod publicznych: `ConfigureServices` i `Configure`

`ConfigureServices` Metoda definiuje usług, które będą używane przez aplikację.

`Configure` Umożliwia utworzenie, używając żądania potoku [oprogramowanie pośredniczące](https://docs.microsoft.com/aspnet/core/fundamentals/middleware). Są to składniki używane w potoku aplikacji ASP.NET do obsługi żądań i odpowiedzi. Potoku HTTP zawiera wiele obiektów delegowanych żądania, o nazwie w sekwencji. Każdy delegata można obsłużyć żądania, sama albo przekaż go do następnego delegata.

Delegaty można skonfigurować za pomocą `Run`,`Map`, i `Use` metod `IApplicationBuilder`, ale `Run` metody nigdy nie wywoła dalej delegata i zawsze powinna być używana na końcu potoku sieci.

`Configure` Metody wcześniej utworzonego szablonu korzysta z wbudowanej wykonać kilka czynności. Po pierwsze umożliwia skonfigurowanie wyjątek strony do użycia podczas tworzenia. Następnie wysyła odpowiedź na żądania strony sieci web z prostego "Hello World".

Ten prosty Hello, World projektu teraz uruchomić bez jakiegokolwiek dodatkowego kodu dodawany. Aby uruchomić aplikację, a następnie go wyświetlić w przeglądarce, naciśnij przycisk Play (triangulacji) na pasku narzędzi:

![Uruchamianie aplikacji](media/asp-net-core-image5.png)

Visual Studio for Mac używa losowego portu można uruchomić projektu sieci web. Aby dowiedzieć się, co ten port jest, otwórz danych wyjściowych aplikacji, która jest wyświetlana w obszarze **Widok > konsole**. Dane wyjściowe powinny znaleźć podobnie jak pokazano poniżej:

![Dane wyjściowe aplikacji wyświetlanie port nasłuchujący](media/asp-net-core-image6.png)

Otwórz wybraną przeglądarkę i wprowadź `http://localhost:5000/`, zastępując `5000` z portem, że w danych wyjściowych aplikacji dane wyjściowe programu Visual Studio. Powinien zostać wyświetlony tekst `Hello World!`:

![tekst przedstawiający przeglądarki](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Dodawanie kontrolera

Aplikacje platformy ASP.NET Core Użyj wzorca projektowego Model-widok-kontroler (MVC), aby podać logicznej rozdzielenie obowiązków dla każdej części aplikacji. MVC zawiera następujące składniki:

- **Model**: Klasa reprezentująca danych aplikacji.
- **Widok**: Wyświetla interfejs użytkownika aplikacji (która jest często dane modelu).
- **Kontroler**: dane wejściowe użytkownika i interakcja odpowiada klasy, która obsługuje żądania przeglądarki.

Aby uzyskać więcej informacji na temat używania MVC dotyczą [Przegląd platformy ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/mvc/overview) przewodnik.

Aby dodać kontroler, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy nazwę projektu i wybierz **Dodaj > nowe pliki**. Wybierz **ogólne > pustą klasę**, a następnie wprowadź nazwę kontrolera:

    ![Okno dialogowe nowego pliku](media/asp-net-core-image8.png)

2. Nowy kontroler, Dodaj następujący kod:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Dodaj `Microsoft.AspNetCore.Mvc` zależności w projekcie, klikając prawym przyciskiem myszy **zależności** folder, a następnie wybierając **Dodawanie pakietu...** .

4. Użyj pola wyszukiwania do przeglądania biblioteki NuGet `Microsoft.AspNetCore.Mvc`i wybierz **Dodaj pakiet**. Może to potrwać kilka minut na zainstalowanie i użytkownik może zostać poproszony o zaakceptowanie różnych licencji dla wymaganych zależności:

    ![Dodaj Nuget](media/asp-net-core-image9.png)

5. W klasie uruchamiania Usuń `app.Run` lambda i logiki routingu adresu URL używany przez MVC w celu określenia, którego kod: należy wywołać do następującego zestawu:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Upewnij się usunąć `app.Run` lambda, jak to spowoduje zastąpienie logiki routingu.

    Aby określić, które kodu do uruchomienia są używane następujący format:

    `/[Controller]/[ActionName]/[Parameters]`

    Po dodaniu powyżej fragmentu kodu sprawi, że aplikacja domyślnie `HelloWorld` kontrolera, a `Index` metody akcji.

6. Dodaj `services.AddMvc();` wywołanie `ConfigureServices` metody, jak przedstawiono poniżej:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Można również przekazać informacje o parametrach z adresu URL do kontrolera.

7. Dodaj do Twojej HelloWorldController innej metody, jak przedstawiono poniżej:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Jeśli uruchomisz aplikację teraz, powinno zostać automatycznie otwarte przeglądarki:

    ![Aplikacja uruchomiona w przeglądarce](media/asp-net-core-image13.png)

9. Spróbuj przejść do `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (zastępowanie `xxxx` z właściwego portu), należy znaleźć w następujących tematach:

    ![Aplikacja uruchomiona w przeglądarce z argumentami](media/asp-net-core-image10.png)


## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli musisz zainstalować oprogramowanie .NET Core ręcznie w Mac OS 10.11 (El Capitan) lub nowszym, wykonaj następujące czynności:

1. Przed rozpoczęciem instalowania platformy .NET Core, upewnij się, że masz zaktualizowane wszystkie aktualizacje systemu operacyjnego do najnowszej wersji stabilnej. Można to sprawdzić, przechodząc do aplikacji Sklep z aplikacjami i wybierając kartę aktualizacje.

2. Wykonaj następujące czynności na [lokacji .NET Core](https://www.microsoft.com/net/core#macos).

Upewnij się wykonać wszystkie cztery kroki pomyślnie, aby upewnić się, że oprogramowanie .NET Core została pomyślnie zainstalowana.

## <a name="summary"></a>Podsumowanie

W tym przewodniku udzielił wprowadzenie do platformy ASP.NET Core. Opisuje, co jest, kiedy należy używać i podano informacje na temat używania go w programie Visual Studio dla komputerów Mac.
Więcej informacji na następnych kroków w tym miejscu można znaleźć w następujących przewodnikach:
- [Platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/?view=aspnetcore-2.1#build-web-ui-and-web-apis-using-aspnet-core-mvc) dokumentów.
- [Tworzenie usługi wewnętrznej bazy danych dla natywnych aplikacji mobilnej](https://docs.microsoft.com/aspnet/core/mobile/native-mobile-backend), który wskazuje sposób tworzenia usługi REST przy użyciu platformy ASP.NET Core dla aplikacji platformy Xamarin.Forms.
- [Laboratorium praktycznego platformy ASP.NET Core](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).
