---
title: Idiaframedata::get_allocatesbasepointer — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3259aa3dca2fba1867df11b0b9dea467b7fecf37
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677132"
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiaframedata::get_allocatesbasepointer —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer).  
  
Pobiera flagę wskazującą, czy podstawowy wskaźnik jest przydzielany dla kodu w tym zakresie adresów. Ta metoda jest przestarzała.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` Jeśli podstawowy wskaźnik jest przydzielany; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość powinna być używana tylko przez kod, który poprzednio dostępny FPO_DATA lub gdy zwracany ciąg program przez [idiaframedata::get_program —](../../debugger/debug-interface-access/idiaframedata-get-program.md) metodą jest `NULL`. W przeciwnym razie ciąg program zawiera wszystkie informacje potrzebne do obliczenia poprzedniej wartości rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)



