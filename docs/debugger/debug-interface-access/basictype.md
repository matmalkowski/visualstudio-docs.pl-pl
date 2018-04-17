---
title: Basictype — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df12ce7ff026215e7051142c2cbba47cb82ffc25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="basictype"></a>BasicType
Określa podstawowy typ symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elementy  
 btNoType  
 Nie podstawowe określono typu.  
  
 btVoid  
 Typ podstawowy jest `void`.  
  
 btChar  
 Typ podstawowy jest `char` (C/C++ typu).  
  
 btWChar  
 Typ podstawowy jest znaków dwubajtowych (Unicode) (`WCHAR`).  
  
 btInt  
 Typ podstawowy jest `signed int` (C/C++ typu).  
  
 btUInt  
 Typ podstawowy jest `unsigned int` (C/C++ typu).  
  
 btFloat  
 Typ podstawowy jest liczba zmiennoprzecinkowa (`FLOAT`).  
  
 btBCD  
 Typ podstawowy jest kodowane dane binarne wartości dziesiętnej (`BCD`).  
  
 btBool  
 Typ podstawowy jest wartością logiczną (`BOOL`).  
  
 btLong  
 Typ podstawowy jest `long int` (C/C++ typu).  
  
 btULong  
 Typ podstawowy jest `unsigned long int` (C/C++ typu).  
  
 btCurrency  
 Typ podstawowy jest waluty.  
  
 btDate  
 Typ podstawowy jest daty/godziny (`DATE`).  
  
 btVariant  
 Podstawowy typ jest strukturą typu zmiennej (`VARIANT`).  
  
 btComplex  
 Typ podstawowy jest liczbą.  
  
 btBit  
 Typ podstawowy jest typu bit.  
  
 btBSTR  
 Podstawowy typ to ciąg podstawowego lub binarne (`BSTR`).  
  
 btHresult  
 Typ podstawowy jest `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie wartości są zwracane przez [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)