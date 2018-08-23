---
title: IDiaSymbol::get_isAcceleratorStubFunction | Dokumentacja firmy Microsoft
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
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 524c2abd38583af867e6c2be0f2e25cf0b4b80ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678364"
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDiaSymbol::get_isAcceleratorStubFunction](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction).  
  
Wskazuje, czy symbol odpowiada symbolowi funkcji najwyższego poziomu do programu do cieniowania, skompilowane dla akceleratora, który odpowiada `parallel_for_each` wywołania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 [out] Wskaźnik do `BOOL` oznacza to, czy symbol odpowiada symbolowi funkcji najwyższego poziomu do programu do cieniowania, skompilowane dla akceleratora, który odpowiada `parallel_for_each` wywołania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



