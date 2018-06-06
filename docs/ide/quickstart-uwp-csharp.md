---
title: 'Szybki Start: Tworzenie pierwszej aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio XAML i C# | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology:
- vs-acquisition
ms.topic: quickstart
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 6d8585d2f8ec34371226c2211e318b71e356a331
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765872"
---
# <a name="quickstart-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Szybki Start: Tworzenie pierwszej aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio z XAML i C&#35;

W tym wprowadzeniu do programu Visual Studio zintegrowane środowisko programistyczne (IDE) 5 – 10 minut utworzysz aplikację "Hello World", która działa na dowolnym urządzeniu z systemem Windows 10. Aby to zrobić, użyjesz szablon projektu uniwersalnej platformy systemu Windows (UWP), Extensible Application Markup Language (XAML) i język programowania C#.

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt platformy uniwersalnej systemu Windows. Typ projektu zawiera wszystkie pliki szablonów potrzebne przed nawet dodano niczego!

1. Otwórz program Visual Studio 2017 r.

2. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu**.

3. W lewym okienku **nowy projekt** okna dialogowego rozwiń **Visual C#**, a następnie wybierz pozycję **uniwersalnych systemu Windows**. W środkowym okienku wybierz **pusta aplikacja (uniwersalna systemu Windows)**. Następnie, nazwij projekt *HelloWorld* i wybierz polecenie **OK**.

   ![Windows Universal szablonu projektu w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Jeśli nie widzisz **pusta aplikacja (uniwersalna systemu Windows)** projektu szablonu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe.<br><br>![Kliknij łącze Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Uruchamia Instalator programu Visual Studio. Wybierz **rozwoju platformy uniwersalnej systemu Windows** obciążenia, a następnie wybierz pozycję **Modyfikuj**.<br><br>![Uniwersalny obciążenia rozwoju platformy systemu Windows w Instalatorze programu Visual Studio](../ide/media/uwp-dev-workload.png)

4. Gdy **nowego projektu platformy uniwersalnej systemu Windows** zostanie wyświetlone okno dialogowe, wybierz **OK**.

   ![Zaakceptuj domyślne docelową wersję i minimalna wersja ustawień w oknie dialogowym Nowy projekt platformy uniwersalnej systemu Windows](../ide/media/new-uwp-project-target-minver-dialog.png)

  > [!NOTE]
  > Jeśli po raz pierwszy używasz programu Visual Studio umożliwiające utworzenie aplikacji platformy uniwersalnej systemu Windows, **ustawienia** pojawi się okno dialogowe. Wybierz **tryb dewelopera**, a następnie wybierz pozycję **tak**.<br><br>
 ![Włącz tryb dewelopera, w oknie dialogowym Ustawienia platformy uniwersalnej systemu Windows](../ide/media/enable-developer-mode.png)<br><br>Visual Studio instaluje dodatkowe pakietu tryb dewelopera. Po zakończeniu instalacji pakietu Zamknij **ustawienia** okno dialogowe.

## <a name="create-the-application"></a>Tworzenie aplikacji

Nadszedł czas, aby rozpocząć tworzenie. Będzie dodać kontrolkę przycisku, Dodaj akcję na przycisk, a następnie uruchom aplikację "Hello World", aby wyświetlić, wygląda następująco.

### <a name="add-a-button-to-the-design-canvas"></a>Dodawanie przycisku do obszaru projektowania

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie *MainPage.xaml* otwarcie widoku podziału.

  ![Otwórz MainPage.xaml z Eksploratora rozwiązań ](../ide/media/uwp-solution-explorer-MainPage-xaml.png)

  Istnieją dwa okienka: **projektanta XAML**, która obejmuje obszaru roboczego projektowanie i **edytora XAML**, którym można dodać lub zmienić kod.

  ![W okienku projektanta XAML w edytorze XAML](../ide/media/uwp-xaml-editor.png)

2. Wybierz **przybornika** można otworzyć okna wysuwanego przybornika.

  ![Kliknij przycisk przybornika, aby otworzyć okno wysuwanego przybornika](../ide/media/uwp-toolbox.png)

  (Jeśli nie widzisz **przybornika** opcji, możesz otworzyć go na pasku menu. Aby to zrobić, wybierz **widoku** > **narzędzi**. Możesz również nacisnąć klawisz **Ctrl**+**Alt**+**X**.)

3. Kliknij przycisk **numeru Pin** ikonę, aby dock okno przybornika.

  ![Kliknij ikonę pinezki do dock okno przybornika](../ide/media/uwp-toolbox-autohide.png)

4. Kliknij przycisk **przycisk** kontroli, a następnie przeciągnij go do obszaru projektowania.

   ![Formantu przycisku kliknij i przeciągnij go do obszaru projektowania](../ide/media/uwp-toolbox-add-button-control.png)

  Jeśli przyjrzymy się kod w **edytora XAML**, zobaczysz, że przycisk został dodany, za:

  ![Formantu przycisku kliknij i przeciągnij go do obszaru projektowania](../ide/media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Dodaj etykietę do przycisku

1. W **edytora XAML**, zmień wartość przycisk zawartości z "Button" na "Hello World!"

   ![Zmień wartość zawartości przycisku na Hello World](../ide/media/uwp-change-button-text-in-xaml-code-window.png)

2. Należy zauważyć, że przycisk w **projektanta XAML** zmiany zbyt.

   ![Przycisk zmiany Hello World w obszarze roboczym projekt](../ide/media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Dodaj program obsługi zdarzeń

Dźwięki "obsługi zdarzeń" skomplikowane, ale jest po prostu inną nazwę dla kodu, który jest wywoływany, gdy zdarzenie. W takim przypadku dodaje akcję "Witaj świecie!" przycisk.

1. Kliknij dwukrotnie ikonę w obszarze roboczym projektowania formantu przycisku.

2. Edytuj kod obsługi zdarzeń w *MainPage.xaml.cs*, strony związane z kodem.

 Jest to, gdzie interesujący rzeczy. Domyślny program obsługi zdarzeń wygląda następująco:

   ![Domyślny program obsługi zdarzeń Button_Click ](../ide/media/uwp-button-click-code.png)

 Zmieńmy, więc wygląda następująco:

    ![Nowy program obsługi zdarzeń Button_Click async ](../ide/media/uwp-add-hello-world-async-code.png)

  Oto kod, aby skopiować i wkleić:

  ```C#
  private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
  ```

#### <a name="what-did-we-just-do"></a>Co tak jak?

Kod używa niektórych interfejsów API systemu Windows w celu utworzenia obiektu syntezy mowy i nadaje mu po część tekstu, aby podać. (Aby uzyskać więcej informacji na temat używania `SpeechSynthesis`, zobacz <xref:System.Speech.Synthesis>.)

## <a name="run-the-application"></a>Uruchamianie aplikacji

Nadszedł czas na tworzenie, wdrażanie i uruchamianie aplikacji platformy uniwersalnej systemu Windows "Hello World" Aby zobaczyć, co sprawdza i brzmi jak. Poniżej przedstawiono sposób.

1. Wybierz **komputera lokalnego** do uruchomienia aplikacji.

   ![Kliknij komputer lokalny, aby uruchomić i debugowanie aplikacji platformy uniwersalnej systemu Windows](../ide/media/uwp-start-or-debug.png)

   (Można też wybrać **debugowania** > **Rozpocznij debugowanie** z paska menu lub naciśnij klawisz **F5** można uruchomić aplikacji.)

2. Wyświetlanie aplikacji, który jest wyświetlany zaraz po zniknie ekranu powitalnego. Aplikacja powinna wyglądać podobnie do poniższego:

   ![Platformy uniwersalnej systemu Windows aplikacja "Hello World"](../ide/media/uwp-hello-world-app.png)

3. Kliknij przycisk **Hello World** przycisku.

 Z systemu Windows 10 dosłownie dowiesz się urządzenie, "Hello, World!"

4. Aby zamknąć aplikację, kliknij przycisk **Zatrzymaj debugowanie** przycisku w pasku narzędzi. (Można również wybrać **debugowania** > **Zatrzymaj debugowanie** z paska menu, lub naciśnij klawisz **Shift**+**F5**.)

## <a name="next-steps"></a>Następne kroki

Gratulujemy Kończenie pracy tego przewodnika Szybki Start! Mamy nadzieję, że znasz już podstawowe zasady dotyczące platformy uniwersalnej systemu Windows i programu Visual Studio IDE. Aby dowiedzieć się więcej, kontynuuj samouczek następujące:

> [!div class="nextstepaction"]
> [Tworzenie interfejsu użytkownika](/windows/uwp/design/basics/xaml-basics-ui)
