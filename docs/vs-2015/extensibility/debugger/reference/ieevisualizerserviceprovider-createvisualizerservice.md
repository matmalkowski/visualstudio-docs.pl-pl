---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Dokumentacja firmy Microsoft
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
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cf31da1dab9e53a1c473ee8024a7fe1cb9a5f2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681619"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEEVisualizerServiceProvider::CreateVisualizerService](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice).  
  
Ta metoda tworzy usługę wizualizatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `binder`  
 [in] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obiekt przekazany do [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) obiekt przekazany do `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiekt przekazany do `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Implementowanie obiektu [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfejsu (dostarczonych przez ewaluatora wyrażeń).  
  
 `ppService`  
 [out] Utworzono usługę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `binder`, `pSymProv`, I `pAddress` parametry zostały przekazane do `IDebugParsedExpression::EvaluateSync` metody. `CreateVisualizerService` jest wywoływane tylko z `IDebugParsedExpression::EvaluateSync` jako część ewaluatora wyrażeń obsługę wizualizatorów typu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

