---
title: Interfejs IPerPropertyBrowsing2 1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2-interface-1"></a>Interfejs IPerPropertyBrowsing2 1
Uzyskuje dostęp do informacji na stronach właściwości oferowane przez obiekt.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|`GetDisplayString`|Zwraca ciąg tekstowy opisujące określonej właściwości.|  
|`MapPropertyToPage`|Zwraca identyfikator CLSID strony właściwości, która umożliwia modyfikowanie określonej właściwości.|  
|`GetPredefinedStrings`|Zwraca tablicę zliczona ciągów (`LPOLESTR` wskaźniki) wyświetlanie opisów dopuszczalne wartości akceptujących określonej właściwości.|  
|`SetPredefinedValue`|Ustawia wartości właściwości do wstępnie zdefiniowanych wartości identyfikowana na podstawie tokenu`dwCookie.`|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop.h