---
title: Oczekiwano VBArray | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-expected"></a>Oczekiwano VBArray
Należy podać obiekt, który nie był safeArray Visual Basic, gdy oczekiwano jednej.  
  
```  
new VBArray(safeArray);  
```  
  
 VBArrays są tylko do odczytu i nie można utworzyć bezpośrednio. SafeArray argument jest wartością VBArray i musi mieć wartość VBArray uzyskane przed przesłaniem do `VBArray` konstruktora. To jest możliwe tylko przez pobieranie wartości z istniejących ActiveX lub innego obiektu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, możesz przekazać tylko **VBArray** obiekty do **VBArray** konstruktora.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)