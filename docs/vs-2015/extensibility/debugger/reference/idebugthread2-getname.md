---
title: IDebugThread2::GetName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8bd570c2610a20c3647e530af2bc7b9f916adbe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632078"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugThread2::GetName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugthread2-getname).  
  
Pobiera nazwę wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrName`  
 [out] Zwraca nazwę wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Pobrana nazwa jest zawsze nazwę, która może być wyświetlany, i tę nazwę w tym artykule opisano wątku. Nazwa wątku mogą pochodzić z architektury środowiska wykonawczego, że obsługuje o nazwie wątków lub może być nazwy pochodzące z aparatu debugowania. Nazwa wątku mogą także ustawić za pomocą wywołania [setthreadname —](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Setthreadname —](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)

