---
title: IDebugProcessQueryProperties | Dokumentacja firmy Microsoft
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
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 542933f414e4ca95da181d26d2cc49c582e553c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42672245"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugProcessQueryProperties](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessqueryproperties).  
  
Ten interfejs jest implementowany przez interfejs rozszerzenia [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) implementacje. Umożliwia ona implementujący można pobrać informacji na temat środowiska debugowania procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Implementuje ten interfejs, aby uzyskać informacje o środowisku wykonawczym debugowania procesu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProcessQueryProperties`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Zapytania dotyczące wartości właściwości.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Zapytania dotyczące wartości właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs rzadko jest zaimplementowana.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

