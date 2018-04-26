---
title: Przy użyciu ustawień EditorConfig w programie Visual Studio
ms.date: 12/13/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.openlocfilehash: ff3391023d9a863bd9f06b4608b327902a17f0ac
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Utwórz Edytor przenośny, niestandardowe ustawienia z EditorConfig

W programie Visual Studio 2017 r, można dodać [EditorConfig](http://editorconfig.org/) plik do projektu lub codebase do wymuszania spójne kodowania style dla wszystkich użytkowników, które działają w bazowej kodu. Ustawienia EditorConfig pierwszeństwo tekstu Visual Studio globalnego ustawienia edytora. Oznacza to, które można dostosować każdy ścieżki bazowej kodu do używania ustawienia edytora tekstu, które są specyficzne dla tego projektu. Nadal można ustawić preferencje osobiste Edytor w programie Visual Studio **opcje** okno dialogowe. Ustawienia te dotyczą pracy codebase bez *.editorconfig* pliku, lub gdy *.editorconfig* pliku nie zastąpi danego ustawienia. Przykładem takich preferencji jest wcięcie styl&mdash;tabulatory lub spacje.

Ustawienia EditorConfig są obsługiwane przez wiele edytorów kodu i IDEs, łącznie z programu Visual Studio. Jest składnikiem przenośne podróżuje swoim własnym kodem, którą można wymusić kodowania style nawet poza Visual Studio.

> [!NOTE]
> Po dodaniu pliku EditorConfig do projektu programu Visual Studio, formatowanie istniejącego kodu nie ulega zmianie, chyba że formatowania dokumentu (**Edytuj** > **zaawansowane**  >  **Format dokumentu** lub **Ctrl**+**K**, **Ctrl**+**D**). Jednak wszystkie nowe wiersze kodu są formatowane zgodnie z ustawieniami EditorConfig.

## <a name="coding-consistency"></a>Kodowanie spójności

Ustawień w plikach EditorConfig umożliwiają Obsługa spójne styl kodowania i ustawienia w codebase, takich jak styl wcięcie, karta szerokości, znaki końca wiersza, kodowanie, a więcej, niezależnie od tego, czy edytor lub IDE używasz. Na przykład podczas kodowania w języku C#, jeśli baza kodu ma Konwencję preferować, że wcięć zawsze składa się z pięciu znaków spacji, dokumentów Użyj kodowania UTF-8, a każdy wiersz zawsze kończy się wyrazem CR/LF, można skonfigurować *.editorconfig* plik w tym celu.

Konwencje używanego w projektach osobiste kodowania mogą się różnić od używanych w przypadku projektów zespołu. Na przykład wybrać, czy żądanie jest pisania kodu, wcięcia dodaje znak tabulacji. Jednakże zespołu łączyli czy wcięcia dodaje czterech znaków spacji zamiast znak tabulacji. Pliki EditorConfig rozwiązać ten problem, umożliwiając ma konfiguracji dla każdego scenariusza.

Ponieważ ustawienia są przechowywane w pliku w bazowej kodu, podróży wraz z tym codebase. Tak długo, jak możesz otworzyć plik kodu w edytorze EditorConfig zgodne, są stosowane ustawienia edytora tekstu. Aby uzyskać więcej informacji na temat plików EditorConfig zobacz [EditorConfig.org](http://editorconfig.org/) witryny sieci Web.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor programu Visual Studio obsługuje podstawowy zestaw [właściwości EditorConfig](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- końcowy\_of_line
- zestaw znaków
- TRIM\_trailing_whitespace
- Wstaw\_final_newline
- root

Ustawienia edytora EditorConfig są obsługiwane we wszystkich językach obsługiwanych przez program Visual Studio z wyjątkiem XML. Ponadto program obsługuje EditorConfig [kodu stylu](../ide/editorconfig-code-style-settings-reference.md) i [nazewnictwa](../ide/editorconfig-naming-conventions.md) konwencje języka C# i Visual Basic.

## <a name="adding-and-removing-editorconfig-files"></a>Dodawanie i usuwanie plików EditorConfig

Dodawanie EditorConfig plików do projektu lub ścieżka bazowa kodu nie konwertuje stylów na nowe pliki. Na przykład jeśli masz wcięcia w pliku sformatowane przy użyciu karty, i Dodaj plik EditorConfig wcięcia spacji, znaków wcięcie nie są automatycznie konwertowane na spacje. Jednak wszystkie nowe wiersze kodu są sformatowane zgodnie z pliku EditorConfig. Ponadto jeśli formatowania dokumentu (**Edytuj** > **zaawansowane** > **dokumentu w formacie** lub **Ctrl** + **K**, **Ctrl**+**D**), ustawienia w pliku EditorConfig są stosowane do istniejących wierszy kodu.

Usunięcie pliku EditorConfig z projektu lub ścieżka bazowa kodu, musisz zamknąć i otwórz ponownie wszystkie pliki otwarte kod, aby powrócić do ustawienia globalnego edytora dla nowych wierszy kodu.

### <a name="to-add-an-editorconfig-file-to-a-project-or-solution"></a>Aby dodać plik EditorConfig do projektu lub rozwiązania

1. Otwórz projekt lub rozwiązanie programu Visual Studio. Wybierz projekt lub rozwiązanie węzła, w zależności od tego, czy Twoje *.editorconfig* ustawienia dotyczą wszystkich projektów w rozwiązaniu lub jeden z nich. Można również wybrać folder w projekcie lub rozwiązaniu, aby dodać *.editorconfig* pliku.

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element...** , lub naciśnij klawisz **Ctrl**+**Shift**+**A**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. W kategorii po lewej stronie, wybierz opcję **ogólne**, a następnie wybierz pozycję **pliku tekstowego** szablonu. W **nazwa** tekst wprowadź `.editorconfig` , a następnie wybierz **Dodaj**.

   *.Editorconfig* plik zostanie wyświetlony w Eksploratorze rozwiązań i zostanie otwarty w edytorze.

   ![plik .editorconfig w Eksploratorze rozwiązań](media/editorconfig-in-solution-explorer.png)

1. Przeprowadź edycję pliku zgodnie z potrzebami, na przykład:

   ```EditorConfig
   root = true

   [*.{cs,vb}]
   indent_size = 4
   trim_trailing_whitespace = true

   [*.cs]
   csharp_new_line_before_open_brace = methods
   ```

Alternatywnie możesz zainstalować [rozszerzenia usługi języka EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig). Po zainstalowaniu tego rozszerzenia, po prostu wybierz **Dodaj** > **.editorconfig pliku** z menu kliknij prawym przyciskiem myszy lub w kontekście węzła rozwiązania, węzeł projektu lub folderu w Eksploratorze rozwiązań.

![Dodaj .editorconfig plik z rozszerzeniem](media/editorconfig-extension-add.png)

## <a name="override-editorconfig-settings"></a>Zastąpienie ustawień EditorConfig

Po dodaniu *.editorconfig* plik do folderu w hierarchii plików, jego ustawienia mają zastosowanie do wszystkich odpowiednich plików na tym poziomie i poniżej. Możesz też przesłonić ustawienia EditorConfig dla konkretnego projektu, codebase lub część codebase, tak, aby były używane konwencje innego niż inne części bazy kodu. Może to być przydatne, gdy dołączyć kod w innym miejscu, a nie chcesz zmienić jego Konwencji.

Aby zastąpić niektórych lub wszystkich ustawień EditorConfig, Dodaj *.editorconfig* pliku na poziomie hierarchii plików tych przesłoniętych ustawienia mają być stosowane. Nowe ustawienia pliku EditorConfig zostaną zastosowane do plików na tym samym poziomie i podkatalogów.

![EditorConfig hierarchii](../ide/media/vside_editorconfig_hierarchy.png)

Jeśli chcesz przesłonić niektórych, ale nie wszystkie ustawienia, określ tylko te ustawienia w *.editorconfig* pliku. Tylko te właściwości, które jawnie listy w pliku niższego poziomu zostaną zastąpione. Inne ustawienia z wyższego poziomu *.editorconfig* pliki w dalszym ciągu zastosowanie. Jeśli chcesz upewnić się, że _nie_ ustawień z _żadnych_ wyższego poziomu *.editorconfig* pliki są stosowane do tej części bazy kodu, Dodaj ```root=true``` właściwości niższego poziomu *.editorconfig* pliku:

```EditorConfig
# top-most EditorConfig file
root = true
```

EditorConfig pliki są odczytywane od góry do dołu, a najbliższego pliki EditorConfig ostatnio. Konwencje z dopasowywania EditorConfig sekcje są stosowane w kolejności ich odczytano tak konwencje w plikach bliżej wyższy priorytet.

## <a name="editing-editorconfig-files"></a>Edytowanie plików EditorConfig

Visual Studio pomaga edytować *.editorconfig* plików, udostępniając liście uzupełniania IntelliSense.

![IntelliSense w pliku .editorconfig](media/editorconfig-intellisense-no-extension.png)

Po zakończeniu edycji pliku EditorConfig, należy ponownie załadować do plików kodu, aby nowe ustawienia zaczęły obowiązywać.

Po zmodyfikowaniu wiele *.editorconfig* plikami, może się okazać [rozszerzenia usługi języka EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) przydatne. Niektóre funkcje tego rozszerzenia obejmują składni wyróżnianie ulepszone IntelliSense, sprawdzanie poprawności i formatowania kodu.

![IntelliSense dla rozszerzenia usługi języka EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Przykład

Poniższy przykład przedstawia stan wcięcie fragment kodu C#, przed i po dodaniu *.editorconfig* plik do projektu. **Karty** w **opcje** okno dialogowe Edytor tekstu Visual Studio ma ustawioną wartość utworzyć znaki spacji, kiedy naciśniesz klawisz **kartę** klucza.

![Ustawienie Karta Edytor tekstu](../ide/media/vside_editorconfig_tabsetting.png)

Zgodnie z oczekiwaniami, naciskając klawisz **kartę** klucza w następnym wierszu wcięcia wiersza przez dodanie czterech dodatkowych białych znaków.

![Kod przed użyciem EditorConfig](../ide/media/vside_editorconfig_before.png)

Dodaj nowy plik o nazwie *.editorconfig* do projektu, z następującą zawartość. `[*.cs]` Ustawienie oznacza, że ta zmiana ma zastosowanie tylko do plików kodu C# w projekcie.

```EditorConfig
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Teraz, gdy ponownie naciśniesz **kartę** klucza, możesz uzyskać znaki tabulacji zamiast spacji.

![Klawisz TAB dodaje znak tabulacji](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Rozwiązywanie problemów z ustawieniami EditorConfig

Jeśli istnieje plik EditorConfig dowolne miejsce w strukturze katalogów równą lub nowszą lokalizacji projektu, Visual Studio stosuje ustawienia edytora w tym pliku do edytora. W takim przypadku może zostać wyświetlony następujący komunikat w pasku stanu:

   **"Preferencje użytkownika dla tego typu pliku są zastępowane przez ten projekt Konwencji kodowania".**

Oznacza to, że jeśli ustawień w edytorze **narzędzia** > **opcje** > **Edytor tekstu** (na przykład wcięcie rozmiaru i stylu, Rozmiar tabulatora lub kodowania konwencje) są określone w pliku EditorConfig równą lub nowszą projektu w strukturze katalogów, w pliku EditorConfig Konwencji Zastąp ustawienia w **opcje**. To zachowanie można kontrolować, przełączając **projektu wykonaj konwencje kodowania** opcji **narzędzia** > **opcje**  >  **Edytor tekstu**. Zaznaczenia opcji wyłącza obsługę EditorConfig dla programu Visual Studio.

![Opcje narzędzia - wykonaj projektu konwencje kodowania](media/coding_conventions_option.png)

Można znaleźć żadnego *.editorconfig* plików w katalogach nadrzędnych, otwierając wiersz polecenia i uruchom następujące polecenie w folderze głównym dysku zawierającego projektu:

```Shell
dir .editorconfig /s
```

Zakres z Konwencji EditorConfig można kontrolować przez ustawienie ```root=true``` właściwości w *.editorconfig* pliku w folderze głównym Twojego repozytorium lub w katalogu, w którym znajduje się projekt. Program Visual Studio jest szuka pliku o nazwie *.editorconfig* w katalogu otwarty plik i w każdym katalogu nadrzędnego. Wyszukiwanie kończy się po osiągnięciu filepath głównego lub jeśli *.editorconfig* pliku z ```root=true``` został znaleziony.

## <a name="see-also"></a>Zobacz także

- [Konwencje styl kodu platformy .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Konwencje nazewnictwa platformy .NET](../ide/editorconfig-naming-conventions.md)
- [Obsługa EditorConfig usługi języka](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](http://editorconfig.org/)
- [Pisanie kodu w edytorze](writing-code-in-the-code-and-text-editor.md)