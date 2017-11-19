---
title: "endsWith — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6d57d501f0f100f069522e4b51666918168fa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="endswith-method-string-javascript"></a>endsWith (String) — metoda (JavaScript)
Zwraca wartość wskazującą, czy ciąg lub podciąg kończy się na inną określony ciąg.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. Obiekt ciągu wyszukiwania.  
  
 `str`  
 Wymagany. Ciąg wyszukiwania.  
  
 `position`  
 Opcjonalny. Pozycja pierwszego znaku w celu wyszukiwania w obiekcie string, zaczynając od 0.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli na początku ciąg `position` kończy ciąg wyszukiwania `endsWith` metoda zwraca `true`; w przeciwnym razie zwraca `false`.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `str` jest `RegExp`, `TypeError` jest generowany.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]