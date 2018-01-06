---
title: IDebugExpressionEvaluator3 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c067875853a63bc1f861d93e8d70a15dcf3114df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Reprezentuje ewaluatora wyrażeń (EE) z drzewo rozszerzone analizatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2  
```  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ta wersja analizatora przekazuje symbol dostawcy i adres oszacowania ramki.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interfejsu, tego interfejsu implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Konwertuje ciąg wyrażenia wyrażenia przeanalizowanego danego dostawcy symboli i adres oszacowania ramki.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll