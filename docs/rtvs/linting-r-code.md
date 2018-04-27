---
title: Kod linting R
description: Jak pracować z R, włącznie z opcjami linting obsługę linting kompilacji w Visual Studio.
ms.date: 01/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: e5494283fdf759ddc664207d62d40f7f83993632
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="linting-r-code-in-visual-studio"></a>Kod linting R w programie Visual Studio

Linting analizuje kod, aby odkryć potencjalne błędy, formatowanie i innych szumu kodu, takie jak fałszywe odstępu. Linting pomaga również w zachęca niektórych Konwencji kodowania, takich jak nazewnictwa identyfikatorów. Takie konwencje są pomocne w obrębie zespołów i innych sytuacjach współpracy.

R narzędzi dla programu Visual Studio (RTVS) zawiera wbudowane linting R z zachowaniem jest kontrolowany za pomocą różnych opcji opisanych w tym artykule. Te opcje można znaleźć w **Narzędzia > Opcje > Edytor tekstu > R > wierszu**.

Linting jest domyślnie wyłączona. Aby włączyć linting, ustaw **wszystkie > Włącz wierszu** opcję na wartość true.

Po włączeniu linting jest stosowana w edytorze podczas pisania. Problemy są wyświetlane jako zygzaki zielony. Na przykład na poniższym rysunku RTVS zidentyfikowała sześć linting problemy, w tym użycie `=` zamiast `<-` przydziału, brak odstępy dookoła argumenty funkcji, użyj przypadku Pascal identyfikatorów pisanych wielkimi literami i korzystanie z średnika. Ustawiając kursor nad rozwiązaniem problemu zawiera opis.

![Przykłady linting dla kodu języka R](media/linting-01.png)

Często Zmień opcje linting zależnie od potrzeb projektu lub pliku. Na przykład użyć przykładowego kodu z kursu online `=` zamiast `<-` wraz z identyfikatory przypadku Pascal. Taki kod może wyświetlić częste linting ostrzeżenia, ponieważ domyślne opcje linting Flaga tych przypadkach. Następnie podczas pracy z kodem, można wyłączyć opcji zamiast poświęcany czas korygowanie każde wystąpienie.

## <a name="assignment-group"></a>Przypisanie grupy

| Opcja | Wartość domyślna | Efekt linting |
| --- | --- | --- |
| Wymuszanie \<- | `True` | Określa, kiedy `<-` nie jest używany do przypisania. |

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