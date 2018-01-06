---
title: "Porady: Użyj punktów przerwania z XSLT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1407d34bc833c5c8a911adc87c8fa7cfec933256
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Porady: Użyj punktów przerwania z XSLT
Można ustawić punktów przerwania, w arkuszu stylów XSLT lub w dokumencie źródłowym XML. Jeśli ustawisz punkt przerwania w tagu, gdy rozpoczyna się wykonywanie punkt przerwania zostanie przeniesione do następna instrukcja, która ma informacji o wierszu źródłowym.  
  
 Aby uzyskać więcej informacji, zobacz [podstawy debugowania: punktów przerwania](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>Ustaw punkt przerwania w arkuszu stylów  
 Tagi początkowe, tagi końcowe i węzły tekstowe z arkusz stylów XSLT można ustawić punktów przerwania. Ponadto można ustawić punktów przerwania na kod w bloku skryptu.  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Aby ustawić punkt przerwania w arkuszu stylów  
  
1.  Otwórz arkusz stylów w edytorze XML.  
  
2.  Umieść kursor w lokalizacji punktu przerwania, kliknij prawym przyciskiem myszy, wskaż polecenie **punktu przerwania**i kliknij przycisk **wstawić punktu przerwania**.  
  
3.  Kliknij przycisk Przeglądaj przycisk przeglądania (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu.  
  
4.  Zlokalizuj źródło dokumentu w formacie XML, a następnie kliknij przycisk **Otwórz**.  
  
     Pojedynczy plik dokument źródłowy, który służy do przekształcenia XSLT.  
  
5.  Kliknij przycisk **debugowania XSL** przycisk na pasku narzędzi edytora XML.  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Ustaw punkt przerwania w dokumencie XML źródła  
 Elementy, atrybuty, przestrzeń nazw, komentarze, instrukcji przetwarzania i węzły tekstowe dokumentu XML źródła można ustawić punktów przerwania. Nie można ustawić punktu przerwania, w węźle dokumentu lub w węźle przestrzeni nazw, które jest dziedziczone z elementu nadrzędnego.  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Aby ustawić punkt przerwania w dokumencie XML źródła  
  
1.  Otwórz dokument XML w edytorze XML.  
  
2.  Umieść kursor w lokalizacji punktu przerwania, kliknij prawym przyciskiem myszy, wskaż polecenie **punktu przerwania**i kliknij przycisk **wstawić punktu przerwania**.  
  
3.  Kliknij przycisk Przeglądaj przycisk przeglądania (**...** ) na **arkusza stylów** pola w oknie właściwości dokumentu.  
  
4.  Zlokalizuj źródło dokumentu w formacie XML, a następnie kliknij przycisk **Otwórz**.  
  
     Pojedynczy plik dokument źródłowy, który służy do przekształcenia XSLT.  
  
5.  Kliknij przycisk **debugowania XSL** przycisk na pasku narzędzi edytora XML.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)