---
title: IDebugEngine3::LoadSymbols | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::LoadSymbols
helpviewer_keywords: IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad486256b194ae0f03ed3fe41c23a71f2f9159c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Symbole obciążenie (w razie potrzeby) dla wszystkich modułów, które jest debugowane ten aparat debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Spowoduje to załadowanie symboli debugowania dla wszystkich modułów odwołuje się ten aparat debugowania. Załadowano symbole tylko wtedy, gdy ich nie zostały jeszcze załadowane. Symbole są przeszukiwane w ścieżkach ustawiony przez wywołanie do [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Zobacz też  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)