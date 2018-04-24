---
title: Rozszerzanie programu Visual Studio for Mac wskazówki
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: fdfbc5c10c3b49165960938f7f8832f61a37a805
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Rozszerzanie programu Visual Studio for Mac wskazówki

Ten temat przeprowadzi Cię przez tworzenie [pakietu rozszerzenia proste](https://github.com/mjh4/AddIns/tree/master/DateInserter). Pakiet rozszerzenia utworzy nowe polecenie w programie Visual Studio dla menu Edycja Mac firmy przez użytkownika wstawić bieżącą datę i godzinę do dokumentu tekstowego otwarte.

W tym przykładzie użyto Maker dodatku. Maker dodatku tworzy nowy szablon projektu i wypełnia wymaganych plików dla naszych pakietu rozszerzenia niestandardowego.

1.   Rozpocznij poprzez uruchomienie programu Visual Studio dla komputerów Mac, jeśli nie jest jeszcze otwarty:

  ![Visual Studio for Mac zrzut ekranu](media/extending-visual-studio-mac-addin3.png)

2.   Zainstaluj _pakiet rozszerzenia dodatku Maker_ za pomocą Menedżera rozszerzenia. Z menu programu Visual Studio wybierz **rozszerzeń...** :

  ![Karta Menedżer dodatków](media/extending-visual-studio-mac-addin4.png)

3.   Przejdź na kartę Galeria i wpisz `Addin Maker` na pasku wyszukiwania w prawym górnym rogu. Wybierz dodatek Maker z kategorii dodatku programowanie i kliknij przycisk <kbd>zainstalować</kbd>. Jeśli nic nie zostaną wyświetlone, kliknij przycisk Odśwież i ponowić wyszukiwanie:

  ![Menedżer dodatków](media/extending-visual-studio-mac-addin5.png)

4.   Teraz, gdy jest zainstalowany dodatek Maker, można rozpocząć tworzenie pakietu rozszerzenia. Rozpocznij od utworzenia nowego rozwiązania.

5.  Z **okno dialogowe nowego rozwiązania**, wybierz **innych > Różne > Ogólne > Xamarin Studio Addin > C#** szablonu i na poniższym ekranie Nazwa nowego rozwiązania `DateInserter`:

  ![Tworzenie nowego rozwiązania](media/extending-visual-studio-mac-addin7New.png)

6.   Visual Studio for Mac zostaną wyświetlone nowe rozwiązanie:

  ![Wypełnione rozwiązania](media/extending-visual-studio-mac-addin8.png)

7.   Usuń kod szablonu w `Manifest.addin.xml` i zastąp go następującym kodem:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
        <ExtensionModel>
            <Extension path = "/MonoDevelop/Ide/Commands/Edit">
                <Command id = "DateInserter.DateInserterCommands.InsertDate"
                    _label = "Insert Date"
                    defaultHandler = "DateInserter.InsertDateHandler" />
            </Extension>

            <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
                <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
            </Extension>
        </ExtensionModel>
    ```

8.   Teraz należy skonfigurować pliki, które po pewnym czasie będzie obsługiwać Wstawianie daty i godziny do edytora tekstu. Kliknij prawym przyciskiem myszy węzeł projektu i dodać nowy plik. Wybierz **ogólne > pustą klasę** i nazwę nowego pliku *InsertDateHandler*:

  ![Wstaw Data obsługi](media/extending-visual-studio-mac-addin9.png)

9.   Umożliwia usunięcie kod szablonu z `InsertDateHandler.cs` i zastąp go następującym kodem:

    ```cs
    using MonoDevelop.Components.Commands;
    using MonoDevelop.Ide;
    using MonoDevelop.Ide.Gui;
    using System;

    namespace DateInserter
    {
        class InsertDateHandler : CommandHandler
        {
            protected override void Run()
            {

            }

            protected override void Update(CommandInfo info)
            {

            }
        }
    }
    ```

  Firma Microsoft będzie później rozszerzyć tych dwóch metod symbol zastępczy.

10.   Kliknij prawym przyciskiem myszy **DateInserter** projekt i wybierz **Dodaj > Nowy plik**. Wybierz **ogólne > puste wyliczenie**, a następnie podaj nazwę nowego pliku *DateInserterCommands*:

  ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11.   Dodaj `InsertDate` polecenie jako nowego wyliczenia w `DateInserterCommands.cs` pliku:

    ``` cs
    using System;

    namespace DateInserter
    {
        public enum DateInserterCommands
        {
            InsertDate,
        }
    }
    ```

12.   W tym momencie powinna mieć pakiet rozszerzenia pracy. Można przetestować go przez zapisanie pracy i działania aplikacji. IDE zostanie uruchomione nowe wystąpienie programu Visual Studio dla komputerów Mac przy użyciu nowego pakietu rozszerzenia zainstalowane. Jeśli przejdziesz do **menu Edycja**, zobaczysz, że program Visual Studio for Mac ma nową opcję o nazwie **Wstaw datę**, jak pokazano na poniższym zrzucie ekranu:

  ![Wstaw Data — polecenie](media/extending-visual-studio-mac-addin11.png)

  Należy pamiętać, że wybierając z menu Wstaw datę nie ma znaczenia, ponieważ bieżąca implementacja tylko metod symbol zastępczy.

13.   Platformę znajduje się w miejscu pakietu rozszerzenia, a następnie należy napisać kod, który obsługuje Wstawianie daty. Najpierw upewnij się, że **polecenia Wstaw data** jest włączona tylko, gdy użytkownik ma plik otwarty, zastępując tekst `Update` metoda `InsertDateHandler.cs` następującym kodem:

    ```cs
    protected override void Update(CommandInfo info)
    {
        info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14.   Polecenie Uaktualnij `Run` metodę, aby wstawić datę i godzinę z następującym kodem:

    ``` cs
    protected override void Run () {
        var editor = IdeApp.Workbench.ActiveDocument.Editor;
        var date = DateTime.Now.ToString ();
        editor.InsertAtCaret (date);

    }
    ```

15.   Na koniec uruchom umożliwia naszych pakiet rozszerzenia testowania go. W nowym wystąpieniu programu Visual Studio for Mac, wybierz **Edytuj > Wstaw datę**. Bieżąca data i godzina jest wstawione w naszym karetki, jak pokazano na poniższym zrzucie ekranu:

  ![Wstaw Data zrzut ekranu](media/extending-visual-studio-mac-addin12.png)
