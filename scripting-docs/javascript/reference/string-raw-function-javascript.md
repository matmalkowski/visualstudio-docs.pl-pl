---
title: String.RAW — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791557"
---
# <a name="stringraw-function-javascript"></a>String.raw — funkcja (JavaScript)
Zwraca ciąg szablonu formę nieprzetworzony ciąg.  
  
## <a name="syntax"></a>Składnia  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>Parametry  
 `templateStr`  
 Wymagany. Ciąg szablonu.  
  
 `obj`  
 Wymagany. Obiekt poprawnie sformułowanym określony przy użyciu notacji literału obiektu, takich jak {raw: "value"}.  
  
 `...substitutions`  
 Opcjonalny. Tablica ( [parametru rest](../../javascript/functions-javascript.md)) składające się z jednego lub więcej wartości zastępcze.  
  
## <a name="remarks"></a>Uwagi  
 `String.raw` Funkcji jest przeznaczony do użycia z [ciągi szablonu](../../javascript/advanced/template-strings-javascript.md). Nieprzetworzony ciąg zawiera znaki specjalne, a ukośników odwrotnych, które znajdują się w ciągu.  
  
 Jeśli zostanie zgłoszony błąd `obj` nie jest poprawnie sformułowanym obiektu.  
  
## <a name="example"></a>Przykład  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]