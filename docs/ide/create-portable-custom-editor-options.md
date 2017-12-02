---
title: "Przy użyciu ustawień EditorConfig w Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 39b3228e64257552c8b629e421c9b5aa4f0e0931
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Utwórz Edytor przenośny, niestandardowe ustawienia z EditorConfig

Ustawienia edytora tekstu w programie Visual Studio mają zastosowanie do wszystkich projektów danego typu. Tak, na przykład, jeśli zmienisz Edytor tekstu C# ustawienie to ustawienie dotyczy *wszystkie* projektów C# w programie Visual Studio. Jednak w niektórych przypadkach może być konieczne używać konwencji, które różnią się od preferencje osobiste edytora. [EditorConfig](http://editorconfig.org/) pliki umożliwiają w tym celu opisujące typowe opcje edytora tekstu, na przykład rozmiar wcięcie na podstawie na projekt. EditorConfig ustawienia, które znajdują się w pliku .editorconfig znajdujący się obok kodu i pliki projektu, pierwszeństwo tekstu Visual Studio globalnego ustawienia edytora. Oznacza to, które można dostosować każdy ścieżki bazowej kodu do używania ustawienia edytora tekstu, które są specyficzne dla tego projektu. Wtyczka nie jest wymagana do tej funkcji można używać w programie Visual Studio.

## <a name="coding-consistency"></a>Kodowanie spójności

Ustawień w plikach EditorConfig umożliwiają Obsługa spójne styl kodowania i ustawienia w codebase, takich jak styl wcięcie, karta szerokości, znaki końca wiersza, kodowanie, a więcej, niezależnie od tego, czy edytor lub IDE używasz. Na przykład podczas kodowania w języku C#, jeśli baza kodu ma Konwencję preferować wcięć zawsze składają się z pięciu znaków spacji, dokumentów Użyj kodowania UTF-8 i każdym wierszu zawsze kończy się wyrazem CR/LF, można skonfigurować plik .editorconfig w tym celu.

Konwencje używanego w projektach osobiste kodowania mogą się różnić od używanych w przypadku projektów zespołu. Na przykład wybrać, czy żądanie jest pisania kodu, wcięcia dodaje znak tabulacji. Jednakże zespołu łączyli czy wcięcia dodaje czterech znaków spacji zamiast znak tabulacji. Pliki EditorConfig rozwiązać ten problem, umożliwiając ma konfiguracji dla każdego scenariusza.

Ponieważ ustawienia są przechowywane w pliku w bazowej kodu, podróży wraz z tym codebase. Tak długo, jak możesz otworzyć plik kodu w edytorze EditorConfig zgodne, są stosowane ustawienia edytora tekstu. Aby uzyskać więcej informacji na temat plików EditorConfig zobacz [EditorConfig.org](http://editorconfig.org/) witryny sieci Web.

## <a name="override-editorconfig-settings"></a>Zastąpienie ustawień EditorConfig

Po dodaniu pliku .editorconfig do folderu w hierarchii plików jego ustawienia mają zastosowanie do wszystkich odpowiednich plików na tym poziomie i poniżej. Aby przesłonić ustawienia EditorConfig dla określonego projektu lub ścieżki bazowej kodu w taki sposób, że używa konwencji innego niż plik EditorConfig najwyższego poziomu, Dodaj plik .editorconfig do głównego katalogu z codebase repozytorium lub projektu. Upewnij się umieścić ```root=true``` właściwość w pliku tak wygląda żadnych dalszych zapasowej struktury katalogów, plików .editorconfig programu Visual Studio. Nowe ustawienia EditorConfig w pliku zostaną zastosowane do plików w tym samym poziomie i podkatalogów.

```
# top-most EditorConfig file
root = true
```

![EditorConfig hierarchii](../ide/media/vside_editorconfig_hierarchy.png)

EditorConfig pliki są odczytywane od góry do dołu, a najbliższego pliki EditorConfig ostatnio. Konwencje z dopasowywania EditorConfig sekcje są stosowane w kolejności ich odczytano tak konwencje w plikach bliżej wyższy priorytet.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor w programie Visual Studio obsługuje następujące z podstawowy zestaw [właściwości EditorConfig](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- końcowy\_of_line
- zestaw znaków
- root

Ustawienia edytora EditorConfig są obsługiwane we wszystkich językach obsługiwanych przez program Visual Studio z wyjątkiem XML. Ponadto program obsługuje EditorConfig [kodu stylu](../ide/editorconfig-code-style-settings-reference.md) i [nazewnictwa](../ide/editorconfig-naming-conventions.md) konwencje języka C# i Visual Basic.

## <a name="editing-editorconfig-files"></a>Edytowanie plików EditorConfig

Program Visual Studio udostępnia pewne IntelliSense do edycji plików .editorconfig. Po zmodyfikowaniu wiele plików .editorconfig może się okazać [usługi języka EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) przydatne rozszerzenia.

Po zakończeniu edycji pliku EditorConfig, należy ponownie załadować do plików kodu, aby nowe ustawienia zaczęły obowiązywać.

## <a name="adding-and-removing-editorconfig-files"></a>Dodawanie i usuwanie plików EditorConfig

Dodawanie EditorConfig plików do projektu lub ścieżka bazowa kodu zostanie nie przekonwertować istniejące style na nowe pliki. Na przykład jeśli masz wcięcia w pliku sformatowane przy użyciu karty, i Dodaj plik EditorConfig wcięcia spacji, znaków wcięcie zostanie nie konwertowane na spacje. Jednak wszystkie nowe wiersze kodu zostanie sformatowany zgodnie z pliku EditorConfig.

Usunięcie pliku EditorConfig z projektu lub ścieżka bazowa kodu, musisz zamknąć i otwórz ponownie wszystkie pliki otwarte kod, aby powrócić do ustawienia globalnego edytora dla nowych wierszy kodu.

## <a name="example"></a>Przykład

Poniżej przedstawiono przykład zawierający stan wcięcie wstawki kodu C#, przed i po dodaniu pliku .editorconfig do projektu. **Karty** w **opcje** okno dialogowe Edytor tekstu Visual Studio ma ustawioną wartość utworzyć znaki spacji, kiedy naciśniesz klawisz **kartę** klucza.

![Ustawienie Karta Edytor tekstu](../ide/media/vside_editorconfig_tabsetting.png)

Zgodnie z oczekiwaniami, naciskając klawisz **kartę** klucza w następnym wierszu wcięcia wiersza przez dodanie czterech dodatkowych białych znaków.

![Kod przed użyciem EditorConfig](../ide/media/vside_editorconfig_before.png)

Zostanie dodany nowy plik o nazwie .editorconfig do projektu, z następującą zawartość. `[*.cs]` Ustawienie oznacza, że zmiana zostanie zastosowana tylko do plików kodu C# w tym projekcie.

```
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Teraz, gdy ponownie naciśniesz **kartę** klucza, możesz uzyskać znaki tabulacji zamiast spacji.

![Klawisz TAB dodaje znak tabulacji](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Rozwiązywanie problemów z ustawieniami EditorConfig

Jeśli istnieje plik EditorConfig dowolne miejsce w strukturze katalogów równą lub nowszą lokalizacji projektu, Visual Studio będzie dotyczyć edytora ustawienia edytora w tym pliku. W takim przypadku może zostać wyświetlony następujący komunikat w pasku stanu:

   **"Preferencje użytkownika dla tego typu pliku są zastępowane przez ten projekt Konwencji kodowania".**

Oznacza to, że jeśli ustawień w edytorze **narzędzia**, **opcje**, **Edytor tekstu** (na przykład wcięcie rozmiaru i stylu, Rozmiar tabulatora lub konwencje kodowania) są określone w Plik EditorConfig równą lub nowszą projektu w strukturze katalogów, w pliku EditorConfig Konwencji zastąpią ustawienia w opcjach. To zachowanie można kontrolować, przełączając **projektu wykonaj konwencje kodowania** opcji **narzędzia**, **opcje**, **Edytor tekstu**. Zaznaczenia opcji spowoduje wyłączenie obsługi EditorConfig dla programu Visual Studio.

![Opcje narzędzia - wykonaj projektu konwencje kodowania](media/coding_conventions_option.png)

Można znaleźć żadnych plików .editorconfig w obiekcie nadrzędnym katalogów otwierając wiersz polecenia i uruchom następujące polecenie w folderze głównym dysku zawierającego projektu:

```
dir .editorconfig /s
```

Zakres z Konwencji EditorConfig można kontrolować przez ustawienie ```root=true``` właściwość w pliku .editorconfig w katalogu głównym Twojego repozytorium lub w katalogu, w którym znajduje się projekt. Program Visual Studio jest szuka pliku o nazwie .editorconfig w katalogu otwarty plik i w każdym katalogu nadrzędnego. Zatrzymuje program Visual Studio po osiągnięciu filepath głównego lub jeśli plik .editorconfig z ```root=true``` został znaleziony.

## <a name="see-also"></a>Zobacz także

[Konwencje styl kodu platformy .NET](../ide/editorconfig-code-style-settings-reference.md)  
[Obsługa EditorConfig usługi języka](../extensibility/supporting-editorconfig.md)  
[EditorConfig.org](http://editorconfig.org/)  
[Pisanie kodu w edytorze](writing-code-in-the-code-and-text-editor.md)