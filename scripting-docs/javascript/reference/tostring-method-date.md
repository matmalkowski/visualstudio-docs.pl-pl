---
title: toString — metoda (Data) | Dokumentacja firmy Microsoft
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791584"
---
# <a name="tostring-method-date"></a>toString — Metoda (Data)
Zwraca reprezentację ciągu daty. Format ciągu zależy od ustawień regionalnych. Dla Stanów Zjednoczonych Angielski (en-us), jest następujący:  
  
 *dzień tygodnia* *miesiąca* *dzień* *godzina*: *minutę*:*drugi* *strefa czasowa* *roku*  
  
## <a name="syntax"></a>Składnia  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>Parametry  
 `date`  
 Wymagany. Data do reprezentowania jako ciąg.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca reprezentację ciągu daty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toString` metody z datą.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]