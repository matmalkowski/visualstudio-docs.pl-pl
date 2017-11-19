---
title: "Właściwości danych lub właściwości metody dostępu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="data-properties-and-accessor-properties"></a>Właściwości danych lub właściwości metody dostępu
Ta sekcja zawiera informacje, które prawdopodobnie będą potrzebne właściwości danych lub właściwości metody dostępu.  
  
### <a name="data-properties"></a>Właściwości danych  
 A *właściwości danych* jest właściwością, który można pobrać i ustawić wartość. Właściwości danych zawierają `value` i `writable` ich deskryptorów właściwości.  
  
 W poniższej tabeli przedstawiono atrybuty dla deskryptora właściwości danych.  
  
|Atrybut deskryptora danych|Opis|Domyślny|  
|-------------------------------|-----------------|-------------|  
|`value`|Bieżąca wartość właściwości.|`undefined`|  
|`writable`|`true`lub `false`. Jeśli `writable` ma ustawioną wartość `true`, można zmodyfikować wartości właściwości.|`false`|  
|`enumerable`|`true`lub `false`. Jeśli `enumerable` ustawiono `true`, właściwości mogą być wyliczane przy `for...in` instrukcji.|`false`|  
|`configurable`|`true`lub `false`. Jeśli `configurable` ma ustawioną wartość `true`, można zmienić właściwości atrybutów i właściwości mogą zostać usunięte.|`false`|  
  
 Jeśli nie ma deskryptora `value`, `writable`, `get`, lub `set` atrybut i określona nazwa właściwości nie istnieje, jest dodawany właściwości danych.  
  
 Gdy `configurable` atrybutu `false` i `writable` jest `true`, `value` i `writable` można zmienić atrybutów.  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>DefineProperty właściwości dodane bez przy użyciu danych  
 Jeśli właściwość danych została dodana bez stosowania `Object.defineProperty`, `Object.defineProperties`, lub `Object.create` funkcje, `writable`, `enumerable`, i `configurable` atrybuty są ustawione `true`. Po dodaniu właściwości można modyfikować go za pomocą `Object.defineProperty` funkcji.  
  
 Można użyć następujących sposoby dodawania właściwości danych:  
  
-   Operator przypisania (=), jak w`obj.color = "white";`  
  
-   Literał, podobnie jak w obiektu`obj = { color: "white", height: 5 };`  
  
-   Funkcja konstrukcji, zgodnie z opisem w [za pomocą konstruktorów do definiowania typów](../../javascript/advanced/using-constructors-to-define-types.md)  
  
### <a name="accessor-properties"></a>Właściwości metody dostępu  
 *Akcesor właściwości* wywołuje funkcję użytkownika zawsze ustawić lub pobrać wartości właściwości. Deskryptor właściwości metody dostępu zawiera `get` atrybutu `set` atrybutu lub jednocześnie.  
  
 W poniższej tabeli przedstawiono atrybuty dla deskryptora właściwości metody dostępu.  
  
|Atrybut deskryptor metody dostępu|Opis|Domyślny|  
|-----------------------------------|-----------------|-------------|  
|`get`|Funkcja, która zwraca wartość właściwości. Funkcja nie ma parametrów.|`undefined`|  
|`set`|Funkcja, która ustawia wartości właściwości. Ma jeden parametr, który zawiera wartość do przypisania.|`undefined`|  
|`enumerable`|`true`lub `false`. Jeśli `enumerable` ustawiono `true`, właściwości mogą być wyliczane przy `for...in` instrukcji.|`false`|  
|`configurable`|`true`lub `false`. Jeśli `configurable` ma ustawioną wartość `true`, można zmienić właściwości atrybutów i właściwości mogą zostać usunięte.|`false`|  
  
 Gdy `get` zdefiniowano metody dostępu i próby uzyskania dostępu do wartości właściwości wartość `undefined` jest zwracany. Gdy `set` zdefiniowano metody dostępu i próby przypisać wartości do właściwości metody dostępu nic się nie dzieje.  
  
### <a name="property-modifications"></a>Zmiany właściwości  
 Jeśli obiekt ma już właściwość o podanej nazwie, atrybuty są modyfikowane. Po zmodyfikowaniu właściwości atrybutów, które nie są określone w deskryptorze pozostają takie same.  
  
 Jeśli `configurable` atrybutu istniejącej właściwości `false`, dozwolone jest zmiana modyfikacji tylko `writable` atrybutu z `true` do `false`.  
  
 Właściwości danych można zmienić właściwości metody dostępu i na odwrót. Jeśli to zrobisz, `configurable` i `enumerable` atrybuty, które nie są określone w deskryptorze zostaną zachowane we właściwości. Inne atrybuty, które nie są określone w deskryptorze są ustawiane na wartości domyślne.  
  
 Przyrostowo można zdefiniować właściwości metody dostępu można skonfigurować przy użyciu wielu wywołań `Object.defineProperty` funkcji. Na przykład jeden `Object.defineProperty` wywołania mogą definiować tylko `get` metody dostępu. Zdefiniować nowsze wywołanie tej samej nazwie właściwości `set` metody dostępu. Właściwość będzie zmuszony zarówno `get` metody dostępu i `set` dostępu.  
  
 Aby uzyskać obiekt deskryptora, która ma zastosowanie do istniejącej właściwości, można użyć [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
 Można użyć [Object.Seal — funkcja](../../javascript/reference/object-seal-function-javascript.md) i [Object.FREEZE — funkcja](../../javascript/reference/object-freeze-function-javascript.md) zapobiegające modyfikacji właściwości atrybutów.