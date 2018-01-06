---
title: IDiaLoadCallback::RestrictSymbolServerAccess | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 05c79edf44b9a853917ade19d1616219ae2c1308
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Określa, czy jest dozwolony dostęp do serwera symboli do rozpoznawania symboli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT RestrictSymbolServerAccess();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Inne niż powrotnych kodu `S_OK` uniemożliwia korzystanie z serwera symboli w celu rozpoznania symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)