---
title: IDebugProgram2::EnumCodePaths | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::EnumCodePaths
helpviewer_keywords: IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c9e87e3435f5902e277a2c80c68ab2dab891bd38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Pobiera listę ścieżki kodu dla danej pozycji w pliku źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszHint`  
 [in] Word pod kursorem w **źródła** lub **dezasemblacji** widoku w IDE.  
  
 `pStart`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt reprezentujący bieżący kontekst kodu.  
  
 `pFrame`  
 [in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obiekt reprezentujący ramki stosu skojarzone z bieżącym punktu przerwania.  
  
 `fSource`  
 [in] Różna od zera (`TRUE`) Jeśli w **źródła** widoku lub zero (`FALSE`) Jeśli w **dezasemblacji** widoku.  
  
 `ppEnum`  
 [out] Zwraca [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) obiektu zawierającego listę ścieżki kodu.  
  
 `ppSafety`  
 [out] Zwraca [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiektów reprezentującą kontekst dodatkowy kod ma być ustawiona jako punkt przerwania, w przypadku, gdy wybrana kodu ścieżka zostanie pominięta. Może to nastąpić w przypadku zwartym wyrażenie logiczne, np.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ścieżka kodu opisuje nazwę metody lub funkcji, która została wywołana na uzyskanie dostępu do bieżącego punktu podczas wykonywania programu. Lista ścieżek kodu reprezentuje stosu wywołań.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)