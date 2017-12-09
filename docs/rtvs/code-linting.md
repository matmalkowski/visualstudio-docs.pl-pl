---
title: "Linting R kodu za pomocą narzędzia R dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords: vs.toolsoptionspages.text_editor.r.lint
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 3c84424f052f8ba150c47a72048d4782b7c2a8de
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="linting-r-code-in-visual-studio"></a>Kod linting R w programie Visual Studio

Linting jest procesem, która analizuje kod, aby odkryć potencjalne błędy, a także kwestie związane z formatowaniem i innych szumu w plikach kodu (na przykład fałszywe białych znaków). Linting pomaga również w zachęca niektórych Konwencji kodowania, takich jak identyfikatory nazewnictwa, która jest bardzo pomocne w obrębie zespołów i innych sytuacjach współpracy.

R narzędzi dla programu Visual Studio (RTVS) zawiera wbudowane linting R z zachowaniem steruje się za pomocą różnych opcji. Te opcje można znaleźć w **Narzędzia > Opcje > Edytor tekstu > R > wierszu**.

Linting jest domyślnie wyłączona. Aby włączyć linting, ustaw **wszystkie > Włącz wierszu** opcję na wartość true. Kolejne sekcje w tym temacie opisano inne opcje linting:

Po włączeniu linting jest stosowana w edytorze podczas pisania. Problemy są wyświetlane jako zygzaki zielony. Na przykład na poniższym rysunku RTVS zidentyfikowała sześć linting problemy, w tym użycie `=` zamiast `<-` przydziału, brak odstępy dookoła argumenty funkcji, użyj przypadku Pascal identyfikatorów pisanych wielkimi literami i korzystanie z średnika. Ustawiając kursor nad rozwiązaniem problemu zawiera opis.

![Przykłady linting dla kodu języka R](media/linting-01.png)

## <a name="assignment-group"></a>Przypisanie grupy

| Opcja | Wartość domyślna | Efekt linting |
| --- | --- | --- |
| Wymuszanie\<- | `True` | Określa, kiedy `<-` nie jest używany do przypisania. |

## <a name="naming-group"></a>Grupy nazewnictwa

Te opcje Flaga identyfikatorów, które używają różnych konwencji nazewnictwa:

| Opcja | Wartość domyślna | Efekt linting |
| --- | --- | --- |
| Flaga (camelcase) | `False` | Identyfikatory flagi, które używają (camelcase). |
| Długie nazwy flagi | `False` | Flagi identyfikatory którego nazwanego przekracza ustawienie "Maksymalna długość nazwy". |
| Flaga wiele punktów | `True` | Flagi identyfikatorów, które używają wielu punktów. |
| Flaga PascalCase | `True` | Identyfikatory flagi, które używają PascalCase. |
| Flaga snake_case | `False` | Identyfikatory flagi używających znaki podkreślenia. |
| Flaga wielkimi literami | `True` | Identyfikatory flagi używających wersalików. |
| Maksymalna długość nazwy | 32 | Długość stosowana z "flagi długich nazw" ustawienie. |

## <a name="spacing-group"></a>Odstępy grupy

Te opcje, które są ustawione na `True` domyślnie kontrolować, gdzie linter identyfikuje problemy odstępy: po nazwy funkcji wokół przecinkami dookoła operatorów, otwierające i zamykające nawiasy pozycji odstęp przed (i miejsce wewnątrz ().

## <a name="statements-group"></a>Grupy — instrukcje

| Opcja | Wartość domyślna | Efekt linting |
| --- | --- | --- |
| Wielokrotne | `True` | Identyfikuje, gdy użycie wielu instrukcji w tym samym wierszu. |
| Średnikami | `True` | Identyfikuje używa średnikami. |

## <a name="text-group"></a>Tekst grupy

| Opcja | Wartość domyślna | Efekt linting |
| --- | --- | --- |
| Limit długości wiersza | `False` | Określa, czy linter flagi wierszy przekracza opcji "Maksymalna długość wiersza". |
| Maksymalna długość wiersza | 80 | Ustawia długość wiersza stosowane przy użyciu opcji "Limit długości wiersza". |

## <a name="whitespace-group"></a>Grupy odstępu

Te opcje, które są ustawione na `True` domyślnie kontrolować, gdzie linter identyfikuje problemy odstępu: Korzystanie z kart, użyj podwójnych cudzysłowów, końcowe puste wiersze i końcowe.