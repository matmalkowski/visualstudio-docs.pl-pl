---
title: "Etykietą — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="labeled-statement-javascript"></a>Instrukcja Labeled (JavaScript)
Zawiera identyfikator dla instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>Parametry  
 *etykiety*  
 Wymagany. Unikatowy identyfikator używany podczas odwoływania się do instrukcji etykietą.  
  
 `statements`  
 Opcjonalny. Co najmniej jeden oświadczeniami o *etykiety*.  
  
## <a name="remarks"></a>Uwagi  
 Etykiety są używane przez **podziału** i **kontynuować** instrukcje, aby określić instrukcji, do którego **podziału** i **kontynuować** zastosowania.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie **kontynuować** odwołuje się do **dla** pętli, które jest poprzedzony `Inner:` instrukcji. Gdy `j` to 24, **kontynuować** instrukcja powoduje, że **dla** przejdź do następnej iteracji pętli. Numery 21 do 23 i 25 do 30 wydruku w każdym wierszu.  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcja BREAK](../../javascript/reference/break-statement-javascript.md)   
 [Continue — instrukcja](../../javascript/reference/continue-statement-javascript.md)