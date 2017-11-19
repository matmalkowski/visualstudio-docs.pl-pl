---
title: Metoda IActiveScriptProfilerCallback3::SetWebWorkerId | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>Metoda IActiveScriptProfilerCallback3::SetWebWorkerId
Powiadamia profilera o identyfikatorze procesu roboczego do użycia dla tej sesji profilowania. Jeśli funkcja nie jest wykonywany w kontekście strony, ta metoda nie jest wywoływana. Wartość `webWorkerId` przyrostem 1 w przypadku każdy pracownik rozpoczyna się od 1. Wartości Identyfikatora nie mają być stała poza sesji i odpowiadają ich kolejność, w której utworzono pracowników.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `webWorkerId`  
 Identyfikator procesu roboczego sieci web.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość ta metoda jest ignorowana przez aparat skryptów.