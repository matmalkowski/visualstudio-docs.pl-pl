---
title: IDebugEvent2::GetAttributes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEvent2::GetAttributes
helpviewer_keywords: IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff7b568feb2eddff3d712c494e610fc6b9a6b262
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Pobiera atrybuty dla tego zdarzenia debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```csharp  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwAttrib`  
 [out] Kombinacja flag z [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs jest wspólny dla wszystkich zdarzeń. Ta metoda opisuje typ zdarzenia; na przykład jest zdarzenie synchroniczna lub asynchroniczna i czy jest zdarzeniem zatrzymującym.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)