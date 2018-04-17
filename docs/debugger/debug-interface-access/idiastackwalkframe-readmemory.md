---
title: IDiaStackWalkFrame::readMemory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9874972bd5d6ec72ecd36e32d4487343fa4c231e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Odczytuje pamięci z obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 [in] Jeden z [memorytypeenum — wyliczenie](../../debugger/debug-interface-access/memorytypeenum.md) wartości wyliczenia, które określa rodzaj pamięci, aby uzyskać dostęp.  
  
 `va`  
 [in] Lokalizacja wirtualnego adresu w obrazie ma rozpocząć się odczyt.  
  
 `cbData`  
 [in] Rozmiar buforu danych w bajtach.  
  
 `pcbData`  
 [out] Zwraca liczbę bajtów zwracanych. Jeśli `data` jest `NULL`, następnie `pcbData` zawiera całkowitą liczbę bajtów dostępnych danych.  
  
 `data`  
 [out] Buforu, który ma zostać wypełniony przy użyciu danych z określonej lokalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)