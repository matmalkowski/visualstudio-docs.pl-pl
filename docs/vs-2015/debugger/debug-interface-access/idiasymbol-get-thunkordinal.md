---
title: Idiasymbol::get_thunkordinal — | Dokumentacja firmy Microsoft
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
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8af5be5e094d01d5015fdd181be6d7348d6ff68
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679902"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasymbol::get_thunkordinal —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-thunkordinal).  
  
Pobiera typ thunk funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca wartość z zakresu od [thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md) wyliczenie, który określa typ thunk funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest prawidłowa tylko wtedy, gdy symbol jako [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartość `SymTagThunk`.  
  
 "thunk" jest fragmentem kodu, który wykonuje konwersję między pamięci 32-bitowej przestrzeni adresowej (znany także jako płaska przestrzeń adresowa) i 16-bitowej przestrzeni adresowej (znanych jako przestrzeń adresową segmenty).  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)



