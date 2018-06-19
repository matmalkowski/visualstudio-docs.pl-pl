---
title: findIndex — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8da475b776e1c04e4fe5bfc7062318cfec952c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790483"
---
# <a name="findindex-method-array-javascript"></a>findIndex (Array) — metoda (JavaScript)
Zwraca wartość indeksu pierwszego elementu tablicy, czy spełnia testu kryteria określone w funkcji wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. Obiekt array.  
  
 `callbackfn`  
 Wymagany. Funkcja wywołania zwrotnego do testowania każdego elementu w tablicy.  
  
 `thisArg`  
 Opcjonalny. Określa `this` obiektu w funkcji wywołania zwrotnego. Jeśli nie zostanie określony, `this` obiektu jest zdefiniowana.  
  
## <a name="remarks"></a>Uwagi  
 `findIndex` Wywołuje funkcję wywołania zwrotnego jeden raz dla każdego elementu w tablicy, w kolejności rosnącej, dopóki nie zwraca element `true`. Jak element zwraca wartość true, `findIndex` zwraca wartość indeksu elementu, który zwraca wartość true. Jeśli zwróci wartość true, nie elementów w tablicy `findIndex` zwraca wartość -1.  
  
 `findIndex`nie zmodyfikować obiekt array.  
  
## <a name="callback-function-syntax"></a>Składnia funkcji wywołania zwrotnego  
 Składnia funkcji wywołania zwrotnego jest następująca:  
  
 `function callbackfn(value, index, thisArg)`  
  
 Funkcję wywołania zwrotnego można zadeklarować przy użyciu maksymalnie trzech parametrów.  
  
 Parametry funkcji wywołania zwrotnego są następujące.  
  
|Argument wywołania zwrotnego|Definicja|  
|-----------------------|----------------|  
|`value`|Wartość elementu tablicy.|  
|`index`|Indeks liczbowy elementu tablicy.|  
|`arrayObj`|Obiekt tablicy można przechodzić.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie funkcja wywołania zwrotnego sprawdza, czy każdy element tablicy jest równa 2.  
  
```JavaScript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto składni strzałkę do testowania każdego elementu. W tym przykładzie zwróci żadnych elementów `true`, i `findIndex` zwraca wartość -1.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.   
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]