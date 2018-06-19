---
title: Fill — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4546bafb3fa3a8c242b8b7ef4ef2863ea86bf179
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790450"
---
# <a name="fill-method-array-javascript"></a>fill (Array) — metoda (JavaScript)
Wypełnia tablicę o określonej wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. Obiekt array.  
  
 `value`  
 Wymagany. Wartość używana do wypełniania tablicy.  
  
 `start`  
 Opcjonalny. Indeks początkowy używany do wypełnienia tablicy wartości. Wartość domyślna to 0.  
  
 `end`  
 Opcjonalny. Indeks końcowy służące do wypełniania tablicy wartości. Wartość domyślna to właściwość długość `this` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `start` jest ujemna, `start` jest traktowany jako `length` + `start`, gdzie `length` jest długości tablicy. Jeśli `end` jest ujemna, `end` jest traktowany jako `length` + `end`.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach kodu wypełnienia tablicy wartości.  
  
```JavaScript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]