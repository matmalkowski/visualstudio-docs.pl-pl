---
title: Analizowanie i modelowanie architektury
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be58a86ec6c3b87954ff5b5be012ce636ad52204
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="analyze-and-model-your-architecture"></a>Analizowanie i modelowanie architektury
Upewnij się, że aplikacja spełnia wymagania architektury za pomocą architektury programu Visual Studio i modelowanie narzędzia do projektowania i modelu aplikacji.

* Łatwiej zrozumieć istniejący kod programu przy użyciu programu Visual Studio do wizualizacji struktury kodu, zachowania i relacje.

* Poinformuj zespołu konieczność przestrzegania zależnościami architektury.

* Tworzenie modeli na różnych poziomach szczegółów w całym cyklu życia aplikacji w ramach procesu tworzenia.

Zobacz [scenariusz: zmiana projektu z wykorzystaniem wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>Do

|||
|-|-|
|**Tworzenie wizualizacji kodu**:<br /><br /> — Zobacz organizacji i relacje kodu przez utworzenie mapy kodu. Wizualizowanie zależności między zestawy, przestrzenie nazw, klasy, metody i tak dalej.<br />— Zobacz strukturze klas i członków dla konkretnego projektu przez tworzenie diagramów klas z kodu.<br />-Znalezienie konfliktów między kodu i jego projekt, tworząc diagramy zależności Weryfikacja kodu.|-   [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)<br />-   [Praca z klasami i innymi typami (Projektant klas)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Wideo: Zrozumienie projektu z kodu przy użyciu map kodu programu Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Zdefiniuj architektura**:<br /><br /> -Definiujące i wymuszające ograniczenia dotyczące zależności między składnikami kodu przez tworzenie diagramów zależności.|-   [Wideo: Sprawdzanie poprawności zależnościami architektury z programem Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Weryfikacja systemu z wymaganiami i przeznaczony projekt:**<br /><br /> -Sprawdzanie poprawności kodu zależności z diagramy zależności, które opisują architekturę zamierzone i zapobiec zmiany, które może powodować konflikt z projektu.|-   [Wideo: Sprawdzanie poprawności zależnościami architektury z programem Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Dostosowywanie modeli i diagramów**:<br /><br /> -Utwórz języków specyficznego dla domeny.|-   [Modelowanie zestawu SDK dla programu Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generowanie tekstu przy użyciu szablonów T4**:<br /><br /> -Użyj bloki tekstu i logiki kontroli wewnątrz szablonów na wygenerowanie plików tekstowych.<br /> -T4 kompilacji szablonu przy użyciu programu MSBuild uwzględnione w programie Visual Studio|-   [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Udostępnianie modeli, diagramy oraz mapy kodu przy użyciu kontroli wersji Team Foundation**:<br /><br /> -Umieścić mapy kodu, projektów i diagramów zależności w ramach kontroli wersji Team Foundation, aby można je udostępnić.| |

Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdej funkcji, zobacz [obsługę wersji architektura i modelowanie narzędzi](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Typy modeli i typowe zastosowania

### <a name="code-maps"></a>Mapy kodu
Kod mapy pomocy, zobacz organizacji i relacji w kodzie.

**Typowe zastosowania:**

-   Sprawdź kod programu, można lepiej zrozumieć jego struktury i jego zależności, jak zaktualizować go i oszacowanie kosztów proponowane zmiany.

**Zobacz:**

-   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
-   [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagram"></a>Diagram zależności
Diagramy zależności umożliwiają zdefiniowanie struktury aplikacji jako zestaw warstw lub bloki z jawne zależności. Można uruchomić sprawdzania poprawności do wykrywania konfliktów między zależności w kodzie i opisano na diagramie zależności zależności.

**Typowe zastosowania:**

-   Ustabilizowania struktury aplikacji za pomocą wiele zmian przez jego użytkowania.
-   Wykryj konfliktów zależności niezamierzone przed zaewidencjonowaniem zmian w kodzie.

**Zobacz:**

-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
-   [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Języka specyficznego dla domeny (DSL)
DSL jest notacji, który projekt z określonym przeznaczeniem. W programie Visual Studio jest zwykle graficznego.

**Typowe zastosowania:**

-   Generowanie lub skonfiguruj części aplikacji. Praca jest wymagany do opracowywania notacji i narzędzia. Może to spowodować powstanie lepszym rozwiązaniem niż dostosowania UML do domeny.
-   Dla dużych projektów lub, w którym inwestycji w opracowywaniu DSL i jej narzędzi jest zwracany przez użyciem jej w więcej niż jednym projekcie linii produktów.

**Zobacz:**

-   [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?

[Visual Studio wizualizacji & modelowania Forum narzędzia](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>Zobacz także

- [Nowości](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps i zarządzanie cyklem życia aplikacji](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
