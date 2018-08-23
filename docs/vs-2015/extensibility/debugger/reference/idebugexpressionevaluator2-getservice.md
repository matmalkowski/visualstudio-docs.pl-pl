---
title: IDebugExpressionEvaluator2::GetService | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e8ef02bee0f716194f1d37d619f070e00ecadbe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676860"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugExpressionEvaluator2::GetService](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluator2-getservice).  
  
Pobiera obiekt usługi, na podstawie jego unikatowy identyfikator.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `uid`  
 [in] Unikatowy identyfikator usługi do pobrania.  
  
 `ppService`  
 [out] Zwraca obiekt, który reprezentuje usługę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 To mogą być używane przez ewaluatora wyrażeń innych firm, można uzyskać usługi z innego Ewaluator wyrażeń. Na przykład tej metody może służyć do uzyskiwania interfejsu usługi Wizualizator z domyślną Ewaluator wyrażeń. Ewaluatory wyrażeń firm prawdopodobnie nie trzeba implementować ten interfejs.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)

