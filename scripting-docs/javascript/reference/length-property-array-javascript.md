---
title: length — właściwość (tablica) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- Length property
- length property (array)
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e69fd5387b1d7430491b1693dec07581f165cc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790885"
---
# <a name="length-property-array-javascript"></a>length — Właściwość (Tablica) (JavaScript)
Pobiera lub ustawia długość tablicy. To jest numer wyższy niż najwyższy element zdefiniowany w tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
numVar = arrayObj.length   
```  
  
## <a name="parameters"></a>Parametry  
 `numVar`  
 Wymagany. Dowolna liczba.  
  
 `arrayObj`  
 Wymagany. Wszelkie `Array` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 W języku JavaScript tablice są rozrzedzonych i elementów w tablicy musi być ciągłe. `length` Właściwość nie jest zawsze liczba elementów w tablicy. Na przykład w następującej definicji tablicy `my_array.length` zawiera 7 nie 2:  
  
```JavaScript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Jeśli wprowadzisz `length` mniejszy niż poprzednia wartość właściwości, tablicy został obcięty, a wszelkie elementy z tablicy indeksów równa lub większa niż wartość nowego `length` właściwości zostaną utracone.  
  
 Jeśli właściwość długość dokonać większa niż poprzednia wartość, tablicy jest rozwinięta i wszelkie nowe elementy utworzone ma wartość `undefined`.  
  
 Poniższy przykład przedstawia użycie `length` właściwości:  
  
```JavaScript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  Począwszy od tryb standardów programu Internet Explorer 9, przecinki końcowe uwzględnione podczas inicjowania tablicy są obsługiwane inaczej.