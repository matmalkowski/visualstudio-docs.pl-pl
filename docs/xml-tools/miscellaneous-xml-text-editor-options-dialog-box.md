---
title: Inne, XML, Edytor tekstu, opcje — Okno dialogowe
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
ms.openlocfilehash: 0dfc0a4e3841f30c2be81b60b2e86d9fd29bb801
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Inne, XML, Edytor tekstu, opcje — Okno dialogowe

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

## <a name="see-also"></a>Zobacz też

- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Składniki edytora XML](../xml-tools/xml-editor-components.md)