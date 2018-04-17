---
title: 'Porady: oceny wyrażenia XPath | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c026e9d2005156189afc9dd478c75397a997d8f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Porady: oceny wyrażenia XPath
Można obliczyć wyrażenia XPath z **QuickWatch** okno dialogowe. Wyrażenie XPath musi być prawidłowa zgodnie z zaleceniem W3C XPath 1.0. Bieżącego kontekstu XSLT — to znaczy `self::node()` w węźle **zmiennych lokalnych** okna — udostępnia kontekst oceny dla wyrażenia XPath.  
  
 Na poniższej liście opisano, jakie funkcje są obsługiwane podczas obliczania wyrażenia XPath:  
  
-   Obsługiwane są wbudowane funkcje XPath.  
  
-   Funkcje wbudowane XSLT nie są obsługiwane.  
  
-   Funkcje zdefiniowane przez użytkownika nie są obsługiwane.  
  
> [!NOTE]
>  W poniższej procedurze użyto pliki belowAvg.xsl i books.xml z [wskazówki: debugowanie arkusz stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tematu.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Można oszacować wyrażenia XPath  
  
1.  Wstaw punkt przerwania w `xsl:if` tag początkowy.  
  
2.  Kliknij przycisk **debugowania XSL** przycisk na pasku narzędzi edytora XML.  
  
     Debuger uruchamia i dzieli na `xsl:if` tagu.  
  
3.  Kliknij prawym przyciskiem myszy i wybierz **QuickWatch**.  
  
     **QuickWatch** zostanie wyświetlone okno dialogowe.  
  
4.  Wprowadź `./price/text()` w **wyrażenie** pole **QuickWatch** okno dialogowe i kliknij przycisk **obliczyć ponownie**.  
  
     Cena bieżącego węzła książki pojawia się w **wartość** pole.  
  
5.  Zmień wyrażenie XPath wskazujące `./price/text() < $bookAverage` i kliknij przycisk **obliczyć ponownie**.  
  
     **Wartość** pole pokazuje, że wyrażenie XPath zwraca `true`.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)