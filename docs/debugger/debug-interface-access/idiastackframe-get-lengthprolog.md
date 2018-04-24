---
title: IDiaStackFrame::get_lengthProlog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthProlog method
ms.assetid: 9894c5ca-835f-41e9-a35e-70e046dfb7f0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74c46c4ae4c5400ce94c34c448756cba5e013354
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackframegetlengthprolog"></a>IDiaStackFrame::get_lengthProlog
Pobiera liczbę bajtów prologu kod w bloku.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_lengthProlog (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca liczbę bajtów kodu prologu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)