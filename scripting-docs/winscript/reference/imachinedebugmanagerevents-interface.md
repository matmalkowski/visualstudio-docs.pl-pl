---
title: Interfejs IMachineDebugManagerEvents | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagerevents-interface"></a>Interfejs IMachineDebugManagerEvents
Sygnalizuje zmiany w działaniu listy aplikacji przez Menedżera maszyny debugowania. Ten interfejs umożliwia przez debuger IDE wyświetlić listę dynamicznych aplikacji.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IMachineDebugManagerEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Obsługuje zdarzenie po dodaniu aplikacji do uruchamiania liście aplikacji.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Obsługuje zdarzenie, gdy aplikacja zostanie usunięta z uruchomionym listy aplikacji.|