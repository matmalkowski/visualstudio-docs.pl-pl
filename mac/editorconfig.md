---
title: EditorConfig
description: Przy użyciu pliku editorconfig umożliwiających zgodne projektu kodowania style w programie Visual Studio dla komputerów Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 553a8ceeae16b660115ea3c8e32e544e903a72af
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Tworzenie i edytowanie niestandardowego pliku EditorConfig

W programie Visual Studio dla komputerów Mac, można dodać [EditorConfig](http://editorconfig.org/) plik do projektu lub codebase do wymuszania spójne kodowania style dla wszystkich użytkowników, które działają w bazowej kodu. Ustawienia zadeklarowany w pliku EditorConfig pierwszeństwo tekstu Visual Studio globalnego ustawienia edytora. Przy użyciu EditorConfig w projekcie lub ścieżka bazowa kodu można ustawić sieci styl kodowania, preferencji i ostrzeżenia dla projektu. Ułatwia wszystkie Visual Studio dla użytkowników komputerów Mac do przestrzegania praktyk kodowania projektu.

[EditorConfig](http://editorconfig.org/) pliki są obsługiwane na wiele edytorów IDEs i kodu, w tym Visual Studio 2017 r. 

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor programu Visual Studio obsługuje podstawowy zestaw [właściwości EditorConfig](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

Obsługuje również EditorConfig [formatowania kodu stylu](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) w języku C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Dodawanie pliku EditorConfig do projektu

### <a name="adding-a-new-editorconfig-file"></a>Dodanie nowego pliku EditorConfig

1. Otwórz projekt w programie Visual Studio dla komputerów Mac. Wybierz węzeł projektu, który chcesz dodać pliki.

2. Z węzła projektu wybrany, przejdź do **Plik > Nowy plik...** na pasku menu, aby otworzyć **nowy plik** okna dialogowego.

3. Wybierz **różne > pusty plik tekstowy** i nadaj mu **nazwa** `.editorconfig`. Naciśnij klawisz **nowy** do tworzenia pliku i otwórz go w edytorze:

    ![Okno dialogowe nowego pliku](media/editorconfig-image1.png)

4. Edytuj plik. Na przykład:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Dodawanie pliku nie jest aktualizowana automatycznie ustawień. Aby uwzględnić ustawienia z `.editorconfig` plików, wybierz węzeł projektu i wybierz **Edytuj > Format > dokumentu w formacie** na pasku menu:

    ![Element menu Format dokumentu](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Dodawanie istniejącego pliku EditorConfig

Jeśli pracujesz z projekt lub rozwiązanie już zawiera `.editorconfig` plików, nie ma nic, które należy wykonać, aby zastosować ustawienia. Zgodnie z ustawieniami EditorConfig sformatowane żadnych nowych wierszy kodu. Należy zauważyć, że podczas programu Visual Studio dla komputerów Mac szanuje `.editorconfig` pliki na poziomie rozwiązania, mogą nie być wyświetlane w konsoli do rozwiązania, ze względu na fakt, do którego pliki, począwszy od `.` są ukryte pliki w macOS.

Może zajść potrzeba ponownego użycia istniejącej `.editorconfig` pliku w projekcie. Aby dodać istniejący plik, najpierw należy wyświetlić ukryte pliki w wyszukiwarce, wprowadzając następujące polecenie w **Terminal**:

```
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

Raz `.editorconfig` plik jest widoczny, przeciągnij go do Twojego węzła projektu. Gdy są dostępne następujące okno dialogowe, wybierz **skopiuj plik do katalogu** opcję i zaznacz **OK**:

![Element menu Format dokumentu](media/editorconfig-image3.png)

Aby uwzględnić ustawienia z `.editorconfig` plików, wybierz węzeł projektu i wybierz **Edytuj > Format > dokumentu w formacie** na pasku menu.

## <a name="editing-an-editorconfig-file"></a>Edytowanie pliku EditorConfig

Pliki EditorConfig używanie układu pliku prostego do określenia ustawień, które jest szczegółowo poniżej w poprzednim przykładzie:


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Ustawienie `root` do `true` będzie Flaga ten plik jako plik najwyższy bazy kodu i wyżej `.editorconfig` pliki w projekcie zostaną zignorowane, zgodnie z objaśnieniem w [Zastąp ustawienia EditorConfig](#override-editorconfig-settings) sekcji.

Każda sekcja jest oznaczona kwadratowe (**[**) nawiasy klamrowe i określa informacje na typy plików powinny dotyczą następujących właściwości.

W powyższym przykładzie niektóre ustawienia są stosowane do wszystkich plików w projekcie, a inne są dodawane tylko do plików języka C#. Poniższe zrzuty ekranu Pokaż przed i po `.editorconfig` ustawienia zostały zastosowane:

**Przed**:

![Przed editorconfig ustawienia zostały zastosowane](media/editorconfig-image4.png)

**Po**:

![Po zastosowaniu ustawień editorconfig](media/editorconfig-image5.png)

Aby uzyskać więcej informacji na temat dostępnych ustawień EditorConfig, zobacz [.NET kodowania Konwencji ustawienia EditorConfig](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) artykułu i [obsługiwane właściwości](http://editorconfig.org/#supported-properties) sekcji w oficjalnej dokumentacji.

## <a name="override-editorconfig-settings"></a>Zastąpienie ustawień EditorConfig

Można mieć więcej niż jeden `.editorconfig` pliku w poszczególnych rozwiązaniach. Programu Visual Studio for Mac odczyty `.editorconfig` plików od góry do dołu w rozwiązaniu, dodawanie i zastępowanie ustawień, ponieważ przechodzi. Oznacza to, że ustawienia w `.editorconfig` _najbliższego_ do edytowania pliku będzie mieć wyższy priorytet. 

Jeśli chcesz upewnić się, że _nie_ ustawień z każdym wyższego poziomu `.editorconfig` pliki są stosowane do tej części bazy kodu, Dodaj `root=true` właściwości na początku niższego poziomu `.editorconfig` pliku:

```EditorConfig
# top-most EditorConfig file
root = true
```