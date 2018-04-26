---
title: Funkcje IntelliSense w edytorze XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c2b87f9d1b850ce93851d78a8b43420ae473c41
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xml-editor-intellisense-features"></a>Funkcje IntelliSense w edytorze XML

Edytor XML zawiera pełną funkcje IntelliSense porównywalna innych edytorów języka podany w programie Visual Studio. W tej sekcji opisano, jak za pomocą funkcji IntelliSense języka definicji schematu XML (XSD) i dokumentów XSLT.

## <a name="intellisense-in-an-xsd-document"></a>IntelliSense w dokumencie XSD
 Schemat jest powiązany z dokumentem, możesz otrzymywać listy rozwijanej elementów oczekiwanego dowolnej chwili możesz wpisać `"<"` lub kliknij przycisk **wyświetlania listy członków obiektu** przycisk na pasku narzędzi edytora XML. Aby uzyskać informacje o sposobach kojarzenia schematów z dokumentami XML, zobacz [sprawdzanie poprawności kodu XML dokumentu](../xml-tools/xml-document-validation.md).

 Po wpisaniu ilość miejsca od wewnątrz tagu początkowego umożliwia również wyświetlenie listy rozwijanej, przedstawiający wszystkie atrybuty, które mogą zostać dodane do bieżącego elementu.

 Podczas wpisywania `"="` dla wartości atrybutu lub cudzysłów otwierający dla wartości, możesz również pobrać listy możliwych wartości dla tego atrybutu. Wartości są udostępniane tylko, jeśli schemat zawiera wartości wyliczenia za pomocą `xsd:enumeration` aspektów, lub jeśli atrybut `Boolean` typu. Dostępne są również listę kodów języków znane IntelliSense dla `xml:lang` lub `simpleType` która pochodzi z `xsd:language`. IntelliSense listę znanych `targetNamespace` podano wartości dla deklaracji przestrzeni nazw.

 Lista IntelliSense możliwych wartości jest również udostępniany po wpisaniu `">"` zamknięcia tagu początkowego, jeśli element jest `simpleType`. Zachowanie dla elementów jest podobne do zachowania dla atrybutów opisane w poprzednim akapicie.

 Etykietki narzędzi również występować w tych list IntelliSense, na podstawie `xsd:annotation` i `xsd:documentation` znaleźć informacji o w schemacie skojarzone.

## <a name="intellisense-in-an-xslt-document"></a>IntelliSense w dokumencie XSLT
 Po dodaniu nazwany szablon lub atrybutu w dokumencie XSLT umożliwia IntelliSense Wstaw następujące czynności:

-   Ustawić atrybutu nazwy.

-   Tryby szablonu.

-   Nazwy szablonów.

-   Nazwy parametrów dla danego trybu.

-   Nazwy parametrów dla danego szablonu o nazwie.

Aby uzyskać więcej informacji, zobacz [wskazówki: Korzystanie z IntelliSense XSLT](../xml-tools/walkthrough-using-xslt-intellisense.md) tematu.

## <a name="auto-completion"></a>Automatyczne uzupełnianie
 Edytor XML powoduje edycji XML łatwiejsze wypełniając wymaganej składni XML dla Ciebie. Jeśli na przykład wpisz następujący tag początkowy:

 `<book>`

 Edytor XML wypełnia tagu końcowego i umieszcza kursor po tagu początkowego. Poniżej przedstawiono przykład ("&#124;" Uwagi dotyczące pozycji kursora):

 `<book>`&#124;`</book>`

 Ponieważ wartości atrybutów musi zawsze mieć oferty, to edytor XML wypełnia cudzysłowy. Jeśli na przykład wpisz następujące polecenie:

 `<book title=`

 Edytor XML dodaje cudzysłowy i umieszcza kursor w cudzysłowy:

 `<book title="`&#124;`"`

 Podobnie Edytor XML są wstawiane następującej składni XML automatycznie dla Ciebie:

-   Zakończenie instrukcji przetwarzania:  `?>`

-   Koniec bloku CDATA: `]]>`

-   Zakończenie komentarza: `-->`

-   Zakończenie deklaracji DTD: `>`

Edytor XML ma również możliwości wstawiania przestrzeń nazw deklaracji, jeśli zostanie wybrany element kwalifikowaną przestrzeni nazw lub atrybut z listy IntelliSense i przestrzeń nazw dla tego elementu lub atrybutu nie jest jeszcze w zakresie.

Na przykład w przypadku wybrania `e:Book` element z listy IntelliSense, gdy prefiks jest powiązany z `http://books` przestrzeni nazw, która nie została zadeklarowana w dokumencie edytora XML wstawia deklaracji wymaganej przestrzeni nazw. Poniżej przedstawiono tekstu XML:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Parowanie nawiasów klamrowych
 Edytor XML zawiera nawias klamrowy wyróżnianie daje natychmiast uzyskuje opinie na elementy, które zostały zamknięte. Można również Użyj skrótu klawiaturowego (CTRL +]), aby przejść z jednej nawiasu klamrowego do pasującego nawiasu klamrowego.

 Edytor XML robi to następujące elementy:

-   Pasującego tagu początkowego i końcowego.

-   Każdej pary "\<" lub ">" nawiasy.

-   Początek i koniec komentarze.

-   Początek i koniec instrukcji przetwarzania.

-   Początek i koniec bloki CDATA.

-   Początek i koniec deklaracje DTD.

-   Otwieranie i zamykanie ofert dla atrybutów.

## <a name="modifying-the-intellisense-options"></a>Modyfikowanie opcji IntelliSense
 Funkcje IntelliSense i automatycznego uzupełniania są domyślnie włączone. Jednak możesz to zmienić, modyfikując ustawienia opcji narzędzi.

 **Automatyczne wstawianie** sekcji **różne** strony kontrolki następujące działania:

|Nazwa|Opis|
|----------|-----------------|
|Zamknij tagów|Wstawia Zamknij tagi dla nowych elementów.|
|Cudzysłowy atrybutu|Wstawia wartości atrybutów w cudzysłowie, gdy wprowadź nową nazwę atrybutu.|
|Inne znaczników|Kończy się komentarze, CDATA DOCTYPE, przetwarzanie instrukcji i innych deklaracji znaczników.|

#### <a name="to-change-the-auto-completion-behavior"></a>Aby zmienić zachowanie automatyczne uzupełnianie

1.  Wybierz **opcje** z **narzędzia** menu.

2.  Rozwiń węzeł **Edytor tekstu**, rozwiń węzeł **XML**i wybierz **różne**.

3.  Wprowadź wszelkie zmiany do **automatyczne wstawianie** sekcji, a następnie kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

- [Edytor XML](../xml-tools/xml-editor.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Przewodnik: Używanie XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)