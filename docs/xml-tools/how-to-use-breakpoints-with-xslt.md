---
title: 'Porady: Użyj punktów przerwania z XSLT | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f262fa2b1822f74dc15b6f8599b88161c0a1cf8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Porady: Użyj punktów przerwania z XSLT

Można ustawić punktów przerwania, w arkuszu stylów XSLT lub w dokumencie źródłowym XML. Jeśli ustawisz punkt przerwania w tagu, gdy rozpoczyna się wykonywanie punkt przerwania zostanie przeniesione do następna instrukcja, która ma informacji o wierszu źródłowym.

Aby uzyskać więcej informacji, zobacz [podstawy debugowania: punktów przerwania](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Ustaw punkt przerwania w arkuszu stylów

Tagi początkowe, tagi końcowe i węzły tekstowe z arkusz stylów XSLT można ustawić punktów przerwania. Ponadto można ustawić punktów przerwania na kod w bloku skryptu.  
  
### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Aby ustawić punkt przerwania w arkuszu stylów
  
1.  Otwórz arkusz stylów w edytorze XML.  
  
2.  Umieść kursor w lokalizacji punktu przerwania, kliknij prawym przyciskiem myszy, wskaż polecenie **punktu przerwania**i kliknij przycisk **wstawić punktu przerwania**.  
  
3.  Kliknij przycisk Przeglądaj przycisk przeglądania (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu.  
  
4.  Zlokalizuj źródło dokumentu w formacie XML, a następnie kliknij przycisk **Otwórz**.  
  
     Pojedynczy plik dokument źródłowy, który służy do przekształcenia XSLT.  
  
5.  Kliknij przycisk **debugowania XSL** przycisk na pasku narzędzi edytora XML.  

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Ustaw punkt przerwania w dokumencie XML źródła

Elementy, atrybuty, przestrzeń nazw, komentarze, instrukcji przetwarzania i węzły tekstowe dokumentu XML źródła można ustawić punktów przerwania. Nie można ustawić punktu przerwania, w węźle dokumentu lub w węźle przestrzeni nazw, które jest dziedziczone z elementu nadrzędnego.  

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Aby ustawić punkt przerwania w dokumencie XML źródła

1.  Otwórz dokument XML w edytorze XML.  
  
2.  Umieść kursor w lokalizacji punktu przerwania, kliknij prawym przyciskiem myszy, wskaż polecenie **punktu przerwania**i kliknij przycisk **wstawić punktu przerwania**.  
  
3.  Kliknij przycisk Przeglądaj przycisk przeglądania (**...** ) na **arkusza stylów** pola w oknie właściwości dokumentu.  
  
4.  Zlokalizuj źródło dokumentu w formacie XML, a następnie kliknij przycisk **Otwórz**.  
  
     Pojedynczy plik dokument źródłowy, który służy do przekształcenia XSLT.  
  
5.  Kliknij przycisk **debugowania XSL** przycisk na pasku narzędzi edytora XML.  
 
## <a name="see-also"></a>Zobacz także

[Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)