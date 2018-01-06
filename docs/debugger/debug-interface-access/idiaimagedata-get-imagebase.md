---
title: IDiaImageData::get_imageBase | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5e3730e7bc543d0b7bdea18e162dfe83e1d803bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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