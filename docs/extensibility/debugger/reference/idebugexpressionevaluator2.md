---
title: IDebugExpressionEvaluator2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b4fc704475c35e9fcd07bba260eb3de9626fe2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Reprezentuje rozbudowaną wersją ewaluatora wyrażeń (EE).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez ewaluatora wyrażeń.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfejsu, tego interfejsu implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Funkcja GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Pobiera obiekt usługi na podstawie jego unikatowy identyfikator.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Wstępnie ładuje moduły wskazywany przez dostawcę określony symbol.|  
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Umożliwia ewaluatora wyrażenia (EE) określić interfejs wywołania zwrotnego, który aparat debugera (DE) będzie używany do odczytu ustawień metryki.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Ustawia ścieżkę do środowisko uruchomieniowe języka wspólnego (CLR) załadowane w debugerze.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Umożliwia to aparat debugowania do przekazania wywołanie zwrotne do ewaluatora wyrażeń podczas inicjowania.|  
|[Zakończenie](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Zatrzymuje i czyści ewaluatora wyrażenia.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll