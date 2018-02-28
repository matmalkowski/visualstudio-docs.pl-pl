---
title: IDiaLineNumber::get_columnNumberEnd | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 04894f9ef6d1779b5e27c2552b5ea05d84649a2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Pobiera numer kolumny na podstawie jednego źródła, gdy kończy się wyrażenia lub instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca numer kolumny, w którym kończy się wyrażenia lub instrukcji. Jeśli wartość wynosi zero, informacji o kolumnie końcowy nie jest obecny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość kolumny zwracane przez tę metodę jest bajt przesunięcie do wiersza do położenia za ostatni znak instrukcją w wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)