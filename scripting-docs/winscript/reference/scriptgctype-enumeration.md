---
title: Wyliczenie SCRIPTGCTYPE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d42187cc7467bea9d777f35bb208c4e42cabb31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796405"
---
# <a name="scriptgctype-enumeration"></a>Wyliczenie SCRIPTGCTYPE
Typ operacji wyrzucania elementów bezużytecznych do wykonania. Używane w [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|Wyrzucanie elementów bezużytecznych normalnego. Wartość całkowita jest 0.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Wyrzucanie elementów bezużytecznych wyczerpujący. Wartość całkowita jest 1.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kody błędów, wyliczenia i stałe aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)