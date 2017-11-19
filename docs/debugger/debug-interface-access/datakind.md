---
title: "Datakind — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e9ffa36facb3c7f64f7eb2c0b96ef5209f70c78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="datakind"></a>DataKind
Wskazuje określonego zakresu wartości danych.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elementy  
 DataIsUnknown  
 Nie można określić symbolu danych.  
  
 DataIsLocal  
 Element danych jest zmienną lokalną.  
  
 DataIsStaticLocal  
 Element danych jest statyczna zmienna lokalna.  
  
 DataIsParam  
 Element danych jest parametrów formalnych.  
  
 DataIsObjectPtr  
 Element danych jest wskaźnik do obiektu (`this`).  
  
 DataIsFileStatic  
 Element danych jest zmienną zakresu pliku.  
  
 DataIsGlobal  
 Element danych jest zmienną globalną.  
  
 DataIsMember  
 Element danych jest zmienna obiektu elementu członkowskiego.  
  
 DataIsStaticMember  
 Element danych jest zmienną statyczną klasy.  
  
 DataIsConstant  
 Element danych jest wartością stałą.  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie wartości są zwracane przez [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)