---
title: IDiaEnumSectionContribs::Next | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4580c677fa5d6757e1fffb28cdc021a3be1e5a58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Pobiera określoną liczbę sekcji wkładów w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba sekcji wkładów w moduł wyliczający, które mają zostać pobrane.  
  
 rgelt  
 [out] Tablica, która ma zostać wypełnione [idiasectioncontrib —](../../debugger/debug-interface-access/idiasectioncontrib.md) obiekty reprezentujące wkładów żądaną sekcji.  
  
 pceltFetched  
 [out] Zwraca liczbę sekcji wkładów w pobranych modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej wkładów sekcji. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsectioncontribs —](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)