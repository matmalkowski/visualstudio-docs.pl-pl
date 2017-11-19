---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2434dac0a4f0e4d9ff1c998f0cd70da4f9c558b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Pobiera flagę wskazującą, czy symbol odpowiada *definicji symbolu zakresu* składnika tag zmiennej wskaźnikowej w kodzie skompilowanym dla C++ AMP akceleratora. Symbol zakresu definicji jest lokalizacja zmiennej dla zakresu adresów.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 [out] Wskaźnik do `BOOL` wskazująca, czy symbol odnosi się do definicji symbolu zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)