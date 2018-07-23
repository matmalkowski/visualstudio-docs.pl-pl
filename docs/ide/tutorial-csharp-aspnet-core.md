---
title: Wprowadzenie do języka C# i ASP.NET Core w programie Visual Studio
ms.custom: ''
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9df1cbae3b0233a8711ab6a287513d89670df4d4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177373"
---
# <a name="get-started-with-c-and-aspnet-in-visual-studio"></a>Wprowadzenie do języka C# i platformy ASP.NET w programie Visual Studio

W tym samouczku dla rozwoju języka C# za pomocą programu ASP.NET Core przy użyciu programu Visual Studio będzie tworzenie aplikacji internetowej w języku C# ASP.NET Core, dodać do niego kod, zapoznaj się z niektórymi funkcjami środowiska IDE i uruchomić aplikację.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Poniżej przedstawiono listę często zadawanych PYTAŃ szybkie wprowadzenie do niektórych kluczowych pojęć.

### <a name="what-is-c"></a>Co to jest C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) jest zorientowany obiektowo i bezpieczny typowo język programowania, który ma możliwość zarówno niezawodne i łatwe do opanowania.

### <a name="what-is-aspnet-core"></a>Co to jest platforma ASP.NET Core?

Platforma ASP.NET Core to platforma typu open source i dla wielu platform, podczas tworzenia aplikacji połączonej z Internetem, takich jak aplikacje sieci web i usług. Aplikacje platformy ASP.NET Core mogą być uruchamiane na platformy .NET Core lub .NET Framework. Można tworzyć i uruchamiać aplikacje dla wielu platform ASP.NET Core na Windows, Mac i Linux. Platforma ASP.NET Core to "open source" na [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Co to jest program Visual Studio?

Program Visual Studio jest zintegrowanego rozwoju pakietu narzędzi zwiększających produktywność dla deweloperów. Go traktować jako program, który służy do tworzenia aplikacji i programów.

## <a name="start-developing"></a>Zacznij programować

Gotowe do rozpoczęcia tworzenia? Chodźmy!

### <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt programu ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic.

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **Visual C#**, rozwiń węzeł **Web**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**, nadaj plikowi nazwę *MyCoreApp*, a następnie wybierz **OK**.

   ![Szablon projektu aplikacji sieci Web platformy ASP.NET Core w oknie dialogowym Nowy projekt w środowisku IDE programu Visual Studio](../ide/media/new-project-csharp-aspnet-mycoreapp.png)

#### <a name="add-a-workload-optional"></a>Dodaj obciążenie (opcjonalnie)

Jeśli nie widzisz **aplikacji sieci Web programu ASP.NET Core** szablon projektu, możesz ją uzyskać, dodając **ASP.NET i tworzenie aplikacji internetowych** obciążenia. Można dodać tego obciążenia w jednej z dwóch sposobów, zależności od tego, które aktualizacje programu Visual Studio 2017 są instalowane na komputerze.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: Użyj okna dialogowego Nowy projekt

1. Wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe.

   ![Wybierz link Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, a następnie wybierz **Modyfikuj**.

   ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../ide/media/asp-dot-net-web-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2: Skorzystaj z paska menu Narzędzia

1. Anuluj poza **nowy projekt** okna dialogowego pole, a następnie na pasku menu u góry wybierz **narzędzia** > **Pobierz narzędzia i funkcje**.

2. Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, a następnie wybierz **Modyfikuj**.

#### <a name="add-a-project-template"></a>Dodaj szablon projektu

1. W **Nowa aplikacja internetowa ASP.NET Core** okna dialogowego wybierz **aplikacji sieci Web (Model-View-Controller)** szablonu projektu.

2. Wybierz **ASP.NET Core 2.0** z górnego menu rozwijanego. (Jeśli nie widzisz **ASP.NET Core 2.0** na liście, zainstaluj ją, wykonując **Pobierz** link, który powinien zostać wyświetlony w żółty pasek w górnej części okna dialogowego.) Wybierz **OK**.

   ![Okno dialogowe nowej aplikacji sieci Web programu ASP.NET Core](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>O rozwiązaniu

To rozwiązanie następuje po wzorcu architektury Model-View-Controller (MVC) dzieli aplikację na trzy główne składniki:

* **Modele** zawierają klasy reprezentujące dane aplikacji. Klasy modeli Użyj logikę weryfikacji, aby wymuszać reguły biznesowe do tych danych. Zazwyczaj obiekty modelu pobierania i przechowywania stanu modelu w bazie danych.
* **Widoki** przedstawiono składniki, które wyświetlają aplikacji interfejsu użytkownika (UI). Ogólnie rzecz biorąc ten interfejs użytkownika Wyświetla określone dane modelu.
* **Kontrolery** zawierają klasy obsługujące żądania przeglądarki. Pobierają dane z modelu i wywołać Przeglądanie szablonów, które zwracają odpowiedzi. W aplikacji MVC widoku są wyświetlane tylko informacje; Kontroler obsługuje i reaguje na dane wejściowe użytkownika i interakcji.

Wzorzec MVC pomaga w tworzeniu aplikacji, które mogą pozwalać na łatwiejsze testowanie i aktualizowanie niż tradycyjne aplikacje monolityczne.

### <a name="tour-your-solution"></a>Poznasz rozwiązania

 1. Szablon projektu tworzy rozwiązanie za pomocą pojedynczego projektu ASP.NET Core, który nosi nazwę **MyCoreApp**. Rozwiń węzeł projektu, aby udostępnić jego zawartość.

    ![Eksplorator rozwiązań ASP.NET w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp.png)

 2. Otwórz *HomeController.cs* plik wchodzącej w skład **kontrolerów** folderu.

     ![Pliku HomeController.cs w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 3. Widok *HomeController.cs*

     ![HomeController.cs w oknie kodu programu Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

 4. Projekt ma również **widoków** folder, który zawiera inne foldery, które mapowania na każdy kontroler (oraz jeden dla **Shared** widoków). Na przykład, Wyświetl plik CSHTML (rozszerzenie HTML) do */Home/About* byłaby to ścieżka w *Views/Home/About.cshtml*. Otwórz ten plik.

     ![About.cshtml pliku w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

 5. Ten plik CSHTML używa składni Razor do renderowania elementów HTML oparte na kombinacji standardowych tagów i wbudowany języka C#.

     ![About.cshtml w oknie kodu programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

   >[!NOTE]
   > Aby dowiedzieć się więcej na ten temat, zobacz [wprowadzenie do języka C# i platformy ASP.NET używająca składni Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c) strony.

 6. Rozwiązanie zawiera także *wwwroot* folderu, który jest głównym witryny sieci Web. Możesz umieścić zawartości statycznej witryny, takiej jak CSS, obrazów i bibliotek JavaScript bezpośrednio w ścieżkach, o których mają one miały po wdrożeniu witryny.

     ![folder Wwwroot w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

 7. Dostępne są także różne pliki konfiguracji, które służą do zarządzania projektu, jego pakietów i aplikacji w czasie wykonywania. Na przykład, domyślna aplikacja [konfiguracji](/aspnet/core/fundamentals/configuration) są przechowywane w *appsettings.json*. Jednak można zastąpić niektórych lub wszystkich tych ustawień na podstawie na środowisku, takie jak, zapewniając *appsettings. Development.JSON* plik **rozwoju** środowiska.

     ![Pliki konfiguracji w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-and-debug-the-application"></a>Uruchamianie i debugowanie aplikacji

1. Wybierz **usług IIS Express** przycisku w środowisku IDE, aby skompilować i uruchomić aplikację w trybie debugowania. (Też nacisnąć klawisz **F5**, lub wybierz **Debuguj > Rozpocznij debugowanie** z paska menu.)

   ![Kliknij przycisk usług IIS Express w programie Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

  > [!NOTE]
  > Jeśli otrzymasz komunikat o błędzie informujący, że **nie można połączyć się z serwerem sieci web usług IIS Express**, zamknij program Visual Studio, a następnie otwórz go za pomocą **Uruchom jako administrator** opcję z menu kliknij prawym przyciskiem myszy lub kontekstu. Następnie uruchom ponownie aplikację.

2. Visual Studio otworzy w przeglądarce. Wybierz **o**.

   ![Wybierz temat w oknie przeglądarki dla aplikacji](../ide/media/csharp-aspnet-browser-page.png)

 Między innymi **o** strony w przeglądarce renderuje tekst, który jest ustawiony w *HomeController.cs* pliku.

   ![Wyświetlanie tekstu na stronie informacje](../ide/media/csharp-aspnet-browser-page-about.png)

3. Zachowaj okna przeglądarki otwartego i z powrotem do programu Visual Studio. Otwórz *Controllers/HomeController.cs* Jeśli nie jest już otwarty.

   ![Otwórz plik HomeController.cs w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

4. Ustaw punkt przerwania w pierwszym wierszu **o** metody. Aby to zrobić, kliknij na marginesie, lub ustaw kursor na wierszu, a następnie naciśnij klawisz **F9**.

  Ten wiersz ustawia dane w **ViewData** kolekcji, który jest renderowany w stronę CSHTML pod *Views/Home/About.cshtml*.

   ![Ustaw punkt przerwania w pierwszym wierszu metody informacje w About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

5. Wróć do przeglądarki i odświeżenia **o** strony. Spowoduje to wyzwolenie punkt przerwania w programie Visual Studio.

6. W programie Visual Studio, wskaźnik myszy nad **ViewData** elementu członkowskiego, aby wyświetlić jego dane.

   ![Wyświetl członka ViewData metody informacje, aby wyświetlić więcej informacji](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

7. Usuń punkt przerwania aplikacji przy użyciu tej samej metody, użytego do ją dodać.

8. Otwórz *Views/Home/About.cshtml*.

   ![W Eksploratorze rozwiązań wybierz About.cshtml](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

9. Zmień tekst **"dodatkowe"** do **"zmienione"** i Zapisz plik.

   ![Zmień tekst, który odczytuje "dodatkowe" na tekst, który odczytuje "zmienione"](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

10. Wróć do okna przeglądarki, aby zobaczyć zaktualizowany tekst. (Odśwież przeglądarkę, jeśli nie widzisz tekst, który został zmodyfikowany.)

    ![Odśwież okno przeglądarki, aby wyświetlić zmieniony tekst](../ide/media/csharp-aspnet-browser-page-about-changed.png)

11. Wybierz **Zatrzymaj debugowanie** przycisk na pasku narzędzi, aby zatrzymać debugowanie. (Też nacisnąć klawisz **Shift**+**F5**, lub wybierz **debugowania** > **Zatrzymaj debugowanie** z paska menu.)

   ![Wybierz przycisk Zatrzymaj debugowanie na pasku narzędzi](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="next-steps"></a>Następne kroki

Gratulujemy wykonanie kroków tego samouczka! Mamy nadzieję, że wiesz już nieco C#, ASP.NET Core i środowisku IDE programu Visual Studio. Aby sprawdzić działanie aplikacji na publiczny serwer, przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](..//deployment/quickstart-deploy-to-azure.md)

Można także zapoznać się przy użyciu framework Model-View-Controller (MVC) w programie ASP.NET Core, postępując zgodnie z samouczkiem, [wprowadzenie do ASP.NET Core MVC i programu Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x).
