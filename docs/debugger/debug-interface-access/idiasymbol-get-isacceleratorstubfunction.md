---
title: IDiaSymbol::get_isAcceleratorStubFunction | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6a7d2f27e776b37c392eb0116425ceeb6916031
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Wskazuje, czy symbol odpowiada symbolem funkcji najwyższego poziomu dla modułu skompilowanego dla akceleratora, który odpowiada `parallel_for_each` wywołania.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 [out] Wskaźnik do `BOOL` wskazująca, czy symbol odpowiada symbolem funkcji najwyższego poziomu dla modułu skompilowanego dla akceleratora, który odpowiada `parallel_for_each` wywołania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)