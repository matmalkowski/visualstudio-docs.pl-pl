---
title: Idiastackwalkframe::readmemory — | Dokumentacja firmy Microsoft
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
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e4bad4128ca89cf90ccf1c361bcc6de11d1d8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679205"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiastackwalkframe::readmemory —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkframe-readmemory).  
  
Odczytuje pamięć z obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [in] Jedną z [memorytypeenum — wyliczenie](../../debugger/debug-interface-access/memorytypeenum.md) wartości wyliczenia, które określa rodzaj pamięci, aby uzyskać dostęp.  
  
 `va`  
 [in] Wirtualny adres lokalizacji obrazu ma rozpocząć się odczyt.  
  
 `cbData`  
 [in] Rozmiar buforu danych, w bajtach.  
  
 `pcbData`  
 [out] Zwraca liczbę bajtów zwróconych. Jeśli `data` jest `NULL`, następnie `pcbData` zawiera całkowitą liczbę bajtów dostępnych danych.  
  
 `data`  
 [out] Buforu, który jest wypełniona danymi z określonej lokalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



