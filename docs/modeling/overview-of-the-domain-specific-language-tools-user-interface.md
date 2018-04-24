---
title: Omówienie interfejsu użytkownika narzędzi językowych właściwych dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: fc96b4be1d0bcec47019439b8ddd6145f4257a8a
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Omówienie interfejsu użytkownika narzędzi językowych właściwych dla domeny
Po pierwszym otwarciu rozwiązania narzędzia języka specyficznego dla domeny (narzędzia DSL) w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], interfejs użytkownika będzie wyglądać poniższej ilustracji.

 ![Projektant DSL](../modeling/media/dsl_designer.png "dsl_designer")

 W poniższej tabeli opisano, jak są używane elementy interfejsu użytkownika.

|**Element**|**Definicja**|
|-----------------|--------------------|
|Diagram|Model domeny są wyświetlane na diagramie.<br /><br /> Diagram zawiera dwie strony. Po jednej stronie określa typy elementów w modelach. Druga strona definiuje wygląd modeli na ekranie.|
|Przybornik|Przeciągnij narzędzia z przybornika do dodawania domeny klas i typów do diagramu kształtów. Aby dodać relacji, łączniki i map kształtu, kliknij narzędzie, a następnie kliknij węzeł źródłowy na diagramie, a następnie węzeł docelowy.|
|Eksplorator modelu DSL|**Eksplorator DSL** jest wyświetlany, gdy definicji DSL jest aktywnym oknem. DSL jest pokazywana jako drzewa. Eksplorator DSL pozwala edytować funkcji modelu, które nie są wyświetlane na diagramie. Na przykład możesz dodać elementy przybornika i Włącz procesu weryfikacji przy użyciu **DSL Explorer**.|
|Okno Szczegóły DSL|**Szczegóły DSL** okno zawiera właściwości domeny elementy modelu, dzięki którym można kontrolować sposób wyświetlania elementów oraz jak elementy są kopiowane i usunąć.<br /><br /> -Domyślnie **szczegóły DSL** obok przycisku zostanie wyświetlone okno **listy błędów** i **dane wyjściowe** systemu windows.|

## <a name="the-domain-model-diagram"></a>Diagram modelu domeny
 Diagram modelu domeny jest podzielona na dwie części. Po jednej stronie diagramu zawiera elementów i relacji w modelu. Druga strona pokazuje, jak model jest wyświetlana i zawiera kształty, które są używane do wyświetlania elementów i właściwości diagramu modelu. Na poniższej ilustracji przedstawiono elementów diagramu.

 ![Projektant DSL z tor](../modeling/media/dsl_desinger.png "dsl_desinger")

 W poniższej tabeli opisano niektóre elementy na diagramie modelu domeny.

|**Termin**|**Definicja**|
|--------------|--------------------|
|Klasa domeny|Typy elementów w modelach występują następujące klasy domeny.<br /><br /> Klasa domeny może występować więcej niż raz na diagramie, jeśli jest ona elementem docelowym więcej niż jedną relację.<br /><br /> Aby dodać klasy domeny, przeciągnij narzędzie klasy domeny z **przybornika** do **klasy i relacje** stronie diagramu.|
|Relacja domeny|Relacje domeny są typy łącza między elementami w modelach.<br /><br /> *Relacja osadzania* wskazuje, że element docelowy jest własnością lub zawarte w elemencie źródła i będzie wyświetlany jako linię ciągłą. Każdego elementu w modelu powinien być elementem docelowym jedna relacja osadzania, tak, czy model formularzy drzewa. A *odwołania relacji* oznacza ogólne łącza między elementami modelu i zostanie wyświetlone jako linia przerywana. Każdy element może mieć dowolną liczbę linki odwołań.<br /><br /> Tworzenie relacji, klikając narzędzie **przybornika**, klikając klasy domeny źródłowej, a następnie klikając klasy docelowej.|
|Kształty i łączniki|Kształty Określ, jak elementy modelu powinien być wyświetlany na diagramie DSL., łączników określić wiersze na diagramie DSL, który może służyć do wyświetlenia relacji.<br /><br /> Aby utworzyć łącznik lub kształt, przeciągnij narzędzie do **elementów diagramu** stronie diagramu.|
|Kształt mapy|Mapy kształt jest wyświetlany jako wiersz na diagramie modelu domeny łączenie kształtu do klasy domeny, który jest wyświetlany, lub łącznika do relacji domeny, który jest wyświetlany.|

## <a name="see-also"></a>Zobacz też

- [Przegląd narzędzi języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
- [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)