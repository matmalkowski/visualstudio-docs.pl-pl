---
title: IDebugDisassemblyStream2::Seek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55a8c2c205627130e8dd6dd28f288b2d3dee9d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Przesuwa kursor odczytu w strumieniu dezasemblacji daną liczbę instrukcji względem określonej pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSeekStart`  
 [in] Wartość z zakresu od [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) wyliczenia, która określa względne położenie, aby rozpocząć proces wyszukiwania.  
  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt reprezentujący kontekst kodu, będącą względem operacji wyszukiwania. Ten parametr jest używany tylko wtedy, gdy `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; w przeciwnym razie ten parametr jest ignorowany i może być wartością null.  
  
 `uCodeLocationId`  
 [in] Identyfikator lokalizacji kod operacji wyszukiwania jest względem. Ten parametr jest używany, jeśli `dwSeekStart`  =  `SEEK_START_CODELOCID`; w przeciwnym razie ten parametr jest ignorowany i może być równa 0. W sekcji uwag [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) metody opis identyfikator lokalizacji kodu.  
  
 `iInstructions`  
 [in] Liczbę instrukcji, aby przenieść względem pozycja określona w `dwSeekStart`. Ta wartość może być ujemna, aby ruch do tyłu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli pozycji wyszukiwania do punktu poza listy dostępnych instrukcji. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli do pozycji przed początek listy wyszukiwania, pozycja odczytu wynosi pierwszej instrukcji na liście. Jeśli Zobacz do pozycji na końcu listy, pozycja odczytu jest ustawiona na ostatni instrukcji na liście.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)