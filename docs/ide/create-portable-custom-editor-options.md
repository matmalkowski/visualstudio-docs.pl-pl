---
title: "Utwórz Edytor przenośny, niestandardowe ustawienia z EditorConfig | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 2c1df6f8e34d2b8e72486dd804ba57f0dcf2406b
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Utwórz Edytor przenośny, niestandardowe ustawienia z EditorConfig
Ustawienia edytora tekstu w programie Visual Studio mają zastosowanie do wszystkich projektów danego typu. Tak, na przykład, jeśli zmienisz Edytor tekstu C# ustawienie to ustawienie dotyczy *wszystkie* projektów C# w programie Visual Studio. Jednak w niektórych przypadkach może być konieczne używać konwencji, które różnią się od preferencje osobiste edytora. [EditorConfig](http://editorconfig.org/) pliki umożliwiają to zrobić przez podanie tekstu typowe opcje edytora dla projektu. EditorConfig ustawienia, które znajdują się w pliku .editorconfig dodane do baza kodu, zastępują globalne ustawienia Edytor tekstu Visual Studio. Oznacza to, które można dostosować każdy ścieżki bazowej kodu do używania ustawienia edytora tekstu, preferowany. Wtyczka nie jest wymagana do tej funkcji można używać w programie Visual Studio.

## <a name="coding-consistency"></a>Kodowanie spójności
Ustawień w plikach EditorConfig umożliwiają Obsługa spójne style kodowania i ustawienia języka, takich jak styl wcięcie, karta szerokości, znaki końca wiersza, kodowanie, a więcej, w codebase niezależnie od tego, czy edytor lub IDE jest używany. Na przykład podczas kodowania w języku C#, jeśli baza kodu ma Konwencję preferować wcięć zawsze składają się z pięciu znaków spacji, dokumentów Użyj kodowania UTF-8 i każdym wierszu zawsze kończy się wyrazem CR/LF, można skonfigurować plik .editorconfig w tym celu.

Konwencje używanego w projektach osobiste kodowania mogą się różnić od używanych w przypadku projektów zespołu. Na przykład wybrać, czy żądanie jest pisania kodu, naciskając klawisz Tab dodaje znak TABULACJI. Jednakże zespołu łączyli czy wcięcia dodaje czterech znaków spacji zamiast znak TABULACJI. Pliki EditorConfig rozwiązać ten problem, umożliwiając ma konfiguracji dla każdego scenariusza.

Ponieważ ustawienia są przechowywane w pliku w bazowej kodu, podróży wraz z tym codebase. Tak długo, jak możesz otworzyć plik kodu w edytorze EditorConfig zgodne, są stosowane ustawienia edytora tekstu. Aby uzyskać więcej informacji na temat plików EditorConfig zobacz [EditorConfig.org](http://editorconfig.org/) witryny sieci Web.

## <a name="override-editorconfig-settings"></a>Zastąpienie ustawień EditorConfig
Po dodaniu pliku .editorconfig do folderu w hierarchii plików jego ustawienia mają zastosowanie do wszystkich odpowiednich plików na tym poziomie i poniżej. Aby przesłonić ustawienia EditorConfig dla określonego projektu lub ścieżki bazowej kodu w taki sposób, że używa konwencji innego niż plik .editorconfig najwyższego poziomu, Dodaj plik .editorconfig do głównego katalogu z codebase repozytorium lub projektu. Upewnij się umieścić ```root=true``` właściwość w pliku tak wygląda Visual Studio dla dowolnego .editorconfig pliki dalsze zapasowej struktury katalogów. Nowe ustawienia .editorconfig w pliku zostaną zastosowane do poziomu, w którym znajduje się i plików w podkatalogów.

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
- end_of_line
- zestaw znaków
- root

Ponadto program obsługuje [konwencje styl kodu .NET](../ide/editorconfig-code-style-settings-reference.md).  

Ustawienia EditorConfig są obsługiwane we wszystkich językach obsługiwanych przez program Visual Studio z wyjątkiem XML.

## <a name="intellisense"></a>IntelliSense
Program Visual Studio oferuje ograniczone IntelliSense do edycji plików .editorconfig. Po zmodyfikowaniu wiele plików .editorconfig może się okazać [usługi języka EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) przydatne rozszerzenia.

## <a name="example"></a>Przykład
Oto przykład pokazujący stan wcięcie fragment kodu C#, przed i po dodaniu pliku .editorconfig do projektu. **Karty** w **opcje** okno dialogowe Edytor tekstu Visual Studio ma ustawioną wartość utworzyć znaki spacji, kiedy naciśniesz klawisz **kartę** klucza w kodzie.

![Ustawienie Karta Edytor tekstu](../ide/media/vside_editorconfig_tabsetting.png)

Zgodnie z oczekiwaniami, naciskając klawisz **kartę** klucza w następnym wierszu wcięcia wiersza przez dodanie czterech dodatkowych białych znaków.

![Kod przed użyciem EditorConfig](../ide/media/vside_editorconfig_before.png)

Zostanie dodany nowy plik o nazwie .editorconfig do projektu, z następującą zawartość. `[*.cs]` Ustawienie oznacza, że zmiana zostanie zastosowana tylko do plików .cs w tym projekcie.  

![Plik .editorconfig dodany do projektu](../ide/media/vside_editorconfig_addconfig.png)

Teraz, gdy ponownie naciśniesz **kartę** klucza, możesz uzyskać znaki tabulacji zamiast spacji.

![Karta dodaje znak tabulacji](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  Dodawanie .editorconfig plików do projektu lub ścieżka bazowa kodu zostanie Konwertuj istniejącą style do nowych, ma zastosowanie tylko do nowo dodanych wierszy. Jeśli z projektu usunięto plik .editorconfig lub ścieżka bazowa kodu, należy ponownie załadować plików kodu dla ustawienia edytora powrócić do ustawienia globalnego. W oknie Lista błędów w programie Visual studio zostały zgłoszone żadne błędy w plikach .editorconfig.

## <a name="troubleshooting-editorconfig-settings"></a>Rozwiązywanie problemów z ustawieniami EditorConfig
Jeśli istnieje plik EditorConfig dowolne miejsce w strukturze katalogów równą lub nowszą lokalizacji projektu, Visual Studio będzie dotyczyć edytora ustawienia edytora w tym pliku. W takim przypadku może zostać wyświetlony następujący komunikat w pasku stanu:

**"Preferencje użytkownika dla tego typu pliku są zastępowane przez ten projekt Konwencji kodowania".**

Oznacza to, że jeśli ustawień w edytorze **narzędzia**, **opcje**, **Edytor tekstu** (na przykład wcięcie rozmiar, Rozmiar tabulatora wcięcie styl &mdash; karty lub spacji ani kodowania konwencje, takie jak użycie `var`) w pliku są określone EditorConfig równą lub nowszą projektu w strukturze katalogów w pliku EditorConfig Konwencji zastąpią ustawienia w opcjach. To zachowanie można kontrolować, przełączając **projektu wykonaj konwencje kodowania** opcji **narzędzia**, **opcje**, **Edytor tekstu**. Zaznaczenia opcji spowoduje wyłączenie obsługi EditorConfig dla programu Visual Studio.

![Opcje narzędzia - wykonaj projektu konwencje kodowania](media/coding_conventions_option.png)

.Editorconfig plików można znaleźć w katalogach nadrzędnych, otwierając wiersz polecenia i uruchom następujące polecenie z katalogu głównego dysku, który zawiera projektu:

```
dir .editorconfig /s
```

Zakres z Konwencji EditorConfig można kontrolować przez ustawienie ```root=true``` właściwość w pliku .editorconfig w katalogu głównym Twojego repozytorium lub w katalogu, w którym znajduje się projekt. Program Visual Studio jest szuka pliku o nazwie .editorconfig w katalogu otwarty plik i w każdym katalogu nadrzędnego. Zatrzymuje programu Visual Studio po osiągnięciu filepath głównego lub jeśli plik .editorconfig o ```root=true``` został znaleziony.

## <a name="support-editorconfig-for-your-language-service"></a>Obsługuje EditorConfig usługi języka
W większości przypadków podczas implementowania usługi języka Visual Studio, żadne dodatkowe czynności jest wymagane do obsługi EditorConfig uniwersalnych właściwości. Edytor core automatycznie wykrywa i odczytuje plik .editorconfig po otwarciu plików i ustawia opcje buforu i widoku odpowiedni tekst. Jednak niektóre usługi języka zdecydować się na użycie odpowiedni tekst kontekstowe opcji widoku, a nie za pomocą ustawienia globalne dla elementów, takich jak karty i spacje, gdy użytkownik edytuje lub formatowania tekstu. W takich przypadkach usługi języka muszą zostać zaktualizowane do obsługi plików EditorConfig.

Poniżej przedstawiono zmiany konieczne do aktualizowania usługi języka do obsługi plików EditorConfig, zastępując globalnym _specyficzny dla języka_ opcję z _kontekstowe_ opcji:  

### <a name="indent-style"></a>Styl wcięcie
Zastąp:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs  
_lub_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs  

Z:  

! textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  
_lub_  
! textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  

### <a name="indent-size"></a>Wcięcie
Zastąp:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize  
_lub_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize  

Z:  

textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)  
_lub_  
textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)  

### <a name="tab-size"></a>Rozmiar tabulatora
Zastąp:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize  
_lub_  
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize  

Z:  

textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)  
_lub_  
textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)  

## <a name="see-also"></a>Zobacz także
[Konwencje styl kodu platformy .NET](../ide/editorconfig-code-style-settings-reference.md)  
[EditorConfig.org](http://editorconfig.org/)  
[Pisanie kodu w edytorze](writing-code-in-the-code-and-text-editor.md)