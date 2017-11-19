---
title: IDiaStackWalkFrame::put_registerValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkFrame::put_registerValue method
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f04710993efc9c1b0d0508a428c55013208f13a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkframeputregistervalue"></a>IDiaStackWalkFrame::put_registerValue
Ustawia wartość rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 [in] Wartość z zakresu od [cv_hreg_e — wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md) wyliczenie opisujące rejestru do zapisu.  
  
 `NewVal`  
 [in] Nowa wartość rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiastackwalkframe —](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [Cv_hreg_e — wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md)