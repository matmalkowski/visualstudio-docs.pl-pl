---
title: Tworzenie aplikacji internetowej platformy ASP.NET Core w języku C# przy użyciu programu Visual Studio
description: Dowiedz się, jak utworzyć aplikację internetową platformy ASP.NET Core w programie Visual Studio w języku C#, krok po kroku.
ms.custom: mvc
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 83811499782fedd5b869ca6587a6d13d60af187d
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176307"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki Start: Używanie programu Visual Studio do utworzenia pierwszej aplikacji sieci web platformy ASP.NET Core

W ramach tego wprowadzenia do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut utworzysz prostą aplikację sieci web w języku C# ASP.NET Core.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci web platformy ASP.NET Core. Typ projektu jest dostarczany z plików szablonów, wchodzących w skład aplikacji sieci web funkcjonalności, zanim jeszcze dodano niczego!

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** rozwiń w lewym okienku w oknie dialogowym **Visual C#**, następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**, następnie wybierz **OK**.

     Jeśli nie widzisz **platformy .NET Core** projektu kategorii szablonu, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie. Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, wybierz **Modyfikuj**.

     ![Obciążenie platformy ASP.NET w Instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)

1. W **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, wybierz opcję **ASP.NET Core 2.0** z górnego menu rozwijanego. (Jeśli nie widzisz **ASP.NET Core 2.0** na liście, zainstaluj ją, wykonując **Pobierz** link, który powinien zostać wyświetlony w żółty pasek w górnej części okna dialogowego.) Wybierz **OK**.

   ![Okno dialogowe nowej aplikacji sieci Web programu ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>Eksploruj IDE

1. W **Eksploratora rozwiązań** narzędzi rozwiń **stron** folderu, wybierz **About.cshtml** aby go otworzyć w edytorze. Ten plik odnosi się do strony o nazwie **o** w aplikacji sieci web.

1. W edytorze wybierz `AboutModel` , a następnie naciśnij klawisz **F12** lub wybierz **przejdź do definicji** z menu kontekstowego (kliknij prawym przyciskiem myszy). To polecenie powoduje przejście do definicji `AboutModel` klasy C#.

   ![Menu kontekstowe przejdź do definicji](../ide/media/quickstart-aspnet-gotodefinition.png)

1. Następnie wyczyść `using` dyrektywę w górnej części pliku, za pomocą prostego skrótu. Wybierz dowolną wyszarzona dyrektywy using a [szybkie akcje](../ide/quick-actions.md) żarówki pojawi się na lewym marginesie lub pod karetką. Wybierz żarówki, a następnie wybierz **Usuń niepotrzebne użycia**.

     Niepotrzebne użycia są usuwane z pliku.

1. W `OnGet()` metody, należy zmienić treść z następującym kodem:

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. Zostaną wyświetlone dwie faliste podkreślenia są wyświetlane w obszarze **środowiska** i **ciąg**, ponieważ te typy nie są w zakresie. Otwórz **lista błędów** narzędzi, aby wyświetlić błędy w tej samej liście. (Jeśli nie widzisz **lista błędów** narzędzi, wybierz **widoku** > **lista błędów** na pasku menu u góry.)

   ![Lista błędów](../ide/media/quickstart-aspnet-errorlist.png)

1. W oknie edytora umieść kursor w dowolnym wierszu, który zawiera błąd, a następnie wybierz żarówki szybkich akcji na lewym marginesie. Z menu rozwijanego wybierz **przy użyciu systemu;** dodanie tej dyrektywy do początku pliku i naprawić błędy.

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** Aby uruchomić aplikację, a następnie otwórz go w przeglądarce sieci web.

1. W górnej części witryny sieci Web wybierz **o** się w katalogu, komunikat zostanie dodany do `OnGet()` metodę **o** strony.

1. Zamknij przeglądarkę sieci web.

> [!NOTE]
> Jeśli otrzymasz komunikat o błędzie informujący, że **nie można połączyć się z serwerem sieci web usług IIS Express**, zamknij program Visual Studio, a następnie otwórz go za pomocą **Uruchom jako administrator** opcję z menu kliknij prawym przyciskiem myszy lub kontekstu. Następnie uruchom ponownie aplikację.

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco środowiska IDE programu Visual Studio. Jeśli chcesz delve głębiej do jego możliwości, kontynuuj samouczek z **samouczki** części spisu treści.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco C#, ASP.NET Core i środowisku IDE programu Visual Studio. Aby sprawdzić działanie aplikacji na publiczny serwer, przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](..//deployment/quickstart-deploy-to-azure.md)

Aby dowiedzieć się więcej, Kontynuuj z kolejnymi samouczkami, [wprowadzenie do języka C# i platformy ASP.NET w programie Visual Studio](tutorial-csharp-aspnet-core.md) i [wprowadzenie do ASP.NET Core MVC i programu Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x).
