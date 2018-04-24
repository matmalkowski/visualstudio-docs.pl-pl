---
title: THUNK_ORDINAL — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0701706deee68cf2dde522d48f9aa62b9a00142
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Określa typy thunk.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elementy  
 THUNK_ORDINAL_NOTYPE  
 Konwersja standardowa.  
  
 THUNK_ORDINAL_ADJUSTOR  
 A `this` adjustor thunk.  
  
 THUNK_ORDINAL_VCALL  
 Konwersja wirtualnego wywołania.  
  
 THUNK_ORDINAL_PCODE  
 Thunk P-code.  
  
 THUNK_ORDINAL_LOAD  
 Thunk obciążenia opóźnienia.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Thunk przyrostowe trampoline (trampoline thunk służy do Odbijanie wywołania z miejsca w pamięci na inny).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Thunk trampoline punktu gałęzi.  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie wartości są zwracane po wywołaniu [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)