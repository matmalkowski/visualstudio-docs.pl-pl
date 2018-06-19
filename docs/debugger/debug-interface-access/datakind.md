---
title: Datakind — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3de9ef6128c3cd5ca6eae80a257b3dc2982cd0f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458193"
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