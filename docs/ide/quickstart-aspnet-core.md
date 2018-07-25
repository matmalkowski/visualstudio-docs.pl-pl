---
title: Tworzenie aplikacji internetowej platformy ASP.NET Core w języku C# przy użyciu programu Visual Studio
description: Dowiedz się, jak utworzyć aplikację internetową platformy ASP.NET Core w programie Visual Studio w języku C#, krok po kroku.
ms.custom: mvc
ms.date: 07/20/2018
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
ms.openlocfilehash: a39c042b4a4badd46f7650fe0f2530527c5d537d
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232197"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Szybki Start: Używanie programu Visual Studio do utworzenia pierwszej aplikacji sieci web platformy ASP.NET Core

W ramach tego wprowadzenia 5 – 10 minut, jak używać programu Visual Studio utworzysz prostą aplikację "Hello World" przy użyciu szablonu projektu programu ASP.NET i języka programowania C#.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci web platformy ASP.NET Core. Typ projektu jest dostarczany z wszystkich plików szablonów do tworzenia aplikacji sieci web, przed nawet dodano niczego!

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **Visual C#**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**. Następnie nadaj plikowi nazwę `HelloWorld` i wybierz polecenie **OK**.

   ![Utwórz nowy projekt aplikacji sieci Web programu ASP.NET Core dla języka C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Jeśli nie widzisz **platformy .NET Core** projektu kategorii szablonu, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie.
   >![Instalator programu Visual Studio Otwórz okno dialogowe Nowy projekt](../ide/media/open-visual-studio-installer.png)
   >
   > Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, a następnie wybierz **Modyfikuj**.
   >
   > ![Obciążenie platformy ASP.NET w Instalatorze programu VS](../ide/media/quickstart-aspnet-workload.png)
   >
   >(Może być ma zamknięcie programu Visual Studio, zanim będzie można kontynuować instalowania nowego obciążenia).

1. W **Nowa aplikacja internetowa ASP.NET Core** okna dialogowego Sprawdź, czy **ASP.NET Core 2.0** pojawia się w menu u góry listy rozwijanej. Następnie wybierz **aplikacji sieci Web** i wybierz polecenie **OK**.

   ![Okno dialogowe nowej aplikacji sieci Web programu ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

Wkrótce potem Visual Studio otwiera plik projektu.

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W **Eksploratora rozwiązań**, rozwiń węzeł **stron** folder, a następnie wybierz **About.cshtml**.

   ![Wybierz plik About.cshtml z poziomu Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ten plik odnosi się do strony, który nosi nazwę **o** w aplikacji sieci web.

   ![Na stronie informacje w aplikacji sieci web](../ide/media/csharp-aspnet-about-page.png)

   W edytorze zostaną wyświetlone HTML kodu dla obszaru "informacje dodatkowe" **o** strony.

   ![Kod HTML dla obszaru dodatkowe informacje w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Zmień tekst "informacje dodatkowe" do odczytu "**Hello World!**".

   ![Zmień domyślny kod HTML dla obszaru dodatkowe informacje w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. W **Eksploratora rozwiązań**, rozwiń węzeł **About.cshtml**, a następnie wybierz **About.cshtml.cs**. (Ten plik, ale także odpowiada **o** strony w aplikacji sieci web.)

   ![Wybierz plik About.cshtml z poziomu Eksploratora rozwiązań](../ide/media/csharp-aspnet-about-page-code-file.png)

   W edytorze zostaną wyświetlone C# kod, który zawiera tekst dla obszaru "application description" **o** strony.

   ![Kod C# obszar opisu aplikacji w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Zmień tekst komunikatu "description aplikacji" do odczytu "**co to jest wiadomość?**".

   ![Zmień domyślny tekst komunikatu dla obszaru Opis aplikacji, w edytorze programu Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** Uruchom aplikację i otworzyć go w przeglądarce sieci web.

   > [!NOTE]
   > Jeśli otrzymasz komunikat o błędzie informujący, że, **nie można połączyć się z serwerem sieci web usług IIS Express**, zamknij program Visual Studio, a następnie otwórz go za pomocą **Uruchom jako administrator** opcję z menu kliknij prawym przyciskiem myszy lub kontekstu. Następnie uruchom ponownie aplikację.

1. W górnej części strony sieci web wybierz **o**.

   ![Wybierz informacje ze strony internetowej](../ide/media/csharp-aspnet-home-page-about.png)

1. Zaktualizowany tekst, który został dodany do wyświetlenia **o** strony.

   ![Wyświetl zaktualizowane informacje o stronie, który zawiera tekst, który został dodany](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zamknij przeglądarkę sieci web.

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco C#, ASP.NET Core i programu Visual Studio IDE (zintegrowanym środowiskiem programistycznym).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej, przejdź z następujących samouczków:

> [!div class="nextstepaction"]
> [Wprowadzenie do języka C# i platformy ASP.NET w programie Visual Studio](tutorial-csharp-aspnet-core.md)
>
> [!div class="nextstepaction"]
> [Wprowadzenie do ASP.NET Core MVC i programu Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)

## <a name="see-also"></a>Zobacz także

[Publikowanie aplikacji sieci web w usłudze Azure App Service przy użyciu programu Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
