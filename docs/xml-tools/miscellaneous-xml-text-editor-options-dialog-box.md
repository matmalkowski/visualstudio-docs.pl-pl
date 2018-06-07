---
title: Inne, XML, Edytor tekstu, Opcje, okno dialogowe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd6ee70f99f3b82505d210ab95f8359b5c7f90c8
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571773"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Różne, XML, Edytor tekstu, opcje — Okno dialogowe

To okno dialogowe umożliwia zmianę ustawień automatycznego uzupełniania i schematu edytora XML. Dostęp można uzyskać **opcje** okno dialogowe z **narzędzia** menu.

> [!NOTE]
> Te ustawienia są dostępne po wybraniu **Edytor tekstu** folderu, **XML** folder, a następnie **różne** opcję **opcje** okno dialogowe.


## <a name="auto-insert"></a>Automatyczne wstawianie
 **Zamknij tagów**

 Jeśli ustawienie autocompletion jest zaznaczone, Edytor automatycznie dodaje tag końcowy po wpisaniu nawiasu ostrego prawo (>), aby zamknąć tagu początkowego, jeśli znacznik nie jest już zamknięty. Jest to zachowanie domyślne.

 Uzupełnianie pustego elementu nie zależy od ustawienia autocompletion. Możesz zawsze autouzupełniania pustego elementu, wpisując ukośnika (/).

 **Cudzysłowy atrybutu**

 Podczas tworzenia atrybutów XML, Edytor wstawia `=" "` znaków i umieszcza daszek (^) wewnątrz cudzysłowów.

 Domyślnie zaznaczone.

 **Deklaracje Namespace**

 Edytor automatycznie wstawia deklaracje przestrzeni nazw wszędzie tam, gdzie jest to konieczne.

 Domyślnie zaznaczone.

 **Inne znaczników (komentarze, CDATA)**

 Komentarze, CDATA DOCTYPE, przetwarzanie instrukcji i innych znaczników są automatycznie wypełnianej.

 Domyślnie zaznaczone.

## <a name="network"></a>Sieć
 **Automatycznie pobieraj definicje DTD i schematy**

 Schematy i definicji typu dokumentu (pliki DTD) są automatycznie pobierane z lokalizacji HTTP. Funkcja ta używa przestrzeni nazw System.Net z serwera proxy na automatyczne wykrywanie serwerów włączone.

 Domyślnie zaznaczone.

## <a name="outlining"></a>Tworzenie konspektu
 **Trybu zwijania przy otwieraniu plików**

 Włącza funkcję zwijania po otwarciu pliku.

 Domyślnie zaznaczone.

## <a name="caching"></a>Buforowanie
 **Schematy**

 Określa lokalizację pamięci podręcznej schematu. Przycisk przeglądania (**...** ) otwiera **Przeglądaj katalog** okno dialogowe w bieżącej lokalizacji pamięci podręcznej schematu. Możesz wybrać inny katalog lub możesz wybrać folder, w oknie dialogowym kliknij prawym przyciskiem myszy i wybierz polecenie **Otwórz** co znajduje się w katalogu.

## <a name="see-also"></a>Zobacz także

- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Składniki edytora XML](../xml-tools/xml-editor-components.md)