---
title: startsWith — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 871def4a-0f96-4675-b6ff-2349f4996511
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74970a9a3bfe280e91f2df39340732eda8664142
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791551"
---
# <a name="startswith-method-string-javascript"></a>startsWith (String) — metoda (JavaScript)
Zwraca wartość wskazującą, czy ciąg lub podciąg rozpoczyna się od innego określony ciąg.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
  
stringObj.startsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. Obiekt ciągu wyszukiwania.  
  
 `str`  
 Wymagany. Ciąg wyszukiwania.  
  
 `position`  
 Opcjonalny. Pozycja pierwszego znaku w celu wyszukiwania w obiekcie string, zaczynając od 0.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli na początku ciąg `position` rozpoczyna się od ciągu wyszukiwania `startsWith` metoda zwraca `true`; w przeciwnym razie zwraca `false`.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `str` jest `RegExp`, `TypeError` jest generowany.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]