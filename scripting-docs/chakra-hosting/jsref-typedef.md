---
title: "JsRef — Typedef | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsref-typedef"></a>JsRef — Typedef
Odwołanie do obiektu należących do modułu zbierającego elementy bezużyteczne Chakra.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe Chakra automatycznie śledzi odwołania JsRef tak długo, jak długo są przechowywane w zmiennych lokalnych lub parametrów (tj. na stosie). Przechowywanie JsRef innych niż w dowolnym miejscu na stosie wymaga wywoływania jsaddref — oraz jsrelease — Zarządzanie okres istnienia obiektu, w przeciwnym razie moduł garbage collector może zwolnić obiektu, gdy jest on nadal używany.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)