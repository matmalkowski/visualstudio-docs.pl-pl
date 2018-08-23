---
title: Ukrywanie właściwości, które mają właściwości podrzędnej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: bd340b748311bbb257ed0c4bbfe7b972cbf7beb9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690740"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ukrywanie właściwości, które mają właściwości podrzędnej
Czy chcesz ukryć właściwości, które mają właściwości podrzędnej:  
  
-   Jeśli masz zagnieżdżonych projektów, gdzie projekt nadrzędny programowo określa niektóre aspekty projekt podrzędny.  
  
-   Jeśli możesz użyć formantu przy użyciu wyspecjalizowanego projektanta i nie chcesz dają deweloperom pełny dostęp do wszystkich właściwości formantu.  
  
-   Jeśli masz zakresie własności obiektu i chce ograniczyć widoku właściwości.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Aby ukryć właściwości, które mają właściwości podrzędnej  
  
1.  Ustaw `pfDisplay` parametru w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> do `FALSE`.  
  
2.  Ustaw `pfHide` parametru w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> do `TRUE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Siatka wyświetlania właściwości](../extensibility/internals/properties-display-grid.md)