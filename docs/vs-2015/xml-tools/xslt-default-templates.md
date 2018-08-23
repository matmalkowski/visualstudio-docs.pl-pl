---
title: Szablony domyślne XSLT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e5ddc4765ee8e2efe7dc8842abdb071a2fd37057
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42689054"
---
# <a name="xslt-default-templates"></a>Szablony domyślne XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślny szablon jest używany podczas przetwarzania, gdy nie ma pasującego jawnego szablonu reguły w arkuszu stylów XSLT. Domyślny szablon, nazywana także wbudowany szablon reguły, jest zdefiniowany w sekcji 5.8 zalecenia 1.0 W3C XSLT. Domyślny szablon umożliwia procesora XSLT można przetworzyć węzła, nawet jeśli nie jawnego szablonu reguły, który mu odpowiada. Jednak ponieważ reguły wbudowany szablon nie jest jawnie zdefiniowany w arkuszu stylów, może to prowadzić do nieoczekiwanych lub mylące wyniki przekształcenia XSLT.  
  
 Debuger XSLT wyświetla teraz kod szablony domyślne XSLT. Kiedy wkraczasz przy użyciu transformacji XSLT, jeśli użyty zostanie szablon domyślny, debuger wyświetla domyślny szablon w oknie. Dzięki temu można przejść przez kod szablonu domyślnego i ustawiania punktów przerwania w instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)

