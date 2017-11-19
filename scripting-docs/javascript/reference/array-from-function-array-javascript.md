---
title: Funkcja Array.from (Array) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a240cb439942bfeb6b4c9a1febb4d24cef1c5c18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="arrayfrom-function-array-javascript"></a>Array.from (Array) — funkcja (JavaScript)
Zwraca tablicę z tablicy lub iterable obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `arrayLike`  
 Wymagany. Tablicy lub iterable obiektu.  
  
 `mapfn`  
 Opcjonalny. Mapowanie funkcji, aby wywołać dla każdego elementu w `arrayLike`.  
  
 `thisArg`  
 Opcjonalny. Określa `this` obiektu w funkcji mapowania.  
  
## <a name="remarks"></a>Uwagi  
 `arrayLike` Parametr musi być obiekt z elementami indeksowane i `length` właściwość lub obiekt iterable, takich jak `Set` obiektu.  
  
 Wywołania funkcji opcjonalnych mapowania dla każdego elementu w tablicy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca tablicę z kolekcji węzły elementów modelu DOM.  
  
```JavaScript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca tablicę znaków.  
  
```JavaScript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca tablicę obiektów zawartych w kolekcji.  
  
```JavaScript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";   
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono użycie składni strzałkę i mapowanie funkcji, aby zmienić wartości elementów.  
  
```JavaScript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]