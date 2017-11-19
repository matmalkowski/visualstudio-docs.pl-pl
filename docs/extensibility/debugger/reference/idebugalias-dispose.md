---
title: IDebugAlias::Dispose | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias::Dispose
helpviewer_keywords: IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10b1e45f9970b2bf331b590f709ef0d8cd15bcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Oznacza ten alias do usunięcia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Dispose();  
```  
  
```csharp  
int Dispose();  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta metoda jest wywoływana, alias nie jest już dostępny.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)