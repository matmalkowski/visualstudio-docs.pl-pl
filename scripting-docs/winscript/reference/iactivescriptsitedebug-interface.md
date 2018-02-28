---
title: Interfejs IActiveScriptSiteDebug | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug-interface"></a>Interfejs IActiveScriptSiteDebug
Wdrożenie hostów inteligentnych `IActiveScriptSiteDebug` interfejsu, aby przeprowadzić Zarządzanie dokumentami i brać udziału w debugowaniu. `IActiveScriptSite` Obiektu zwykle zapewnia implementacja `IActiveScriptSiteDebug` interfejsu. Jeśli zostanie to zrobione, należy wywołać `IActiveScriptSite::QueryInterface` metodę, aby uzyskać `IActiveScriptSiteDebug` interfejsu.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IActiveScriptSiteDebug` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Używane przez aparat języka Aby delegować `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Zwraca obiekt aplikacji debugowania skojarzonych z tą lokacją skryptu.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Pobiera węzeł aplikacji w obszarze skryptu, który ma zostać dodany dokumentów.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Umożliwia host inteligentny do określenia sposobu obsługi błędów czasu wykonywania.|