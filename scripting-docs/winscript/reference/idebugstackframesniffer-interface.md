---
title: Interfejs IDebugStackFrameSniffer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesniffer-interface"></a>Interfejs IDebugStackFrameSniffer
Umożliwia wyliczenie ramek stosu logiczne znane przez składnik. Liczba aparatów skryptów zwykle implementuje ten interfejs. Używa Menedżera debugowania procesu to interfejs, aby znaleźć wszystkie ramki stosu skojarzone z danym wątku.  
  
> [!NOTE]
>  Debuger wywołuje tego interfejsu w wątku zainteresowań. Aparat skryptu musi zidentyfikować bieżącego wątku i zwracać odpowiedniego modułu wyliczającego.  
  
## <a name="methods"></a>Metody  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugStackFrameSniffer` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Zwraca moduł wyliczający ramek stosu dla bieżącego wątku.|