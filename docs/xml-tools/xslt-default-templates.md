---
title: Szablony domyślne XSLT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b1d2f0a7102821041bf76f1e8dcd73ff01baacc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="xslt-default-templates"></a>Szablony domyślne XSLT
Domyślny szablon jest używany podczas przetwarzania, gdy istnieje żadna reguła dopasowywania jawnego szablonu w arkuszu stylów XSLT. Szablonu domyślnego, nazywana także wbudowanych szablonów reguł, jest zdefiniowany w sekcji 5.8 zaleceń 1.0 W3C XSLT. Domyślny szablon umożliwia procesorze XSLT do przetwarzania węzeł, nawet jeśli nie zasady jawnego szablonu, który dopasowuje je. Jednak ponieważ reguły wbudowane szablonu nie jest jawnie zdefiniowany w arkuszu stylów, może to prowadzić do nieoczekiwanych lub mylące wyniki przekształcenie XSLT.  
  
 Debuger XSLT są obecnie wyświetlane kod XSLT domyślnych szablonów. Podczas przechodzenia do kolejnych transformację XSLT i jeśli użyty zostanie szablon domyślny, debuger wyświetla szablon domyślny w oknie. Dzięki temu można wykonywać krokowo kodu domyślnego szablonu i ustaw punkty przerwania w instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)