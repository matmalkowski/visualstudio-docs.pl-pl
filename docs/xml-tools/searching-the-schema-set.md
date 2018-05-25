---
title: Eksploratora schematu XML — wyszukiwanie w zestawie schematów
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c110344499281243628d633d005506af5cd801d0
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="search-the-schema-set"></a>Wyszukiwanie w zestawie schematów

**Eksploratora schematu XML** umożliwia wyszukiwanie schematu ustawiony w następujący sposób:

-   Wyszukiwanie słów kluczowych.

-   Wyszukiwania specyficznego dla schematu.

## <a name="keyword-search"></a>Wyszukiwanie słów kluczowych

 Wyszukiwanie słów kluczowych, wprowadzając podciągu w **SchemaSet wyszukiwania** pole tekstowe z **Eksploratora schematu XML** paska narzędzi.

 ![Wyszukiwanie słów kluczowych Eksploratora schematu XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 **Eksploratora schematu XML** wyszukuje schematu, ustaw następujące atrybuty:

-   Wszelkie `name` lub `ref` atrybuty, które odpowiada określonym słowem kluczowym. Nazwę można znaleźć elementy, atrybuty, typy i tak dalej.

-   `schemaLocation` Atrybuty instrukcji #include.

-   `namespace` Atrybuty instrukcje importu.

## <a name="schema-specific-search"></a>Wyszukiwanie określonego schematu

 **Eksploratora schematu XML** zawiera również wbudowane wyszukiwania, które mogą korzystać za pomocą menu kontekstowego **Eksploratora schematu XML**. Aby uzyskać więcej informacji na temat menu kontekstowe dostępne, zobacz [menu kontekstowe](../xml-tools/context-menus-xml-schema-explorer.md). Można również wykonać wyszukiwanie określonego schematu z widoku startowego; Aby uzyskać więcej informacji, zobacz sekcję "Schematu Określanie szczegółów" w [widoku startowego](../xml-tools/start-view.md) tematu.

## <a name="display-and-navigate-search-results"></a>Wyświetl i przejdź do wyników wyszukiwania

 Po zakończeniu wyszukiwania w okienku wyników podsumowania jest dodawany do paska narzędzi z wynikami wyszukiwania. Wyniki wyszukiwania są wyróżnione **Eksploratora schematu XML** i oznaczone przez znaczniki na pionowy pasek przewijania. Wyniki wyszukiwania można przejść za pomocą **przejdź do następnego wyniku wyszukiwania** i **przejdź do wyników poprzedniego wyszukiwania** przycisków w okienku wyników podsumowania **Eksploratora schematu XML**narzędzi; za pomocą klawiszy **F3** i **Shift**+**F3**; lub przez kliknięcie przycisku znaczników na pasku przewijania.

 Wyniki wyszukiwania można dodać do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku podsumowania wyników.

 ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clear-search-results"></a>Wyczyść wyniki wyszukiwania

 Wyczyść wyniki wyszukiwania, kliknij przycisk **x** przycisku w okienku wyników podsumowania **Eksploratora schematu XML** narzędzi wyszukiwania.

## <a name="see-also"></a>Zobacz także

- [Eksplorator schematu XML](../xml-tools/xml-schema-explorer.md)