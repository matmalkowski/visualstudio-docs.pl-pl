---
title: IDiaTable::Item | Dokumentacja firmy Microsoft
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
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 12d04da8ea2c2a136b61924578fcb925b17fc12f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiatableitem"></a>IDiaTable::Item
Pobiera odwołanie do określonego wpisu w tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 [in] Indeks wpisu tabeli w zakresie od 0 do `count`-1, gdzie `count` zwróconego przez [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)metody.  
  
 `element`  
 [out] Zwraca `IUnknown` obiekt, który reprezentuje wpis określonej tabeli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tabela reprezentuje kolekcję obiektów. W zależności od tych obiektów parametru elementu mogą być rzutowane na odpowiedniego interfejsu. Na przykład, jeśli tabela zawiera [idiasegment —](../../debugger/debug-interface-access/idiasegment.md) obiektów, a następnie parametru elementu mogą być rzutowane na `IDiaSegment` interfejsu.  
  
 Jest bardziej popularne podejście do wywołania `QueryInterface` metody w [idiatable —](../../debugger/debug-interface-access/idiatable.md) interfejsu dla interfejsu odpowiedniego modułu wyliczającego i użycia modułu wyliczającego określonych metod dostępu do zawartości tabeli. Zobacz [idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfejsu, na przykład.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiatable —](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [Idiasegment —](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)