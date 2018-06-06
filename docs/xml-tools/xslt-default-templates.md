---
title: Szablony domyślne XSLT
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b50a7457ddbae24f2a00e4c631371cb2aeb1169
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693958"
---
# <a name="xslt-default-templates"></a>Szablony domyślne XSLT

Domyślny szablon jest używany podczas przetwarzania, gdy istnieje żadna reguła dopasowywania jawnego szablonu w arkuszu stylów XSLT. Szablonu domyślnego, nazywana także wbudowanych szablonów reguł, jest zdefiniowany w sekcji 5.8 zaleceń 1.0 W3C XSLT. Domyślny szablon umożliwia procesorze XSLT do przetwarzania węzeł, nawet jeśli nie zasady jawnego szablonu, który dopasowuje je. Jednak ponieważ reguły wbudowane szablonu nie jest jawnie zdefiniowany w arkuszu stylów, może to prowadzić do nieoczekiwanych lub mylące wyniki przekształcenie XSLT.

Debuger XSLT są obecnie wyświetlane kod XSLT domyślnych szablonów. Podczas przechodzenia do kolejnych transformację XSLT i jeśli użyty zostanie szablon domyślny, debuger wyświetla szablon domyślny w oknie. Dzięki temu można wykonywać krokowo kodu domyślnego szablonu i ustaw punkty przerwania w instrukcji.

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)