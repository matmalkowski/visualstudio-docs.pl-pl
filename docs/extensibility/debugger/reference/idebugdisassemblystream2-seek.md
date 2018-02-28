---
title: IDebugDisassemblyStream2::Seek | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2725eb876cf66665c27027dd4d9b250ed7e866e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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