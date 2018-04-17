---
title: IDiaStackFrame::get_rawLVarInstanceValue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69e6fc35d9ac5dcc57ffe136d88069003635fe8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Ta metoda pobiera wartość określonej zmiennej lokalnej raw bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pInstance`  
 [in] `IDiaLVarInstance` Obiekt reprezentujący wystąpienie zmiennej lokalnej można pobrać wartość.  
  
 `cbDataMax`  
 [in] Maksymalna liczba bajtów w buforze wskazywana przez `pbData`. Może to być maksymalnie 8 bajtów (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Zwraca wartość rzeczywistą liczbę bajtów przechowywanych w buforze.  
  
 `pbData`  
 [out] Bufor w celu wprowadzenia danych. Nie może to być `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)