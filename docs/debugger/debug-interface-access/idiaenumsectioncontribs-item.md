---
title: IDiaEnumSectionContribs::Item | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9338d1297263ebd55748f6438bbbec2d4ee4f044
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Pobiera wkładów sekcji za pomocą indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 indeks  
 [in] Indeks o [idiasectioncontrib —](../../debugger/debug-interface-access/idiasectioncontrib.md) obiektu do pobrania. Indeks znajduje się w zakresie od 0 do `count`-1, gdy `count` zwróconego przez [idiaenumsectioncontribs::get_count —](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) metody.  
  
 sekcja  
 [out] Zwraca [idiasectioncontrib —](../../debugger/debug-interface-access/idiasectioncontrib.md) obiekt reprezentujący wkład żądaną sekcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsectioncontribs::get_count —](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [Idiasectioncontrib —](../../debugger/debug-interface-access/idiasectioncontrib.md)