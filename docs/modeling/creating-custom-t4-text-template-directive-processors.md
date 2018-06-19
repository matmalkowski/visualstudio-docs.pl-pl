---
title: Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 49a3c24116e6cc78084d0830a662ad7a3522d32c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950595"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego

*Proces transformacji szablonu tekstowego* przyjmuje *szablonu tekstowego* pliku jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe. *Aparat przekształcania szablonu tekstowego* formanty proces i aparat współdziała z hosta transformacji szablonu tekstowego i co najmniej jeden szablon tekstu *procesory dyrektywy* do ukończenia proces. Aby uzyskać więcej informacji, zobacz [proces transformacji szablonu tekstowego](../modeling/the-text-template-transformation-process.md).

Aby utworzyć niestandardowego procesora dyrektywy, należy utworzyć klasę, która dziedziczy albo <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Jest to różnica między nimi <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementuje interfejs minimalnej, które są niezbędne, można pobrać parametrów od użytkownika oraz do generowania kodu, który spowoduje utworzenie pliku danych wyjściowych szablonu. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementuje wzorzec projektowy wymaga/udostępnia. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> obsługuje dwa parametry specjalne, `requires` i `provides`.  Na przykład niestandardowego procesora dyrektywy może Zaakceptuj nazwy pliku od użytkownika, Otwórz i odczytać pliku, a następnie zapisać tekst pliku w zmiennej o nazwie `fileText`. Podklasa <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> klasy może potrwać nazwy pliku od użytkownika jako wartość `requires` parametr i nazwę zmiennej do przechowywania tekstu jako wartość `provides` parametru. Tego procesora może otworzyć i odczytać pliku i następnie umieść tekst pliku w określonej zmiennej.

Przed wywołaniem niestandardowego procesora dyrektywy z szablonu tekstowego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], należy go zarejestrować.

Aby uzyskać więcej informacji na temat dodawania klucza rejestru, zobacz [wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Dyrektywy niestandardowych

Niestandardowe dyrektywy wygląda następująco:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Jeśli chcesz uzyskać dostęp do danych zewnętrznych lub zasobów z szablonu tekstowego, można użyć niestandardowego procesora dyrektywy.

Szablony tekstowe różnych można udostępniać funkcje, które udostępnia pojedynczy procesor dyrektywy, więc procesory dyrektywy umożliwiają współczynnik kodu do ponownego użycia. Wbudowane `include` dyrektywa jest podobne, ponieważ służy do współczynnika kodu i udostępniać je między szablony inny tekst. Różnica jest to, że żadnej funkcji, który `include` dyrektywa zawiera jest stała i nie akceptuje parametrów. Aby zapewnić często używane funkcje do szablonu tekstowego i pozwala szablonu do przekazania parametrów, należy utworzyć niestandardowego procesora dyrektywy.

Przykłady niestandardowego procesory dyrektywy może być:

-   Procesor dyrektywy, aby zwrócić dane z bazy danych, która przyjmuje jako parametry nazwę użytkownika i hasło.

-   Procesor dyrektywy otwieranie i Odczyt pliku, który przyjmuje nazwę pliku jako parametr.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Podmiot zabezpieczeń części niestandardowego procesora dyrektywy

Aby opracować procesora dyrektywy, należy utworzyć klasę, która dziedziczy albo <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Najważniejsze `DirectiveProcessor` dostępne są następujące metody, które należy zaimplementować.

-   `bool IsDirectiveSupported(string directiveName)` -Return `true` Jeśli procesora dyrektywy mogą dotyczyć dyrektywy o nazwie.

-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Aparat szablonu wywołuje tę metodę dla każdego wystąpienia dyrektywy w szablonie. Procesor należy zapisać wyniki.

Po wszystkie wywołania ProcessDirective() aparatu tworzenia szablonów wywoła tych metod:

-   `string[] GetReferencesForProcessingRun()` -Zwraca nazwy zestawów, które wymaga kod szablonu.

-   `string[] GetImportsForProcessingRun()` -Zwróć przestrzenie nazw, które mogą być używane w kodzie szablonu.

-   `string GetClassCodeForProcessingRun()` -Zwracają kod metody, właściwości i innych deklaracji używających kod szablonu. Najprostszym sposobem, w tym celu jest kompilacji ciąg zawierający języka C# lub kod Visual Basic. Aby procesora dyrektywy stanie wywoływana z szablonu, który korzysta z dowolnego języka CLR, można utworzyć instrukcje jako drzewo CodeDom i następnie zwrócenia wyniku serializacji drzewa języka używanego w szablonie.

-   Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md) wyjaśniono, jak zarejestrować niestandardowego procesora dyrektywy.
- [Wskazówki: Tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md) opisuje sposób tworzenia niestandardowego procesora dyrektywy, jak zarejestrować i przetestować procesora dyrektywy oraz format pliku wyjściowego w formacie HTML.