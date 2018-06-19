---
title: Debug.setnonusercodeexceptions — właściwość | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790357"
---
# <a name="debugsetnonusercodeexceptions-property"></a>Debug.setNonUserCodeExceptions — właściwość
Określa, czy wszystkie bloków try-catch w tym zakresie są traktowane przez debuger jako nieobsługiwanych przez użytkownika. Wyjątki może być sklasyfikowane jako zgłoszono nieobsługiwany przez użytkownika lub nieobsługiwany.  
  
 Jeśli ta właściwość jest ustawiona na `true` w danym zakresie debuger może następnie określać wykonania określonych czynności (na przykład podział) na wyjątki zgłaszane wewnątrz tego zakresu, jeśli dewelopera życzy sobie być dzielone w wyjątkach nieobsługiwanych przez użytkownika. Jeśli ta właściwość jest ustawiona na `false` jest taka sama jak, jeśli nie ustawiono właściwości.  
  
 Aby uzyskać więcej informacji dotyczących debugowania, zobacz [przegląd debugowania skryptu Active](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób ustawić tę właściwość.  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]