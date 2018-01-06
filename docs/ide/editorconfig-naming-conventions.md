---
title: Konwencje nazewnictwa .NET dla EditorConfig | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/20/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.workload: multiple
ms.openlocfilehash: 5b6d7f0dc43ca11b6fee4b97d5422b863a7b89f4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="naming-conventions-for-editorconfig"></a>Konwencje nazewnictwa dla EditorConfig

Konwencje nazewnictwa dotyczą nazw elementów kodu, takich jak klasy, właściwości i metody. Na przykład można określić, że publiczne elementy członkowskie muszą być kapitalizacji lub że metod asynchronicznych musi kończyć się "Async". Te zasady można wymusić, określając je w [pliku .editorconfig](../ide/create-portable-custom-editor-options.md). Naruszenia reguły nazewnictwa się na liście błędów lub propozycją pod nazwą, w zależności od ważności wybranej reguły. Nie istnieje potrzeba aby skompilować projekt, aby wyświetlić naruszenia.

Konwencje nazewnictwa powinna być wyświetlana z określonych najbardziej do najmniej specyficznych dla w pliku .editorconfig. Pierwsza reguła napotkano, który można zastosować jest tylko regułę, która została zastosowana.

Dla każdego konwencji nazewnictwa należy określić symbole, których on obowiązuje, styl nazewnictwa i ważność wymuszania Konwencji, za pomocą właściwości opisanych poniżej. Kolejność właściwości nie jest ważna.

Aby rozpocząć, wybierz tytuł dla tej reguły nazewnictwa, która będzie używana we wszystkich właściwości, które są niezbędne do pełnego opisano reguły. Na przykład `public_members_must_be_capitalized` jest, właściwą opisową nazwę reguły nazewnictwa. Firma Microsoft będzie odwoływać się do wybrania jako tytuł **< namingRuleTitle\>**  w kolejnych sekcjach.

## <a name="symbols"></a>Symbole

Ustalenie grupy symboli, aby zastosować reguły nazewnictwa. Ta właściwość ma następujący format:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Nadaj nazwę grupie symboli, zastępując **< symbolTitle\>**  wartości z opisowy tytuł, na przykład `public_symbols`. Użyjesz **< symbolTitle\>**  wartości w nazwach trzy właściwości, które opisują symboli reguła jest stosowana do (rodzaje symboli, poziomy ułatwień dostępu i Modyfikatory).

### <a name="kinds-of-symbols"></a>Rodzaje symboli

Do opisania rodzaj symbole, aby zastosować reguły nazewnictwa, określ właściwość w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

Na poniższej liście przedstawiono dopuszczalnych wartości, a następnie można określić wiele wartości, rozdzielając je przecinkami.

- \*(Użyj tej wartości, aby określić wszystkie symbole)
- class
- struktura 
- interface
- enum
- property
- — metoda
- pole
- zdarzenie
- delegate
- parametr

### <a name="accessibility-levels-of-symbols"></a>Poziomy ułatwień dostępu symboli

Do opisania poziomów ułatwień dostępu, który ma być stosowana reguła nazewnictwa symboli, określ nazwę właściwości w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

Na poniższej liście przedstawiono dopuszczalnych wartości, a następnie można określić wiele wartości, rozdzielając je przecinkami.

- \*(Użyj tej wartości, aby określić wszystkie poziomy ułatwień dostępu)
- public
- wewnętrzny lub przyjaciel
- private
- protected
- chronione\_wewnętrzny lub protected_friend

> [!NOTE]
> Musisz określić poziom dostępności jako część Konwencja nazewnictwa, w przeciwnym razie Konwencja nazewnictwa może być ignorowane.

### <a name="symbol-modifiers"></a>Modyfikatory symbol

Do opisania Modyfikatory symboli ma być stosowana reguła nazewnictwa, określ nazwę właściwości w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

Na poniższej liście przedstawiono dopuszczalnych wartości, a następnie można określić wiele wartości, rozdzielając je przecinkami.

- abstrakcyjny lub must_inherit
- async
- const
- readonly
- statyczny lub wspólny

`required_modifiers`jest to opcjonalna właściwość. W przypadku pominięcia tej właściwości, reguły nazewnictwa będą dotyczyć wszystkich modyfikatorów.

## <a name="style"></a>Styl

Teraz, gdy określiliśmy grupy symboli, aby zastosować reguły nazewnictwa musi przedstawione styl nazewnictwa. Czy nazwa ma niektórych prefiksu lub sufiksu niektórych, lub czy poszczególnych wyrazów w nazwie są oddzielone znakiem niektórych, może być styl. Można również określić styl wielkość liter. Właściwości stylu ma następujący format:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Nadaj nazwę stylu zastępując **< styleTitle\>**  wartości z opisowy tytuł, na przykład `first_word_upper_case_style`. Użyjesz **< styleTitle\>**  wartości nazw właściwości, które opisują styl nazewnictwa (prefiks, sufiks znak separatora word i wielkich liter). Do opisania własnego stylu, należy użyć co najmniej jeden z tych właściwości.

### <a name="require-a-prefix"></a>Jest wymagany prefiks

Aby określić, że nazwy symboli musi rozpoczynać się od niektórych znaków, użyj tej właściwości:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Wymagaj sufiks

Aby określić nazwy symbolu musi być zakończona odpowiadającą niektórych znaków, użyj tej właściwości:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Wymaga separatora programu word

Aby określić, że poszczególnych wyrazów w nazwach symbol muszą być oddzielone znakiem niektórych, użyj tej właściwości:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Wymagaj styl wielkość liter

Aby określić styl określonego wielkość liter nazwy symbolu, użyj tej właściwości:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Dopuszczalne wartości dla tej właściwości to:

- pascal_case
- camel_case
- pierwszy\_word_upper
- wszystkie\_górny
- all_lower

> [!NOTE]
> Należy określić styl wielkość liter w ramach swojego nazewnictwa stylu, w przeciwnym razie własnego stylu nazewnictwa może być ignorowane.

## <a name="severity"></a>Ważność

Do opisania ważności naruszenia reguły nazewnictwa, określ właściwość w następującym formacie:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

W poniższej tabeli przedstawiono wartości ważności dopuszczalny i ich znaczenie:

Ważność | Efekt
------------ | -------------
Brak lub dyskretnej | Gdy nie trwa występuje ten styl, nie pokazuj żadnych użytkownikowi; jednak automatycznie wygenerowany kod następuje tym stylem.
Sugestia | Gdy nie trwa występuje ten styl, Pokaż go do użytkownika jako sugestia jako podstawowej kropki na pierwszych dwóch znaków. Go nie ma znaczenia w czasie kompilacji.
ostrzeżenie | Gdy nie trwa występuje ten styl, Pokaż ostrzeżenie kompilatora na liście błędów.
Błąd | Gdy nie trwa występuje ten styl, Pokaż błąd kompilatora na liście błędów.

> [!NOTE]
> Nie masz skompilować projekt, aby zobaczyć naruszenia reguły nazewnictwa. Pojawią się one edycji kodu na liście błędów lub jako sugestię.

## <a name="example"></a>Przykład

Następujący plik .editorconfig zawiera konwencji nazewnictwa, która określa, że właściwości publiczne, metody pól, zdarzeń i delegatów należy wpisać wielkimi literami. Zwróć uwagę, że tę konwencję nazewnictwa określa wiele rodzajów symbolu, aby zastosować regułę, użyj przecinka, aby oddzielić wartości.

```
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

Poniższy zrzut ekranu przedstawia wynik tę konwencję nazewnictwa w edytorze. Dwie zmienne publiczne zostały nazwane bez użycia wielkich liter pierwszej litery. Jedna jest `const`, a drugi `readonly`. Ponieważ reguła nazewnictwa ma zastosowanie tylko do *tylko do odczytu* symbole tylko `readonly` zmienna pokazuje sugestia reguły nazewnictwa.

![Sugestia reguły nazewnictwa](media/editorconfig-naming-rule-suggestion.png)

Teraz Zmieńmy ważności naruszenia można `warning`:

```
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Jeżeli Zamknij i otwórz ponownie pliku kodu zamiast wyświetlanie uwag w obszarze naruszenie Nazwa wyświetlana zielona dowolnym kształcie i ostrzeżenie na liście błędów:

![Ostrzeżenie reguły nazewnictwa](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Zobacz także

[Języka .NET i Konwencji formatowania](../ide/editorconfig-code-style-settings-reference.md)  
[Tworzenie niestandardowego edytora przenośne opcji](../ide/create-portable-custom-editor-options.md)