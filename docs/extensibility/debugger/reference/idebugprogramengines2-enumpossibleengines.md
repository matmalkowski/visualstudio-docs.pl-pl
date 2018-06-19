---
title: IDebugProgramEngines2::EnumPossibleEngines | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d30eb28398569aa3d14b4a7dd363abac785f352c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116077"
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