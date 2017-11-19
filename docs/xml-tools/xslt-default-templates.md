---
title: "Szablony domyślne XSLT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e72f0f4b12921c07a66b590655bb8583eb3f9786
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="xslt-default-templates"></a>Szablony domyślne XSLT
Domyślny szablon jest używany podczas przetwarzania, gdy istnieje żadna reguła dopasowywania jawnego szablonu w arkuszu stylów XSLT. Szablonu domyślnego, nazywana także wbudowanych szablonów reguł, jest zdefiniowany w sekcji 5.8 zaleceń 1.0 W3C XSLT. Domyślny szablon umożliwia procesorze XSLT do przetwarzania węzeł, nawet jeśli nie zasady jawnego szablonu, który dopasowuje je. Jednak ponieważ reguły wbudowane szablonu nie jest jawnie zdefiniowany w arkuszu stylów, może to prowadzić do nieoczekiwanych lub mylące wyniki przekształcenie XSLT.  
  
 Debuger XSLT są obecnie wyświetlane kod XSLT domyślnych szablonów. Podczas przechodzenia do kolejnych transformację XSLT i jeśli użyty zostanie szablon domyślny, debuger wyświetla szablon domyślny w oknie. Dzięki temu można wykonywać krokowo kodu domyślnego szablonu i ustaw punkty przerwania w instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie XSLT](../xml-tools/debugging-xslt.md)