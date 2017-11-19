---
title: Interfejs IDebugAsyncOperation | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperation-interface"></a>Interfejs IDebugAsyncOperation
Implementuje Menedżera debugowania procesu `IDebugAsyncOperation` interfejsu. Aparat języka wywołuje `IDebugApplication::CreateAsyncDebugOperation` metodę, aby uzyskać odwołania do tego interfejsu. Można używać aparatu języka `IDebugAsyncOperation` interfejs umożliwia asynchroniczne dostęp do operacji synchronicznych debugowania.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugAsyncOperation` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Zwraca operacji synchronicznych debugowania skojarzone z tym obiektem.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Powoduje, że operacja asynchroniczna rozpocząć.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Anuluje operację.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Określa, czy operacja debugowania została ukończona.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Udostępnia wartość zwrotna i parametr obiektu zwracanego przez operację debugowania synchronicznego.|