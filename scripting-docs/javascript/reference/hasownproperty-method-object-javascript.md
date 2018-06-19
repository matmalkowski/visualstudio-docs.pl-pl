---
title: hasOwnProperty — metoda (obiekt) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790699"
---
# <a name="hasownproperty-method-object-javascript"></a>hasOwnProperty — Metoda (Obiekt) (JavaScript)
Określa, czy obiekt nie ma właściwości o określonej nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Wystąpienie obiektu.  
  
 `proName`  
 Wymagany. Wartość Nazwa właściwości ciągu.  
  
## <a name="remarks"></a>Uwagi  
 `hasOwnProperty` Metoda zwraca `true` Jeśli `object` ma właściwości o określonej nazwie `false` jeśli jej nie ma. Ta metoda sprawdza właściwości w łańcuchu prototypu obiektu; Właściwość musi należeć do samego obiektu.  
  
 Ta właściwość nie jest obsługiwana w obiektach hosta dla programu Internet Explorer 8 oraz niższych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wszystkie `String` obiektów korzystają ze wspólnego split — metoda. Następujący kod do wyświetlenia **false** i **true**.  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [in — Operator](../../javascript/reference/in-operator-decrementjavascript.md)