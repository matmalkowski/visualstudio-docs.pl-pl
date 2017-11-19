---
title: IDebugProgramEngines2::EnumPossibleEngines | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords: IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1cf3eead4b268dbbca5ad4333adcc647522b051
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Zwraca identyfikatory GUID dla wszystkich możliwych aparatami debugowania (DE), które można debugować ten program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celtBuffer`  
 [in] Liczba identyfikatorów GUID DE do zwrócenia. Maksymalny rozmiar określa również `rgguidEngines` tablicy.  
  
 `rgguidEngines`  
 [w, out] Tablica identyfikatorów GUID DE zostać wypełnione.  
  
 `pceltEngines`  
 [out] Zwraca aktualną liczbę identyfikatorów GUID DE, którego są zwracane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` lub [C#] 0x8007007A, jeśli bufor nie jest wystarczająco duży.  
  
## <a name="remarks"></a>Uwagi  
 Aby ustalić, ile aparaty są, wywołania tej metody jeden raz z `celtBuffer` parametru równa 0 i `rgguidEngines` ustawionym na wartość null. To polecenie zwróci `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A dla C#) i `pceltEngines` parametr zwraca niezbędne rozmiar buforu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)