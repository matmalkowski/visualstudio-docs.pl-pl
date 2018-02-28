---
title: Interfejs IDebugStackFrameSnifferEx | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferex-interface"></a>Interfejs IDebugStackFrameSnifferEx
Umożliwia wyliczenie ramek stosu logiczne znane przez składnik. Liczba aparatów skryptów zwykle implementuje ten interfejs. Używa Menedżera debugowania procesu to interfejs, aby znaleźć wszystkie ramki stosu skojarzone z danym wątku.  
  
> [!NOTE]
>  Ten interfejs jest wywoływana z w wątku zainteresowań. Implementacja interfejsu musi zidentyfikować bieżącego wątku i zwracać odpowiedniego modułu wyliczającego.  
  
 Oprócz dziedziczone z metody `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Zwraca moduł wyliczający ramek stosu dla bieżącego wątku.|