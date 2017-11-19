---
title: "Witaj świecie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/10/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18a0e18589574c689ebbddbaf28448cf5539ad96
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-your-first-extension-hello-world"></a>Tworzenie pierwszego rozszerzenia: Witaj świecie

W tym przykładzie Hello World przeprowadzi Cię przez proces tworzenia pierwszej rozszerzenia dla programu Visual Studio. Ten samouczek przedstawia sposób dodawania nowego polecenia dla programu Visual Studio.

W procesie, dowiesz się jak:

* **[Utwórz projekt rozszerzalności](#create-an-extensibility-project)**
* **[Dodawanie polecenia niestandardowego](#add-a-custom-command)**
* **[Modyfikowanie kodu źródłowego](#modify-the-source-code)**
* **[Uruchom go](#run-it)**

Na przykład użyjesz Visual C# do dodania przycisku menu niestandardowe o nazwie "Powiedzieć Hello World!" która wygląda następująco:

![Witaj świecie polecenia](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem, upewnij się, że zainstalowana **tworzenia rozszerzenia programu Visual Studio** obciążenia, w tym szablonie VSIX będzie konieczne i przykładowy kod.

Uwaga: Możesz użyć dowolnej wersji programu Visual Studio (Community, Professional lub Enterprise), aby utworzyć projekt Visual Studio Extensibility.

## <a name="create-an-extensibility-project"></a>Utwórz projekt rozszerzalności

Krok 1. Z **pliku** menu, kliknij przycisk **nowy projekt**. W dolnej części ekranu można wprowadzić nazwę projektu.

Krok 2. Z **szablony** menu, kliknij przycisk **Visual C#**, kliknij przycisk **rozszerzalności**, a następnie kliknij przycisk **projektu VSIX**.

![Nowy projekt](media/hello-world-new-project.png)

Powinien zostać wyświetlony na stronie wprowadzenie i kilka przykładowych zasobów.

Jeśli chcesz pozostawić w tym samouczku, a następnie powrót do niego nowego projektu HelloWorld można znaleźć w **— strona początkowa** w **ostatnie** sekcji.

## <a name="add-a-custom-command"></a>Dodawanie polecenia niestandardowego

Krok 1. W przypadku wybrania manifest widać, jakie są opcje modyfikowalne wystąpienia, metadane, opis i wersji.

Krok 2. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie). W menu kontekstowym kliknij **Dodaj**, a następnie kliknij przycisk **kontrolki użytkownika**.

Krok 3. Wróć do **rozszerzalności** sekcji, a następnie kliknij przycisk **polecenia niestandardowych**.

Krok 4. W **nazwa** u dołu ekranu, nadaj mu nazwę, na przykład Command.cs.

![polecenia niestandardowych](media/hello-world-custom-command.png)

Nowe polecenie będzie wyświetlane w **Eksploratora rozwiązań** w obszarze **zasobów** gałęzi. Jest to również, gdzie można znaleźć innych plików związanych z polecenia, takich jak pliki PNG i ICO, jeśli chcesz zmodyfikować obraz.

## <a name="modify-the-source-code"></a>Modyfikowanie kodu źródłowego

W tym momencie przycisk dodawany jest dość ogólny. Musisz zmodyfikować pliku VSCT i CS plik, jeśli chcesz wprowadzić zmiany.

* Plik VSCT jest, gdzie możesz można zmienić nazwy poleceń, a także zdefiniować, gdy przejdą w systemie polecenia programu Visual Studio. Ci poznać platformę pliku VSCT, można zauważyć wiele komentarze kodu, który objaśnia, w jaki każdej sekcji Formanty kodu.

* Plik CS jest, gdzie można definiować akcji, takich jak obsługi kliknięcia.

Krok 1. W **Eksploratora rozwiązań**, znaleźć pliku VSCT nowe polecenie. W takim przypadku zostanie wywołany CommandPackage.vsct.

![polecenie pakietu vsct](media/hello-world-command-package-vsct.png)

Krok 2. Zmień `ButtonText` parametru "Oznacza Hello World!"

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Krok 3. Wróć do **Eksploratora rozwiązań** i Znajdź plik Command.cs. Zmień ciąg `message` polecenia `string.Format(..)` na "Hello World!"

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Upewnij się zapisać zmiany w każdym pliku.

## <a name="run-it"></a>Uruchom go

Teraz możesz uruchomić kod źródłowy w Visual Studio eksperymentalne wystąpienie programu.

Krok 1. Kliknij przycisk **Start** na pasku narzędzi. To spowoduje skompilowanie projektu i uruchomienia debugera, uruchamianie nowego wystąpienia programu Visual Studio o nazwie **eksperymentalne wystąpienie**.

Zobaczysz wyrazy "Eksperymentalne wystąpienie" na pasku tytułu programu Visual Studio.

![pasek tytułu eksperymentalne wystąpienie](media/hello-world-exp-instance.png)

Krok 2. Na **narzędzia** menu **eksperymentalne wystąpienie**, kliknij przycisk **powiedzieć Hello World!**.

![wynik końcowy](media/hello-world-final-result.png)

Powinny pojawić się dane wyjściowe z nowego polecenia niestandardowych, w tym przypadku okna dialogowego w Centrum ekranu, który zapewnia "Witaj świecie!" Komunikat.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy znasz już podstawy pracy z programu Visual Studio Extensibility, Oto, gdzie możesz dowiedzieć się więcej:

* [Rozpoczyna tworzenie rozszerzenia dla programu Visual Studio](starting-to-develop-visual-studio-extensions.md) — przykłady i samouczki. i publikowania rozszerzenia.
* [What's New in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) — nowe funkcje rozszerzalności programu Visual Studio 2017 r
* [W programie Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) — szczegóły dotyczące programu Visual Studio Extensibility