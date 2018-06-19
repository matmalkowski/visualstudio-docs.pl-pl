---
title: Boolean — obiekt (JavaScript) | Dokumentacja firmy Microsoft
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
- boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789040"
---
# <a name="boolean-object-javascript"></a>Boolean — Obiekt (JavaScript)
Tworzy wartość logiczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>Parametry  
 `boolObj`  
 Wymagany. Nazwa zmiennej, do której `Boolean` obiekt jest przypisany.  
  
 `boolValue`  
 Opcjonalny. Wartość logiczna początkowej dla nowego obiektu. Jeśli `boolvalue` zostanie pominięty lub jest `false`, 0, `null`, `NaN`, lub pusty ciąg, wartość początkowa obiektu logiczna jest `false`. W przeciwnym razie jest to wartość początkowa `true`.  
  
## <a name="remarks"></a>Uwagi  
 `Boolean` Obiekt jest otoki dla typu Boolean. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]niejawnie wykorzystuje `Boolean` obiekt zawsze, gdy typ danych logicznych jest konwertowana na `Boolean` obiektu.  
  
 Rzadko wystąpienia `Boolean` jawnie obiektu.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `Boolean` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[constructor — właściwość](../../javascript/reference/constructor-property-boolean.md)|Określa funkcja, która tworzy wartość typu Boolean.|  
|[prototype — właściwość](../../javascript/reference/prototype-property-boolean.md)|Zwraca odwołanie do prototyp wartość logiczną.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Boolean` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[toString — metoda](../../javascript/reference/tostring-method-boolean-1.md)|Zwraca wartość logiczną reprezentację ciągu.|  
|[valueOf — metoda](../../javascript/reference/valueof-method-boolean.md)|Pobiera odwołanie do typu Boolean.|  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]