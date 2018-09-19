---
title: Tworzenie aplikacji internetowej platformy ASP.NET Core w języku C# przy użyciu programu Visual Studio
description: Dowiedz się, jak utworzyć prostą aplikację sieci web Hello World w programie Visual Studio w języku C# i ASP.NET Core, który krok po kroku.
ms.custom: mvc
ms.date: 07/30/2018
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
ms.openlocfilehash: ae4dc5f14db66bee10c8b2e95ea687f71ced2abb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135616"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki Start: Używanie programu Visual Studio do utworzenia pierwszej aplikacji sieci web platformy ASP.NET Core

W ramach tego wprowadzenia 5 – 10 minut, jak używać programu Visual Studio utworzysz prostą aplikację sieci web "Hello World" przy użyciu szablonu projektu programu ASP.NET i języka programowania C#.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci web platformy ASP.NET Core. Poniżej przedstawiono sposób.

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **Visual C#**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**. Następnie nadaj plikowi nazwę `HelloWorld` i wybierz polecenie **OK**.

1. W **Nowa aplikacja internetowa ASP.NET Core** okna dialogowego Sprawdź, czy **ASP.NET Core 2.0** pojawia się w menu u góry listy rozwijanej. Następnie wybierz **aplikacji sieci Web** i wybierz polecenie **OK**.

  ![Wyświetl plik animowany obraz GIF, który pokazuje, jak utworzyć projekt C# ASP.NET Core w programie Visual Studio](../ide/media/csharp-aspnet-animated-create-project.gif)

  Wkrótce potem Visual Studio otwiera plik projektu.

   > [!NOTE]
   > Jeśli nie widzisz **platformy .NET Core** projektu kategorii szablonu, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie.
   >
   > ![Instalator programu Visual Studio Otwórz okno dialogowe Nowy projekt](../ide/media/open-visual-studio-installer.png)
   >
   > Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, a następnie wybierz **Modyfikuj**.
   >
   > ![Obciążenie platformy ASP.NET w Instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Może być ma zamknięcie programu Visual Studio, zanim będzie można kontynuować instalowania nowego obciążenia).

## <a name="create-and-run-the-app"></a>Tworzenie i uruchamianie aplikacji

Następnie będzie tworzenie i uruchamianie aplikacji sieci web "Hello World". Poniżej przedstawiono sposób.

1. W **Eksploratora rozwiązań**, rozwiń węzeł **stron** folder, a następnie wybierz **About.cshtml**.

   Ten plik odnosi się do strony, który nosi nazwę **o** w aplikacji sieci web.

   ![Na stronie informacje w aplikacji sieci web](../ide/media/csharp-aspnet-about-page.png)

1. Zmień tekst "informacje dodatkowe" do odczytu "**Hello World!**".

1. W **Eksploratora rozwiązań**, rozwiń węzeł **About.cshtml**, a następnie wybierz **About.cshtml.cs**.

1. Zmień tekst komunikatu "description aplikacji" do odczytu "**co to jest wiadomość?**".

1. Wybierz **usług IIS Express** lub naciśnij **Ctrl**+**F5** Uruchom aplikację i otworzyć go w przeglądarce sieci web.

  ![Wyświetl animowany obraz GIF pliku, który pokazuje, jak utworzyć i uruchomić aplikację sieci web platformy ASP.NET Core C# w programie Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Jeśli otrzymasz komunikat o błędzie informujący, że, **nie można połączyć się z serwerem sieci web usług IIS Express**, zamknij program Visual Studio, a następnie otwórz go za pomocą **Uruchom jako administrator** opcję z menu kliknij prawym przyciskiem myszy lub kontekstu. Następnie uruchom ponownie aplikację.

1. Upewnij się, że **o** strona zawiera zaktualizowane tekstu.

1. Zamknij przeglądarkę sieci web.

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco C#, ASP.NET Core i programu Visual Studio IDE (zintegrowanym środowiskiem programistycznym).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź do następującego samouczka:

> [!div class="nextstepaction"]
> [Wprowadzenie do języka C# i platformy ASP.NET w programie Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Zobacz także

[Publikowanie aplikacji sieci web w usłudze Azure App Service przy użyciu programu Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
