---
title: 'Porady: Użyj punktów przerwania z XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 430b7f14f35506b45fe73be47d056cdd7b6a9c95
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548362"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Porady: Użyj punktów przerwania z XSLT

Można ustawić punktów przerwania, w arkuszu stylów XSLT lub w dokumencie źródłowym XML. Jeśli ustawisz punkt przerwania w tagu, gdy rozpoczyna się wykonywanie punkt przerwania zostanie przeniesione do następna instrukcja, która ma informacji o wierszu źródłowym.

Aby uzyskać więcej informacji, zobacz [podstawy debugowania: punktów przerwania](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Ustaw punkt przerwania w arkuszu stylów

Tagi początkowe, tagi końcowe i węzły tekstowe z arkusz stylów XSLT można ustawić punktów przerwania. Ponadto można ustawić punktów przerwania na kod w bloku skryptu.

### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Aby ustawić punkt przerwania w arkuszu stylów

1.  Otwórz arkusz stylów w edytorze XML.

2.  Umieść kursor w lokalizacji punktu przerwania, kliknij prawym przyciskiem myszy, wskaż polecenie **punktu przerwania**i kliknij przycisk **wstawić punktu przerwania**.

3.  Kliknij przycisk Przeglądaj (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu.

4.  Zlokalizuj źródło dokumentu w formacie XML, a następnie kliknij przycisk **Otwórz**.

     Pojedynczy plik dokument źródłowy, który służy do przekształcenia XSLT.

5.  Kliknij przycisk **debugowania XSL** przycisk na pasku narzędzi edytora XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Ustaw punkt przerwania w dokumencie XML źródła

Elementy, atrybuty, przestrzeń nazw, komentarze, instrukcji przetwarzania i węzły tekstowe dokumentu XML źródła można ustawić punktów przerwania. Nie można ustawić punktu przerwania, w węźle dokumentu lub w węźle przestrzeni nazw, które jest dziedziczone z elementu nadrzędnego.

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Aby ustawić punkt przerwania w dokumencie XML źródła

1.  Otwórz dokument XML w edytorze XML.

2.  Umieść kursor w lokalizacji punktu przerwania, kliknij prawym przyciskiem myszy, wskaż polecenie **punktu przerwania**i kliknij przycisk **wstawić punktu przerwania**.

3.  Kliknij przycisk Przeglądaj (**...** ) na **arkusza stylów** pola w oknie właściwości dokumentu.

4.  Zlokalizuj źródło dokumentu w formacie XML, a następnie kliknij przycisk **Otwórz**.

     Pojedynczy plik dokument źródłowy, który służy do przekształcenia XSLT.

5.  Kliknij przycisk **debugowania XSL** przycisk na pasku narzędzi edytora XML.

## <a name="see-also"></a>Zobacz także

- [Wskazówki: Debugowanie arkusz stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)