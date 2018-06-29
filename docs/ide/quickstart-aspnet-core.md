---
title: Tworzenie aplikacji sieci web platformy ASP.NET Core w języku C# za pomocą programu Visual Studio
description: Informacje o sposobie tworzenia aplikacji sieci web platformy ASP.NET Core w programie Visual Studio w języku C#, krok po kroku.
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
ms.openlocfilehash: 9d8aa6a6147ff57ba72f1cc69240ef5a7137cd73
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089302"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki Start: Program Visual Studio umożliwia tworzenie pierwszej aplikacji sieci web platformy ASP.NET Core

W tej 5 – 10 min wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz prostą aplikację sieci web platformy ASP.NET Core C#.

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci web platformy ASP.NET Core. Typ projektu jest dostarczany z plików szablonów, które stanowią aplikacji sieci web funkcjonalności, zanim nawet dodano niczego!

1. Otwórz program Visual Studio 2017 r.

1. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu**.

1. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **Visual C#**, a następnie wybierz **.NET Core**. W środkowym okienku wybierz **aplikacji sieci Web platformy ASP.NET Core**, a następnie wybierz **OK**.

     Jeśli nie widzisz **.NET Core** projektu szablonu kategorii, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie. Uruchamia Instalator programu Visual Studio. Wybierz **ASP.NET i sieć web development** obciążenia, a następnie wybierz **Modyfikuj**.

     ![Obciążenie platformy ASP.NET w Instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)

1. W **nową aplikację sieci Web Core ASP.NET** okno dialogowe, wybierz opcję **ASP.NET Core 2.0** z górnego menu rozwijanego. (Jeśli nie widzisz **ASP.NET Core 2.0** na liście, zainstaluj go, wykonując **Pobierz** łącza, które powinny być wyświetlane w żółty pasek w górnej części okna dialogowego.) Wybierz **OK**.

   ![Okno dialogowe Nowy aplikacji sieci Web platformy ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>Eksploruj IDE

1. W **Eksploratora rozwiązań** narzędzi, rozwiń węzeł **stron** folder, a następnie wybierz **About.cshtml** aby otworzyć go w edytorze. Ten plik odpowiada stronę o nazwie **o** w aplikacji sieci web.

1. W edytorze, wybierz `AboutModel` , a następnie naciśnij klawisz **F12** lub wybierz **przejdź do definicji** z menu kontekstowego (kliknij prawym przyciskiem myszy). To polecenie powoduje przejście do definicji `AboutModel` klasy C#.

   ![Menu kontekstowe przejdź do definicji](../ide/media/quickstart-aspnet-gotodefinition.png)

1. Następnie wyczyść `using` dyrektywy w górnej części pliku przy użyciu skrótu simple. Wybierz dowolną wyszarzona dyrektyw using a [szybkie akcje](../ide/quick-actions.md) żarówki pojawi się na lewym marginesie lub pod karetką. Wybierz żarówkę, a następnie wybierz **usunąć niepotrzebne deklaracje Using**.

     Niepotrzebne deklaracje Using są usuwane z pliku.

1. W `OnGet()` metody, należy zmienić treść poniższy kod:

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. Zobaczysz dwóch faliste podkreślenie są wyświetlane w obszarze **środowiska** i **ciąg**, ponieważ te typy nie są w zakresie. Otwórz **listy błędów** narzędzi, aby wyświetlić błędy tej samej liście. (Jeśli nie widzisz **listy błędów** narzędzi wybierz **widoku** > **listy błędów** na pasku menu u góry.)

   ![Lista błędów](../ide/media/quickstart-aspnet-errorlist.png)

1. W oknie edytora umieść kursor na jednej osi, który zawiera błąd, a następnie wybierz żarówkę szybkie akcje na lewym marginesie. Z menu rozwijanego wybierz **przy użyciu systemu;** dodawania tej dyrektywy do góry pliku i napraw błędy.

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** do uruchomienia aplikacji, a następnie otwórz go w przeglądarce sieci web.

1. W górnej części witryny sieci web, wybierz **o** wyświetlić komunikatu dodanych w katalogu `OnGet()` metodę **o** strony.

1. Zamknij przeglądarkę sieci web.

> [!NOTE]
> Jeśli zostanie wyświetlony komunikat o błędzie informujący o **nie można nawiązać połączenia z serwerem sieci web usług IIS Express**, zamknij program Visual Studio, a następnie otwórz go przy użyciu **Uruchom jako administrator** opcji z menu kliknij prawym przyciskiem myszy lub kontekstu. Następnie uruchom ponownie aplikację.

Gratulujemy Kończenie pracy tego przewodnika Szybki Start! Mamy nadzieję, że znasz nieco o środowiska IDE programu Visual Studio. Jeśli chcesz delve głębiej do jego możliwości, kontynuuj samouczek w **samouczki** sekcji spisu treści.

## <a name="next-steps"></a>Następne kroki

Gratulujemy Kończenie pracy tego przewodnika Szybki Start! Mamy nadzieję, że znasz nieco o C#, platformy ASP.NET Core i środowiska IDE programu Visual Studio. Aby wyświetlić aplikacji uruchomionych na serwerze publiczne, przycisk.

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](..//deployment/quickstart-deploy-to-azure.md)

Aby dowiedzieć się więcej, kontynuuj samouczki, [wprowadzenie do języka C# i ASP.NET w programie Visual Studio](tutorial-csharp-aspnet-core.md) i [wprowadzenie do platformy ASP.NET Core MVC i Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x).
