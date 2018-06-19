---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91fc97cafdb3037bb3cca4c93ee874ee329d794c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467291"
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
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)