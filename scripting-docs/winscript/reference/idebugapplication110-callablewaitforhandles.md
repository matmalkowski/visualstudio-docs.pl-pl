---
title: IDebugApplication110::CallableWaitForHandles | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b259f5296f8e0b32def793a81e4c2e1069643306
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793759"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Czeka na dowolny określony uchwyt do zasygnalizować zezwalając międzywątkowe do zaksięgowania tego wątku. Ta metoda musi zostać wywołana z wątku debugera.  
  
> [!IMPORTANT]
>  [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) jest implementowany przez PDM v11.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handleCount`  
 Liczba dojść oczekiwania.  
  
 `pHandles`  
 Zestaw uchwyty oczekiwania.  
  
 `pIndex`  
 Gdy ustawiona wartość HRESULT to S_OK, indeks `pHandles` dla dojście zostało sygnalizowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)