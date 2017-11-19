---
title: "add — metoda (Set) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-set-javascript"></a>add — Metoda (Set) (JavaScript)
Dodaje nowy element do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>Parametry  
 `setObj`  
 Wymagany. A `Set` obiektu.  
  
 `value`  
 Wymagany. Nowy element `Set`.  
  
## <a name="remarks"></a>Uwagi  
 Nowy element może być dowolnego typu i musi być unikatowa. Jeśli użytkownik dodany element nie jest unikatowa `Set`, nie zostanie dodany nowy element do kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można dodawać członków do zestawu, a następnie pobrać je.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]