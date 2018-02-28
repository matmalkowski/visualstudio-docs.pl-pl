---
title: IDiaStackWalker::getEnumFrames | Dokumentacja firmy Microsoft
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
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 908c6d172a0219d17353701ae13c807f78bc11e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Pobiera moduł wyliczający ramki stosu dla x86 platform.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT getEnumFrames(   
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHelper`  
 [in] Pomocnik [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) obiektu.  
  
 `ppEnum`  
 [out] Zwraca [idiaenumstackframes —](../../debugger/debug-interface-access/idiaenumstackframes.md) obiekt, który zawiera listę [idiastackframe —](../../debugger/debug-interface-access/idiastackframe.md) obiektów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać listę ramek stosu na innych platform, należy wywołać [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiastackwalker —](../../debugger/debug-interface-access/idiastackwalker.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Idiastackframe —](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)