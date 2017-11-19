---
title: Interfejs IDebugSessionProviderEx | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionproviderex-interface"></a>Interfejs IDebugSessionProviderEx
Podstawowy interfejs dostarczony przez debuger IDE, aby włączyć debugowanie inicjowane przez hosta i języka. Ustanawia ona sesję debugowania dla działającej aplikacji. Ten interfejs jest implementowany przez Menedżer debugowania komputera.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugSessionProviderEx` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Określa, czy tylko w czasie debugowania jest możliwe za pomocą określonej aplikacji.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Inicjuje sesję debugowania z określonej aplikacji.|