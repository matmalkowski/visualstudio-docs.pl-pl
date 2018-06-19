---
title: Interfejs IDebugSyncOperation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6705c2aa990aef3cf551a94546bf78a64026cecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794257"
---
# <a name="idebugsyncoperation-interface"></a>Interfejs IDebugSyncOperation
Udostępnia aparat skryptu abstrakcyjnej operację (na przykład Obliczanie wyrażenia), która musi zostać wykonana podczas zagnieżdżona w szczególności wątku zablokowanych. Interfejs zawiera również mechanizm Trwa anulowanie operacji nie odpowiada.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugSyncOperation` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Zwraca wątku aplikacji docelowej dla tej operacji synchronicznych.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Synchronicznie wykonuje operację i zwraca.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Anuluje operację w toku w innym wątku.|