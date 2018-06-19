---
title: Interfejs IDebugStackFrame | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36fa0ba2d1b4049ad41ff0502ed33be0a706d9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794413"
---
# <a name="idebugstackframe-interface"></a>Interfejs IDebugStackFrame
Reprezentuje ramka stosu logiczne na stosie wątku. Wywołanie `IDebugStackFrame::QueryInterface` metodę, aby uzyskać `IDebugExpressionContext` interfejsu, dzięki czemu wyrażenie oceny i obejrzyj systemu windows.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugStackFrame` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Zwraca bieżący kontekst kodu ramki stosu.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Zwraca opis krótka lub długo tekstową ramki stosu.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Zwraca krótka lub długo tekstowy opis języka.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Zwraca wątek skojarzony z tą ramką stosu.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Zwraca przeglądarką właściwości dla bieżącej ramki.|