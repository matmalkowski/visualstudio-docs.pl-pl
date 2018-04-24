---
title: IDiaStackWalkHelper::symbolForVA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e70dac639f18f934bb997cc4979bdbe6a7d8c4c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Pobiera symbol, który zawiera określony wirtualny adres.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `va`  
 [in] Wirtualny adres jest zawarty w żądanej symbolu. Musi być `SymTagFunctionType` (wartość z zakresu od [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wyliczenie).  
  
 `ppSymbol`  
 [out] [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt reprezentujący symbol pod określonym adresem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)