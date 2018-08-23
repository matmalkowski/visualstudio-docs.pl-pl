---
title: Idiatable::Item — | Dokumentacja firmy Microsoft
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
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ad4b51a125af1f08d8766c4c34a2bdd0c54ff64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685375"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiatable::Item —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiatable-item).  
  
Pobiera odwołanie do określonego wpisu w tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 [in] Indeks wpisu tabeli z zakresu od 0 do `count`-1, gdzie `count` jest zwracany przez [idiatable::get_count —](../../debugger/debug-interface-access/idiatable-get-count.md)metody.  
  
 `element`  
 [out] Zwraca `IUnknown` obiekt, który reprezentuje wpis określonej tabeli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tabela reprezentuje kolekcję obiektów. W zależności od tych obiektów parametru elementu mogą być rzutowane na odpowiedni interfejs. Na przykład, jeśli tabela zawiera [idiasegment —](../../debugger/debug-interface-access/idiasegment.md) obiektów, a następnie można rzutować parametru elementu `IDiaSegment` interfejsu.  
  
 Jest bardziej powszechne podejście do wywołania `QueryInterface` method in Class metoda [idiatable —](../../debugger/debug-interface-access/idiatable.md) interfejsu dla interfejsu odpowiedniego modułu wyliczającego i umożliwia dostęp do treści modułu wyliczającego konkretnych metod. Zobacz [idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfejsu, na przykład.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiatable —](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable::get_count —](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [Idiasegment —](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



