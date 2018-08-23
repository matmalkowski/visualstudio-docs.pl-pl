---
title: Idiaimagedata::get_imagebase — | Dokumentacja firmy Microsoft
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
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 278ea226c9531cdf16cc7660bb4eba67860430a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682296"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiaimagedata::get_imagebase —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaimagedata-get-imagebase).  
  
Pobiera lokalizację pamięci, gdzie obraz powinien opierać się.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca obraz sugerowane wartości bazowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Z powodu konfliktów podstawowego obrazu obraz może być zmieniona automatycznie lokalizacją nieużywanej pamięci podczas jego ładowania. Ta metoda zwraca podstawowej wskazówki (lokalizacja zalecany rozmiar pamięci) są przechowywane w module w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)



