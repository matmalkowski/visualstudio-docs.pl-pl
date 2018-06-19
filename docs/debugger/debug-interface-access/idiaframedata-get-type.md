---
title: IDiaFrameData::get_type | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b95262fb5cc9afce25e9f4120b981543939e5be
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460443"
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Pobiera typ ramki specyficznych dla kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca wartość z zakresu od [stackframetypeenum — wyliczenie](../../debugger/debug-interface-access/stackframetypeenum.md) wyliczenia wskazująca typ ramki specyficznych dla kompilatora.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)   
 [Stackframetypeenum — wyliczenie](../../debugger/debug-interface-access/stackframetypeenum.md)