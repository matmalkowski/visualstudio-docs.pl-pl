---
title: Normalizuj — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791131"
---
# <a name="normalize-method-string-javascript"></a>Normalizuj — metoda (ciąg) (JavaScript)
Zwraca forma normalizacji Unicode określonego ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. Obiekt ciągu do przetestowania.  
  
 `form`  
 Opcjonalny. Wartość forma normalizacji Unicode.  
  
## <a name="return-value"></a>Wartość zwracana  
 Forma normalizacji Unicode określonego ciągu.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `form` jest nieobsługiwana wartość `RangeError` jest generowany.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `stringObj` nie jest ciągiem, zostanie przekonwertowany na ciąg przed metoda próbuje zwrócić forma normalizacji Unicode ciągu.  
  
 `form`musi być wartością forma normalizacji Unicode "NFC", "NFD", "NFKC" lub "NFKD", odpowiadający wartości określone dla [Unicode standardowe załącznika 15](http://www.unicode.org/reports/tr15/). Wartość domyślna `form` jest "NFC".  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach kodu pokazano stosowania `normalize` metody.  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]