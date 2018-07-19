---
title: Rozszerzenie IntelliCode pytań i odpowiedzi
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: 79e18778eae231d16cf32c0fa68bcb6f5564b09d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079314"
---
# Program Visual Studio IntelliCode — często zadawane pytania

Dziękujemy za zainteresowanie usługą Visual Studio IntelliCode. Ten krótki — często zadawane pytania będzie miejmy nadzieję uzyskania odpowiedzi na niektóre pytania, które mogą wiązać Ciebie.

## PYTANIA I ODPOWIEDZI. Co to jest Visual Studio IntelliCode?

W kompilacji 2018 r. Firma Microsoft ogłosiła Visual Studio IntelliCode, nowe możliwości, które usprawnia tworzenie oprogramowania za pomocą sztucznej Inteligencji. Rozszerzenie IntelliCode ułatwia deweloperom i zespołom kod bez obaw, znaleźć problemy i skupić się przeglądów kodu.

Wczesne widok jak IntelliCode pokazano, jak zwiększa procesu tworzenia oprogramowania w następujący sposób:

- Zapewnia uzupełnianie kodu oparte na kontekście
- Zawiera informacje na temat deweloperzy mogą stosować się do wzorców i style ich zespołu
- Umożliwia znalezienie problemów z kodem trudne catch
- Koncentruje się przeglądów kodu za pomocą rysowania uwagę na obszary, które naprawdę mają znaczenie

Deweloperzy mogą znaleźć więcej informacji i zaloguj się do grup dyskusyjnych i przyszłych prywatnych wersji zapoznawczych w [ https://aka.ms/intellicode ](https://aka.ms/intellicode).

## PYTANIA I ODPOWIEDZI. Co program Visual Studio IntelliCode umożliwia klientom wykonywanie?

Visual Studio IntelliCode to szeroką gamę możliwości oferuje nowych udoskonaleń dotyczących produktywności za pomocą sztucznej inteligencji (AI).

Deweloperzy mogą [Pobierz eksperymentalne rozszerzenie](https://go.microsoft.com/fwlink/?linkid=872707) programu Visual Studio 2017 wersji 15.7 lub nowszej. Rozszerzenie udostępnia obecnie:

- Ulepszone sztucznej Inteligencji funkcji IntelliSense, które przewiduje najprawdopodobniej poprawne interfejsu API dla deweloperów do użycia zamiast po prostu prezentowanie alfabetyczną listę elementów członkowskich. Aby udostępnić tę listę dynamiczne używa bieżący kontekst kodu i wzorców dla deweloperów.

- Wnioskowanie styl kodu i formatowania Konwencji, które ułatwiają Zapewnij spójność kodu przez dynamiczne tworzenie [pliku .editorconfig](../create-portable-custom-editor-options.md) z Twojej bazy kodu w celu zdefiniowania kodowania stylów i formatów. Tych konwencji programowi Visual Studio do zaoferowania styl automatycznych i format poprawek wyczyścić dokumentu.

Zaktualizujemy rozszerzenie więcej możliwości w nadchodzących miesiącach.

## PYTANIA I ODPOWIEDZI. Dlaczego wnioskowania EditorConfig dołączana 1 do nazwy pliku?

1 spowoduje, że to znany problem w możliwościach rozszerzania programu Visual Studio. ma zostać dołączony do nazwy pliku .editorconfig podczas jego tworzenia, kliknij prawym przyciskiem myszy i wybierając pozycję **Dodaj > Nowy element**. Pliki o nazwie w ten sposób nie są rozpoznawane przez procesor polecenia editorconfig w programie Visual Studio. Problem ten został rozwiązany w Visual Studio 2017 w wersji Preview należy zachować 15,8 4, ale w międzyczasie można obejść, usuwając 1 w **Dodaj nowy element** okna dialogowego.

## PYTANIA I ODPOWIEDZI. Nie widzę mojego konwencje EditorConfig działają — Dlaczego
Istnieje kilka typowych przyczyn, że ten problem może wystąpić:

- W wersjach programu Visual Studio 2017 przed należy zachować 15,8 w wersji zapoznawczej 3, musisz zamknąć i otworzyć ponownie wszystkie otwarte dokumenty, aby zobaczyć konwencje w pliku EditorConfig, możesz utworzyć zaczęły obowiązywać. Ten problem jest rozwiązany w wersji zapoznawczej należy zachować 15,8 wersji 3.
- Konwencje formatowania nigdy nie pojawiają się w **lista błędów** lub jako "zygzaki" w kodzie. Jednak mogą być rozwiązane za pomocą nowego rozszerzenia Formatuj dokument (Ctrl + K, Ctrl + D) w programie Visual Studio 2017 wersja 15.8 3 lub nowszym w wersji zapoznawczej

## PYTANIA I ODPOWIEDZI. Format dokumentu nie naprawianie Dlaczego mój Konwencji stylistycznych?
Istnieje kilka typowych przyczyn, że ten problem może wystąpić:

- Nie używasz programu Visual Studio 2017 w wersji 15.8 (wersja zapoznawcza), 3 lub nowszej. Należy tej wersji, aby można było użyć rozszerzonego poleceń "Formatuj dokument" do wykonywania oczyszczania dodatkowy kod dla bieżącego dokumentu.
- Może nie być wybrana została opcja w stylu poprawki. Rozszerzone możliwości ustalenia możliwości oparty na Konwencji problemów w dokumencie Format tylko obejmuje ustalony zestaw elementów problemów. Możesz zmienić rozwiązane problemy w **opcje narzędzi** w obszarze **Edytor tekstu > C# > Styl kodu > Formatowanie > Ogólne > ustawień dokumentów w formacie (eksperyment)**. Zwróć uwagę, ustawienia domyślne nie rozwiązują niektóre konwencje stylu. Można włączyć do tych za pośrednictwem **Narzędzia > Opcje**. Na przykład "Zastosuj niejawnej/jawnej preferencjach" uruchomi reguły stylów dotyczących używania `var`.

## PYTANIA I ODPOWIEDZI. Konwencje EditorConfig, które może wywnioskować w Visual Studio IntelliCode

Obecnie ta funkcja jest eksperymentalny, więc firma Microsoft nie obsługuje pełny zestaw konwencje udokumentowane w artykule [odwołanie do ustawienia stylu kodu](../editorconfig-code-style-settings-reference.md) jeszcze.

Rozszerzenie IntelliCode aktualnie może wywnioskować następujących konwencji:

Konwencje formatowania:

-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_method_declaration_empty_parameter_list_parentheses
-   csharp_space_between_method_call_name_and_opening_parenthesis
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_call_empty_parameter_list_parentheses
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_parentheses
-   csharp_space_after_cast
-   csharp_space_after_colon_in_inheritance_clause
-   csharp_space_before_colon_in_inheritance_clause
-   csharp_space_around_binary_operators
-   csharp_indent_switch_labels
-   csharp_indent_case_contents
-   csharp_indent_case_contents_when_block
-   csharp_indent_labels
-   csharp_preserve_single_line_blocks
-   csharp_preserve_single_line_statements
-   csharp_new_line_before_open_brace
-   csharp_new_line_before_else
-   csharp_new_line_before_catch
-   csharp_new_line_before_finally
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_between_query_expression_clauses

Konwencje stylu
-   csharp__new_line_before_catch
-   csharp_new_line_before_else
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_finally_style
-   csharp_new_line_between_query_expression_clauses
-   csharp_prefer_braces_style
-   csharp_preferred_modifier_order_style
-   csharp_prefer_simple_default_expression
-   csharp_preserve_single_line_blocks
-   csharp_space_after_cast
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_parentheses
-   csharp_style_expression_bodied_accessors
-   csharp_style_expression_bodied_constructors
-   csharp_style_expression_bodied_indexers
-   csharp_style_expression_bodied_methods
-   csharp_style_expression_bodied_operators
-   csharp_style_expression_bodied_properties
-   csharp_style_inlined_variable_declaration
-   csharp_style_pattern_local_over_anonymous_function
-   csharp_style_pattern_matching_over_as_with_null_check
-   csharp_style_var_for_built_in_types
-   csharp_style_var_when_type_is_apparent
-   dotnet_sort_system_directives_first
-   dotnet_style_explicit_tuple_names
-   dotnet_style_object_initializer
-   dotnet_style_predefined_type_for_locals_parameters_members
-   dotnet_style_predefined_type_for_member_access
-   dotnet_style_prefer_inferred_anonymous_type_member_names
-   dotnet_style_qualification_for_event
-   dotnet_style_qualification_for_field
-   dotnet_style_qualification_for_method
-   dotnet_style_qualification_for_property
-   dotnet_style_require_accessibility_modifiers

## PYTANIA I ODPOWIEDZI. Czy istnieją inne funkcje dostępne do rozszerzenia programu Visual Studio IntelliCode?

Aktywnie pracujemy nad pewną liczbę funkcji, które Cieszymy się do publicznego udostępniania w miarę ich udostępniania. Możesz zalogować się do wiadomości i aktualizacje w [ https://aka.ms/intellicode ](https://aka.ms/intellicode) jako pierwszy, aby dowiedzieć się, gdy mamy nowych funkcji dostępnych.

## P: co sprawia, że "wspierane przez Sztuczną inteligencję IntelliSense" obsługiwane przez IntelliCode lepsze niż regularne IntelliSense?

Za pomocą IntelliCode na liście uzupełniania sugeruje, że najbardziej prawdopodobne Popraw interfejsu API dla deweloperów, można użyć zamiast prezentacji prostego Alfabetyczna lista elementów członkowskich. Używa bieżący kontekst kodu dla deweloperów i wzorce oparte na 2000 wysokiej jakości, typu open-source projektów, w witrynie GitHub każdego z ponad 100 gwiazdek, aby udostępnić tę listę dynamicznych. Wyniki tworzą modelu, który najprawdopodobniej i najbardziej efektywnym wywołań interfejsu API.

## P: jak dobre są sugestie uzupełniania IntelliCode?

Firma Microsoft wcześniej użyto zalecenia rozszerzenia IntelliCode wewnętrznie w firmie Microsoft przez pewien czas i uważają, że przydają się sugestie. Ostatecznie jednak będzie dowód w jak użyteczne te zalecenia są dla Ciebie jako kodowania. Chcielibyśmy Cię jednak do wypróbowania programu Visual Studio [rozszerzenia IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) try. Daj nam znać, jak działa dla Ciebie i wyślij nam swoją opinię. Również nauczymy nasz model, w oparciu o wybór w Nasze zalecenia, a dodamy rozszerzenia, ponieważ zwiększa modelu.

> [!NOTE]
> Brak kodu użytkownika nie są zbierane. Zobacz pytanie na [zachowania](#privacy).

## PYTANIA I ODPOWIEDZI. Jaka jest przyszłość IntelliCode?

Firma Microsoft Eksplorowanie szereg sposobów na zwiększenie produktywności deweloperów za pomocą sztucznej Inteligencji i inne zaawansowane techniki. W programie Microsoft Build 2018 pokazaliśmy wczesne widok Niektóre scenariusze, w którym uważamy, że AI może pomóc deweloperom, ale istnieje wiele więcej! Jesteśmy zainteresowani learning od deweloperów, które eksperymentować, co firma Microsoft już widoczny, tak logowania przez wiadomości i aktualizacje, [ https://aka.ms/intellicode ](https://aka.ms/intellicode).

## PYTANIA I ODPOWIEDZI. Ile kosztuje?

Nie mamy żadnych ogłoszenia dotyczące cen w chwili obecnej.

## PYTANIA I ODPOWIEDZI. Kiedy zostanie wydana IntelliCode?

IntelliCode wspierane przez Sztuczną inteligencję w technologii IntelliSense jest obecnie w wersji zapoznawczej swoje pierwsze eksperymentalne. Będziemy można zaktualizować rozszerzenia eksperymentalne i dodamy więcej możliwości w przyszłości. Mamy bez harmonogramu ostatecznego wydania, ale zachęcamy opinii od deweloperów, dzięki czemu firma Microsoft mogą dostarczać najlepsze możliwe środowisko. Możesz zalogować się do wiadomości i aktualizacje w [ https://aka.ms/intellicode ](https://aka.ms/intellicode).

## PYTANIA I ODPOWIEDZI. Jest to środowisko dostępne tylko w programie Visual Studio i języka C#?

Środowisko wyświetleniem konferencji Build 2018 w programie Visual Studio 2017 kodu C#. Jednakże chętnie rozszerzanie IntelliCode do większej liczby języków i narzędzi z rodziny Visual Studio w przyszłości.

## PYTANIA I ODPOWIEDZI. <a name="whynointellisense"/> Nie widzę sugestie IntelliCode w mojej C# edytowanie - co się dzieje?

Sugestie IntelliCode są wyświetlane w standardowych technologii IntelliSense interfejsie użytkownika Visual Studio dla języka C#. Rozszerzenia, które zastępują ten interfejs użytkownika uniemożliwia sugestie "oznaczone" IntelliCode pojawianiu się u góry listy. Aby sprawdzić, czy rozszerzenia są przyczyną to zachowanie, wyłączając je i podjęcie ponownej próby IntelliSense.

Jeśli to nie rozwiąże problemu, dla Ciebie, zgłoś problem za pomocą programu Visual Studio [Zgłoś Problem](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) funkcji i wspomnieć o IntelliCode w raporcie.

## PYTANIA I ODPOWIEDZI. Jakie wersji programu Visual Studio należy uruchomić to rozszerzenie?

Rozszerzenie Visual Studio IntelliCode jest obsługiwana w wersji 15.7 programu Visual Studio 2017 w wersji zapoznawczej 5 i nowsze (wszystkie jednostki SKU). Instalacja rozszerzenia zostanie zatrzymany z "to rozszerzenie nie jest możliwe na żadnym z aktualnie zainstalowanych produktów". Jeśli nie ma minimalnej wymaganej wersji zainstalowane.

## PYTANIA I ODPOWIEDZI. Jest to środowisko dostępna tylko w języku angielskim?

IntelliCode to rozszerzenie w wersji zapoznawczej już dziś i chcielibyśmy się dowiedzieć, jak użyteczne te funkcje są dla szerokiego zakresu klientów. Gdy podejmujemy IntelliCode poza wersję zapoznawczą teraz bez obaw przyjrzymy się które ustawień regionalnych lub język na potrzeby obsługi pierwszy i jak jest spakowany, na podstawie tych opinii.

## <a name="privacy"/> P: co mogę zrobić informacji o prywatności? Jest wysyłany jest kod w chmurze? Jakie dane klienta są wysyłane do firmy Microsoft?

Deweloperzy są zaproszeni do środowiska Visual Studio IntelliCode w obecnie jako rozszerzenie eksperymentalnej wersji zapoznawczej. Cel rozszerzenia jest umożliwiają deweloperom, aby przetestować funkcje IntelliCode i aby przekazać opinię do zespołu produktu.

Przechwytujemy niektóre anonimowe dane dotyczące użycia i raportowanie błędów z rozszerzenia, aby pomóc w ulepszaniu produktu. Brak kodu użytkownika są wysyłane do firmy Microsoft, ale firma Microsoft gromadzi informacje o sposobie używania IntelliCode wyników. Dane obejmują tylko typu open source i platformy .NET typów i elementów członkowskich, które wybrane z listy sugerowanych IntelliCode. Deweloperzy mogą zrezygnować z [Visual Studio Experience Improvement Program](../../ide/visual-studio-experience-improvement-program.md), która wyłącza zbieranie danych dla rozszerzenia IntelliCode zbyt. Na pasku menu wybierz **pomocy** > **Wyślij opinię** > **ustawienia**. W **Visual Studio Experience Improvement Program** okno dialogowe, wybierz opcję **nie, nie chcę uczestniczyć** , a następnie wybierz **OK**.

Rozszerzenie IntelliCode może okresowo prosić deweloperowi na ukończenie ankietę ponownie są anonimowe. Użytkownicy, można zarejestrować nowości i przyszłych prywatnej wersji zapoznawczej, ale obecnie nie są wymagane w tym celu próbę użycia rozszerzenia eksperymentalne.

Przyszłych funkcji mogą wymagać dostępu do usługi, które będą wymagać rejestracji. Opublikujemy więcej szczegółów, jeśli te funkcje są gotowe do prywatnej wersji zapoznawczej.
