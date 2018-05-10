---
title: Tworzenie wizualizacji kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 027a73343683b7953e70b597a8f9a222b56eb01f
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="visualize-code"></a>Tworzenie wizualizacji kodu

Wizualizacji i modelowania narzędzia w programie Visual Studio umożliwia ułatwić zrozumienie istniejący kod i opis aplikacji. Dzięki temu można wizualnie Dowiedz się, jak zmiany mogą wpłynąć na kod i pomocy oceny pracy i zagrożeń wynikających z tych zmian. Na przykład:

- Aby poznać relacji w kodzie, mapowanie wizualnie tych relacji.

- Opis architektury systemu i zachować zgodnie z jego projekt kodu, tworzenie diagramów zależności i sprawdzanie poprawności kodu względem tych diagramy.

- Do opisania klasy, struktury, tworzenie diagramów klasy.

Te narzędzia też pomóc Ci łatwiej komunikować się z osoby biorące udział w projekcie.

Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdej funkcji, zobacz [obsługę wersji architektura i modelowanie narzędzi](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|||
|-|-|
|**Zrozumienie kodu oraz jego relacji:**<br /><br /> Mapowanie relacji między określonym fragmentów kodu.<br /><br /> Zobacz Omówienie relacji w kodzie dla całego rozwiązania.<br /><br /> **Uwaga**: W tej wersji programu Visual Studio, termin *mapy kodu* jest używany zamiast *wykresu zależności*.|- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Zrozumienie struktury klasy:**<br /><br /> Umożliwia wizualizację struktury klas w projekcie przez tworzenie diagramów klas z kodu.|[Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Opis projektu systemu wysokiego poziomu, a następnie sprawdź kod dla tego projektu:**<br /><br /> Opis projektu wysokiego poziomu systemu i jego zależności zamierzone przez tworzenie diagramów zależności. Weryfikacja kodu dla tego projektu do upewnij się, że zależności w kodzie zachowania zgodności z projektu.|- [Tworzenie diagramów zależności w kodzie](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Łącza**|
|------------------|---------------|
|**Fora**|- [Visual Studio wizualizacji & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />- [Visual Studio wizualizacji & modelowania SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogi**|[Visual Studio ALM i Team Foundation Server blogu](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**Artykuły techniczne i arkuszy**|[Forum MSDN architektury](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Zobacz też

- [Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
