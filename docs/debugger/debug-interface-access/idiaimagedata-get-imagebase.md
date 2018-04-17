---
title: IDiaImageData::get_imageBase | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 032ff3cee51c3c8295395aba6e9e60bfa4e9a400
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Pobiera lokalizacji pamięci, której powinny być oparte obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca obraz sugerowane wartości podstawowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Z powodu konfliktów podstawowej obrazów obraz może można ponownie automatycznie do lokalizacji nieużywanej pamięci po załadowaniu go. Ta metoda zwraca podstawowej wskazówki (lokalizacja zalecany rozmiar pamięci) są przechowywane w module w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)