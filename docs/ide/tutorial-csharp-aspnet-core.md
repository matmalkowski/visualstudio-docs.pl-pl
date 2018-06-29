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
ms.openlocfilehash: 40aba1d8847b405c3e80f0d6890471f0e2065a86
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089454"
---
# <a name="get-started-with-c-and-aspnet-in-visual-studio"></a>Wprowadzenie do języka C# i ASP.NET w programie Visual Studio

W tym samouczku środowiska deweloperskiego C# przy użyciu platformy ASP.NET Core za pomocą programu Visual Studio będzie utworzenia aplikacji sieci web platformy ASP.NET Core C#, Dodaj do niej kod, Eksploruj niektóre funkcje IDE i uruchom aplikację.

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="before-you-begin"></a>Przed rozpoczęciem

W tym miejscu jest szybkie często zadawane pytania na przedstawiono niektóre podstawowe pojęcia.

### <a name="what-is-c"></a>Co to jest C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) to bezpieczne i zorientowany obiektowo język programowania, zaprojektowany zarówno niezawodne i łatwe dowiedzieć się więcej.

### <a name="what-is-aspnet-core"></a>Co to jest platformy ASP.NET Core?

Platformy ASP.NET Core to struktura open source i wielu platform przy tworzeniu aplikacji podłączonej do Internetu, takich jak aplikacje sieci web i usług. Aplikacje platformy ASP.NET Core można uruchomić na .NET Framework lub .NET Core. Mogą tworzyć i uruchom wieloplatformowych aplikacji programu ASP.NET Core w systemie Windows, Mac i Linux. Platformy ASP.NET Core to typu open source w [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Co to jest program Visual Studio?

Visual Studio to zestaw zintegrowanych programowanie wydajności narzędzi dla deweloperów. Go traktować jako program, który służy do tworzenia programy i aplikacje.

## <a name="start-developing"></a>Rozpocząć tworzenie

Czy chcesz rozpocząć tworzenie? Chodźmy!

### <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt platformy ASP.NET Core. Typ projektu zawiera wszystkie pliki szablonu, które będą potrzebne, zanim nawet dodano niczego.

1. Otwórz program Visual Studio 2017 r.

2. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu**.

3. W **nowy projekt** okno dialogowe w lewym okienku rozwiń **Visual C#**, rozwiń węzeł **sieci Web**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz **aplikacji sieci Web platformy ASP.NET Core**, nadaj nazwę plikowi *MyCoreApp*, a następnie wybierz pozycję **OK**.

   ![Szablon projektu aplikacji sieci Web platformy ASP.NET Core w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-csharp-aspnet-mycoreapp.png)

#### <a name="add-a-workload-optional"></a>Dodaj obciążeń (opcjonalnie)

Jeśli nie widzisz **aplikacji sieci Web platformy ASP.NET Core** szablon projektu, możesz pobrać go przez dodanie **ASP.NET i sieć web development** obciążenia. Możesz dodać to obciążenie w jednym z dwóch sposobów, w zależności od zainstalowanych aktualizacji programu Visual Studio 2017 na tym komputerze.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: Użyj okna dialogowego Nowy projekt

1. Wybierz **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe.

   ![Wybierz łącze Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Uruchamia Instalator programu Visual Studio. Wybierz **ASP.NET i sieć web development** obciążenia, a następnie wybierz pozycję **Modyfikuj**.

   ![Obciążenie wiele platform .NET core w Instalatorze programu Visual Studio](../ide/media/asp-dot-net-web-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2: Użyj paska menu Narzędzia

1. Anuluj poza **nowy projekt** okna dialogowego polu, a następnie na pasku menu u góry wybierz **narzędzia** > **Pobierz narzędzia i funkcje**.

2. Uruchamia Instalator programu Visual Studio. Wybierz **ASP.NET i sieć web development** obciążenia, a następnie wybierz pozycję **Modyfikuj**.

#### <a name="add-a-project-template"></a>Dodaj szablon projektu

1. W **nową aplikację sieci Web Core ASP.NET** oknie dialogowym wybierz **aplikacji sieci Web (Model-View-Controller)** szablonu projektu.

2. Wybierz **ASP.NET Core 2.0** z górnego menu rozwijanego. (Jeśli nie widzisz **ASP.NET Core 2.0** na liście, zainstaluj go, wykonując **Pobierz** łącza, które powinny być wyświetlane w żółty pasek w górnej części okna dialogowego.) Wybierz **OK**.

   ![Okno dialogowe Nowy aplikacji sieci Web platformy ASP.NET Core](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Rozwiązania — informacje

To rozwiązanie jest zgodny ze wzorcem architektury Model-widok-kontroler (MVC), która oddziela aplikację na trzy główne składniki:

* **Modele** zawierają klasy reprezentujące dane aplikacji. Klasy modeli umożliwia logikę weryfikacji wymuszania reguł biznesowych dla tych danych. Zazwyczaj obiekty modelu pobrać i przechowywanie stanu modelu w bazie danych.
* **Widoki** są składnikami wyświetlającymi interfejs użytkownika aplikacji (UI). Ogólnie rzecz biorąc to interfejs użytkownika wyświetla dane modelu.
* **Kontrolery** zawierać klasy, które obsługuje żądania przeglądarki. Pobierają dane z modelu i wywołać szablonów widoków, które zwracają odpowiedź. W aplikacji MVC widok zawiera tylko informacje; Kontroler obsługuje i ma odpowiadać na dane wejściowe użytkownika i interakcja.

Wzorzec MVC pomaga w tworzeniu aplikacji, które są łatwiejsze testowanie i aktualizowanie niż tradycyjne aplikacje wbudowanymi.

### <a name="tour-your-solution"></a>Samouczek rozwiązania

 1. Szablon projektu tworzy rozwiązanie z pojedynczego projektu platformy ASP.NET Core o nazwie **MyCoreApp**. Rozwiń węzeł projektu, aby udostępnić jego zawartość.

    ![Eksplorator rozwiązań ASP.NET w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp.png)

 2. Otwórz *HomeController.cs* plik z **kontrolerów** folderu.

     ![Pliku HomeController.cs w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 3. Widok *HomeController.cs*

     ![HomeController.cs w oknie kodu programu Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

 4. Projekt ma również **widoków** folder zawierający innych folderach, które mapują na każdym kontrolerze (oraz jednego dla **Shared** widoków). Na przykład, Wyświetl plik CSHTML (rozszerzenia HTML) dla *domowej/o* ścieżka byłaby w *Views/Home/About.cshtml*. Otwórz ten plik.

     ![Plik About.cshtml w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

 5. Ten plik CSHTML używa składni Razor do renderowania elementów HTML oparty na kombinacji standardowych znaczników i wbudowane C#.

     ![About.cshtml w oknie kodu programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

   >[!NOTE]
   > Aby dowiedzieć się więcej na ten temat, zobacz [wprowadzenie do języka C# i ASP.NET przy użyciu składni Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c) strony.

 6. Rozwiązanie zawiera także *wwwroot* folder główny witryny sieci web. Możesz umieścić zawartości statycznej witryny, takiej jak CSS, obrazy i biblioteki języka JavaScript bezpośrednio w ścieżkach mają one znajdować się w po wdrożeniu lokacji.

     ![folder Wwwroot w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

 7. Dostępne są także różne pliki konfiguracji, które służą do zarządzania projektu, jego pakietów i aplikacji w czasie wykonywania. Na przykład domyślna aplikacja [konfiguracji](/aspnet/core/fundamentals/configuration) są przechowywane w *appsettings.json*. Jednak można zastąpić niektórych lub wszystkich tych ustawień na podstawie na środowisku, takich jak zapewniając *appsettings. Development.JSON* plik **programowanie** środowiska.

     ![Pliki konfiguracji w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-and-debug-the-application"></a>Uruchom i debugowania aplikacji

1. Wybierz **usług IIS Express** przycisk w IDE, aby skompilować i uruchomić aplikację w trybie debugowania. (Można również nacisnąć klawisz **F5**, lub wybierz **Debuguj > Rozpocznij debugowanie** na pasku menu.)

   ![Wybierz przycisk usług IIS Express programu Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

  > [!NOTE]
  > Jeśli zostanie wyświetlony komunikat o błędzie informujący o **nie można nawiązać połączenia z serwerem sieci web usług IIS Express**, zamknij program Visual Studio, a następnie otwórz go za pomocą **Uruchom jako administrator** opcji z menu kliknij prawym przyciskiem myszy lub kontekstu. Następnie uruchom ponownie aplikację.

2. Visual Studio uruchamia okno przeglądarki. Wybierz **o**.

   ![Wybierz informacje, w oknie przeglądarki dla aplikacji](../ide/media/csharp-aspnet-browser-page.png)

 Między innymi **o** renderowania strony w przeglądarce tekst, który jest ustawiony w *HomeController.cs* pliku.

   ![Wyświetlanie tekstu na stronie informacje](../ide/media/csharp-aspnet-browser-page-about.png)

3. Zachowaj okna przeglądarki Otwórz i z powrotem do programu Visual Studio. Otwórz *Controllers/HomeController.cs* , jeśli nie jest jeszcze otwarty.

   ![Otwórz plik HomeController.cs w Eksploratorze rozwiązań w programie Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

4. Ustaw punkt przerwania w pierwszym wierszu **o** metody. Aby to zrobić, kliknij na marginesie lub ustaw kursor na wiersza i naciśnij klawisz **F9**.

  Ten wiersz ustawia niektóre dane w **ViewData** kolekcji, który jest renderowany na stronie CSHTML w *Views/Home/About.cshtml*.

   ![Ustaw punkt przerwania w pierwszym wierszu metody informacje w About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

5. Wróć do przeglądarki i Odśwież **o** strony. Spowoduje to wyzwolenie punktu przerwania w programie Visual Studio.

6. W programie Visual Studio myszą **ViewData** element członkowski, aby wyświetlić jego dane.

   ![Widok Członkowskie ViewData metody informacje, aby zobaczyć więcej informacji](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

7. Usuń punkt przerwania aplikacji przy użyciu tej samej metody używane ją dodać.

8. Otwórz *Views/Home/About.cshtml*.

   ![Wybierz About.cshtml w Eksploratorze rozwiązań](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

9. Zmiana tekstu **"dodatkowe"** do **"zmienione"** i Zapisz plik.

   ![Zmień tekst o treści "dodatkowe" na tekst, który odczytuje "zmienione"](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

10. Wróć do okna przeglądarki, aby wyświetlić zaktualizowany tekst. (Odśwież przeglądarkę, jeśli nie widzisz tekst, który został zmodyfikowany.)

    ![Odśwież okno przeglądarki, aby wyświetlić zmieniony tekst](../ide/media/csharp-aspnet-browser-page-about-changed.png)

11. Wybierz **Zatrzymaj debugowanie** przycisku paska narzędzi, aby zatrzymać debugowanie. (Można również nacisnąć klawisz **Shift**+**F5**, lub wybierz **debugowania** > **Zatrzymaj debugowanie** na pasku menu.)

   ![Kliknij przycisk Zatrzymaj debugowanie na pasku narzędzi](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="next-steps"></a>Następne kroki

Gratulujemy wykonanie kroków tego samouczka! Mamy nadzieję, że znasz nieco o C#, platformy ASP.NET Core i środowiska IDE programu Visual Studio. Aby wyświetlić aplikacji uruchomionych na serwerze publiczne, przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](..//deployment/quickstart-deploy-to-azure.md)

Można także zapoznać się używając framework Model-widok-kontroler (MVC) w ASP.NET Core samouczka, [wprowadzenie do platformy ASP.NET Core MVC i Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x).
