---
title: IDebugArrayObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject
helpviewer_keywords: IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a447a54fa0fcbc686cee0229c4c8dc6e80eeb20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs reprezentuje obiekt array.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń implementuje ten interfejs do reprezentowania tablicy.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu można uzyskać interfejsu za pomocą [QueryInterface](/cpp/atl/queryinterface) Jeśli obiekt reprezentuje tablicę.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metod na `IDebugObject` interfejsu, następujące metody są implementowane na `IDebugArrayObject` interfejsu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Pobiera liczbę elementów w tablicy.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Pobiera element tablicy.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Pobiera wszystkie elementy tablicy.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Pobiera rangą tablicy.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Pobiera wymiarów tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 Ewaluator wyrażeń używa tego interfejsu do reprezentowania tablic w drzewie analizy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)