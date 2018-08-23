---
title: IDebugMethodField::GetGlobalContainer | Dokumentacja firmy Microsoft
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
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aec4171c4e1203c8637e0d03bb7c031442813bf8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680600"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugMethodField::GetGlobalContainer](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmethodfield-getglobalcontainer).  
  
Pobiera kontener globalnego metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppClass`  
 [out] Zwraca [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) modułu, w którym zdefiniowano tej metody reprezentująca.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócony [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt reprezentuje cały moduł i jest obiektem sztuczny, oznacza to, że moduł sam nie rzeczywista klasa ale może być reprezentowany przez `IDebugClassField` obiektu, dzięki czemu różne elementy modułu być wyliczone i odnalezione.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

