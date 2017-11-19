---
title: IDiaStackFrame::get_registerValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a454beb98fc8579bf625dbdb64db1cf60f8dd50a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Pobiera wartość określonego rejestru zapisane w ramce stosu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `registerIndex`  
 [in] Jeden z [cv_hreg_e — wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md) wartości wyliczenia.  
  
 `pRetVal`  
 [out] Wartość przechowywana w rejestrze.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiastackframe —](../../debugger/debug-interface-access/idiastackframe.md)   
 [Cv_hreg_e — wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md)