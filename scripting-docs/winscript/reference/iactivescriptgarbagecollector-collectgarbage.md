---
title: IActiveScriptGarbageCollector::CollectGarbage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07d5a00e04939331f85c4c74727aaf03b62814fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793312"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Host skryptów aktywnych wywołuje tę metodę, aby uruchomić odzyskiwanie pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptgctype`  
 [in] [Wyliczenie SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) Określa, czy do normalnej lub wyczerpujący wyrzucania elementów bezużytecznych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptGarbageCollector](../../winscript/reference/iactivescriptgarbagecollector-interface.md)