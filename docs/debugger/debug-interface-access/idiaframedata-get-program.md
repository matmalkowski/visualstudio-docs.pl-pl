---
title: IDiaFrameData::get_program | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc770db5f5cf16d9870e05ada01e235206b94078
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Pobiera ciąg program, który jest używany do obliczania rejestru ustawić przed wywołaniem do bieżącej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca ciąg program.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ciąg program jest sekwencję makra jest interpretowana w celu ustanowienia prologu. Na przykład ramka stosu typowe może użyć ciągu program `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Format jest Polski odwrotnej notacji, gdzie operatory wykonaj argumenty operacji. `T0` reprezentuje zmiennej tymczasowej na stosie. W tym przykładzie wykonuje następujące czynności:  
  
1.  Przenieś zawartość rejestru `ebp` do `T0`.  
  
2.  Dodaj `4` wartość `T0` do utworzenia adresu, pobrać wartości z tego adresu i przechowywać wartość rejestru `eip`.  
  
3.  Pobiera wartość z adresu przechowywane w `T0` i Zapisz tę wartość rejestru `ebp`.  
  
4.  Dodaj `8` wartość `T0` i Zapisz tę wartość rejestru `esp`.  
  
 Należy pamiętać, że program ciągu określonego procesora CPU i Konwencja wywoływania dla funkcji reprezentowany przez bieżącej ramki stosu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)