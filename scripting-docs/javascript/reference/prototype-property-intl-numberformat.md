---
title: prototype — właściwość (Intl.NumberFormat) | Dokumentacja firmy Microsoft
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b037ce7476574252966e17fcf64246beeaaea1e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791215"
---
# <a name="prototype-property-intlnumberformat"></a>prototype — Właściwość (Intl.NumberFormat)
Zwraca odwołanie do prototypu dla elementu formatującego.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
numberFormat.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `numberFormat` Argument jest nazwą elementu formatującego.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `Intl.NumberFormat` obiektów, która zwraca wartość największego elementu zestawu, zadeklarować funkcję, dodaj go do `Intl.NumberFormat.prototype`, a następnie użyć go.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]