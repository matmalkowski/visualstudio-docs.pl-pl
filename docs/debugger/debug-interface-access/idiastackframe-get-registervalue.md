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
ms.workload: multiple
ms.openlocfilehash: 5a718ae9dc610494d76b1c950a77b8e939f67860
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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