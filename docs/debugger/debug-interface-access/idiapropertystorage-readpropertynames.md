---
title: IDiaPropertyStorage::ReadPropertyNames | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 338d2c4f59eb9023d8a7d8c8618585bb902785f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Pobiera odpowiednie nazwy ciągów dla danego identyfikatory właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cpropid`  
 [in] Liczba identyfikatorów właściwości w `rgpropid`.  
  
 `rgpropid`  
 [in] Tablica identyfikatory właściwości, dla którego można pobrać nazwy (`PROPID` jest zdefiniowany w WTypes.h jako `ULONG`).  
  
 `rglpwstrName`  
 [w, out] Tablica nazw właściwości identyfikatorów określonej właściwości. Tablica musi można wstępnie przydzielić do przechowywania żądaną liczbę nazw właściwości i musi być w stanie co najmniej `cpropid``BSTR` ciągów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Nazwy właściwości zwrócony musi zostać zwolniony (wywołując `SysFreeString` funkcji) po są już potrzebne.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiapropertystorage —](../../debugger/debug-interface-access/idiapropertystorage.md)