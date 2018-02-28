---
title: Obiekt JSON (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JSON object
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5310132368f665c6734c469a67636d33a08858d4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="json-object-javascript"></a>Obiekt JSON (JavaScript)
Obiekt wewnętrzny zapewniająca funkcje, aby przekonwertować [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wartości do i z formatu JavaScript Object Notation (JSON). `JSON.stringify` Serializuje funkcja [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wartość na tekst w formacie JSON. `JSON.parse` Funkcja deserializuje tekst JSON w celu utworzenia [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
JSON.[method]  
  
```  
  
## <a name="parameters"></a>Parametry  
 `Method`  
 Wymagany. Nazwa metody `JSON` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Nie można utworzyć `JSON` obiektu przy użyciu `new` operatora. Podjęcie takiej próby spowoduje wystąpienie błędu. Jednak można zastąpić lub zmodyfikować `JSON` obiektu.  
  
 Tworzy aparat skryptów `JSON` obiektu po załadowaniu przez aparat. Jego metody są zawsze dostępne dla skryptu.  
  
 Aby użyć wewnętrznego `JSON` obiektów, upewnij się, że możesz nie zastępuj ją z inną `JSON` obiekt, który jest zdefiniowany w skrypcie. Może być konieczne, zmodyfikuj istniejące instrukcje skryptu, które wykrywania obecności `JSON` obiektu, ponieważ te instrukcje będą oceniać inaczej. Jest to zaprezentowane w poniższym przykładzie.  
  
```JavaScript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 W poprzednim przykładzie `!this.JSON` daje w wyniku wartość false w [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)]. W związku z tym kodu wewnątrz `if` nie wykonuje instrukcję.  
  
## <a name="functions"></a>Funkcje  
 [JSON.Parse — funkcja](../../javascript/reference/json-parse-function-javascript.md)  
  
 [Funkcja JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toJSON — metoda (Data)](../../javascript/reference/tojson-method-date-javascript.md)   
 [JavaScript — obiekty](../../javascript/reference/javascript-objects.md)   
 [Koncentrator szablonu przykładowej aplikacji (w Sklepie Windows)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)